# innodbcluster84
How to set up mysql innodb cluster with mysql 8.4 version

## 1. 클러스터 생성에 필요한 파라미터 추가 : dba.configureInstance("admin@vm-1:3306") 
![image](https://github.com/user-attachments/assets/f079c02a-348c-4e52-ba59-61580b200e26)

### 서버 재시작 : Restaring server
<img width="741" alt="image" src="https://github.com/user-attachments/assets/e5bec2c6-ae7c-45db-8302-6c668343de7e" />
 
## 2. 파라미터 설정상태 체크 : dba.checkInstanceConfiguration("admin@vm-1:3306") 
![image](https://github.com/user-attachments/assets/98c0b585-950e-4867-8831-f3395896a0c6)

## 3. 클러스터 생성 : myc = dba.createCluster('myc') 
![image](https://github.com/user-attachments/assets/501ae8f0-d2ee-46cb-bddc-26f503132d35)

## 4.  클러스터의 상태 확인: myc.status()
![image](https://github.com/user-attachments/assets/b6436e82-f71c-48c4-bc46-aebc4935a940)

 ## 5. 2번 노드 대해서도 설정 추가: dba.configureInstance 
<img width="729" alt="image" src="https://github.com/user-attachments/assets/1dd6b88d-8b37-4e33-abf6-5dee2cb7cf99" />

## 6. 클러스터에 2번노드 추가
![image](https://github.com/user-attachments/assets/2e3c68f1-4a87-461b-ae80-c529e540d74d)
