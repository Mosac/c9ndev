FROM centos:7.5.1804

RUN mkdir /app
WORKDIR /app

RUN yum groupinstall -y "Development tools" && \
  yum install -y epel-release && \
  yum install -y glibc-static which && \
  yum install -y openssl-devel readline-devel && \
  yum install -y gcc libxml2 libxml2-devel libcurl libcurl-devel libpng libpng-devel libmcrypt libmcrypt-devel libtidy libtidy-devel libxslt libxslt-devel openssl-devel bison libjpeg-turbo-devel readline-devel autoconf bzip2-devel libicu-devel

RUN git clone https://github.com/riywo/ndenv ~/.ndenv && \
  git clone https://github.com/riywo/node-build.git ~/.ndenv/plugins/node-build && \
  echo 'export PATH="$HOME/.ndenv/bin:$PATH"' >> ~/.bash_profile && \
  echo 'eval "$(ndenv init -)"' >> ~/.bash_profile

RUN git clone https://github.com/sstephenson/rbenv.git ~/.rbenv && \
  git clone https://github.com/sstephenson/ruby-build.git ~/.rbenv/plugins/ruby-build && \
  echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bash_profile && \
  echo 'eval "$(rbenv init -)"' >> ~/.bash_profile

RUN cd /usr/local/src && \
  git clone https://github.com/CHH/phpenv.git && \
  cd phpenv/bin/ && \
  ./phpenv-install.sh && \
  git clone https://github.com/CHH/php-build.git ~/.phpenv/plugins/php-build && \
  echo 'export PATH="$HOME/.phpenv/bin:$PATH"' >> ~/.bash_profile && \
  echo 'eval "$(phpenv init -)"' >> ~/.bash_profile

RUN source ~/.bash_profile && \
  ndenv install v10.5.0 && \
  ndenv install v6.14.3 && \
  rbenv install 2.5.1 && \
  phpenv install 7.2.7 && \
  phpenv install 7.1.19 && \
  phpenv install 7.0.30 && \
  phpenv install 5.6.36 && \
  phpenv install 5.5.38 && \
  phpenv install 5.4.45

RUN source ~/.bash_profile && \ 
  cd / && \
  git clone https://github.com/c9/core.git c9sdk && \
  cd c9sdk && \
  ndenv local v6.14.3 && \
  scripts/install-sdk.sh
