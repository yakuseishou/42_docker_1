# **************************************************************************** #
#                                                                              #
#                                                         :::      ::::::::    #
#    Dockerfile                                         :+:      :+:    :+:    #
#                                                     +:+ +:+         +:+      #
#    By: kchen2 <kchen2@student.42.fr>              +#+  +:+       +#+         #
#                                                 +#+#+#+#+#+   +#+            #
#    Created: 2019/08/13 14:36:33 by kchen2            #+#    #+#              #
#    Updated: 2019/09/10 20:22:58 by kchen2           ###   ########.fr        #
#                                                                              #
# **************************************************************************** #

FROM debian
ENV TS3SERVER_LICENSE=accept

WORKDIR home/teamspeak
EXPOSE 9987/udp 10011 30033

RUN apt-get update && apt-get upgrade -y \
&& apt-get install -y wget bzip2 \
&& wget http://dl.4players.de/ts/releases/3.8.0/teamspeak3-server_linux_amd64-3.8.0.tar.bz2 \
&& tar -xvf teamspeak3-server_linux_amd64-3.8.0.tar.bz2

WORKDIR teamspeak3-server_linux_amd64

ENTRYPOINT sh ts3server_minimal_runscript.sh