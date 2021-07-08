# push error

```bash
$ git push origin master

To https://github.com/[user name]/[project name]
 ! [rejected]        master -> master (fetch first)
 # 에러
error: failed to push some refs to 'https://github.com/edutak/edutak.git'
# 로컬에 원격 저장소 작업이 없어서 Updates이 거절되었다.
hint: Updates were rejected because the remote contains work that you do
hint: not have locally. This is usually caused by another repository pushing
# push하기 전에 먼저 원격저장소 변경사항들을 통합해야한다.

hint: to the same ref. You may want to first integrate the remote changes
hint: (e.g., 'git pull ...') before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.

```

## 확인 해보기

> 원격저장소 커밋과 로컬 저장소 커밋 히스토리를 서로 비교

## 해결 방법

```bash
$ git pull origin master

$ git log --oneline
# Merge 커밋 => 원격이랑, 로컬 다른 버전을 두개 합침.
b7b72e1 (HEAD -> master) Merge branch 'master' of https://github.com/[user name]/[project name]
3946b62 Update 경력
e884994 (origin/master) Update README.md
dcf3558 Add README
```

```bash
$ git push origin master

Enumerating objects: 10, done.
Counting objects: 100% (10/10), done.
Delta compression using up to 12 threads
Compressing objects: 100% (4/4), done.
Writing objects: 100% (6/6), 725 bytes | 725.00 KiB/s, done.
Total 6 (delta 1), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (1/1), done.
To https://github.com/edutak/edutak.git
   e884994..b7b72e1  master -> master

```
