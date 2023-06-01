# All about RNN


## What is RNN?

RNN is a class of artificial neural networks where connections between nodes can create a cycle, allowing output from some nodes to affect subsequent input to the same nodes. i.e, RNN is specialized for processing a sequence of data with the time step.


### Structure

Similar to MLP, RNN has Input Layer, Hidden Layer and Output Layer. Unlike MLP, there exists recurrent edge between Hidden Layer. These edges connect nodes in Hidden Layer. 

![image](https://github.com/IyLias/i-am-a-developer/assets/48081162/f6406eb6-71d1-4180-8815-ec7a36ea35af)
[reference](https://www.deeplearningbook.org/contents/rnn.html)

This recurrent edge behaves as time flows. We can express this time connection property by equation. 

$h^t = f(h^{t-1},x^t; \theta)$

This equation shows that $h^t$(i.e, value at time t) is decided by input value $x^t$ (i.e, at time t) and hidden layer value $h^{t-1}$(i.e, at time t-1)



### Behavior




### BPTT Algorithm (Back Propagation Through Time)



 
### Difference between MLP(DMLP) and RNN 

* DMLP has one Input Layer at first and one Output Layer at last but RNN has Input and Output Layer at every moment.


* RNN shares weights. So we just write its weight as $W$


### BRNN

BRNN connect two hidden layers of opposite directions to the same output. 



### Problems of RNN

* Vanishing Gradient


* Gradient Explosion


<br><br>

### LSTM : Long Short Term Memory

LSTM is made for solving RNN's problems. 


