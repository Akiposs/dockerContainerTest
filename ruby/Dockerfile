FROM centos:centos8

LABEL maintainer="Akipon <test@test.com>"

# 必要なライブラリダウンロード
RUN yum update -y && yum install -y \
  sudo\
  git\
  make\
  bzip2\
  gcc\
  openssl-devel\
  readline-devel\
  zlib-devel\
  gcc-c++\
  sqlite-devel\
  mercurial\
  ncurses-devel
  
#rbenvのPATH登録
ENV PATH $PATH:~/.rbenv/bin

#rbenv・ruby-buildクローン、rubyインストール・設定反映・グローバルver設定・
#バンドラーインストール・railsインストール、sasscインストール、sqllite3インストール
RUN git clone https://github.com/sstephenson/rbenv.git ~/.rbenv && \
git clone https://github.com/sstephenson/ruby-build.git ~/.rbenv/plugins/ruby-build && \
  rbenv install -v 2.7.0 && \
  rbenv rehash && \
  rbenv global 2.0.0-p353 && \
  gem install bundle && \
  gem install rails && \
  gem install sassc -v '2.2.1' --source 'https://rubygems.org/' && \
  gem install sqlite3 -v '1.4.2' --source 'https://rubygems.org/'
EXPOSE 80
