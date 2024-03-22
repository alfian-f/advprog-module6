# advprog-module6
Alfian Fadhlurrahman - 2206821683

#### Commit 1 Reflection notes
`main.rs` shows a simple TCP server that deals with connections coming in and understands HTTP requests. This Rust code starts a TCP listener on `127.0.0.1:7878`, and manages connections as they come. When a connection is made, it reads lines from the stream until it finds an empty line, putting them together into a list that represents an HTTP request. Then, it shows the HTTP request.