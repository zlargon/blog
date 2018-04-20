title: "Install Redmine on Mac"
date: 2017-10-10 19:46:51
categories:
	- Redmine
tags:
	- Redmine
---

{% asset_img "redmine.png" "redmine" %}

## 1. Install Brew & Git

```
# Brew
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
 
# Git
brew install git
```

## 2. Install and Setup MySQL (5.7.19)

```
brew install mysql
```

``` bash
mysql.server start           # start mysql server
mysqladmin -u root password  # enter your new passowrd at first time
mysql -u root -p             # login MySQL with password
```

``` sql
CREATE DATABASE redmine CHARACTER SET utf8mb4;
CREATE USER 'redmine'@'localhost' IDENTIFIED BY 'my_password';
GRANT ALL PRIVILEGES ON redmine.* TO 'redmine'@'localhost';
```

## 3. Download and Setup Redmine (3.4.2)

- [redmine-3.4.2.tar.gz](http://www.redmine.org/releases/redmine-3.4.2.tar.gz) (md5: 2980b80e9acc81c01c06adb86eb4f37d)

- Copy `config/database.yml.example` to `config/database.yml` and edit this file in order to configure your database settings for `production` environment.

``` yml
production:
  adapter: mysql2
  database: redmine
  host: localhost
  port: 3307
  username: root
  password: {yourpassword}
  encoding: utf8
```

## 4. Run Bundle

``` bash
sudo gem install bundler
 
# execute under redmine's folder
bundle install --without development test
bundle exec rake generate_secret_token
RAILS_ENV=production bundle exec rake db:migrate
RAILS_ENV=production bundle exec rake redmine:load_default_data
```

### Trouble Shooting:

(1) `mysql2 0.4.9`
```
An error occurred while installing mysql2 (0.4.9), and Bundler cannot continue.
Make sure that `gem install mysql2 -v '0.4.9'` succeeds before bundling.
```

Solution:
``` bash
xcode-select --install
```

(2) `rmagick 2.16.0`
```
Fetching rmagick 2.16.0
Installing rmagick 2.16.0 with native extensions
Errno::EACCES: Permission denied @ rb_sysopen - /usr/local/lib/ruby/gems/2.5.0/gems/rmagick-2.16.0/.editorconfig
An error occurred while installing rmagick (2.16.0), and Bundler cannot continue.
Make sure that `gem install rmagick -v '2.16.0'` succeeds before bundling.
 
In Gemfile:
  rmagick
```

Solution:
``` bash
brew install imagemagick@6
brew link --force imagemagick@6
echo 'export PATH="/usr/local/opt/imagemagick@6/bin:$PATH"' >> ~/.bash_profile
 
sudo gem install rmagick -v '2.16.0'
```

## 5. Start Redmine

``` bash
mysql.server restart
bundle exec rails server webrick -e production -p 5432  # port 5432
```

# Reference

* http://www.redmine.org/projects/redmine/wiki/RedmineInstall
* http://www.redmine.org/projects/redmine/wiki/RedmineInstallOSXMavericksServer
