## repository = 저장소
파일을 변경이력을 기준으로 구분하여 저장함
1.원격 저장소 - 파일이 서버에서 일괄 관리되는 저장소(github) - 이를 통해 공유를 통한 공동작업이 이루어짐 -기본설정된 저장소 주소를 origin이라 부름
2.지역 저장소 = 개별 PC에 파일이 저장되는 저장소(내PC)
-내 PC의 지역 저장소에서 작업 - 원격저장소에 업로드 하거나 타인의 작업 내용을 다운로드 해서 사용

commit= 작업공간 안에 있는 모든 파일과 파일의 데이터를 사진 찍듯이 복사해서 저장소에 보존
=작업공간의 어떤 시점의 스냅샷

commit 한다 = 커밋을 저장소에 추가한다. =현재 작업공간의 상태를 커밋으로 만들어 저장소에 저장한다는 의미 - 이전 커밋부터 현재 상태까지의 변경 이력이 기록된 커밋 생성
커밋별commit Hash값이 부여되며 이를 통해 각 커밋을 구분한다.
commit은 commit 메세지가 반드시 필요함 없다면 실행x
커밋끼리는 체인 구조를 형성(이전 커밋 훼손 시 이후 커밋도 망가짐)

branch = 원래 버전에서 갈라져 나온 것(분기) -새로운 버전
브랜치 간 영향을 받지 않아 여러 작업을 동시에 진행이 가능함.

master branch=기본 설정된 브랜치에 붙는 이름 = 완성된 배포 버전이라는 의미도 있음.
HEAD = 지금 작업중인 브랜치를 가리킨
work tree(working space) = 개인 컴퓨터 환경에서 소스코드를 편집하는 일반적인 프로젝트 폴더

stage = 작업 공간에서 변경이 발생한 파일을 다음 커밋에 포함되도록 예약하는 것.(추적이라함)
index = staging area
인덱스에 등록 = stage
인덱스에서 제외 = unstage
작업 트리 <-> 인덱스 <->저장소

github = 원격저장소 호스팅을(업다운로드) 지원하는 사이트

### remote

git config 는 설정창이라 볼 수 있는데, 
git config --global alias.st status 라고 지정하면 앞으로 st를 입력시 
자동으로 status로 바꾸어 달라는 의미를 뜻한다. 
이 기능으로 자신만의 단축키 설정이 가능하다.
git config --global -e로 에디터를 사용해 config설정을 지정해줄 수 있다.



## local저장소에서 원격저장소로 저장방법(upload)

1.working directory
git add 
git add * = 모든 파일을 add해라(삭제했던 것들도 들어감)
git add . = 존재하는 모든 파일을 add해라
2.stage
git reset으로 unstage가 가능함
git commit  = 만 하면 vscode로 열리면서 원하는 commit 메세지를 저장 후 등록됨
git commit -m "~~" 하면 괄호 안의 내용이 commit 메세지로 저장됨
git commit -am "~~" (all message) 하면 add 없이 바로 모든 파일을 commit 가능하며
괄호안의 내용이 저장됨

3.directory
directory에 올라간 파일들은 버전별로 저장되어 있다. 언제든 되돌리는 것이 가능함
그래서 history라고 이야기 하더라.
적당히 작은 단위로 나누어 저장하고 commit 내용을 내용에 맞도록 지어 주어야 관리하기 수월함.
git push를 통해 원격 저장소로 저장한다.

4.remote save
의 저장상태를 가진다.

hash코드 값으로 언제 누가 commit 했는지를 git log에 기록되어있다.(commit hash도 확인가능)
다시 되돌리고 싶을때 이값을 사용하여 불러오는게 가능

##local repository를 원격저장소와 연결하는 방법 두가지(download)
###1.
git init = 프로젝트를 시작한다
git rempte add origin [URL] = url을 원격 저장소로 지정한다.
git pull origin master = 원격 저장소를 현재 master에 병합한다.
###2.
이를 git clone [URL]로 생략 가능한 것.
git remote-v로 어떤 원격저장소와 연결되어잇는지 확인 가능

git reset은 뒤에 커밋 주소를 넣어줄 경우 해당 위치로 reset이 가능함.
git reset [hash주소값] 또는
git reset HEAD~1  (=HEAD(위치하던 커밋의) 1단계 뒤로 reset해라) 숫자에 따라 reset하는 위치가 달라짐.

