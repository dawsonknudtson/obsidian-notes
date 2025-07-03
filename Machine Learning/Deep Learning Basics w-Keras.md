
creating model in Keras (just a high-level API), used for building and training deep learning models (primarily neural networks)

example : looking for caloric output given the parameters ( 'sugar', 'fiber', ' protein' )

```
from tensorflow import keras
from tensorflow.keras import layers

# Creating network with 1 linear unit

model = keras.Sequential([
	layers.Dense(units=1, input_shape=[3])
])
```

units is representing how many outputs we want, based on the example code above and previous example of calories, only look for 1.

second argument of input_shape is the dimension of inputs to communicate with keras, in this case input_shape = [3] makes sure that this model will accept three feature's (or parameters) as the input, they will be ( 'sugar', 'fiber', 'protien' )

$$
y = wx + b
$$

within keras the w or weights in the equation above is defined as tensors for training neural networks.

Tensors are just Tensorflows Version of a numpy array but making them a little bit better suited for deep learning. 

tensors are compatible with GPU and TPU accelerators. 
****
*What a TPU is because I have never head of it before*

actual definition, tensor-processing unit. A microchip designed to speed up ML workflows (specifically in deep leaning), 

main differentiator between TPU and CPU or even GPU is they are optimized for demands of computation demands of neural networks. More specifically matrix multiplication. 

[That was just a very very high level overview on what they are]

*****
