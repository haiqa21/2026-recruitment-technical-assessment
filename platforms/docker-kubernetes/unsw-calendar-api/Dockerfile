# I will use a minimal nodejs image so that it is lightweight on the host server
FROM node:20-alpine

# For loose coupling with OS, I will imagine this ENV variable to lay down bits 
ENV APP_HOME=/app/nodejs

#Create directory if it doesn't exist
RUN mkdir -p ${APP_HOME}

# Set work directory to $APP_HOME
WORKDIR ${APP_HOME}

# Create group and user. -f ensures it doesn't throw error if already existing
RUN /usr/sbin/groupadd -f nodejs && /usr/sbin/useradd nodejs -g nodejs

# Copy package files first (for caching) 
COPY package*.json ./

# Copy the local unbuilt contents into docker image
# We are assuming CI/CD is doing this
COPY . .

# Install dependencies
RUN npm ci --only=production

# Compiles the Typescript (tsc)
RUN npm run build

# Ensure app directory is owned by nodejs user
RUN chown -R nodejs:nodejs ${APP_HOME}

# Switch to non-root user
USER nodejs

# Expose app port. Note: doesn't actually open the port
EXPOSE 3000

# Start the app
CMD ["npm", "run", "start"]