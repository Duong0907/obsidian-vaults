
---

<aside>
💡 Mục đích của Part này là hỗ trợ method `GetProductPatchLevel`

</aside>

## Hướng dẫn

- Training by anh Thịnh [tại đây](https://opswat2017-my.sharepoint.com/:t:/g/personal/thinh_truong_opswat_com/ETAhO3bLDShCqmCWKs7ESYoBmC7HsPYbwUYoWiGNv1DhJA?e=5muAuL)
- Document [tại đây](https://opswat.atlassian.net/wiki/spaces/OES/pages/3106603960/PART+1+-+Add+feed)

## Cách hoạt động

- Chúng ta có 2 workers là Shelob và Saruman
    - Shelob thực thi script cào dữ liệu bằng script đã viết để lấy các thông tin như version mới nhất, ngày release, link download, … và đẩy vào database
    - Saruman thực thi việc chạy các rule check để kiểm tra version hay ngày release đã đúng định dạng đã đặt hay chưa

## Defenition of done

- Script để sinh ra feed data chạy đúng
- Add được 1 item vào feed json, meta json, cron job json
- Test thành công

## Quá trình

Bước 1: Scripts để tạo feed data: ví dụ `\fv-backend\shelob\scripts\db_scripts\7zip_1000025.rb`

- Tạo file ruby tên có định dạng `<tên product>_<feed id>.rb`
- Sau khi  chạy script cần thu được data sau

```json
{
  "feedId": 1000025,					// (1) https://opswat.atlassian.net/wiki/spaces/OES/pages/2238350492/Maximum+IDs (Version feed for Win)
  "type": 2,							// type 2 mean this is feed for Product Version, type 1 for antimalware info.
  "priority": 1,						// priority should usually be 1 for a feed, the priority 2 and up are for backups and advanced use, don't use it unless its already there or someone who knows what to do explains how/why/when
  "sourceid": 1,						
  "date": "06/19/2024",					// release data -> code cào
  "version": "24.07",					// latest version -> code cào
  "description": "7zip for windows",	
  "downloadInfo": { // optional
    "minFileSize": 957280,
    "downloadDetails": [
      {
        "desc": "Windows x64 Installer",
        "link": "https://www.7-zip.org/a/7z2407-x64.exe"		// downloadlink -> code cào
      }
     ]
  }
}
```

<aside>
💡 Chú ý các thuộc tính

</aside>

- feedId
- date
- version
- downloadInfo (may be)

Bước 2: Lấy feed id và feed association id

- Mỗi product đề có feed và feed association, lấy từ các max id [ở đây](https://opswat.atlassian.net/wiki/spaces/OES/pages/2238350492) (cộng thêm 1 vào)
- Update investigation template (có thể chưa cần làm)

Bước 3: Định nghĩa feed

- Thêm vào file `fv-backend/shelob/scripts/feeds.json` một item có dạng sau:

```jsx
{
	"_id": "1000299", // your feed id from step 1 (Version feed for Win)
	"description": "Microsoft Teams (work or school) for windows", // description that help you know what is this product
	"source_id": 1,
	~~~~"type_id": 2, // type 2 mean this is feed for Product Version, type 1 for antimalware info.
	"priority": 1, // priority should usually be 1 for a feed, the priority 2 and up are for backups and advanced use, don't use it unless its already there or someone who knows what to do explains how/why/when
	"elements": [
		{
			"version": "24004.1309.2689.2246",
			"first_tt": "1712053227",      // chon dai
			"last_tt": "1712053227"      // chon dai
		}
	]
}
```

<aside>
💡 Chú ý các thuộc tính

</aside>

- id
- element

Bước 4: Định nghĩa feed association

- Khi được nhận ticket thì commnet nội dung của association vào ticket để người review add vào database
- Một association item có dạng sau

```jsx
{
    "_id" : NumberInt(1000401), // feed association id from step 1 // Version/Av/defunct association for Win
    "type_id" : NumberInt(4),
    "os_id" : NumberInt(1), 
    "feed_id" : NumberInt(1000129), // feed id from step 1
    "v4_vid" : NumberInt(90), // v4 vendor id from SDK
    "v4_pids" : [ // v4 product ids
        NumberInt(3087) 
    ],
    "v4_signatures" : [ // v4 signature ids
        NumberInt(3202),
        NumberInt(3217),
        NumberInt(3800),
        NumberInt(3801)
    ]
}
```

Bước 5: Thêm cronjob vào `jobs.json`

- Cronjob này sẽ ra lệnh cho hệ thống chạy liên tục và kiểm tra phiên bản của product
- Thêm một item có dạng:

```jsx
{
	"jobs": [
		{
			"scriptId": "visualstudiocode_1000129", // name of the script in the step 4 
			"schedule": "* * * * *", // this mean run every minute, use for testing
			"type": "FEED",
			"description": "Visual Studio Code for Windows product version",
			"outValues": {      // ??????
				"feedId": 1000129 // feed id
			}
		}
	]
}
```

- Lưu ý về thời gian cron, dựa vào độ thường xuyên release sản phẩm

Bước 6: Thêm meta vào `meta.json`

- Thêm một item vào `meta.json` có dạng sau:

```jsx
	{
		"_id": "1000025",
		"description": "7-zip product version",
		"source_id": 1,
		"type_id": 2,
		"priority": 1,
		"defunct": false,
		"validators": [
			{
				"validator": "version",
				"patterns": [
					"\\d+.*"
				],
				"methods": []
			},
			{
				"validator": "date",
				"patterns": [
					"[0-1]\\d\\/[0-3]\\d\\/20\\d\\d"
				],
				"methods": []
			}
		],
		"comparators": [  // Eo biet lam gi, cu copy cho khac qua
			{
				"comparator": "version",
				"priority": 1,
				"code": "default"
			},
			{
				"comparator": "date",
				"priority": 2,
				"code": "P231"
			}
		]
	}

```

- Chú ý thuộc tính `validator`

Bước 6:  Bắt đầu test trên database local

- Chạy lệnh sau để update `feed.json` lên database

```bash
ruby jobsAndScriptsToMongo.rb; ruby updateDatabases.rb --update
```

- Chạy các lệnh sau để run các worker:

```bash
// broker
cd D:\Opswat\softs\apache-activemq-5.15.4-bin\apache-activemq-5.15.4
java -jar activemq-all-5.15.4.jar start

// shelob crawling data from vendor
cd D:\Opswat\Source_code\fv-backend\shelob
java -jar SHELOB-1.0.jar server configuration.yml

// compare data from shelob with meta, verify and insert to database
cd D:\Opswat\Source_code\fv-backend\saruman
java -jar SARUMAN-1.0.jar server configuration.yml
```