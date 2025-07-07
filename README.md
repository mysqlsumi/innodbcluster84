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

## 6. 클러스터에 2번노드 추가 : Clone 방식
![image](https://github.com/user-attachments/assets/2e3c68f1-4a87-461b-ae80-c529e540d74d)
<img width="732" alt="image" src="https://github.com/user-attachments/assets/2b38deab-b57d-44da-9d1d-6d39935ac0e4" />

## 7. 2번 노드 대해서도 설정 추가: dba.configureInstance 
<img width="737" alt="image" src="https://github.com/user-attachments/assets/a689fa11-18cc-49c3-b441-c1ee8af9f0ef" />

## 8. 클러스터에 3번노드 추가
![image](https://github.com/user-attachments/assets/487358b5-e062-421a-9f7b-e35d65b3fd65)

## 9.  클러스터의 상태 확인: myc.status()
<img width="736" alt="image" src="https://github.com/user-attachments/assets/ab6e25d0-d20c-43fe-a17d-ffcd75ab438a" />

## 10. MySQL 라우터 설치 (Generic tar 이용)
<img width="758" alt="image" src="https://github.com/user-attachments/assets/66e34ae4-f5b8-451e-8a9b-f35c11f60617" />


## 11. 라우터 bootstrap
![image](https://github.com/user-attachments/assets/6c8fc120-3c9d-4b1b-b3e2-4d6524ea20c9)

## 12. 라우터 실행
![image](https://github.com/user-attachments/assets/cc3b2277-b5e7-4386-835b-8dd515e670d0)


## 13. 라우터 인스턴스 확인
<img width="763" alt="image" src="https://github.com/user-attachments/assets/b079decf-e29e-4d80-8250-8a5919909c20" />

## 14. 라우터 동작 테스트
![image](https://github.com/user-attachments/assets/92560547-ebcc-4a99-9785-dcf34576f58d)



