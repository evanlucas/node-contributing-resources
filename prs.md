# Pull Requests

Marking a PR as merged when we don't actually use the big green
merge button can be done as follows:

```bash
$ git remote -v
mine	git@github.com:evanlucas/node (fetch)
mine	git@github.com:evanlucas/node (push)
origin	git@github.com:nodejs/node (fetch)
origin	git@github.com:nodejs/node (push)

$ git pull -r origin master
$ git am --abort

# fetch the patch and apply it
$ curl -L <patch url> | git am --whitespace=fix

# Install tool to generate PR meta data
$ npm install -g core-get-reviewers
$ core-get-reviewers <pr number>

# rebase and add meta data
$ git rebase -i HEAD~<number of commits>

# actually merge and push
$ git push mine +HEAD<branch>  \
    && git push origin master  \
    && git push mine :<branch>
```
