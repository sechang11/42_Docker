FROM nginx

RUN apt-get update && apt-get dist-upgrade -y && apt-get clean && apt-get autoclean install openssl -y

ENV WWW_PATH /usr/share/www/html

RUN mkdir -p $WWW_PATH && chown nginx:nginx $WWW_PATH

ARG PASSWORD=pass

# docker build -t --build-arg PASSWORD=pass123 .

RUN printf "user:$(openssl passwd -1 $PASSWORD)\n" >> $WWW_PATH/.htpasswd

RUN rm /etc/nginx/conf.d/default.conf

COPY etc/nginx/conf.d/main.conf /etc/nginx/conf.d/

COPY usr/share/www/html /usr/share/www/html/
