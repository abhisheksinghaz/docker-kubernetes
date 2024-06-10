FROM node:16-alpine as builder
WORKDIR '/app'
COPY package.json .
RUN npm install
COPY . .
RUN npm run build


# This is the second phase
FROM nginx
# This is for Elastic Beanstalk to know which port to expose
EXPOSE 80
# Copy the build folder from the previous stage
COPY --from=builder /app/build /usr/share/nginx/html
# Nginx image will start the server automatically
# So, we don't need to specify the CMD command
