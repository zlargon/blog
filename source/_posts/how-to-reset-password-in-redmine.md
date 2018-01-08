title: "How to Reset Password in Redmine"
date: 2018-01-07 20:41:48
categories:
	- Redmine
tags:
	- Redmine
---

{% asset_img "redmine_cannot_login.png" "Cannot Login" %}

## 1. Login MySQL and find the user id

``` bash
mysql -u root -p             # login MySQL
 
mysql> use redmine;          # choose redmine database
mysql> select * from users;  # show all users' information
```

<script src="https://asciinema.org/a/CVGxSJISAIqLaZReBchnuZsdX.js" id="asciicast-CVGxSJISAIqLaZReBchnuZsdX" async></script>

## 2. Go to the redmine folder and change the password

``` ruby
# start console
RAILS_ENV=production bundle exec rails c
 
# find your user
user = User.where(id: 1).first
 
# set new password
user.password = 'password'
user.password_confirmation = 'password'
 
# save changes
user.save!
```

<script src="https://asciinema.org/a/wDJLeBmAEQBaZPWzLVGcieeu8.js" id="asciicast-wDJLeBmAEQBaZPWzLVGcieeu8" async></script>

## 3. Login redmine and change the password

Now, you can login your account with password `password`, and then you can change your password in __My Account__ page.

{% asset_img "redmine_change_password.png" "Change Password" %}

# Reference

* https://stackoverflow.com/a/30666786/2802074
