[toc]

# Git 초기 설정

## 커밋 작성자(author) 설정

```bash
❯ git config --global user.email "email address"
❯ git config --global user.name "user name"
```

- 커밋을 작성한 사람이 누구인지를 알 수 있게 해줌

<br>

## 지정된 설정 확인

```bash
❯ git config --global -l
# ❯ git config --global --list
```

<br>

## 커밋 편집기 변경

```bash
❯ git config --global core.editor "code --wait"
```

- 해당 명령어는 반드시 `vscode`가 설치되어 있어야 한다.

> 기본 텍스트 편집기 `vim` 을 `vscode` 로 대체하는 명령어이다.

<br>

---

# Git Basic

## 로컬 저장소 설정

```bash
❯ git init

Initialized empty Git repository in /Users/[userName]/[현재폴더]/.git/

~/[현재 위치한 폴더] master ?1
```

- 폴더에 git 저장소를 초기화 하면,
  - `.git` 숨김 폴더가 생기고
  - bash에는 `master` 또는 `(master)` 라고 표시된다.

> 주의사항
>
> - git 저장소 내에 또 다른 git 저장소를 만들면 안된다.
> - `git init` 명령어를 입력할 때, `master` 가 있으면 절대 입력하지 말아야 한다.

<br>

## add

> staging area / INDEX

```bash
❯ git add fileName # 특정 파일
❯ git add . # 현재 디렉토리 모두(하위 디렉토리 포함)
❯ git add folderName/ # 특정 폴더
```

- `working directory` 상태의 파일을 `staging area` 상태로 변경
- commit을 위한 파일 및 폴더들을 추가하는 명령어

```bash
❯ git status
On branch master

No commits yet

Untracked files: # 트래킹 되고 있지 않은 파일들
  (use "git add <file>..." to include in what will be committed)
	00_git_intro.md
	a.txt

nothing added to commit but untracked files present (use "git add" to track)
```

```bash
❯ git add 00_git_intro.md

❯ git status
On branch master

No commits yet

Changes to be committed: # 커밋 예정인 변경사항
  (use "git rm --cached <file>..." to unstage)
	new file:   00_git_intro.md

Untracked files: 
  (use "git add <file>..." to include in what will be committed)
	a.txt
```

> 모든 정보는 `git status`에서 확인 가능하다.

<br>

## commit

```bash
❯ git commit -m "first commit"
[master (root-commit) 3e407e9] first commit
 1 file changed, 85 insertions(+)
 create mode 100644 00_git_intro.md
```

```bash
❯ git log
commit 3e407e94b5977fa04364c8badb077b5b45644d90 (HEAD -> master)
Author: userName <userEmail>
Date:   Mon Jun 7 15:29:18 2021 +0900

    first commit
```

- 커밋을 통해 하나의 버전으로 기록된다.
- 커밋 메세지는 현재 변경사항들을 잘 나타낼 수 있도록 작성하는 것이 권장된다.
- 커밋은 고유한 아이디로 해시 값을 가진다.
  - SHA-1 알고리즘에 의해 생성된다.
- 커밋 목록은 `git log` 를 통해서 확인할 수 있다.

```bash
❯ git log --oneline # 커밋 목록 한 줄로 보기
3e407e9 (HEAD -> master) first commit
```

<br>

## status

- working directory, staging area 공간의 파일 상태를 확인 할 수 있다.

```bash
❯ git status
```

<br>
