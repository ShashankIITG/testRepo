This is a test repository where i practice git commands

## my first ever git command with online repository
I just clone github repository to my local machine using https protcol and clone command.
`git clone https://github.com/ShashankIITG/testRepo.git`

I was unable to use the ssh protocol.
```
$ git clone git@github.com:ShashankIITG/testRepo.git
Cloning into 'testRepo'...
ssh: Could not resolve hostname github.com: Name or service not known
fatal: Could not read from remote repository.

Please make sure you have the correct access rights
and the repository exists.
```
## start ssh agent and add key
```
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/keyname
```
# add ssh config file
```
Host github.com
  HostName github.com
  User git
  IdentityFile ~/.ssh/keyname
```

## check ssh connection
```
ssh -vT git@github.com
```
