# Use the official Alpine Linux image as the base
FROM alpine:latest

# Install necessary tools and prerequisites
RUN apk update && \
    apk add --no-cache curl

# Install Docker inside the container
RUN apk add --update docker openrc
RUN rc-update add docker boot

# Clean up
RUN rm -rf /var/cache/apk/*

# Set up the entry point if needed
# ENTRYPOINT [ "your-entrypoint-command" ]
