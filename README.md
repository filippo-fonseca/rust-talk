# 🎉 Rust Talk

A terminal-based chat app built in Rust.

**NOTE:** This is my first project in Rust, so take it with a grain of salt. It's very basic and probably full of bugs and/or sections that could be cleaned up. :).

### Code Snapshot

A preview of what's inside!

```rust
let mut clients = vec![];
    let (tx, rx) = mpsc::channel::<String>();
    loop {
        if let Ok((mut socket, addr)) = server.accept() {
            println!("Success! {} is connected.", addr);

            let tx = tx.clone();
            clients.push(socket.try_clone().expect("failed to clone client"));

            thread::spawn(move || loop {
                let mut buff = vec![0; MSG_SIZE];
```

See more in the [`server`](https://github.com/filippo-fonseca/rust-talk/tree/main/server) and [`client`](https://github.com/filippo-fonseca/rust-talk/tree/main/client) directories.

## Setup

Make sure you have [Rust](https://www.rust-lang.org/tools/install) and its respective package manager, Cargo, installed on your local machine.

**1. Clone the repo & change directories**

```
git clone git@github.com:filippo-fonseca/rust-talk.git

cd rust-talk
```

**2. Run and/or Build**

To run the app, open two separate terminal windows.

On one of them, `cd` into the `server`, while on the other go into the `client`, as such:

**Window 1:**

```
cd server
```

**Window 2:**

```
cd client
```

Now, in both terminal windows run the following command (make sure you run it in the terminal window assigned to the `server` first, as the `client` will not be able to connect to the server unless it's up):

```
cargo run
```

To create a usable version, run:

```
cargo build
```

Made with ❤️ by [@FilippoFonseca](https://www.twitter.com/FilippoFonseca).
