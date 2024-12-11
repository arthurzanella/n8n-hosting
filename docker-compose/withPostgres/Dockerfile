# Start from the official n8n image
FROM n8nio/n8n

# Switch to root to install custom nodes and dependencies
USER root

# Install the custom Oracle nodes globally
RUN npm_config_user=root npm install -g n8n-nodes-oracle-database

# Define the environment variable for custom extensions
ENV N8N_CUSTOM_EXTENSIONS="/usr/local/lib/node_modules/n8n-nodes-oracle-database"

# Install Oracle Instant Client dependencies
RUN apt-get update && apt-get install -y \
    libaio1 \
    unzip \
    && rm -rf /var/lib/apt/lists/*

# Install Oracle Instant Client
RUN curl -o instantclient.zip https://download.oracle.com/otn_software/linux/instantclient/217000/instantclient-basic-linux.x64-21.7.0.0.0dbru.zip && \
    unzip instantclient.zip && \
    mv instantclient_21_7 /usr/lib/oracle/21.7/client64 && \
    rm instantclient.zip

# Set environment variables
ENV LD_LIBRARY_PATH=/usr/lib/oracle/21.7/client64/lib:$LD_LIBRARY_PATH
ENV PATH=/usr/lib/oracle/21.7/client64/bin:$PATH

# Install node-oracledb
RUN npm install oracledb

# Copy your application code into the container
# COPY . /app

# WORKDIR /app

# Install your Node.js dependencies
RUN npm install

# Expose the app's port (example: 3000)
# EXPOSE 3000

# Command to run your application
# CMD ["node", "app.js"]

