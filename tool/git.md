#

## config

- git config --list --show-origin
- git config --global -e
- git config --global http.proxy 'socks5://127.0.0.1:10808'

## command

- git commit -m "message"
- git checkout -b|-B branch_name
- git branch -f branch_name commit_id
- git reset commit_id
- git revert commit_id
- git rebase branch_name
- git merge branch_name
- git cherry-pick commit_id1 commit_id2
- git rebase -i commit_id
- git pull --rebase ; git push
- git branch -u origin/branch_name branch_name
- git push origin source:destination
- git fetch origin source:destination
- git pull origin source:destination
  