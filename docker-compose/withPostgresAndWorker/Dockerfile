# Start from the official n8n image
FROM n8nio/n8n

# Switch to root to install custom nodes and dependencies
USER root

# Install required dependencies for Oracle Instant Client
RUN apt-get update && \
    apt-get install -y libaio1 wget unzip && \
    rm -rf /var/lib/apt/lists/*

# Download and install Oracle Instant Client
RUN wget https://download.oracle.com/otn_software/linux/instantclient/instantclient-basiclite-linuxx64.zip && \
    unzip instantclient-basiclite-linuxx64.zip -d /opt/oracle && \
    rm instantclient-basiclite-linuxx64.zip && \
    echo "/opt/oracle/instantclient_19_8" > /etc/ld.so.conf.d/oracle-instantclient.conf && \
    ldconfig

# Install the custom Oracle nodes globally
RUN npm_config_user=root npm install -g n8n-nodes-oracle

# Define the environment variable for custom extensions
ENV N8N_CUSTOM_EXTENSIONS="/usr/local/lib/node_modules/n8n-nodes-oracle"

# Switch back to the default user for security
USER node
