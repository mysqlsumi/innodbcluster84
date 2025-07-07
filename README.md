# innodbcluster84
How to set up mysql innodb cluster with mysql 8.4 version

## 1. dba.configureInstance("admin@vm-1:3306") : 클러스터 생성에 필요한 파라미터 추가
![image](https://github.com/user-attachments/assets/f079c02a-348c-4e52-ba59-61580b200e26)

### Restaring server
<img width="741" alt="image" src="https://github.com/user-attachments/assets/e5bec2c6-ae7c-45db-8302-6c668343de7e" />
 
## 2. dba.checkInstanceConfiguration("admin@vm-1:3306") : 파라미터 설정상태 체크
![image](https://github.com/user-attachments/assets/98c0b585-950e-4867-8831-f3395896a0c6)

## 3. myc = dba.createCluster('myc') : 클러스터 생성
![image](https://github.com/user-attachments/assets/501ae8f0-d2ee-46cb-bddc-26f503132d35)

## 4. myc.status() : 클러스터의 상태 확인
![image](https://github.com/user-attachments/assets/b6436e82-f71c-48c4-bc46-aebc4935a940)

 
