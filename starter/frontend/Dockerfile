FROM node:18-alpine

ARG REACT_APP_MOVIE_API_URL
ENV REACT_APP_MOVIE_API_URL=${REACT_APP_MOVIE_API_URL}

WORKDIR /app

# Copy dependdency files
COPY package*.json ./

# Install packages
RUN npm ci --fetch-retries=5 --fetch-retry-mintimeout=20000 --fetch-retry-maxtimeout=120000 --fetch-timeout=600000

# Copy code
COPY . .

# Build the app
RUN npm run build

# Expose the port used by the React app
EXPOSE 3000

# Start the React app when the container starts
CMD ["npm", "run", "serve"]