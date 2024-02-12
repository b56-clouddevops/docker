# Example Of Multi-Stage Docker Imaging
# Stage 1: Build the application
FROM golang:alpine as builder

# Create a directory for the build
RUN mkdir /build

# Add your source code to the build directory
ADD . /build/

# Set the working directory to the build directory
WORKDIR /build

# Build your application (e.g., compile Go code)
RUN go build -o main

# Stage 2: Create a minimal runtime image
FROM alpine

# Create a non-root user for running the application
RUN adduser -S -D -H -h /app appuser

# Set the user context to the non-root user
USER appuser

# Copy the compiled binary from the builder stage to the final image
COPY --from=builder /build/main /app/

# Set the working directory for the application
WORKDIR /app

# Specify the default command to run when the container starts
CMD ["./main"]