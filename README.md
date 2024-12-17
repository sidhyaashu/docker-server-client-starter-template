# Step 1: Create Next.js Project Using Docker:
```bash
docker run -it --rm -v ${PWD}:/app -w /app node:18-alpine npx create-next-app@latest client
```

# Dockerfile for Next.js (in client folder):
```dockerfile
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

```

# Step 2: Create the Express Server:
```bash
mkdir server
cd server
```

# Create a new package.json and install Express using Docker:
```bash
docker run -it --rm -v ${PWD}:/app -w /app node:18-alpine npm init -y
```

# For single dependencies:
```bash
docker run -it --rm -v ${PWD}:/app -w /app node:18-alpine npm install express
```

# Now manually create dependencies in both client and server and add required dependencies like:
1. client/dependencies.txt
```plaintext
axios
react-icons
```
2. server/dependencies.txt
```plaintext
express
nodemon
cors
dotenv
```


# Step 3: Create Dockerfiles for Next.js and Express
# Dockerfile for Next.js (in client folder):
```dockerfile
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

```

# Dockerfile for Express (in server folder):
```dockerfile
# Use Node.js image
FROM node:18-alpine

# Set the working directory for the Express server
WORKDIR /app

# Copy package.json and package-lock.json
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the Express server files
COPY . .

# Expose port 4000 for the Express server
EXPOSE 4000

# Run the Express server
CMD ["node", "index.js"]

```

# Step 4: Combine Everything with Docker Compose (docker-compose.yml)

```yaml
version: "3.8"

services:
  nextjs-app:
    container_name: nextjs-dev
    build: ./client
    ports:
      - "3000:3000"
    volumes:
      - ./client:/app
      - /app/node_modules
    command: ["npm", "run", "dev"]

  express-server:
    container_name: express-dev
    build: ./server
    ports:
      - "4000:4000"
    volumes:
      - ./server:/app
      - /app/node_modules
    command: ["node", "index.js"]

```

# Folder Structure
```plaintext
/project-root
    ├── docker-compose.yml
    ├── my-next-app
    │   ├── Dockerfile
    │   ├── dependencies.txt
    │   ├── package.json
    │   └── (other Next.js app files)
    ├── server
    │   ├── Dockerfile
    │   ├── dependencies.txt
    │   ├── package.json
    │   └── (other Express server files)
```


# Step 5: Build and Run Both Containers
```bash
docker-compose up --build
```



# Example: Install Multiple Dependencies
1. For Next.js Project:
```bash
docker-compose run nextjs-app npm install axios react-icons
```
2. For Express Server:
```bash
docker-compose run express-server npm install express nodemon cors dotenv
```




# To Stop the Server:
```bash
docker-compose down
```


```bash
npm i lucide-react uuid dotenv date-fns framer-motion react-hook-form zod @hookform/resolvers @hello-pangea/dnd --legacy-peer-deps
npm i -D @types/node @types/uuid --legacy-peer-deps

npx shadcn@latest init -d
npx shadcn@latest add accordion avatar button card dialog form input label navigation-menu popover progress select sidebar separator sheet skeleton switch table tabs textarea toggle tooltip


npm i -D prettier-plugin-tailwindcss --legacy-peer-deps
```