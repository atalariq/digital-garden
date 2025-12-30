
Related: [[Concurrency vs Parallelism]]
# Go Concurrency

## Basic: Go Routine, Channel, and WaitGroup

```go
...

func fetch(key string, ch chan<-string, wg *sync.WaitGroup){
	... // Define return data
	defer wg.Done()
	... // Fetch data and do error-handling
	defer res.Body.Close()
	... // Encode data and do error-handling
	ch <- fmt.Sprintf(... data)
	
	return data
}

func main(){
	ch := make(chan string)
	var wg sync.WaitGroup
	for _, v := range queries{
		wg.Add(1)
		go fetch(v, ch, &wg)
	}
	
	go func(){
		wg.Wait()
		ch.Close()
	}()
	
	for result := range ch{
		fmt.Println(result)
	}
}
```

## Mutual Exclusion (Mutex)

> Avoid race condition

## Reference

- [Golang Concurrency - All the Basics you have to know! - YouTube](https://www.youtube.com/watch?v=y2jP45S9BHk)
- [Master Go Programming With These Concurrency Patterns (in 40 minutes) - YouTube](https://www.youtube.com/watch?v=qyM8Pi1KiiM)
