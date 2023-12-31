# fslog

`fslog` is a tool that helps formatting nested and structured logs.

## Example

```python
import fslog

def fact(n):
    if n == 1:
        fslog.log("Reached base case")
        return 1
    fslog.open(f"Computing fact({n})")
    fslog.log(f"Recursive step: {n} * fact({n-1})")
    res = n * fact(n-1)
    fslog.close(f"fact({n})={res}")
    return res

fslog.param["open.style"] = fslog.style.BOLD + fslog.style.YELLOW
fslog.param["log.style"] = fslog.style.UNDERLINE
fslog.param["close.style"] = fslog.style.GREEN

fact(4)
```
Will produce the following output:
```
┌─Computing fact(4)
│ Recursive step: 4 * fact(3)
│ ┌─Computing fact(3)
│ │ Recursive step: 3 * fact(2)
│ │ ┌─Computing fact(2)
│ │ │ Recursive step: 2 * fact(1)
│ │ │ Reached base case
│ │ └─fact(2)=2
│ └─fact(3)=6
└─fact(4)=24
```
Try it on your terminal!

## Others

[`horatio`](https://github.com/fsossai/horatio) is a project that uses fslog. Go take a look!
