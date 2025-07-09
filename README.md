# innodbcluster84
How to set up mysql innodb cluster with mysql 8.4 version
InnoDB Cluster 가 나온지도 꽤 오래되었습니다. 세계의 많은 고객들이 사용하고 있습니다.
InnoDB Cluster는 최소 3개 노드로 구성이 됩니다. 아키텍처는 아래와 같은데요. 3개의 컴포넌트인 Group Replication, MySQL Router, MySQL Shell로 구성되어 있습니다.
<img width="877" alt="image" src="https://github.com/user-attachments/assets/d6cf29ca-b1e8-48ac-985e-beb42b6df072" />


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
![image](https://github.com/user-attachments/assets/64b9ae4a-bde0-4f36-8271-48acb66e4a1c)

## 10. MySQL 라우터 설치 (Generic tar 이용)
![image](https://github.com/user-attachments/assets/d8ada432-61a4-4805-ae6a-af22709476ed)

## 11. 라우터 bootstrap
![image](https://github.com/user-attachments/assets/da68cf56-9d29-417a-84c5-5ea8362dd3b9)

## 12. 라우터 실행
![image](https://github.com/user-attachments/assets/e7b7a1b5-da3c-4282-b1f7-7dbe3c221b71)

## 13. 라우터 인스턴스 확인
![image](https://github.com/user-attachments/assets/f618bf2e-4db8-4dfd-9fbd-3a76dc47313c)


## 14. 라우터 동작 테스트
![image](https://github.com/user-attachments/assets/5bb52ce5-203a-446d-88ec-9a82fa512da9)


## 15. 주의해야 할 사항
### 15-1. 시작 및 종료
MySQL InnoDB Cluster의 경우, Sigle Primary 모드를 권장합니다. 1개의 R/W 노드와 2개의 R/O 노드로 구성됩니다.
그래서 시작할 때는  Primary(Master) 노드를 먼저 시작하고 나머지 Secondary 노드를 시작합니다.
하지만 종료 때는 반대로 Secondary 노드를 모두 종료하고 프로세스가 내려간 것도 확인 후 Primary 노드를 종료합니다.

### 15-2. 전체 클러스터가 내려간 경우(유지보수 작업 등) 
장애이든 아니면 유지보수 작업이든 전체 클러스터가 내려간 경우에는 반드시 아래 API를 이용해서 Cluster를 시작합니다.
dba.rebootClusterFromCompleteOutage()

### 15-3. 한개 노드가 살아있는데 R/O로 동작되는 경우 : no quorum 인 상태
데이터 정합성을 위해 2개 노드가 연결이 안되거나 내려간 경우에는 한개 노드는 R/O로 변경되서 서비스됩니다. 쓰기는 안되는 상태입니다.
이 경우, 1개 노드로 서비스하기 위해 Primary 로 동작하도록 변경할 경우 반드시 아래의 API를 이용해서 진행합니다.
var c = dba.getCluster()
c.forceQuorumUsingPartitionOf('사용자@host명:포트')


