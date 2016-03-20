### rubyをソースコードからインストール
```
# yum -y install zlib-devel openssl-devel sqlite sqlite-devel gcc*

1.9.3系
# wget http://cache.ruby-lang.org/pub/ruby/1.9/ruby-1.9.3-p551.tar.gz

2.0系
# wget http://cache.ruby-lang.org/pub/ruby/2.0/ruby-2.0.0-p598.tar.gz

2.1.5系
# wget http://cache.ruby-lang.org/pub/ruby/2.1/ruby-2.1.5.tar.gz

2.2系
# wget http://cache.ruby-lang.org/pub/ruby/2.2/ruby-2.2.0.tar.gz

#tar xvf <wgetしたファイル>.tar.gz

#cd <解凍したディレクトリ>
# ./configure
# make
# make install
# ruby -v
# gem -v
# ln -s /usr/local/bin/ruby /usr/bin/ruby （rubyのパス調整）
```

### rbenv を使って ruby をインストール
```
# yum install -y readline-deve
# yum -y install git
# git clone https://github.com/sstephenson/rbenv.git ~/.rbenv

--- 環境設定 ---
# echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bash_profile
 -> PATH に追加
# echo 'eval "$(rbenv init -)"' >> ~/.bash_profile
 -> .bash_profile に追加
# exec $SHELL -l
 -> 上記設定の再読み込み
----------------

# rbenv --version
# git clone https://github.com/sstephenson/ruby-build.git ~/.rbenv/plugins/ruby-build
# rbenv install --list
 -> 利用可能なrubyのバージョンを表示
# rbenv install -v <バージョン>
# rbenv rehash
 -> 設定の再読み込み
# rbenv versions
 -> インストールされているruby一覧を確認
# rbenv global <インストールしたバージョン>
 -> 先ほどインストールした最新版に設定
# ruby -v
 -> rubyのバージョンを確認
```


### rvmを用いたRubyのインストール
```
# gpg2 --keyserver hkp://keys.gnupg.net --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3
これを実施しないとrvmのインストールの際に「No public key」というエラーが発生することがある（参考：RVMによるrubyのインストール、vagrantのCentOS環境で。 on @Qiita http://qiita.com/uedatakeshi/items/8138d00a762225f01aa3）

rvmのインストール
# curl -sSL https://get.rvm.io | sudo bash -s stable

profileフォルダ内のスクリプトの実行
# source /etc/profile

利用可能なRubyのバージョンを確認
# rvm list -r

ここでインストール可能なRubyのバージョンを確認して、インストールするバージョンを決める。今回は、
# Remote rubies available:

   jruby-1.7.19
   jruby-src-1.7.19
   ruby-1.9.3-p194
   ruby-1.9.3-p286
   ruby-1.9.3-p327
   ruby-1.9.3-p362
   ruby-1.9.3-p392
   ruby-1.9.3-p429
   ruby-1.9.3-p448
   ruby-1.9.3-p484
   ruby-1.9.3-p547
   ruby-1.9.3-p551
   ruby-2.0.0-p0
   ruby-2.0.0-p195
   ruby-2.0.0-p247
   ruby-2.0.0-p353
   ruby-2.0.0-p481
   ruby-2.0.0-p576
   ruby-2.0.0-p598
   ruby-2.1.0
   ruby-2.1.2
   ruby-2.1.3
   ruby-2.1.5
   ruby-2.2.0
   ruby-2.2.1
と表示されたので、その中で最新版である2.2.1を導入した。
Rubyのインストール

# rvm install ruby-2.2.1
インストール確認兼バージョン確認
# ruby -v
```

### ソースコードからインストールしたRubyをアンインストール
```
# wgetで取得したrubyフォルダに移動
# head .installed.list
# cat .installed.list | xargs rm -rf
# ruby
-> command not foundと出れば成功
```
