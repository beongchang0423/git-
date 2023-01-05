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

branch = 원래 버전에서 갈라져 나온 것(분기) -새로운 버전 =버전관리의 핵심
브랜치 간 독립적인 영역이기 때문에 영향을 받지 않아 여러 작업을 동시에 진행이 가능함.
변경된 내용을 원래의 버전과 비교하여 하나의 새로운 버전으로 합칠 수 있음.

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
git commit -m "메세지"" = commit 메세지로 저장됨
git commit -am "메시지" = a옵션이 파일 자동 stage 기능을 하여 add 없이 commit이 된다고함.

3.directory
directory에 올라간 파일들은 버전별로 저장되어 있다. 언제든 되돌리는 것이 가능함
그래서 history라고 이야기 하더라.
적당히 작은 단위로 나누어 저장하고 commit 내용을 내용에 맞도록 지어 주어야 관리하기 수월함.
git push또는 git push origin master를 통해 원격 저장소로 저장한다. (내 브랜치 이름은 main으로 바꿔두긴 했음)

4.remote save
원격저장소에 저장된 상태를 가진다.

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

.gitignore 확장자를 가지를 파일을 만들어 이를 메모장에 열어 git add . 시에 모든 파일을 옮기지 않도록 제한하는 거름망 역할로 사용가능.(이미 index또는 commit에 추가된 내용은 반영되지 않음)
위 괄호부분을 해결하기 위해 git rm -r --cached . 을 통해 현재 저장소에 있는 파일들을 인덱스에서 일괄 삭제 처리 하고 사용하면 이미 commit된 파일도 gitignore에 반영이 가능함.

git pull을 통해 원격 저장소에서 현재 내 local 저장소로 브랜치를 다운로드 해오는 명령어임
git pull 또는 git pull origin master를 사용(master를 main으로 변경하긴했음)

## conflict
같은 파일이 원격 저장소와 지역저장소에 다른 내용이 저장되어 있다면 어떻게 될까(동시에 수정했음)
둘은 서로 다른 파일이기에 conflict가 발생하는데, 해결하기 위해 git pull을 통해 원격 저장소의 같은 파일을 불러온다. 
그 경우 두 버전 간의 차이점을 자동으로 합쳐주는데 이 차이점을 수정 후 commit을 한 뒤 push하면 conflict문제가 해결된다.

##git branch
git branch  =존재하는 branch확인
git branch "브랜치명"   =새로운 branch추가
git branch -m "브랜치명" "바꿀 이름" =branch의 이름 변경
git branch -d  "브랜치명"   =branch 삭제
git checkout "브랜치명" = branch로 이동
git checkout -b "브랜치명" =브랜치를 만들면서 동시에 전환가능
branch의 경우 같은 파일을 공유하고 있는 관계에서는 정상이동이 가능하지만 추가적인 파일이 있거나 삭제된 파일이 존재하여 브랜치간의 파일보유의 차이가 있는 경우 현재 진행하고 있는 commit을 처리하지 않는다면 branch이동이 불가능함.  
이를 해결하기 위해 
git stash = 현재 작업 중 상황을 임시 저장하고 작업 트리를 깨끗하게(HEAD) 만들어줌
이후에는 branch변경이 자유롭게 가능함
git stash list = 임시 저장된 리스트 확인
git stash apply "불려오려는 인덱스" 시에 git stash list로 확인한 인덱스에 따라 임시 저장된 내용을 불러옴

## branch합치는 방법
![image](https://user-images.githubusercontent.com/43203949/210538768-33f19af4-9eaf-4b6f-863b-bf355d96b339.png)
1.기록을 남기면서 합치기(자동,수동으로 구분된)
1.1Fast-forward
git merge "브랜치명"  = 브랜치를 합쳐주는 명령어 = 해당 브랜치를 HEAD 브랜치에서 commit 내용을 추가하여 합쳐줌(Fast forward = 충돌이 없으며 추가 commit을 내가 적지 않고, 자동으로 원래 있던 commit 그대로 가져오는 방식
두 branch 중 하나는 수정x이고 하나는 수정o인 경우 
1.2 Recursive strategy
마찬가지로 git merge "브랜치명" 으로 브랜치를 합쳐준다.-merge시에 commit이력이 분기되었기 때문에  자동으로 vi창이 뜨며 추가 commit을 작성해줘야 한다.두 branch가 병합했다는 commit(내용은 자동으로 써주더라)이 저장된다는 차이점이 있다.
두 branch 모두 수정이 있었지만 서로 다른 file에 대한 수정이었던 경우(conflict아님)

1.3 수동 병합- conflict 발생했을 경우는 자동 병합이 불가능하여 conflict해결 후 병합해야함.
마찬가지로 git merge "브랜치명" 으로 병합을 시동하고, 충돌이 발생하여 merge가 불가능하다는 매세지가 보일 것이다. 이를 현재 위치한(HEAD) 브랜치에서 충돌 파일에 접근하여 충돌 내용을 수정한 후 해당 내용에 대한 add, commit을 적용하면 merge가 완료된다(완료되면 HEAD브랜치 옆에 |MERGING이라고 표시해져 있던 것이 사라진다.)

2.한줄로 합치기
복잡한 branch 병합 기록은 가독성에 좋지 않다. 그래서 사용하는 것이 rebase이다.
rebase = 별도의 branch 기록을 남기는 대신 공통 조상 커밋을 바탕으로 중간에 commit을 끼워넣어줌으로써 한 줄로 보이도록 함.
![image](https://user-images.githubusercontent.com/43203949/210541292-c185b416-e5b1-4fcb-aa05-fcb883b0ec1a.png)
git rebase "브랜치명"   =현재 HEAD branch에 대상 branch간의 공통 commit 이후에 해당 commit을 배치함 conflict 없을경우에는 Fastfoward로 자동 병합 되지만, conflict발생시에 조금 다른 형태의 수정이 발생함.
기존에는 HEAD의 내용이 앞에 저장되고 나머지가 뒤에 저장되어 충돌내용을 검토받는데, rebase의 경우 반대로 이루어지며 그 이유는 합쳐지는 branch가 중간에 끼어들어 commit되는 형태이기 때문이다.
동일하게 충돌을 정리 후 변경사항 staging(add)한 후 다시 commit해주는 대신에 git rebase  --continue 명령어를 사용하면 현재 rebase 내용을 반영하게 됨(조상 commit을 완료한 지점까지 당겨오는 것) 이를 통해 merge가 마무리 된다.

##잘못된 commit 변경하기
git commit --amend = 연결된 편집기로 자동 이동되며 commit 수정이 가능해짐
![image](https://user-images.githubusercontent.com/43203949/210678051-80c47ec4-2518-4d11-a2ae-3e045bde1f7e.png)


