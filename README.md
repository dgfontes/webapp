# webapp
A simple web-server with a reverse-proxy built on docker

1. Start by downloading the content from GitHub;
2. Once downloaded, verify you have the following files and folders:
- docker-compose.yml file;
- reverse-proxy folder with the following files:
-- Dockerfile
-- .htpasswd
-- nginx.conf
-- webapp.conf 
- web-server folder with the following files:
-- Dockerfile
-- httpd.conf
-- httpd-ssl.conf
-- index.html
3. Assuming you have Docker Desktop for Mac installed on your machine, run the following command from your Terminal within the uncompressed content of the previously downloaded folder:
- docker-compose up -d
4. If no errors were observed, you should see all 12 steps completed for the reverse-proxy and all 9 steps completed for the web-server with the following last two lines shown:
- Creating reverse-proxy ... done
- Creating web-server    ... done
5. Simply access the application via http://localhost or https://localhost and enter the following credentials:
- admin/Password1

