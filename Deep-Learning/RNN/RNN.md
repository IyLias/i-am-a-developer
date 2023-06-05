# All about RNN


## What is RNN?

RNN is a class of artificial neural networks where connections between nodes can create a cycle, allowing output from some nodes to affect subsequent input to the same nodes. i.e, RNN is specialized for processing a sequence of data with the time step.


### Structure

Similar to MLP, RNN has Input Layer, Hidden Layer and Output Layer. Unlike MLP, there exists recurrent edge between Hidden Layer. These edges connect nodes in Hidden Layer. 

![image](https://github.com/IyLias/i-am-a-developer/assets/48081162/f6406eb6-71d1-4180-8815-ec7a36ea35af)


The node that sends output through activation function at Hidden Layer is called "cell". And as it acts like a memory, it's also called "memory cell" or "RNN cell". 



### Behavior

This recurrent edge behaves as time flows. We can express this time connection property by equation. 

$h^t = f(h^{t-1},x^t; \theta)$

We usually use activation function f, tanh function.

선형 함수인 h(x)=cx
를 활성 함수로 사용한 3층 네트워크를 떠올려 보세요. 이를 식으로 나타내면 y(x)=h(h(h(x)))
가 됩니다. 이 계산은 y(x)=c∗c∗c∗x
처럼 세번의 곱셈을 수행하지만 실은 y(x)=ax
와 똑같은 식입니다. a=c3
이라고만 하면 끝이죠. 즉 히든레이어가 없는 네트워크로 표현할 수 있습니다. 그래서 층을 쌓는 혜택을 얻고 싶다면 활성함수로는 반드시 비선형함수를 사용해야 합니다.

This equation shows that $h^t$(i.e, value at time t) is decided by input value $x^t$ (i.e, at time t) and hidden layer value $h^{t-1}$(i.e, at time t-1)


Hidden Layer Operation 

$h^t$ = $\tau(a^t)$, $a^t = Wh^{t-1} + Ux^t + b$ and usually use tanh for $\tau$ function


Ouput Layer Operation

$o^t = Vh^t + c$, $y^t = softmax(o^t)$



<br>


### Various Forms of RNN

* one to many
 
 ex) Image Captioning Process


*  many to one
  
 ex) Spam Detection, Sentiment Classification
 
![image](https://github.com/IyLias/i-am-a-developer/assets/48081162/2cb4960d-6b9f-4782-9a1e-1c60d6bb394e)

* many to many

 ex) Chatbot, Translator
 
![image](https://github.com/IyLias/i-am-a-developer/assets/48081162/96cbb2d9-e75d-4b8d-b7b1-2b0bc22d7255)



### BPTT Algorithm (Back Propagation Through Time)

![image](https://github.com/IyLias/i-am-a-developer/assets/48081162/36e38627-2b5c-4b65-a260-62eda0be7b22)





 
### Difference between MLP(DMLP) and RNN 

* DMLP has one Input Layer at first and one Output Layer at last but RNN has Input and Output Layer at every moment.


* RNN shares weights. So we just write its weight as $W$




### BRNN

BRNN connect two hidden layers of opposite directions to the same output. 



### Problems of RNN

* Gradient Vanishing
  Gradient keeps decreasing and almost converges to 0 so it loses its function to direct to optimized solution.


* Gradient Explosion
  Gradient keeps increasing and gets NAN so it turns into the state that can't keep learning. 


<br><br>

### LSTM : Long Short Term Memory

LSTM is made for solving RNN's problems. 

There exists memory blocks in hidden nodes in LSTM. 







### References

[reference](https://wikidocs.net/22886)

[reference](https://www.deeplearningbook.org/contents/rnn.html)


