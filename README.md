# git-commit-changer-batch

Run the following command on your git/github repo and do 'git push -f' for remote repo.

```
git filter-branch --env-filter '
WRONG_EMAIL="wrongemail@example.com"
NEW_NAME="Siddharth Saurav"
NEW_EMAIL="sid@example.com"

if [ "$GIT_COMMITTER_EMAIL" = "$WRONG_EMAIL" ]
then
    export GIT_COMMITTER_NAME="$NEW_NAME"
    export GIT_COMMITTER_EMAIL="$NEW_EMAIL"
fi
if [ "$GIT_AUTHOR_EMAIL" = "$WRONG_EMAIL" ]
then
    export GIT_AUTHOR_NAME="$NEW_NAME"
    export GIT_AUTHOR_EMAIL="$NEW_EMAIL"
fi
' --tag-name-filter cat -- --branches --tags
```