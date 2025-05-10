Multi-Threaded Proxy Server (With and Without Cache)
📌 Introduction

This project implements a Multi-threaded Proxy Server with optional caching functionality using the LRU (Least Recently Used) algorithm. It demonstrates handling concurrent client requests efficiently using threads, locks, and semaphores.
⚙️ Basic Working Flow of the Proxy Server

    A client sends a request to the proxy server.

    The proxy checks if the requested content is present in the cache (if enabled).

    If it's a cache miss, the request is forwarded to the actual server.

    The response is received and passed to the client (and stored in cache if applicable).

    All steps are handled concurrently using threads.

🧵 How Did We Implement Multi-threading?

    Used Semaphore instead of Condition Variables and pthread_join()/pthread_exit().

        pthread_join() requires a specific thread ID to wait for.

        Semaphores (sem_wait(), sem_post()) don't require parameters and are better suited for general synchronization in this scenario.

💡 Motivation / Need for This Project

To understand and implement:

    The flow of HTTP requests from a local client to a web server.

    Handling multiple concurrent client requests.

    The locking mechanism for concurrency control.

    The concept and behavior of caching in web browsers.

What a Proxy Server Can Do:

    Speeds up access and reduces server load.

    Can block access to specific websites.

    Can anonymize requests by hiding the original IP.

    Can be modified to encrypt traffic, enhancing security.

🎯 Outputs
✅ Functional Highlights:

    Handles multiple client requests using threads.

    Proper concurrency control using locks and semaphores.

    Implements an LRU Cache mechanism.

📁 Execution Demo:

    First-time access to a website results in a cache miss.

    On subsequent access, data is fetched from the cache.

Demo Video:
    📽️[ Execution-video/Screencast From 2025-05-06 19-18-24.mp4](https://github.com/askarthikey/Multithreaded-Proxy-WebServer/blob/main/Execution-video/Screencast%20From%202025-05-06%2019-18-24.mp4)


🧩 OS Concepts Used

    Threading

    Locks

    Semaphore

    Cache (with LRU algorithm)

🚀 How to Run

$ git clone https://github.com/askarthikey/Multithreaded-Proxy-WebServer
$ cd MultiThreadedProxyServerClient
$ make all
$ ./proxy <port number>

Then, open your browser and visit:
👉 http://localhost:<port>/https://www.cs.princeton.edu/
📝 Notes:

    Run only on Linux machines.

    Disable your browser cache to test caching behavior.

    To run without cache:

        Rename the file in Makefile from proxy_server_with_cache.c to proxy_server_without_cache.c.
