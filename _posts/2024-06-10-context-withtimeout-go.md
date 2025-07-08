---
layout: post
title: "Understanding context.WithTimeout in Go"
date: 2024-06-10
author: Abhinav Kumar
categories: [golang, programming]
tags: [go, context, timeout, cancellation]
comments: true
---

When you're building real-world applications, things don’t always go as expected. Maybe an external API is slow, or a background process takes longer than it should. If your program just waits and waits, it can block everything else.

Go provides the `context` package to help deal with these situations. Specifically, `context.WithTimeout` lets you define a maximum time an operation should take — and cancels it if it runs too long.

This post walks through a simple example using `context.WithTimeout`, and how you can apply it in real applications.

**What is the context Package?**  
The `context` package in Go helps manage deadlines, cancellation signals, and request-scoped data across goroutines. In other words, it gives you control over when to stop waiting for something that’s taking too long.

**Why Timeouts Matter**  
Imagine making a network call to an external service. If it hangs or takes too long, your entire app might get stuck. Timeouts help prevent this. By setting a limit on how long you’ll wait, you make your application more robust and responsive.

**A Simple Timeout Example**

Let’s start by simulating a slow operation that takes 5 seconds to complete, but give it only 2 seconds to finish.

```go
package main

import (
	"context"
	"fmt"
	"time"
)

func slowOperation(ctx context.Context) error {
	select {
	case <-time.After(5 * time.Second):
		return nil
	case <-ctx.Done():
		return ctx.Err()
	}
}

func main() {
	ctx, cancel := context.WithTimeout(context.Background(), 2*time.Second)
	defer cancel()

	err := slowOperation(ctx)
	if err != nil {
		fmt.Println("Operation failed:", err)
		return
	}

	fmt.Println("Operation succeeded")
}
```

- `time.After(5 * time.Second)` simulates a slow task.
- `ctx.Done()` is a channel that is closed when the context is canceled or times out.
- Since our context times out in 2 seconds, the function returns early with an error: `context deadline exceeded`.

**Making an HTTP Request with Timeout**

Here’s a practical use case: making an HTTP request that you don’t want to hang indefinitely.

```go
package main

import (
	"context"
	"fmt"
	"net/http"
	"time"
)

func main() {
	ctx, cancel := context.WithTimeout(context.Background(), 2*time.Second)
	defer cancel()

	req, err := http.NewRequestWithContext(ctx, http.MethodGet, "https://httpbin.org/delay/5", nil)
	if err != nil {
		fmt.Println("Error creating request:", err)
		return
	}

	resp, err := http.DefaultClient.Do(req)
	if err != nil {
		fmt.Println("Request failed:", err)
		return
	}
	defer resp.Body.Close()

	fmt.Println("Response status:", resp.Status)
}
```

In this example:
- We request an endpoint that intentionally waits 5 seconds before replying.
- But our context times out in 2 seconds.
- The request fails quickly, and we avoid a long delay.

**Best Practices and Common Mistakes**

- Always call `cancel()` when you use `context.WithTimeout` (or `WithCancel`). This cleans up resources used by the context and avoids memory leaks.
- Don’t ignore `ctx.Err()` – this tells you why the context ended (timeout, manual cancel, etc).
- Don’t block forever – if you don’t listen to `ctx.Done()`, your goroutines may never exit.

**When to Use context.WithTimeout**

- You need to limit how long an operation can run.
- You're making external calls (e.g., HTTP, DB).
- You want graceful cancellation across goroutines.