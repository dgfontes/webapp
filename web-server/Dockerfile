FROM httpd:2.4
ENV CONF 	/usr/local/apache2/conf
ENV HTDOCS	/usr/local/apache2/htdocs
COPY ./httpd.conf	$CONF
WORKDIR /usr/local/apache2/conf
RUN	apt-get update && apt-get install -y openssl apt-utils && \
	openssl genrsa -des3 -passout pass:qwerty -out server.pass.key 2048 && \
	openssl rsa -passin pass:qwerty -in server.pass.key -out server.key && \
	rm server.pass.key && \
	openssl req -new -key server.key -out server.csr \
	 -subj "/C=US/ST=Pennsylvania/L=Media/O=OrgName/OU=IT Department/CN=web-server.com" && \
	openssl x509 -req -days 365 -in server.csr -signkey server.key -out server.crt
# COPY ./server.*		$CONF/
COPY ./httpd-ssl.conf	$CONF/extra/httpd-ssl.conf
COPY ./index.html	$HTDOCS/index.html
EXPOSE 80 443
