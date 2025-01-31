# Use a base image with Apache
FROM httpd:alpine

# Install the necessary utilities (if needed) and enable mod_headers
RUN apk --no-cache add apache2-utils && \
    sed -i '/^#LoadModule headers_module/s/^#//g' /usr/local/apache2/conf/httpd.conf && \
    # Modify the existing Directory block or add a new one without duplication
    sed -i '/<Directory "\/usr\/local\/apache2\/htdocs">/a AllowOverride All' /usr/local/apache2/conf/httpd.conf

# Copy the local project files to the container
COPY . /usr/local/apache2/htdocs/

# Expose port 80 to access the container
EXPOSE 80

# Start Apache
CMD ["httpd", "-D", "FOREGROUND"]
