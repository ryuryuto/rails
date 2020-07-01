## 安装步骤
### Mac OS
1. install rbenv (easy)
* 不要忘了添加rbenv init 到 .bash_profiel 或 .zshrc
2. install ruby.rbenv 直接install会失败,可能是brew版本的rbenv的bug？

解决方法：增加参数

```shell script
 RUBY_CONFIGURE_OPTS="--with-openssl-dir=/usr/local/opt/openssl@1.1 --with-readline-dir=$(brew --prefix readline)" rbenv install -v 2.6.3
```

3. after install ruby，then通过gem安装rails，直接无法安装，需要通过代理
```shell script
gem install rails -v 6.0.2.1 --http-proxy=ip:port
```

4. 通过rails new 创建新项目时要用到bundler，也需要代理，放到.zshrc中

```shell script
export http_proxy=http://127.0.0.1:1087
export HTTP_PROXY=$http_proxy
```
5. homebrew 添加代理
```shell script
export ALL_PROXY=http://127.0.0.1:1087
```

### ubuntu
1. 首先安装代理[Qv2ray](https://qv2ray.github.io/) 并根据文档配置好环境，确保使用代理 
* 可以使用appimage也可以通过deb
* install deb:
```shell
sudo apt install ./deb文件名
```
* uninstall deb:
```shell
sudo apt remove qv2ray
```
之后不再使用的依赖可以通过autoremove删除
```shell
sudo apt autoremove 
```
   
2. 参考官方文档安装[rbenv](https://github.com/rbenv/rbenv#basic-github-checkout)和[ruby-build](https://github.com/rbenv/ruby-build#ruby-build)
   注意：没有ruby-build,rbenv缺少install命令
3. 安装ruby
4. 安装rails
5. 安装[yarn](https://classic.yarnpkg.com/en/docs/install/#debian-stable)
6. rails new，这个时候很可能出错：
> sqlite3 can't compile

解决方法：
> You need the SQLite3 development headers for the gem’s native extension to compile against. You can install them by running (possibly with sudo):
```shell
apt-get install libsqlite3-dev
```
可能还会出错：
> rails 缺少 webpacker

解决方法:
```shell
rails webpacker:install
```
7. 至此可成功运行

