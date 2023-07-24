# Performance Benchmarking For Various Rust Web Frameworks

This repo is just a perf benchmark for various rust backend frameworks likes of actix, rocket, axum etc. Install Rust if you do not already have, use this [link](https://www.rust-lang.org/tools/install) for reference.


We do 3 types of tests in this repo for each framework.

1. Debug Mode Local deployment
2. Release Mode Local deployment
3. Release Mode Docker deployment
   
You can emulate these tests on you machine using tool called wkr (which was used for these tests), the actual numbers on your machine may differ based on the type and resources on system.

Below command was used to formulate all the results mentioned below.

`wkr -t 8 -c 256 -d 30s <url>`

Please install wkr if you do not have it already. 

Use this [link](https://medium.com/@felipedutratine/intelligent-benchmark-with-wrk-163986c1587f) for reference


# How to run simple text api benchmark
1. Debug Mode Local deployment
    Simply run `cargo run` from the directory of the framework of your choice

2. Release Mode Local deployment
    Simply run `cargo run --release` from the directory of the framework of your choice

3. Release Mode Docker deployment [mentioned for each of them, basic is as below]
    Run `docker build -t web-perf-<frameworkname> .`

    Eg. `docker build -t web-perf-actix .`

    Simply run `docker run --init -p 8080:8080 web-perf-<frameworkname>` from the directory of the framework of your choice


## Results for Text Based Api Tests
In this test we had a very minimal API at route `/` which just returned the text exactly 


`Hello from, perf tests!`

Below test runs can be emulated with results are with below command

`wkr -t 8 -c 256 -d 30s http://127.0.0.1/`


### Actix Web Framework
Find out more about actix-web framework on this [link](https://actix.rs/).

Docker deployment
    Run `cd actixweb-perf-test`
    Eg. `docker build -t web-perf-actix .`
    Run With `docker run --init -p 8080:8080 web-perf-actix`

### Rocket Web Framework
Find out more about rocket framework on this [link](https://rocket.rs/).

Docker deployment
    Run `cd rocket-perf-test`
    Eg. `docker build -t web-perf-rocket .`
    Run With `docker run --init -p 8080:8080 web-perf-rocket`


### Axum Web Framework
Find out more about axum framework on this [link](https://github.com/tokio-rs/axum).

Docker deployment
    Run `cd axum-perf-test`
    Eg. `docker build -t web-perf-axum .`
    Run With `docker run --init -p 8080:8080 web-perf-axum`