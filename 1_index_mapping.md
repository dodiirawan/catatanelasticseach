# INDEX dan MAPPING ELASTICSEARCH

## 1. Buat Index

```
curl -XPUT http://localhost:9200/nama_index/?pretty=true
```

## 2. Buat Index Beserta Mapping
```
curl -XPUT http://localhost:9200/nama_index/nama_maping -d '{
	"mappings" : {
		"mahasiswa" : {
			"properties" : {
				"nim" : {
					"type" : "text"
				},
				"nama" : {
					"type" : "text"
				},
				"tgllahir" : {
					"type": "date"
				},
				"alamat" : {
					"properties" : {
						"jln" : {
							"type":"text"
						}
						"pincode": {
							"type":"integer"
						}
					}
				}
			}
		}
	}
}'
```

## 3. Buat Mapping dari index yang sudah ada
Buat Satu Satu propertiesnya
```
curl -XPUT http://localhost:9200/nama_index

curl -XPUT http://localhost:9200/nama_index/_mapping/nama_mapping -d '{
	"properties" : {
		"nim" :  {
			"type" : "text"
		}
		/*
		"nama" : { 
			"type": "text"
		},
		"tgllahir" : {
			"type": "date"
		}
		*/
	}
}'
```

##4. Hapus Index
```
curl -XDELETE http://localhost:9200/nama_index
```

##5. Deskripsi Mapping
```
curl -XGET http://localhost:9200/nama_index/_mappings
```
##6. Melihat Daftar Index

```
curl -XGET http://localhost:9200/_aliases
```