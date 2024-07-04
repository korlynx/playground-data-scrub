# playground-data-scrub
How to scrub passwords or secret credentials from repo, and also detect AWS credentials.

## Install Trufflehog
[Trufflehog](https://github.com/trufflesecurity/trufflehog) secrets help scan for AWS secrets in your code or files in github repository. Scan your code using the below command:

`trufflehog git https://github.com/<github_account_name>/<github_repo_name>`

## Install BFG using brew

Install [BFG](https://rtyley.github.io/bfg-repo-cleaner/) using the below commmand

`brew install bfg`

Manually remove the secrets data in the file from your github repo and commit. Create a password.txt file where all the secrets that are needed to be removed are stored (*This file should not be committed to the github repo!!!). Run the "bfg" command to remove the secrets from the github commit histories.

`bfg --replace-text passwords.txt`

`git reflog expire --expire=now --all && git gc --prune=now --aggressive`

`git push --force`

