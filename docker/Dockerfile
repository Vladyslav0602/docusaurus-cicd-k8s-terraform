# Use the minimal nginx image
FROM nginx:stable-alpine

# Remove the default configuration
RUN rm /etc/nginx/conf.d/default.conf

# Copy our nginx.conf
COPY docker/nginx.conf /etc/nginx/nginx.conf

# Copy the built site into the container
# Considering the relative path from the context of the build
COPY my-doc-site/build /usr/share/nginx/html

# Expose the port
EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
