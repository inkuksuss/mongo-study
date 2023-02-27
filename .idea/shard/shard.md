## Shard
- shard은 Collection 단위로 만들며 여러 개의 Replica로 이루어짐

### 샤딩 상태확인
````text
sh.status()
````

### test Collection에 대한 shard 적용
```text
sh.enableSharding("test")
```

### shard을 위한 abc Collection에 인덱스 설정
````text
db.abc.createIndex({a: 1})
````

### shard 시작
````text
sh.shardCollection("test.abc", {a: 1})
````
