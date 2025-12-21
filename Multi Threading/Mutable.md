[[Python]]
“**Mutable**” simply means **you can change the value after it’s created**.
# In TensorFlow

- `tf.Variable` → **mutable**
    
    `import tensorflow as tf  w = tf.Variable([1, 2, 3]) w.assign([4, 5, 6])  # ✅ allowed print(w)  # <tf.Variable [4 5 6]>`
    
- `tf.constant` → **immutable**
    
    `c = tf.constant([1, 2, 3]) c.assign([4, 5, 6])  # ❌ ERROR`
    

---

# Why it matters

- Neural networks **update weights during training**.
    
- Only **mutable objects** like `tf.Variable` can be updated with optimizers.
    
- Immutable objects like `tf.constant` **cannot be changed**, so they are just fixed values.
- ---
