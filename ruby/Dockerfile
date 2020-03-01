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
  ncurses-devel &&\
  yum clean all

#rbenv
RUN git clone https://github.com/sstephenson/rbenv.git ~/.rbenv

#rbenvのPATH登録
ENV PATH $PATH:~/.rbenv

#ruby-buildクローン、rubyインストール・設定反映・グローバルver設定・
#バンドラーインストール・railsインストール、sasscインストール、sqllite3インストール
RUN git clone https://github.com/sstephenson/ruby-build.git ~/.rbenv/plugins/ruby-build
RUN ~/.rbenv/bin/rbenv install -v 2.7.0
RUN ~/.rbenv/bin/rbenv rehash
RUN ~/.rbenv/bin/rbenv global 2.7.0


RUN ~/.rbenv/shims/gem install bundle
RUN ~/.rbenv/shims/gem install sassc -v '2.2.1' --source 'https://rubygems.org/'
RUN ~/.rbenv/shims/gem install sqlite3 -v '1.4.2' --source 'https://rubygems.org/'
RUN ~/.rbenv/shims/gem install rails

EXPOSE 80

CMD /bin/bash
