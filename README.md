# advprog-module6
Alfian Fadhlurrahman - 2206821683

#### Commit 1 Reflection notes
`main.rs` shows a simple TCP server that deals with connections coming in and understands HTTP requests. This Rust code starts a TCP listener on `127.0.0.1:7878`, and manages connections as they come. When a connection is made, it reads lines from the stream until it finds an empty line, putting them together into a list that represents an HTTP request. Then, it shows the HTTP request.

#### Commit 2 Reflection notes
In this updated code, it reads each line of the request, similar to before. However, it now also generates an HTTP response. It sets a status line indicating success and reads content from a file named "hello.html" to include in the response. 

![Commit 2 screen capture](/assets/images/commit2.png)


#### Commit 3 Reflection notes
In this updated `handle_connection` function, we've made it clearer to understand. Now, it checks the request to see if it's asking for the main page ("/") or something else. If it's asking for the main page, it responds with a success message and shows the content of `hello.html`. But if the requested page isn't found, it responds with a `not found` message and shows the content of `404.html`.

This change helps the server handle requests better. It makes sure that when someone asks for the main page, they get it, and when they ask for something else, it tells them if it's not available. 

![Commit 3 screen capture](/assets/images/commit3.png)

#### Commit 4 Reflection notes
In this updated handle_connection function, there's a new condition added to handle the request for "/sleep". If the request is for "/sleep", it introduces a delay of 10 seconds using the `thread::sleep` function. When `thread::sleep(Duration::from_secs(10))` is called, the thread executing this code will pause its execution for 10 seconds. During this pause, the thread will not perform any further computation or execute any code.

#### Commit 5 Reflection notes
In `main.rs`, the updated main function starts by setting up a TCP listener on `127.0.0.1:7878`. It also establishes a thread pool capable of handling `4` threads. Then, it begins looping to manage incoming connections. For each new connection, the function extracts the stream, ensuring it's available, and assigns a task to the thread pool using a closure. This task invokes the `handle_connection` function, which is responsible for processing the received data. This approach allows the server to handle multiple connections simultaneously by distributing the workload among the available threads in the pool.

In `lib.rs`, it sets up a `ThreadPool` structure to handle tasks across multiple threads. Each thread pool has worker threads that can execute tasks concurrently. When creating a new thread pool, it initializes worker threads and sets up a communication channel. The execute function adds a task to the channel, and worker threads pick up tasks from this channel and execute them.