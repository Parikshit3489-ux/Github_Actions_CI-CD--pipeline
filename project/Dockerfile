FROM nginx:1.25-alpine

ENV NGINX_ENV=production
# Create non-root user
RUN adduser -D -u 1000 webuser

# Create directories with correct ownership
RUN mkdir -p /tmp/nginx && chown webuser:webuser /tmp/nginx
# Remove default content
RUN rm -rf /usr/share/nginx/html/*

# Copy custom NGINX config
COPY nginx.conf /etc/nginx/nginx.conf

# Copy portfolio website
COPY public/ /usr/share/nginx/html/

# Set permissions
RUN chown -R webuser:webuser /usr/share/nginx/html && \
    chmod -R 755 /usr/share/nginx/html

# Switch to non-root user
USER webuser

# Use non-privileged port
EXPOSE 8080

# Start NGINX with custom PID location
CMD ["nginx", "-g", "daemon off;"]