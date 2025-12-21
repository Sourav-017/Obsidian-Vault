[[Tensorflow]]
**`tf.GradientTape`** is TensorFlow’s automatic differentiation tool.  
It _records_ all operations done inside its context and then lets you compute gradients with respect to any variable.
# **1. BASIC USAGE**

### **Step-by-step:**

### **(a) Create a variable**

`x = tf.Variable(3.0)`

### **(b) Open a GradientTape block**

`with tf.GradientTape() as tape:     
	`y = x * x + 2 * x + 1`

### **(c) Compute gradient**

`dy_dx = tape.gradient(y, x)
``print(dy_dx)   # 8.0`

**Meaning:** You recorded the function

$y= x^2 + 2x + 1y$

Then asked the tape for
$$dy\_dx \space= \frac{dy}{dx}$$