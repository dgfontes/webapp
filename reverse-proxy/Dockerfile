FROM nginx:1.17
COPY ./nginx.conf 	/etc/nginx/nginx.conf
COPY ./.htpasswd  	/etc/nginx/conf.d/.htpasswd
WORKDIR	/etc/ssl/private/
RUN  	apt-get update && apt-get install -y openssl && \
	openssl genrsa -des3 -passout pass:qwerty -out proxy.pass.key 2048 && \
	openssl rsa -passin pass:qwerty -in proxy.pass.key -out proxy.key && \
	rm proxy.pass.key && \
	openssl req -new -key proxy.key -out proxy.csr \
	 -subj "/C=US/ST=Pennsylvania/L=Media/O=OrgName/OU=IT Department/CN=reverse-proxy.com" && \
	openssl x509 -req -days 365 -in proxy.csr -signkey proxy.key -out proxy.crt
# COPY ./proxy.crt 	/etc/ssl/private/proxy.crt
# COPY ./proxy.key 	/etc/ssl/private/proxy.key

WORKDIR 	/etc/nginx/conf.d/
RUN		mkdir sites-available
RUN		mkdir sites-enabled
RUN		rm -rf /etc/nginx/conf.d/default.conf

COPY ./webapp.conf 	/etc/nginx/conf.d/sites-available/webapp.conf
RUN 		ln -s /etc/nginx/conf.d/sites-available/webapp.conf /etc/nginx/conf.d/sites-enabled/
EXPOSE		80 443
