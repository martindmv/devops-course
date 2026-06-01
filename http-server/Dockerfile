# Dockerfile
FROM httpd:2.4-alpine

# Copie de la page d'accueil par défaut
COPY index.html /usr/local/apache2/htdocs/

# Remplacement de la configuration par défaut par notre version configurée en Reverse Proxy
COPY httpd.conf /usr/local/apache2/conf/httpd.conf