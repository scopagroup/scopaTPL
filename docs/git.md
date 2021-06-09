## GIT and GitHub

If you have not done so and you are working with me, create a GitHub account: [https://github.com](https://github.com)

Use a reasonable user name, since this will can serve as a business card for promoting yourself and your research. This is my account:

[http://github.com/andreasmang](http://github.com/andreasmang)


### SSH keys

In order to avoid having to type your password to push or pull code from and to GitHub, create an SSH key:

* To check if you already have an SSH key do the following
	1. Open Terminal
	2. Enter `ls -l ~/.ssh`
	3. Check if directly contains files that store a public SSH key. By default these file names are `id_rsa.pub`, `id_ecdsa.pub`, or `id_ed25519.pub`

* If you do not have an existing public or private key pair, create an SSH key as follows
	1. Open Terminal
	2. Enter `ssh-keygen -t rsa -b 4096 -C "youremail@email.com"`
	3. Press enter when asked about where to safe the file, and when asked for a passphrase (i.e., hit enter 3 times)
	4. Copy the content of the file ~/.ssh/id_rsa.pub and enter it on GitHub (in your account options: "settings -> SSH and GPG keys")

A detailed description can be found [here](https://docs.github.com/en/github/authenticating-to-github/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent#generating-a-new-ssh-key)
