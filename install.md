## 安装步骤
1. install rbenv (easy)
* 不要忘了添加rbenv init 到 .bash_profiel 或 .zshrc
2. install ruby.rbenv 直接install会失败,可能是rbenv到bug？

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

