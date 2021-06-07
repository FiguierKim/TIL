

# 원격 저장소(remote repository)

## 기본설정

1. local git 저장소 준비
2. GitHub repository 생성
3. Repository default branch 변경 (settings -> repositories)
   - main -> master로 변경

<br>

## 명령어

### 원격 저장소 주소 추가

```bash
$ git remote add origin 저장소URL
```

> git에게 원격 저장소(remote)를 origin이라는 이름의 저장소URL을 추가(add)하라는 명령어

- origin은 원격 저장소 이름

<br>

## 원격 저장소 목록 보기

```bash
$git remote -v
origin	git@github.com:FiguierKim/TIL.git (fetch) #ssh로 설정한 경우
origin	git@github.com:FiguierKim/TIL.git (push)
```

>잘못 저장한 경우 삭제하는 법
```bash
$git remote rm
```

## 원격 저장소에 업로드(push)

```bash
$ git push -u origin master
Enumerating objects: 11, done.
Counting objects: 100% (11/11), done.
Delta compression using up to 8 threads
Compressing objects: 100% (7/7), done.
Writing objects: 100% (11/11), 2.30 KiB | 2.30 MiB/s, done.
Total 11 (delta 0), reused 0 (delta 0), pack-reused 0
To github.com:FiguierKim/TIL.git
 * [new branch]      master -> master
Branch 'master' set up to track remote branch 'master' from 'origin'.
```

> **원격 저장소에는 commit이 올라간다.**
>
> 즉, commit 이력이 없으면 push 할 수 없다.

