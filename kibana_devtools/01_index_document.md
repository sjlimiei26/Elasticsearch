# 인덱스 생성
```
PUT students
```

# 인덱스 조회
```
GET students
```

# 인덱스 목록 조회
```
GET _cat/indices?v
```

# 복제본 수 변경
```
PUT students/_settings
{
  "index": { "number_of_replicas": 0 }
}
```

# 문서 추가 (인덱싱)
```
PUT students/_doc/1
{
  "name": "박이안",
  "grade": 2,
  "major": "러블리"
}

PUT students/_doc/2
{
  "name": "김진석",
  "grade": 2,
  "major": "우사기"
}

PUT students/_doc/3
{
  "name": "배정윤",
  "grade": 3,
  "major": "윤로드"
}
```

# 문서 목록 조회
```
GET students/_search
```

# 문서 조회
```
GET students/_doc/1
```

# 문서 수정
```
POST students/_update/1
{
  "doc": { "major": "큐트" }
}
```

# 문서 삭제
```
DELETE students/_doc/2
```

# 인덱스 삭제
```
DELETE students
```
