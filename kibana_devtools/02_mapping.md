# 인덱스 생성
```
PUT mapping-lab
{
  "settings": { "number_of_shards": 1, "number_of_replicas": 0 },
  "mappings": {
    "properties": {
      "product_name": {
        "type": "text",
        "fields": { "raw": { "type": "keyword" } }
      },
      "category": { "type": "keyword" },
      "price": { "type": "integer" }
    }
  }
}
```

# 문서 추가
```
POST mapping-lab/_doc/1
{ "product_name": "Red Pants", "category": "Clothing", "price": 45 }

POST mapping-lab/_doc/2
{ "product_name": "Blue Pants", "category": "Clothing", "price": 50 }

POST mapping-lab/_doc/3
{ "product_name": "Red Boots", "category": "Shoes", "price": 80 }
```

# 인덱스 조회
```
GET mapping-lab/_search
```

# 매핑 정보 조회
```
GET mapping-lab/_mapping
```

# match 검색
```
GET mapping-lab/_search
{ "query": { "match": { "product_name": "pants" } } }
```

# term 검색
```
GET mapping-lab/_search
{ "query": { "term": { "product_name": "Red Pants" } } }

GET mapping-lab/_search
{ "query": { "term": { "product_name.raw": "Red Pants" } } }

GET mapping-lab/_search
{ "query": { "term": { "product_name": "red" } } }
```

# 집계 검색
```
GET mapping-lab/_search
{
  "size": 0,
  "aggs": { "by_category": { "terms": { "field": "category" } } }
}

GET mapping-lab/_search
{
  "size": 0,
  "aggs": { "by_name": { "terms": { "field": "product_name" } } }
}
```
