FROM php:7.4-fpm
# install composer
RUN cd /usr/bin && curl -s http://getcomposer.org/installer | php && ln -s /usr/bin/composer.phar /usr/bin/composer

RUN apt-get update \
&& apt-get install -y \
git \
zip \
unzip \
vim
#npm install
COPY --from=node:10.22 /usr/local/bin /usr/local/bin
COPY --from=node:10.22 /usr/local/lib /usr/local/lib

RUN apt-get update \
	&& apt-get install -y libpq-dev \
	&& docker-php-ext-install pdo_mysql pdo_pgsql \
    && apt-get install -y locales \
    && locale-gen ja_JP.UTF-8 \
	&& localedef -f UTF-8 -i ja_JP ja_JP.utf8
ENV LANG ja_JP.UTF-8
ENV LANGUAGE ja_JP:ja
ENV LC_ALL=ja_JP.UTF-8
