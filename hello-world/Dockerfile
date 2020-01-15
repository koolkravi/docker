FROM nginx:alpine

# copy artifact build from the 'build environment'
COPY index.html /usr/share/nginx/html

# copy nginx configuration
#COPY ./nginx/nginx-default.conf /etc/nginx/conf.d/default.conf

# expose port 8080
EXPOSE 8080

# run nginx
CMD ["nginx", "-g", "daemon off;"] 