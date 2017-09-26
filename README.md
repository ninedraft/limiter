# limiter

A dead simple goroutine limiter.
Example:

```go
names := []string{"John", "Ada", "Merlin", "Tanya"}
// parameter is a limit
// .Start() method blocks until number 
// of running goroutines go down
limit := limiter.New(2)
for _, name := range names {
    go func(name string, done func()) {
        defer done()
        fmt.Printf("Hello, %s!\n", name)
    }(name, limit.Start())
}
```