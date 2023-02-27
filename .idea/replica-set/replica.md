## MONGODB 설치

### 1. 설치 파일 복사
````text
sudo cp /Users/{user}/Downloads/{mongodb-directory}/bin/* /usr/local/bin/

sudo ln -s  /Users/{user}/Downloads/{mongodb-directory}/bin/* /usr/local/bin/
````


### 2. 데이터 파일 생성
````text
sudo mkdir -p /usr/local/var/mongodb
````

### 3. 로그 파일 생성
````text
sudo mkdir -p /usr/local/var/log/mongodb
````

### 4. 파일 읽기, 쓰기 권한 확인
````text
sudo chown my_mongodb_user /usr/local/var/mongodb
sudo chown my_mongodb_user /usr/local/var/log/mongodb
````


## 커멘드로 실행

### 1. 실행
- rs1 이름으로 / oplog size 128mb까지
- data는 data1 파일에 저장됨
````text
mongod --replSet rs1 --port 27017 --bind_ip "0.0.0.0" --dbpath /usr/local/var/mongodb/data1  --oplogSize 128
````

### 2. 실행 확인
````text
ps aux | grep -v grep | grep mongod
````

## 설정 파일로 실행

### 1. config파일 생성
````text
vim /usr/local/var/mongodb/config/mongo1.conf


net:
    port: 27019
    bindIp: 0.0.0.0

storage:
    dbPath: "/usr/local/var/mongodb/data3"
    directoryPerDB: true

replication:
    oplogSizeMB: 128
    replSetName: "rs1"

systemLog:
    path: "/usr/local/var/log/mongodb/mongod3.log"
    destination: "file"
````

### 2. 실행
````text
mongod -f /usr/local/var/mongodb/config/mongod1.conf
````