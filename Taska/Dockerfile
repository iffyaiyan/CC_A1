FROM nginx:latest

# Remove the default Nginx config and add a custom one
RUN rm /etc/nginx/conf.d/default.conf
COPY nginx.conf /etc/nginx/conf.d/

# Copy the custom HTML file
COPY index.html /usr/share/nginx/html/ELL887/index.html

# Expose port 80
EXPOSE 80

# Start Nginx
CMD ["nginx", "-g", "daemon off;"]
