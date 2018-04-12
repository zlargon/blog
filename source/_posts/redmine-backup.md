title: "Redmine Backup"
date: 2018-04-11 19:08:32
categories:
	- Redmine
tags:
	- Redmine
	- MySQL
---

{% asset_img "redmine_and_mysql.png" "Redmine and MySQL" %}

### Objective

Backup Redmine or move Redmine to other server

## 1. Use `mysqldump` to backup `redmine` database in MySQL

``` bash
$ mysqldump -u root -h localhost -p redmine > redmine_backup.sql
```

<script src="https://asciinema.org/a/0xyeGjbQi6YVOUL8oHy2KUGmr.js" id="asciicast-0xyeGjbQi6YVOUL8oHy2KUGmr" async></script>

## 2. move your whole Redmine Folder with `redmine_backup.sql` to your new server

You would need to install Redmine first. If not, please read the article {% link "How to install Redmine" https://zlargon.github.io/blog/Redmine/install-redmine-on-mac/ %}.

## 3. create a `redmine_backup` database in MySQL and import the `redmine_backup.sql`

``` sql
CREATE DATABASE redmine_backup CHARACTER SET utf8;
```

``` bash
$ mysql -u root -h localhost -p redmine_backup < redmine_backup.sql
```

<script src="https://asciinema.org/a/asV0WMtsamiQ8YVEBRYQixCkR.js" id="asciicast-asV0WMtsamiQ8YVEBRYQixCkR" async></script>

## 5. Setup the config file in Redmine Folder

Add `backup` config to `config/database.yml`:

``` yml
backup:                     # production → backup
  adapter: mysql2
  database: redmine_backup  # redmine → redmine_backup
  host: localhost
  port: 3307
  username: root
  password: {yourpassword}
  encoding: utf8
```

<script src="https://asciinema.org/a/idldIYm2SiKm3aF1REqJ0wyY8.js" id="asciicast-idldIYm2SiKm3aF1REqJ0wyY8" async></script>

## 6. Run Redmine Server

``` bash
mysql.server restart
bundle exec rails server webrick -e backup -p 5432  # port 5432
```

## Reference:

https://zlargon.github.io/blog/Redmine/install-redmine-on-mac/
https://youtu.be/2-_ZU7N3XEM
