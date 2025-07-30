# Build stage
FROM golang:1.18 AS builder

WORKDIR /app

COPY main.go .

RUN go mod init guestbook
RUN go mod tidy

RUN go build -o main main.go

# Final Stage
FROM ubuntu:18.04

# Copy the static files to the appropriate directory
COPY --from=builder /app/main /app/guestbook
ADD public/index.html /app/public/index.html
ADD public/script.js /app/public/script.js
ADD public/style.css /app/public/style.css
ADD public/jquery.min.js /app/public/jquery.min.js

WORKDIR /app
# Expose port 3000
EXPOSE 3000



# Command to run the application
CMD ["./guestbook"]

