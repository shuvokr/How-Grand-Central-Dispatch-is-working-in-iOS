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

```
func syncWork(){
        let northZone = DispatchQueue(label: "perform_task_with_team_north")
        let southZone = DispatchQueue(label: "perform_task_with_team_south")
        
        northZone.sync {
            for numer in 1...3{ print("North \(numer)")}
        }
        southZone.sync {
            for numer in 1...3{ print("South \(numer)") }
        }
    }
    
    //Call Func here 
    syncWork()
    
//Output
//    North 1
//    North 2
//    North 3
//    South 1
//    South 2
//    South 3
```

Async - execute asynchronously with the async method, the method call returns immediately.

```
func asyncWork(){
        let northZone = DispatchQueue(label: "perform_task_with_team_north")
        let southZone = DispatchQueue(label: "perform_task_with_team_south")
        
        northZone.async {
            for numer in 1...3{ print("North \(numer)") }
        }
        southZone.async {
            for numer in 1...3{ print("South \(numer)") }
        }
    }

//Call Async Task
asyncWork()

//OutPut 
//    North 1
//    South 1
//    North 2
//    South 2
//    North 3
//    South 3
```

## Code Example

### Perform network task with UI updates:

<b>Global Queue</b> - Using to perform non-UI work in the background.

<b>Main Queue</b> - Using to update the UI after completing work in a task on a concurrent queue.

List of DispatchQueue Priority

