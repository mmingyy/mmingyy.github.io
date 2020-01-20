---
layout: post
title:  "[Do it 깃] CH02"
date:   2019-03-23 21:03:36 +0530
categories: Javascript NodeJS
---
깃과 깃허브를 공부하기 위해 Do it! 깃&깃허브 책을 보고 있습니다!
(https://book.naver.com/bookdb/book_detail.nhn?bid=15910099)

2장부터 한 챕터씩 내용을 정리해서 올리려고 합니다!
깃의 완전 기본 개념이나 1장의 내용이 궁금하신 분은 제 블로그 글을 참고해주세요 :) https://mminky.tistory.com/5

-----------------------------------------------------------------------------------------------------------------------------------
CH02. 깃으로 버전 관리하기

오늘은 버전을 관리하는 방법에 대해 알아보려고 합니다.
우선 버전관리를 위해서는 버전을 저장할 수 있는 저장소를 만들어야 합니다.

1) 버전관리를 위한 준비
  $ mkdir git-storage
     : 깃 저장소를 만들 디렉터리 생성

  $ cd git-storage
     : 만든 디렉터리(git-storage)로 이동

  $ git init
     : 깃을 이용할 수 있게끔 디렉터리 초기화

  $ ls -la
     : 상세정보(l), 숨김파일(a) 표시
      git init 이후에 .git/ 디렉터리가 생성된 것을 볼 수 있습니다. 이 디렉터리가 바로 '저장소(repository)' 입니다.

이렇게 저장소를 만든 디렉터리에서 파일의 버전관리를 할 수 있습니다.


2) 작업트리, 스테이지, 저장소

작업 트리, 스테이지, 저장소에 대한 개념을 그림으로 나타내면 다음과 같습니다.



작업트리 : 파일 수정, 저장을 하는 디렉터리
스테이지 : 버전으로 만들 파일이 대기하는 곳
저장소 : 스테이지의 파일들을 버전으로 만들어 저장하는 곳


우리가 a, b, c, d파일을 만들면 위 그림처럼 작업트리에 a.txt, b.txt, c.txt, d.txt파일이 생성됩니다.
그 중 커밋하고 싶은(버전으로 만들고 싶은) a.txt를 골라 커밋합니다. git add a.txt
git commit 을 하면 스테이지에 있는 a, e, f가 커밋됩니다.
저장소로 커밋된 a, e, f는 버전으로 만들어집니다.

3) 깃의 상태
  $ git status

- 작업트리가 비어있을 때
On branch master : master 브랜치에 있습니다. (CH03에 브랜치에 대한 설명이 있습니다.)
No commits yet : 아직 커밋한 파일 이 없습니다.
nothing to commit : 커밋 할 파일이 없습니다.

- 작업트리에 파일 생성
 이번에는 작업트리인 git-storage(위에서 만든 디렉터리)에 filename.txt를 만들어 보겠습니다.
  $ vim filename.txt
  화면이 바뀌면 키보드의 ' I '나 ' A '를 눌러 --끼워넣기--모드로 바꾼 후 내용을 입력합니다.

  내용 입력 후 'Esc'키를 눌러 ex모드로 변환한 후 ' :wq '를 입력해 저장종료합니다. (기억안나면 CH01 복습!!)

On branch master
No commits yet
Untracked files: filename.txt
nothing added to commit but untracked files present
커밋한 것은 없지만 Untracked file(버전관리 한 번도 안 한 파일)이 존재한다.
여기서 Untracked file은 filename.txt를 뜻합니다.

작업트리에 파일이 생김
현재 상황은 위 그림과 같이 작업트리에 filename.txt가 생겼습니다.

 

  - 스테이징(Staging)

  작업트리에 있는 파일을 스테이지로 올리는 과정을 스테이징 이라고 합니다.

 

  $ git add 파일명


git add로 스테이징 하기
warning: LF will be replaced by CRLF in filename.txt.

라는 경고가 뜹니다.

Git Bash에서 리눅스를 기반으로 합니다. 이 경고는 윈도우의 줄바꿈 문자(CR LF)와 리눅스의 줄바꿈 문자(LF)가 다르기 때문에 발생합니다. (맥은 LF이기 때문에 발생하지 않습니다.)

LF가 CRLF로 대체된다고 하네요. (책에서는 반대로 말하는데 뭐가 맞는건진 모르겠어요)

하지만 우리가 해야할 건 없습니다!


작업트리에 파일이 생성되었을 때
Changes to be committed:

   new file: filename.txt

새 파일인 filename.txt를 커밋할 준비가 되었다.

(취소하려면 git rm 명령어 이용)


Staging
스테이징을 그림으로 나타내면 위와 같다.

 

  - 커밋(Commit)

   $ git commit


git commit
이때, 커밋에 메시지를 넣고 싶다면

$ git commit -m "메시지내용" 이렇게 입력합니다.

결과창에 1 file changed, 1 insertion이라고 표시됩니다.

파일 1개가 변경되었고 1개의 내용이 추가되었다는 내용입니다.


git 상태
이 때의 git 상태를 보면 nothing to commit, working tree clean 입니다.

즉 commit 할 것이 없고 작업트리도 수정할 것 없이 깨끗하다라는 뜻 입니다.


commit
커밋을 하면 스테이지에 있던 filename.txt의 버전이 저장소에 생성됩니다.

 

$ git log

저장소에 저장된 버전 확인


git log
git log를 하면 first_message라고 입력했던 커밋을 통해 버전이 만들어졌다는 것을 알 수 있습니다.

 

$ git log --stat


git log --stat
git log 뒤에 --stat을 붙이면 커밋 관련 파일이 표시됩니다.

filename.txt | 1 + 이라는 메시지를 통해 filename.txt파일이 커밋되었음을 알 수 있습니다.

 

$ git commit -am

commit 뒤에 -am을 붙이면 스테이징과 커밋을 한 번에 처리합니다.

메시지를 붙이고 싶다면 $ git commit -am "메시지내용" 를 입력하면 됩니다.

 

4) 파일의 상태

  - tracked & untracked

   tracked : 한 번 이라도 커밋 된 파일

    깃은 한 번이라도 커밋 된 파일의 수정 여부를 계속 추적(track)합니다.

    이런 파일은 수정 후 git status를 확인하면 modified: 라고 표시됩니다.

 

   untracked : 한 번도 커밋되지 않은 파일

    이 파일의 경우 untracked files: 라고 표시 됩니다.

 

5) 작업취소

$ git checkout -- filename.txt

작업 트리에서 작업을 되돌리는 명령어 입니다. checkout으로 되돌린 내용은 복구할 수 없습니다.

 

$ git reset HEAD filename.txt

스테이징을 취소하는 명령어 입니다. 뒤에 파일명(filename.txt)을 입력하지 않으면

모든 파일의 스테이징을 취소합니다.

 

$ git reset HEAD^

가장 마지막에 한 커밋을 취소합니다. 동시에 스테이징도 취소되고 작업트리에만 남게 됩니다.

최근 2개의 커밋을 취소하려면 $ git reset HEAD~2 를 입력하면 됩니다.
