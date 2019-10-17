# **************************************************************************** #
#                                                                              #
#                                                         :::      ::::::::    #
#    Dockerfile                                         :+:      :+:    :+:    #
#                                                     +:+ +:+         +:+      #
#    By: kchen2 <kchen2@student.42.fr>              +#+  +:+       +#+         #
#                                                 +#+#+#+#+#+   +#+            #
#    Created: 2019/08/13 22:49:05 by kchen2            #+#    #+#              #
#    Updated: 2019/09/10 20:30:40 by kchen2           ###   ########.fr        #
#                                                                              #
# **************************************************************************** #

#   docker-machine create -d virtualbox --virtualbox-memory 4096 default   #
#    docker-machine stop                                                   #                                                       
#    VBoxManage modifyvm default --cpus 2                                  #                       
#    VBoxManage modifyvm default --memory 4096                             #                           
#    docker-machine start                                                  #       


FROM debian:9

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update && apt-get install -y --no-install-recommends apt-utils && apt-get upgrade -y
RUN apt-get install -y wget openssh-server ca-certificates
RUN apt-get install -y postfix
RUN wget https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.deb.sh
RUN chmod 777 script.deb.sh
RUN ./script.deb.sh
RUN apt-get update && apt-get install -y gitlab-ce

EXPOSE 443 80 22

ENTRYPOINT (/opt/gitlab/embedded/bin/runsvdir-start &) && gitlab-ctl reconfigure && tail -f /dev/null

# build instruction
# docker build -t my-gitlab .
# docker run -it -p 8080:80 -p 8022:22 -p 8443:443 --privileged my-gitlab