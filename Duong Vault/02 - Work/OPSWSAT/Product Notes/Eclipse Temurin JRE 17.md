## Investigate

- Các phiên bản cũ (thấp hơn 17.0.12) không có user context, mặc định là All Users
- Có 2 trường hợp
    - Có base: patching lên all users, vì base bản cũ luôn là all users
    - Không có base: patch lên current user

## For x86

```json
{
	"_id": "1000338",
	"description": "Eclipse Temurin JRE with Hotspot 17 on Windows x86",
	"source_id": 1,
	"type_id": 2,
	"priority": 1,
	"elements": [
		{
			"version": "17.0.12.7",
			"date": "07/22/2024",
			"first_tt": "1603685583",
			"last_tt": "1603685583"
		}
	]
}
```

```json
{
	"scriptId": "eclipsetemurin_jre_hostpot17_x86_1000338",
	"schedule": "35 */6 * * *",
	"type": "FEED",
	"description": "Eclipse Temurin JRE with Hotspot 17 for Windows x86",
	"outValues": {
		"feedId": 1000338
	}
}
```

```json
{
	"_id": "1000338",
	"description": "Eclipse Temurin JRE with Hotspot 17 for Windows x86",
	"source_id": 1,
	"type_id": 2,
	"priority": 1,
	"defunct": false,
	"validators": [
		{
			"validator": "version",
			"patterns": [
				"17\\.\\d+\\.\\d+\\.\\d+"
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
	"comparators": [
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

```json
{
    "_id" : 1000833,
    "type_id" : 4,
    "os_id" : 1, 
    "feed_id" : 1000338,
    "v4_vid" : 1756,
    "v4_pids" : [
        3337
    ],
    "v4_signatures" : [
        3591
    ]
}
```

## For x64

## Test

- [x]  x86
    - [x]  Có base
    - [x]  Không base
- [ ]  x64:
    - [x]  Có base
    - [x]  Không base