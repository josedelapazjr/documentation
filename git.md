##How to install GIT in MAC

###Install GIT
1. Type git

		> git

2. Select "Install" to install XCode tool that includes thet GIT module.

### Setup GIT

1. Initialize account

		> git config --global color.ui true
		> git config --global user.name "YOUR NAME"
		> git config --global user.email "YOUR@EMAIL.com"
		
2. Generate SSH kesy

		> ssh-keygen -t rsa
		
3. Copy the SSH key and paste it in the SSH keys in your repository.

		> pbcopy < ~/.ssh/id_rsa.pub		
		
4. Confirm if the SSH is working:

		> ssh -T git@github.com
		> ssh -T git@bitbucket.com
		

