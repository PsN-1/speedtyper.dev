# Use Node.js 20 as base image
FROM node:20-alpine

# Install build dependencies for native modules
RUN apk add --no-cache python3 make g++

# Set working directory
WORKDIR /app

# Accept build arguments
ARG NEXT_PUBLIC_SERVER_URL
ARG NEXT_PUBLIC_EXPERIMENTAL_SERVER_URL

# Set environment variables for build
ENV NEXT_PUBLIC_SERVER_URL=$NEXT_PUBLIC_SERVER_URL
ENV NEXT_PUBLIC_EXPERIMENTAL_SERVER_URL=$NEXT_PUBLIC_EXPERIMENTAL_SERVER_URL

# Copy package files
COPY package.json yarn.lock ./

# Install dependencies
RUN yarn install --frozen-lockfile

# Copy source code
COPY . .

# Build the application
RUN yarn build

# Expose port 3001
EXPOSE 3001

# Start the application
CMD ["yarn", "start", "-p", "3001"]
