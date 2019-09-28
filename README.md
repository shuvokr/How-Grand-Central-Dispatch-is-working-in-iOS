# How Grand Central Dispatch is working in iOS

GCD or [Grand Central Dispatch](https://developer.apple.com/documentation/dispatch) is a low level API, which is use for manage concurrent operations in iOS. It will make a iOS application more responsive & helps for improving application performance. It's also use for multiple tasks at the same time. 

## Getting Started

Now the question is how Grand Central Dispatch is working in iOS ?

### Example code for GCD

```
DispatchQueue.main.async {
     // Perform your async code here
}
```

### DispatchQueue

The DispatchQueue API like a company 🏢. Who having staff units like junior level and senior level workers 👷🏼‍. So now the company can take both heavy and light work with there team.

```
One more important thing here its manage task in FIFO Order.
```

### Concurrenct

It’s starting multiple tasks at the same time but not guarantee for the finish at same time. Its can finish any order.

### Serial

It’s executing one task at a time.

### Sync vs Async

Sync - When a work item is executed synchronously with the sync method, the program waits until execution finishes before the method call returns.

