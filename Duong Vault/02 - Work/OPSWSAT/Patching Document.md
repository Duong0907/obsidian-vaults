
---

<aside>
💡 Mục đích của Part này là support 2 method là `GetLatestInstaller` và `InstallFromFiles`

</aside>

## Hướng dẫn

- Traing by anh Thịnh [tại đây](https://opswat2017-my.sharepoint.com/:t:/g/personal/thinh_truong_opswat_com/ESXO4KpLmP5FozngEUnliCgBf9kUSN_BF2WCoGw3na6M_g?e=Zb1Yod)
- Document [tại đây](https://opswat.atlassian.net/wiki/spaces/OES/pages/3106603970/PART+2+-+Patching)

## Cách hoạt động

Chúng ta sẽ viết script để collect dữ liệu boa gồm download link của version mới nhất của product, … từ internet, sau đó hệ thống sẽ chạy lệnh để download và install ở chế độ chạy ngầm (không hiện bất cứ pop up nào)

## Defenition of Done

- Tạo script chạy đúng (trả về patch đúng)
- Add một item vào patch associations
- Test chạy đúng

## Quy trình

Bước 1: Lấy Patch ID và Patch Assocication ID 

- Vào [đây](https://opswat.atlassian.net/wiki/spaces/OES/pages/2238350492/Maximum+IDs) để lấy
- ID cần lấy = max ID + 1

Bước 2: Tạo script lấy thông tin patching

- Tạo file với format `<patch_id>_<product_name>.rb` trong folder `fv-vcrom\patching\collect_installers\`
- JSON trả về có dạng

```jsx
{
  "_id": <patch_id>,
  "type_id": 1, // need to clarify
  "v4_pid": <product_id>,
  "v4_vid": <vendor_id>,
  "feed_id": <feed_id>,
  "os_type": <os_type>,
  "patch_info": {
    "pub_keys": <leaf_cert_public_keys>,
	"cert_paths": <cert_chain>,
    "exe": { // this key name depends on the file extension of the installer, can be zip, exe, msi
      "type_id": 1, // need to clarify
      "download_info": {
        "type_id": 1, // 1 or 3, see definitions in fv-win-vmod - wa_vmod_utils_auto_patch.h
        "language_map": null,
        "arch_map": null,
        "os_id": null,
        "link_patterns": [
          <product_latest_download_link>
        ]
      },
      "install_info": {
        "type_id": 2, // 1 or 2 or 3
        "language_default": "en",
        "language_map": {
          "en": "en",
          "fr": "fr",
          "de": "de",
          "es": "es",
          "zh": "tw",
          "it": "it",
          "ja": "jp",
          "ko": "ko",
          "nl": "nl",
          "pt": "pt",
          "ru": "ru",
          "pl": "pl"
        },
        "alternative_signatures": [
          398,
          3521
        ],
        "arch_map": null,
        "ps_script": <ps_script_content>, // ps script available for install type 2
        "require_restart": 0, // does this product require restart after patch
        "require_close_first": 1, // does this product require close all process before patch?
        "blocking_categories": [ // categories of the product
          10
        ],
        "blocking_pids": [ // product ids that blocking us, use with require_close_first 
          394
        ],
        "require_uninstall_first": 0, // 1 if the product require uninstall old version before install a new one
        "log_paths": [

        ]
      }
    }
  },
  "eula_link": <eula_link>,
  "release_note_link": <release_note_link>,
  "timestamp": "1714724754"
}
```

Bước 3: Tạo patch association để map patch với v4 signature

- Association nằm ở `fv-crom\patching\patch_associations.json`
- Thêm một item có dạng:

```jsx
{
	"_id": <patch_association_id>,			
	"is_latest": true,	// true if the latest version supported -> Change the previous version to false
	"v4_pid": <v4_product_id>,	
	"patch_id": <patch_id>,	
	"v4_signatures": [
		<v4_signature_id>
	],
	"os_bl": "[-2, 1009]",	// os blackist, this means this patch is not supported on selected OS.
	"version_pattern": "^10\\.",// in case this patch is only applicable for specific version range
	"ranges": [
		{
			"start": "10.0.0",
			"limit": "10.99.9999"
		}
	],
	"no_update_signature": true				// default true
},
```

Bước 4: Local testing

- Generate data files

```ruby
# Load the patch and patch associattion to database
ruby fv-vcrom\patching\main.rb		
#: Dir.glob('./collect_installers/211*.rb'){|file_path| 
# Find line 150

# Create patch.data
./create_patch.ps1

# Create vmod-vuln-oft.dat
./create_vmod_vuln_oft_dat.ps1
```

- Test with get latest installer

```bash
# GetLatestInstaller: Return infor of the product
./test_auto_patching.exe --db patch.dat --sig 3112 --get --download 0

./test_auto_patching.exe --db patch.dat --sig 3112 --get --download 1

# InstallFromFile: Patching the product to latest version
./test_auto_patching.exe --db patch.dat --sig 3112 --install --path Firefox.exe 

# InstallFromFile: Patching the product to latest version that force terminate process of the product
./test_auto_patching.exe --db patch.dat --sig 3112 --install --path notepat.exe --force_close 1

# GetProductPatchLevel: Check if the installed product's version and the latest version in database is the same
./test_auto_patching.exe --db vmod-vuln-oft.dat --sig 3112 --check-feed
```