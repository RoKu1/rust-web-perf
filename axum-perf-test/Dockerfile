# use the default dart image as the build image
FROM rust AS builder

# copy the current folder into the build folder
COPY . /app

# set the work directory
WORKDIR /app

# build the app
RUN cargo build --release

# use a slim image
FROM debian:bullseye-slim

# copy the runtime files
COPY --from=builder /app/target/release/axum-perf-test /app/axum 
WORKDIR /app

# start the dart server
CMD ["./axum"]