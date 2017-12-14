#CRUD DATA
##1. Insert Data
```
curl -XPOST http://localhost:9200/nama_index/nama_maping/1?pretty=true -d '{
	"nim":"110200",
	"nama":"NAMA SISWA",
	"tgllahir":"2005-08-12"
}'
```

##2. Update Data / Put Data
Bila kita menimpanya, maka akan membuat dokumen tersebut menjadi versi terbaru
```
curl -XPUT http://localhost:9200/nama_index/nama_maping/1?pretty=true -d '{
	"nim":"110200",
	"nama":"SISWA NAMA",
	"tgllahir":"2005-08-12"
}'
```

##3. Delete Data
```
curl -XDELETE http://localhost:9200/nama_index/nama_maping/1?pretty=true
```

##4. Search Data
```
curl -XGET http://localhost:9200/nama_index/nama_mapping/_search/?pretty=true
```

##5. Search Data Berdasarkan Id
```
curl -XGET http://localhost:9200/nama_index/nama_mapping/1/?pretty=true
```