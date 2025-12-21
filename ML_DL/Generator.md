[[Python]]
process data efficiently without storing everything in memory at once
A generator starts producing values _immediately_, because it is lazy — it computes values **only when needed**.
# ----- 1. List vs Generator -----
`lst = [x*x for x in range(5)]       # List: stores all values
`gen = (x*x for x in range(5))       # Generator: produces values on demand

`print(lst[0])  # reusable
# print(gen[0])  # ❌ Error, cannot index

# ----- 2. Iterating -----
`for x in gen:
    `print(x)    # 0 1 4 9 16 (one-time)`

# ----- 3. Reuse generator -----
`gen = (x*x for x in range(5))
`lst2 = list(gen)  # store to reuse
`print(lst2[0])    # 0

# ----- 4. Fresh independent generators -----
`def make_gen():
  ``  return (x*x for x in range(5))

`g1 = make_gen()
`g2 = make_gen()
`print(next(g1))  # 0
`print(next(g2))  # 0, independent

# ----- 5. Memory efficiency -----
`import sys
`lst_big = list(range(10**6))
`gen_big = (x for x in range(10**6))
`print(sys.getsizeof(lst_big))  # huge
`print(sys.getsizeof(gen_big))  # very small

# ----- Summary -----
# List: stores, reusable, indexable, memory-heavy
# Generator: lazy, memory-light, one-time, cannot copy
