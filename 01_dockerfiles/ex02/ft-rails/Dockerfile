# **************************************************************************** #
#                                                                              #
#                                                         :::      ::::::::    #
#    Dockerfile                                         :+:      :+:    :+:    #
#                                                     +:+ +:+         +:+      #
#    By: kchen2 <kchen2@student.42.fr>              +#+  +:+       +#+         #
#                                                 +#+#+#+#+#+   +#+            #
#    Created: 2019/08/21 16:39:35 by kchen2            #+#    #+#              #
#    Updated: 2019/08/28 14:54:23 by kchen2           ###   ########.fr        #
#                                                                              #
# **************************************************************************** #

FROM ruby:2.6.2

RUN apt-get update && apt-get install -y \
    build-essential \
    libpq-dev \
    nodejs \
    sqlite3 \
    gem

RUN gem install bundler --no-document
RUN gem install rails --no-document
RUN gem install rake -v 12.3.2 --no-document


ONBUILD COPY app /opt/app
ONBUILD WORKDIR /opt/app
ONBUILD EXPOSE 3000
ONBUILD RUN bundle install
ONBUILD RUN rake _12.3.2_ db:migrate
ONBUILD RUN rake _12.3.2_ db:seed
ONBUILD RUN rake _12.3.2_
