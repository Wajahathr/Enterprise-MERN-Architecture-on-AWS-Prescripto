# Base image lightweight alpine version use kar rahe hain
FROM node:18-alpine

# Container ke andar working directory set kar rahe hain
WORKDIR /app

# Pehle sirf package.json files copy karein (dependencies caching ke liye)
COPY package*.json ./

# Dependencies install karein
RUN npm install

# Ab baqi ka saara code copy karein
COPY . .

# Aapka backend jis port par chalta hai (mostly 4000 ya 5000 hota hai)
EXPOSE 4000

# Container start hone par yeh command chalegi
CMD ["node", "server.js"]