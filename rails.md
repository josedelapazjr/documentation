
##How to install Ruby

1. Install homebrew

		> ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
		
2. We're going to use rbenv to install and manage our Ruby versions.

		> brew install rbenv ruby-build

3. Add rbenv to bash so that it loads every time you open a terminal

		echo 'if which rbenv > /dev/null; then eval "$(rbenv init -)"; fi' >> ~/.bash_profile
		source ~/.bash_profile

4. Install ruby

		> rbenv install 2.3.1
		> rbenv global 2.3.1
		> ruby -v

## How to install Rails

1. Install rails

		> sudo gem install rails -v 4.2.6
		
2. Rails is now installed, but in order for us to use the rails executable, we need to tell rbenv to see it:

		> rbenv rehash
		
3. Check installed rails version

		> rails -v

## How to install Postgres

1. Install postgres

		> brew install postgresql
		
2. To have launchd start postgresql now and restart at login:

		> brew services start postgresql

## How to test setup
1. Create a sample rails project

		> rails new sample -d postgresql
		
2. Run bundle

		> cd sample
		> bundle install -V
		
	Note: If error occurred on bundle install that is related to pg, do the following to install pg gem:

		> sudo su
		> env ARCHFLAGS="-arch x86_64" gem install pg
		
3. Create the database

		> rake db:create

4. Run the rails server

		> rails s
	
## How to install Redis
1. Install redis

		> brew install redis
		
2. Run the server

		> redis-server
		
3. Monitor the redis

		> redis-cli monitor
		
4. Clear redis

		> redis-cli flushall	
