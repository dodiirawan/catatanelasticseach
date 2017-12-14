#SEARCH DATA
##1. Cari 
```
curl -XGET http://localhost:9200/nama_index/nama_mapping/_search
```

##2. Cari Match All
```
curl -XPOST http://localhost:9200/nama_index/nama_mapping/?pretty=true -d '{
	"from":0,
	"size":20,
	"query":{
		"match_all":{}
	}
}'
```

##3. Cari Match pada field tertentu
```
curl -XPOST http://localhost:9200/nama_index/nama_mapping/_search -d '{
	"from":0, // dari 0
	"size":10, // sebanyak 10
	"sort":[
		{"_score":"asc"}
	],
	"query":{
		"match" : {
			"summary":"killing"
		}
	},
	"highlight":{
		"pre_tags":["<span>"],
		"post_tags":["</span>"],
		"fields": {
			"summary":{}
		}
	}
	// summary -> nama field
	// killing -> teks yang dicari
}'
```

##4. Cari Dengan Bool Query
```
select * from nama_maping where name like '*x*' and summary like 'fictional' and summary like 'comic'

curl -XPOST http://localhost:9200/nama_index/nama_mapping/_search -d '{
	"from":0,
	"size":10,
	"sort":[
		{"_score":"asc"}
	],
	"query":{
		"bool": {
			"must":{
				"wildcard": {
					"name":"*x*"
				}
			},
			"filter":[
				{"match":{"summary":"fictional"}},
				{"match":{"summary":"comic"}}
			]
		}
	},
	"highlight":{
		"pre_tags":["<span>"],
		"post_tags":["</span>"],
		"fields": {
			"summary":{}
		}
	}
}'
```