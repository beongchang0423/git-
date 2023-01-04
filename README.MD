git config 는 설정창이라 볼 수 있는데, 
git config --global alias.st status 라고 지정하면 앞으로 st를 입력시 
자동으로 status로 바꾸어 달라는 의미를 뜻한다. 
이 기능으로 자신만의 단축키 설정이 가능하다.

1.working directory
git add 
git add * = 모든 파일을 add해라(삭제했던 것들도 들어감)
git add . = 존재하는 모든 파일을 add해라
2.stage
git commit  = 만 하면 vscode로 열리면서 원하는 commit 메세지를 저장 후 등록됨
git commit -m "~~" 하면 괄호 안의 내용이 commit 메세지로 저장됨

git commit -am "~~" (all message) 하면 add 없이 바로 모든 파일을 commit 가능하며
괄호안의 내용이 저장됨

3.directory
directory에 올라간 파일들은 버전별로 저장되어 있다. 언제든 되돌리는 것이 가능함
그래서 history라고 이야기 하더라.
적당히 작은 단위로 나누어 저장하고 commit 내용을 내용에 맞도록 지어 주어야 관리하기 수월함.

git push를 통해 외부로 저장한다.

4.remote save
의 저장상태를 가진다.

hash코드 값으로 언제 누가 commit 했는지를 git log에 기록되어있다.
다시 되돌리고 싶을때 이값을 사용하여 불러오는게 가능

