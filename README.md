# Infra-Web_PlayGround

<br><br><br><br><br><br>

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

## gcloud 명령어 살펴보기
이 gcloud도구는 명령 -h끝에 플래그 (도움말 용)를 추가하여 사용할 수있는 간단한 사용 지침을 제공합니다 gcloud.

다음 명령을 실행하십시오.

gcloud -h
--help명령에 플래그를 추가 하거나 명령을 실행하여 보다 자세한 도움말에 액세스 할 수 있습니다 gcloud help.

다음 명령을 실행하십시오.

gcloud config --help
참고 : 도움말 내용을 스크롤하려면 ENTER 또는 스페이스 바를 누르십시오. 컨텐츠를 종료하려면 Q를 입력하십시오 .
다음 명령을 실행하십시오.

gcloud help config
gcloud config --help및 gcloud help config명령 의 결과 는 동일합니다. 둘 다 길고 자세한 도움말을 반환합니다.

참고 : 도움말 내용을 스크롤하려면 ENTER 또는 스페이스 바를 누르십시오. 컨텐츠를 종료하려면 Q를 입력하십시오 .
gcloud전역 플래그 는 각 호출 수준에서 명령의 동작을 제어합니다. 플래그는 SDK 속성에 설정된 모든 값을 재정의합니다.

환경의 구성 목록을 확인합니다.

gcloud config list
모든 속성 및 해당 설정을 보려면 :

gcloud config list --all
구성 요소를 나열하십시오.

gcloud components list
이 명령어는이 실습에서 사용할 준비가 된 gcloud 구성 요소를 표시합니다.

## 작업 2 : 새 구성 요소 설치
다음으로 gcloud도구에서 더 쉽게 작업 할 수있는 gcloud 구성 요소를 설치합니다 .

자동 완성 모드

gcloud interactive 명령 및 플래그에 대한 자동 프롬프트가 있으며 명령을 입력 할 때 창의 아래쪽 섹션에 인라인 도움말 스 니펫을 표시합니다.

드롭 다운 메뉴를 사용하여 명령 및 하위 명령 이름, 플래그 이름 및 열거 된 플래그 값과 같은 정적 정보를 자동 완성 할 수 있습니다.

베타 구성 요소를 설치합니다.

sudo apt-get install google-cloud-sdk
gcloud interactive모드 활성화 :

gcloud beta interactive
대화 형 모드를 사용하는 경우 TAB 키를 눌러 파일 경로 및 리소스 인수를 완료합니다. 드롭 다운 메뉴가 나타나면 TAB을 눌러 목록 사이를 이동하고 스페이스 바를 눌러 선택 항목을 선택합니다.

이 기능을 시도하려면 다음 명령어를 입력하고 자동 완성을 사용하여 <your_vm>을 프로젝트의 기존 VM으로 바꿉니다.

gcloud compute instances describe <your_vm>
Cloud Shell 창 아래에 명령어 목록이 표시됩니다. F2를 누르면 활성 도움말 섹션이 ON 또는 OFF로 전환됩니다.

대화식 모드를 종료하려면 다음 명령을 실행하십시오.

exit

## 작업 3 : SSH를 사용하여 VM 인스턴스에 연결
gcloud compute인스턴스에 쉽게 연결할 수 있습니다. 이 gcloud compute ssh명령은 인증 및 IP 주소에 대한 인스턴스 이름 매핑을 처리하는 SSH를 둘러싼 래퍼를 제공합니다.

SSH를 사용하여 VM에 연결하려면 다음 명령어를 실행하세요.

gcloud compute ssh gcelab2 --zone $ZONE
출력 :

WARNING: The public SSH key file for gcloud does not exist.
WARNING: The private SSH key file for gcloud does not exist.
WARNING: You do not have an SSH key for gcloud.
WARNING: [/usr/bin/ssh-keygen] will be executed to generate a key.
This tool needs to create the directory
[/home/gcpstaging306_student/.ssh] before being able to generate SSH Keys.
Do you want to continue? (Y/n)
계속하려면 Y를 입력하십시오 .

Generating public/private rsa key pair.
Enter passphrase (empty for no passphrase)
암호를 비워 두려면 Enter 키를 누릅니다 .

여기서 아무것도 할 필요가 없으므로 SSH 연결을 끊고 원격 셸을 종료하려면 다음 명령을 실행합니다.

exit
프로젝트의 명령 프롬프트로 돌아와야합니다.

## 작업 4 : 홈 디렉터리 사용
이제 홈 디렉토리를 사용해보십시오. Cloud Shell 홈 디렉터리의 콘텐츠는 가상 머신이 종료되고 다시 시작된 후에도 모든 Cloud Shell 세션 사이의 프로젝트에서 유지됩니다.

현재 작업 디렉토리 변경 :

cd $HOME
텍스트 편집기 .bashrc를 사용 하여 구성 파일을 엽니 다 vi.

vi ./.bashrc
편집기가 열리고 파일 내용이 표시됩니다.

편집기를 종료하려면 ESC , :wq를 누른 다음 Enter를 누릅니다 .
