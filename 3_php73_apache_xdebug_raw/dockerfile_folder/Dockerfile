FROM php:7.3-apache
LABEL maintainer="raja@discountpartysupplies.com.au"

# RUN docker-php-ext-install mysqli
RUN pecl install xdebug-2.7.0
RUN docker-php-ext-enable xdebug
RUN echo "xdebug.remote_enable=1" >> /usr/local/etc/php/php.ini

# Set to 1 to turn it on for every request
RUN echo "xdebug.profiler_enable=0" >> /usr/local/etc/php/php.ini
# Let's use a GET/POST parameter to turn on the profiler
RUN echo "xdebug.profiler_enable_trigger = 1" >> /usr/local/etc/php/php.ini
# The GET/POST value we will pass; empty for any value
RUN echo "xdebug.profiler_enable_trigger_value = """ >> /usr/local/etc/php/php.ini
# Output cachegrind files to /tmp so our system cleans them up later
RUN echo "xdebug.profiler_output_dir = "/tmp"" >> /usr/local/etc/php/php.ini
RUN echo "xdebug.profiler_output_name = "cachegrind.out.%p"" >> /usr/local/etc/php/php.ini

# RUN apt-get update && apt-get install -y libmcrypt-dev \
#   && pecl install mcrypt-1.0.2 \
#   && docker-php-ext-enable mcrypt