FROM php:8.3.7-fpm

ARG user
ARG uid
ARG workdir

RUN apt-get update && apt-get install -y --no-install-recommends \
	cron \
	unzip \
	zip \
	&& apt-get clean && rm -rf /var/lib/apt/lists/*

COPY --from=composer:2.8.4 /usr/bin/composer /usr/local/bin/composer

RUN useradd -G www-data,root -u $uid -d /home/$user $user \
	&& mkdir -p /home/$user/.composer \
	&& chown -R $user:$user /home/$user \
	&& mkdir -p $workdir \
	&& chown $user:$user $workdir

WORKDIR $workdir
USER $user
