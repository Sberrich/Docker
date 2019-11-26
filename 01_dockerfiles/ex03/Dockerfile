 FROM  ubuntu

 ENV DEBIAN_FRONTEND=noninteractive

 RUN \
        apt-get update -y && apt-get upgrade -y \
        && apt-get install -y curl openssh-server ca-certificates postfix tzdata vim net-tools git\
        && curl -sS https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.deb.sh |  bash \
        && apt-get install gitlab-ce -y

WORKDIR /etc/gitlab/

RUN \
        echo "Port 1337" >> /etc/ssh/ssh_config \
        && echo "Port 1337" >> /etc/ssh/sshd_config \
        && mkdir /etc/gitlab/ssl \
        && cd /etc/gitlab/ssl \
        && openssl req -x509 -newkey rsa:4096 -keyout gitlab.key -out gitlab.crt -days 365 -nodes -subj "/C=MA/ST=khouribga/L=khouribga/O=x/OU=x/CN=x/emailAddress=darksamir2012@gmail.com" \
        && sed -i -e "s/external_url 'http:\/\/gitlab.example.com'/external_url 'https:\/\/10.12.3.7'/g" /etc/gitlab/gitlab.rb \
        && echo "gitlab_rails['gitlab_shell_ssh_port'] = 1337" >> /etc/gitlab/gitlab.rb \
        && echo "nginx['redirect_http_to_https'] = true" >> /etc/gitlab/gitlab.rb \
        && echo "nginx['ssl_certificate']" = '"/etc/gitlab/ssl/gitlab.crt"' >> /etc/gitlab/gitlab.rb \
        && echo "nginx['ssl_certificate_key']" = '"/etc/gitlab/ssl/gitlab.key"' >> /etc/gitlab/gitlab.rb

ENTRYPOINT service ssh restart && (/opt/gitlab/embedded/bin/runsvdir-start&) && gitlab-ctl reconfigure && gitlab-ctl tail

#https clone
#env GIT_SSL_NO_VERIFY=true git clone <link>
#env GIT_SSL_NO_VERIFY=true git push
