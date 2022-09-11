# Connecting to GitHub with SSH

## References
[Connecting to GitHub with SSH](https://docs.github.com/en/authentication/connecting-to-github-with-ssh)\
[Authenticating on multiple GitHub accounts using SSH - _A shot of code_](https://youtu.be/N2hMGEeYR7c)

## Generating a new SSH key

You can generate a new SSH key on your local machine. After you generate the key, you can add the key to your account on GitHub.com to enable authentication for Git operations over SSH.

1. Open Git Bash.
2. Go to .ssh directory. `cd ~/.ssh`
3. Use `ssh-keygen` to create a key pair (private key and public key) in `~/.ssh` directory

```
$ ssh-keygen -t ed25519 -f "agabhinav_id_ed25519"
$ ssh-keygen -t ed25519 -f "seasmokee_id_ed25519"
```

---
## Adding a new SSH key to your GitHub account

You can access and write data in repositories on GitHub.com using SSH (Secure Shell Protocol). When you connect via SSH, you authenticate using a private key file on your local machine.

After you generate an SSH key pair, you must add the public key to GitHub.com to enable SSH access for your account.

Copy the contents of .pub file and provide it in the corresponding GitHub account's settings.

---

## Accessing multiple git accounts using ssh

### .ssh/config file
Create or edit `~/.ssh/config` file.\
Create an entry for each github account that you would like to connect to from your local machine using SSH. Part after _Host_ acts as an alias for that GitHub account. This will be used in `git clone` and other commands as shown later.

```
Host github.com-seasmokee
  HostName github.com
  IdentityFile ~/.ssh/seasmokee_id_ed25519

Host github.com-agabhinav
  HostName github.com
  IdentityFile ~/.ssh/agabhinav_id_ed25519
```

---

### git clone from multiple accounts
Let's say you want to clone a repo from this url `git@github.com:seasmokee/demo-remote.git` and you want to use `seasmokee_id_ed25519` key.

Use `git clone` url with this modification `git clone git@<host from .ssh/config>...`
```
git clone git@github.com-seasmokee:seasmokee/demo-remote.git
```
Similarly, before you can push to a remote origin, you'll have to change the origin url from `git@github.com:seasmokee/demo-remote.git` to `git@github.com-seasmokee:seasmokee/demo-remote.git` as shown below.

```
git remote set-url origin git@github.com-seasmokee:seasmokee/demo-remote.git
```
---
