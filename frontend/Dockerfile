# Utilisation d'une image légère basée sur Alpine Linux
FROM public.ecr.aws/nginx/nginx:stable-alpine
# Copie du fichier HTML de l'application
COPY index.html /usr/share/nginx/html/index.html

# Suppression de la configuration par défaut de Nginx et ajout de la nôtre
RUN rm /etc/nginx/conf.d/default.conf
COPY nginx.conf /etc/nginx/conf.d/default.conf

# Le port standard pour un serveur Web
EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]