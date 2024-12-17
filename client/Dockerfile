# Use Node.js image
FROM node:18-alpine

# Set the working directory for the Next.js app
WORKDIR /app

# Copy package.json and package-lock.json
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the Next.js app files
COPY . .

# Expose port 3000 for the Next.js app
EXPOSE 3000

# Run Next.js development server
CMD ["npm", "run", "dev"]