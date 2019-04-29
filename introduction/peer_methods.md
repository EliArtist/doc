---
layout: default
title: Peer Methods
parent: Introduction
nav_order: 3
---

# Peer Methods

You can easily define methods on your peers. Best shown with the following example for the `main` method on a `Client` peer:

```scala
placed[Client].main {
  println("Hello World!")
}
```

This method prints `Hello World!` to the console whenever a Client is started.

# Methods

There are several other methods you can define on your peers

### `main`

The main method is called when the peer, the main method is defined for, is started.

### `sbj`

`sbj` specifices a subjective value to access different remote values for different Peers. `sbj` binds an identifier to the peer instance that accesses the subjective value. Normally, all peers access the same remote value.
The example below is from a simple chat application:

```scala
val publicMessage = placed[Server].sbj { client: Remote[Client] => {
  message.asLocalFromAllSeq collect {
    case (remote, message) if (remote != client) =>  message
  }
}
```
