# Infra-Web_PlayGround

## GCP qwiklabs 실습
- 인스턴스 설정 : @@.md

## 환경 변수 설정
- 환경 변수는 환경을 정의하고 API 또는 실행 파일이 포함 된 스크립트를 작성할 때 시간을 절약하는 데 도움이됩니다.
- 프로젝트 ID를 저장할 환경 변수를 만들고 이전에 실행 한 명령어의 이름<your_project_ID> 값으로 바꿉니다 .gcloud compute project-info describe
```
export PROJECT_ID=<your_project_ID>
```
- 영역을 저장할 환경 변수를 만들고 이전에 실행 한 명령의 영역<your_zone> 값으로 바꿉니다 .gcloud compute project-info describe
```
export ZONE=<your_zone>
```
- 변수가 올바르게 설정되었는지 확인하려면 다음 명령을 실행하십시오.
```
echo $PROJECT_ID
echo $ZONE
```
- 변수가 올바르게 설정된 경우 echo 명령은 프로젝트 ID와 영역을 출력합니다.

## gcloud 도구로 가상 머신 만들기
- 이 gcloud도구를 사용하여 새 VM (가상 머신) 인스턴스를 만듭니다.

VM을 만들려면 다음 명령어를 실행하세요.

gcloud compute instances create gcelab2 --machine-type n1-standard-2 --zone $ZONE
출력 :

gcloud_vm.png

명령 세부 정보

gcloud compute Compute Engine API보다 간단한 형식으로 Compute Engine 리소스를 관리 할 수 ​​있습니다.

instances create 새 인스턴스를 만듭니다.

gcelab2 VM의 이름입니다.

이 --machine-type플래그는 머신 유형을 n1-standard-2 로 지정합니다 .

이 --zone플래그는 VM이 ​​생성되는 위치를 지정합니다.

--zone플래그 를 생략하면 gcloud도구가 기본 속성을 기반으로 원하는 영역을 유추 할 수 있습니다. machine type및과 같은 기타 필수 인스턴스 설정 image은 create명령에 지정되지 않은 경우 기본값으로 설정됩니다 .

