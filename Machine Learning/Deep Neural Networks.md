NN organize neurons into layers, when collected together linear units have a common set of inputs and form a dense layer. 

Something that look like this 

![[Pasted image 20250703150239.png]]

****

#Definition
 **Layers & Dense Layers** 

Layers : Collection of interconnected (un-isolated) nodes that process info and from their pass it to the next layer in the model

Typically their are three layers

1. input layer 
2. one or more hidden layers 
3. output layer 

example of a neural network w/ two hidden layers 

![what is a 'layer' in a neural network - Stack Overflow](https://i.sstatic.net/Kc50L.jpg)

Dense Layer : each ' neuron ' is connected to every neuron in the preceding layer, this allows complex linear operation to happen as well as followed by a activation function. 

(matrix multiplication and bias addition)

example of a Dense layer


![machine learning - Working of Dense Layer - Data Science Stack Exchange](https://i.sstatic.net/dpp2W.png)

**** 

**Activation Function**

A function applied to each layer's outputs(activations). Most common is the rectifier function max(0,x)

Rectifier Function - also know as ReLU (rectified linear unit)

![A graph of the rectifier function. The line y=x when x>0 and y=0 when x<0, making a 'hinge' shape like '_/'.](https://storage.googleapis.com/kaggle-media/learn/images/aeIyAlF.png)

The function's graph above has a line where the negative part is 'rectified to zero'. Applying this function to outputs of a neuron will put a bend in whatever the data is, moving away from simple lines. 

[More Notes in NoteBook]

*****

Stacking Dense Layers & ReLu

![[Pasted image 20250705141236.png]]

Hidden is because we never see outputs directly. Other tasks (classification) might require an activation function on the output. 

Code below is what builds the image above 

```
from tensorflow import keras
from tensorflow.keras import layers

model = keras.Sequential([
	# Hidden ReLu Layers
	layers.Dense(units=4, activation='relu', input_shape=[2])
	layers.Dense(units=3, activation='relu')
	# linear output layer
	layers.dense(units=1)
])
```

