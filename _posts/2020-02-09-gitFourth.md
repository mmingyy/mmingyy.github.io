---
layout: post
title:  "[Do it 깃] CH04"
date:   2020-02-09
categories: Do_it_Git
---
1) 깃허브란

깃허브는 인터넷에서 제공하는 원격 저장소입니다.
원격저장소는 지역저장소(본인의 컴퓨터)가 아닌 컴퓨터나 서버에 만든 저장소를 뜻합니다.
특히 백업, 협업을 할 때 유용합니다.

* 깃허브 가입방법
<https://mminky.tistory.com/9>

2) 원격저장소 연결
 ```
 $ git remote add origin 주소
 ```
 원격저장소에 연결이 잘 되었는지 확인하는 명령어는 다음과 같습니다.
 ```
 $ git remote -v
 ```
 
 3) 원격저장소에 push, pull
 ```
 push : 지역저장소 -> 원격저장소
 pull :  원격저장소 -> 지역저장소
```
 push, pull 하기 위해서는 지역저장소와 원격저장소의 연결이 필요합니다.
 
 지역저장소의 브랜치를 원격저장소의 master브랜치(origin)에 연결 후 push 하기
 ```
 $ git push -u origin master
 ```
 (깃허브 로그인창이 나타나면 로그인을 합니다.)
 한 번 연결한 후에는 git push만 입력하면 됩니다.
 
 원격저장소 -> 지역저장소 가져오기
```
$ git pull origin master
```
이 때 origin master는 생략하고 $ git pull만 입력해도 됩니다.

4) 보안키 생성
```
$ ssh-keygen
```

자세한 내용은 하단의 블로그름 참고해주세요 :}

<https://mminky.tistory.com/8>


