[[Python]]
- An object that **behaves like a function**.
- You can **call it with parentheses**.   
- It can also **maintain internal state**, unlike plain functions.
`class Counter:`
    `def __init__(self):`
        `self.count = 0`

    def __call__(self):
        self.count += 1
        return self.count

`c = Counter()`
`print(c())  # 1`
`print(c())  # 2`



| `__call__()` | Makes the object callable          |
| ------------ | ---------------------------------- |
| `obj(args)`  | Translates to `obj.__call__(args)` |

