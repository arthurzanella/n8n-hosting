# Start from the official n8n image
FROM n8nio/n8n

# Switch to root to install custom nodes and dependencies
USER root

# Install the custom Oracle nodes globally
RUN npm_config_user=root npm install -g n8n-nodes-oracle-database

# Define the environment variable for custom extensions
ENV N8N_CUSTOM_EXTENSIONS="/usr/local/lib/node_modules/n8n-nodes-oracle-database"


