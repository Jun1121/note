Git 批量修改已提交记录。用户名｜邮箱

```bash
#!/bin/sh

git filter-branch --env-filter '

OLD_EMAIL="yangjun@hikoon.com"
CORRECT_NAME="杨俊"
CORRECT_EMAIL="yangjun@hikoon.com"

if [ "$GIT_COMMITTER_EMAIL" = "$OLD_EMAIL" ]
then
export GIT_COMMITTER_NAME="$CORRECT_NAME"
export GIT_COMMITTER_EMAIL="$CORRECT_EMAIL"
fi
if [ "$GIT_AUTHOR_EMAIL" = "$OLD_EMAIL" ]
then
export GIT_AUTHOR_NAME="$CORRECT_NAME"
export GIT_AUTHOR_EMAIL="$CORRECT_EMAIL"
fi
' --tag-name-filter cat -- --branches --tags

```