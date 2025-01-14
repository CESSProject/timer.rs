# Timer SGX
 
[![Build Status](https://api.travis-ci.org/Yoric/timer.rs.svg?branch=master)](https://travis-ci.org/Yoric/timer.rs)

Simple implementation of a Timer in and for Rust and has support for intel SGX.

# Example
```rust
extern crate timer;
extern crate chrono;
use std::sync::mpsc::channel;

let timer = timer::Timer::new();
let (tx, rx) = channel();

let _guard = timer.schedule_with_delay(chrono::Duration::seconds(3), move || {
  tx.send(()).unwrap();
});

rx.recv().unwrap();
println!("This code has been executed after 3 seconds");
```
