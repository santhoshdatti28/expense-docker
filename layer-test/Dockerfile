FROM node:20.18.3-alpine3.21 AS builder
WORKDIR /opt/backend
COPY package.json .
COPY *.js .
RUN npm install


FROM node:20.18.3-alpine3.21
RUN addgroup -S expense && adduser -S expense -G expense && \
    mkdir /opt/backend && \
    chown -R expense:expense /opt/backend
WORKDIR /opt/backend
# ENV DB_HOST="localhost"
ENV DB_HOST="mysql"
COPY --from=builder /opt/backend /opt/backend
USER expense
CMD ["node", "index.js"]