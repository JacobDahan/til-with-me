---
title: Part 0 - Prologue
blurb: The only thing I know is how much I do not know.
---

### The Journey

As a backend developer at AWS, I spend my days tinkering with complex APIs that are used by millions of customers serving billions of people across the globe.
While we pride ourselves of thinking like a start-up, we necessarily move more slowly due to our sheer size. We work in a legacy, enterprise code base (*think: Java8*).
There is not an appetite for re-writes in more modern languages, nor for re-architecting.

Because working at AWS was my introduction to software engineering, it has also been my only experience in software engineering.
I have never created a mobile app. I have never learned many of [today's most popular languages](https://survey.stackoverflow.co/2024/technology/#admired-and-desired).
I have never needed to design -- from scratch -- a complex system architecture. And I'm ready to change that.

### The Project

In this blog, I'll track my decisions, my progress, and my set-backs as I design, develop, and deploy ***Today I Learned***, a mobile social media app designed for sharing
learnings with friends and followers. I won't get into the tech stack too deeply, here (that's for the design phase!), except to say that I will write the backend in the Go
programming language, and the app itself in Swift for native iOS integration. 

Along the way, I'll learn (and share my learnings of) system design principals, distributed systems, user authentication, and any number of critical subjects I haven't even yet considered.
At the same time, I'll be learning both Go and Swift.

In fact, I have never written a line in either. Let's fix that, at least:

*My first lines in Go:*

```go
package main	

import "fmt"

func main() {
    fmt.Println("Hello, World!")
}
```

*... and my first line in Swift:*

```swift
print("Hello, World!") 
```

Great! Now we're ready to build.

### Project Specifications

Before diving into the design (stay tuned for ***Part 1 - Design***), I'll need to outline some basic *functional* and *non-functional* requirements. 

Too many times, my personal projects have grown in scope until I feel like I'm swimming backwards. Here, I'll lay out the distinct criteria that will enable me to say,
"*project completed* ✅".

#### Functional Requirements

1. Users can ***create accounts*** on the app.
1. Users can ***post*** a "learning", ***edit*** the learning, and ***delete*** the learning.
1. Users can ***link media*** to any learning (images, videos).
1. Users can post ***"secret"*** learnings, which provide only a teaser of the content.
1. Secret learnings can store ***private notes***, so that the content of the learning isn't forgotten.
1. Users are limited to ***three learnings*** per day.
1. Other users can ***react*** to learnings with a "TIL".
1. Users can ***follow*** other users in order to subscribe to learning "feeds".
1. When subscribed to a user's feed, any learning posted in that feed will trigger a ***push alert*** for the follower.
1. Every 24hr without a learning posted, a ***reminder*** will be sent to users to stay active.

#### Non-Functional Requirements

1. ***Scalability***. The system should be able to scale to handle millions of learnings.
1. ***Availability***. The system should be fault tolerant. Each service must be composed of multiple worker nodes, and any worker node failing should not take down the system.
1. ***Latency***. Learnings should immediately notify followers, and be available for reactions as soon as they are posted. Frequently viewed learnings from 
high-follower individuals should be cached.

### What's Next

Well, now it's time to design. Let's jump in!