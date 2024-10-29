
---

[Feed](Feed.md)
[Patch](Patch.md)

## Note

- When installing base Japanese languages, can not open app

![{8E5F23B6-BB6F-446E-8ABE-8BF347CF4B7C}.png](8E5F23B6-BB6F-446E-8ABE-8BF347CF4B7C.png)

- I installed R24.2.53.0.0 (Japanese), The version in Control Panel is R24.2.53.0.0 (Japanese), OESIS detects R24.2.53.0.0 (English)
- Can open multiple instances of AutoCAD (different languages), but they use the same base
- Now we will support fresh install with web installer, update with update patch. 
	- Separate fresh install and update
		- Avoid languages error and future similar error
	- Only support one method of install
		- Simple and reduce the effort for developing, reviewing and testing
	- Users have to pass correct installer when they want to fresh install or update

- https://forums.autodesk.com/t5/installation-licensing/multiple-languages-installed/td-p/9750291

## Questions:

- What is the differences of AutoCAD software after install 4 methods: Install, Download, Direct Download, Custom Install?
- When I installed old version AutoCAD in one method, and then install and overlap the new version using a different method, will it keep my licenses, configurations, or packages I installed?
- Can I silently install AutoCAD using CAD in both 4 methods?

## Pubkeys

- Install
```json
"cert_paths": [
	[
	  {
		"subject": "Autodesk, Inc.",
		"issuer": "DigiCert Trusted G4 Code Signing RSA4096 SHA384 2021 CA1",
		"thumbprint": "7AAD60DF8FB0973090E9CB14406A98576AF76B45"
	  },
	  {
		"subject": "DigiCert Trusted G4 Code Signing RSA4096 SHA384 2021 CA1",
		"issuer": "DigiCert Trusted Root G4",
		"thumbprint": "7B0F360B775F76C94A12CA48445AA2D2A875701C"
	  },
	  {
		"subject": "DigiCert Trusted Root G4",
		"issuer": "DigiCert Trusted Root G4",
		"thumbprint": "DDFB16CD4931C973A2037D3FC83A4D7D775D05E4"
	  }
	]
  ]
```
    
- Download
    ```json
"cert_paths": [
	[
	  {
		"subject": "Autodesk, Inc.",
		"issuer": "DigiCert Trusted G4 Code Signing RSA4096 SHA384 2021 CA1",
		"thumbprint": "07FDB209029F7464F1944FE92E63681A2659F583"
	  },
	  {
		"subject": "DigiCert Trusted G4 Code Signing RSA4096 SHA384 2021 CA1",
		"issuer": "DigiCert Trusted Root G4",
		"thumbprint": "7B0F360B775F76C94A12CA48445AA2D2A875701C"
	  },
	  {
		"subject": "DigiCert Trusted Root G4",
		"issuer": "DigiCert Trusted Root G4",
		"thumbprint": "DDFB16CD4931C973A2037D3FC83A4D7D775D05E4"
	  }
	]
  ]
    ```
    
- Direct download
    
```json
// 2
"cert_paths": [
	[
	  {
		"subject": "Autodesk, Inc.",
		"issuer": "DigiCert Trusted G4 Code Signing RSA4096 SHA384 2021 CA1",
		"thumbprint": "2AB30470546DF0C1C453BB8604602636DFBFC8A0"
	  },
	  {
		"subject": "DigiCert Trusted G4 Code Signing RSA4096 SHA384 2021 CA1",
		"issuer": "DigiCert Trusted Root G4",
		"thumbprint": "7B0F360B775F76C94A12CA48445AA2D2A875701C"
	  },
	  {
		"subject": "DigiCert Trusted Root G4",
		"issuer": "DigiCert Trusted Root G4",
		"thumbprint": "DDFB16CD4931C973A2037D3FC83A4D7D775D05E4"
	  }
	]
  ]
```
    
- Custom install
- Update
    
```json
"cert_paths": [
	[
	  {
		"subject": "Autodesk, Inc.",
		"issuer": "DigiCert Trusted G4 Code Signing RSA4096 SHA384 2021 CA1",
		"thumbprint": "3A67AD663C2A0CC8F4F29E9B576ADCCEF74F7C89"
	  },
	  {
		"subject": "DigiCert Trusted G4 Code Signing RSA4096 SHA384 2021 CA1",
		"issuer": "DigiCert Trusted Root G4",
		"thumbprint": "7B0F360B775F76C94A12CA48445AA2D2A875701C"
	  },
	  {
		"subject": "DigiCert Trusted Root G4",
		"issuer": "DigiCert Trusted Root G4",
		"thumbprint": "DDFB16CD4931C973A2037D3FC83A4D7D775D05E4"
	  }
	]
  ]
```
    

## Next steps

- Install base and patch in different methods to find out if configs will be changed or not

## Patching with different methods

|                 | Install | Download | Direct Download | Custom Install |
| --------------- | ------- | -------- | --------------- | -------------- |
| Install         | OK      | OK       |                 |                |
| Download        |         |          |                 |                |
| Direct Download |         |          |                 |                |
| Custom Install  | Careful | Careful  | Careful         | Careful        |
| Update          |         |          |                 |                |

When use custom install for patching, we should keep the same config as the base

## GetVersion

```json
{
	"result": {
		"version": "R24.2.53.0.0",
		"architecture": {
			"name": "x64",
			"bitness": 64
		},
		"timing": 0,
		"language": {
			"name": "en-US",
			"code": "0x0409"
		},
		"method": 100,
		"code": 0,
		"timestamp": "1729149820",
		"signature": 3841
	}
}
```

## GetProductInfo

```json
{
	"result": {
		"detected_product": {
			"vendor": {
				"name": "Autodesk, Inc.",
				"id": 643
			},
			"categories": [
				10
			],
			"signature": 3841,
			"product": {
				"name": "AutoCAD",
				"id": 1046
			},
			"sig_name": "AutoCAD 2023",
			"methods": {
				"manageability": [
					103
				]
			}
		},
		"method": 109,
		"code": 0,
		"timing": 0,
		"timestamp": "1729149638",
		"signature": 3841
	}
}
```