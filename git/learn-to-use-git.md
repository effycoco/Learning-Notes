initial prompt
```bash
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/effycoco/Learning-Notes.git
git push -u origin main
```
`origin` --name of remote

`main` --name of branch
 
 pull file from github site to disk:

```bash
git clone <clone with ssh link>
```
`ls -la` or `ls -a` show every thing in current directory, including hidden files and folders

after some editing:
```bash
git status
git add .
git commit -m "some message" -m "more detail message"
```
`git add . ` to track all files listed in git status(staging area)

`git rm --cashed r . remove everything in the staging area

## SSH key 
[Reference](https://docs.github.com/en/github/authenticating-to-github/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)

generate a new pair of ssh keys:
```bash
ssh-keygen -t rsa -b 4096 -C "xxx@xx.com"
```
`-t rsa` --type of encryption

`-b 4096` --strength of encrytion

`-C "xxx@xx.com"` --github email adress

by default, the generated key is in `/Users/<username>/.ssh`

its default name is `id_rsa` and `id_rsa.pub`

cd to this location, use `cat id_rsa.pub` to print public key on terminal
copy the public key and paste to github-settings-sshkey-newsshkey

still in .ssh directory, `touch config` if it not already exists, then add following line to the config file:
```
Host *
  AddKeysToAgent yes
  UseKeychain yes
  IdentityFile ~/.ssh/id_rsa
  ```
then save the config file
in the comman line, run `ssh-add -K ~/.ssh/id_rsa` to add ssh private key to ssh-agent

## Personal Access Token
[Reference](https://docs.github.com/en/github/authenticating-to-github/keeping-your-account-and-data-secure/creating-a-personal-access-token)

`git diff <filename.type>` to see the difference of this file between the working directory and local repository

`git checkout <filename.type>` to restore this file back to the last version that was commited in local repository