# heroku --version

查看目前版本

# heroku update

upodate version.

# heroku login

本地登入，会跳转到网页进行授权登入

# heroku login -i

服务器上登入,登入后，命令行会将您的电子邮件地址和API token 保存到~/.netrc 中。

# heroku auth:token

查看自己的token

# heroku create

新建一个项目,该方法会新建一个随机名字的app

# mkdir example
# cd example
# git init
# heroku apps:create example

创建一个名为“ example”的新应用

# cd my-project/
# git init
# heroku git:remote -a my-project

已经有Repository，可以 在新目录或现有目录中初始化git存储库

# heroku apps:destroy fierce-sands-29965

删除你的app

# heroku git:clone -a test-app

复制你的Repository 到本地

# git add .
# git commit -am "make it better"
# git push heroku master

如何部署你的应用

# heroku fork --from sourceapp --to targetapp

需要fork 一个production出来，使用heroku fork复制现有的应用程序，包括加载项，config vars和Heroku Postgres数据。

# heroku apps

查看现有的app

# heroku apps:favorites

查看自己收藏的应用(favorited apps)


# heroku apps:info your-app

查看你的app信息

# heroku config -a sfdc-nodejs

需要查看你的Heroku配置变量

# heroku config:set -a sfdc-nodejs RAILS_ENV=staging RACK_ENV=staging

添加RAILS_ENV和RACK_ENV都为staging


# heroku config:unset -a pernod-ricard-sfdc-nodejs  RAILS_ENV

删除变量

# heroku dyno:restart -a your-app

重启dyno


# heroku logs -a your-app

查看日志Logs

# heroku pg -a your-app

查看postgresql 数据库信息

# heroku apps:rename --app oldname newname

对app进行重命名,名字需要用小写。同时，如果修改名字，所有本地Git URL都得修改。

# heroku regions

展示Heroku 服务器的地区

# heroku run -a yourApp node nodeFile.js

假如在yourApp 下面有nodeFile.js，需要执行，可以执行如下代码

# heroku sessions

查看目前sessions

# heroku addons

查看目前的add-ons

# heroku addons:create  heroku-postgresql:hobby-dev  -a yourApp

新建一个PostgreSQL数据库

# heroku addons:create  scheduler:standard -a yourApp

新建一个scheduler
