# playground-data-scrub
How to scrub password from repo, and to detect AWS credentials

## Install Trufflehog
Trufflehog secrets helps scan for AWS secrets in your codde or files in github repository. Scan your code using the below command:

`trufflehog git https://github.com/<github_account_name>/<github_repo_name>`

## Install BSG using brew

Install [BSG]("https://rtyley.github.io/bfg-repo-cleaner/") using the below commmand

`brew install bfg`
Then manually delete the secrets data in the file from your github repo and commit. Create a password.txt file which all the secrets that need to be romoved are stored (*This file should not be commited to the github repo!!!), run the "bsg" command to remove the secrets from the guthub commit histories.

`bfg --replace-text passwords.txt`
`git reflog expire --expire=now --all && git gc --prune=now --aggressive`
`git push --force`

