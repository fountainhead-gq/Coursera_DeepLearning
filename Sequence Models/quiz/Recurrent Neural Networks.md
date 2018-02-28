## Recurrent Neural Networks

1. Suppose your training examples are sentences (sequences of words). Which of the following refers to the jth word in the ith training example?

- [x] $x^{(i)<j>}$
- [ ] $x^{<i>(j)}$
- [ ] $x^{(j)<i>}$
- [ ] $x^{<j>(i)}$

We index into the $i^{th}$ row first to get the $i^{th}$ training example (represented by parentheses), then the $j^{th}$ column to get the $j^{th}$ word (represented by the brackets).

2. Consider this RNN:
  ![](images/rnn2.png)
  This specific type of architecture is appropriate when:
- [x] $T_x = T_y$
- [ ] $T_x < T_y$
- [ ] $T_x > T_y$
- [ ] $T_x = 1$

It is appropriate when every input should be matched to an output.

3. To which of these tasks would you apply a many-to-one RNN architecture? (Check all that apply).
  ![](images/rnn3.png)

- [ ] peech recognition (input an audio clip and output a transcript)
- [x] Sentiment classification (input a piece of text and output a 0/1 to denote positive or negative sentiment)
- [ ] Image classification (input an image and output a label)
- [x] Gender recognition from speech (input an audio clip and output a label indicating the speaker’s gender)

4. You are training this RNN language model.
  ![](images/rnn4.png)
  At the $t^{th}$ time step, what is the RNN doing? Choose the best answer.

- [ ] Estimating $P(y^{<1>}, y^{<2>}, …, y^{<t-1>})$
- [ ] Estimating $P(y^{<t>})$
- [x] Estimating $P(y^{<t>} \mid  y^{<1>}, y^{<2>}, …, y^{<t-1>})$
- [ ] Estimating $P(y^{<t>} \mid y^{<1>}, y^{<2>}, …, y^{<t>})$

 Yes,in a language model we try to predict the next step based on the knowledge of all prior steps.

5. You have finished training a language model RNN and are using it to sample random sentences, as follows:
  ![](images/rnn5.png)
  What are you doing at each time step t?

 - [ ] (i) Use the probabilities output by the RNN to pick the highest probability word for that time-step as $\hat{y}^{<t>}$. (ii) Then pass the ground-truth word from the training set to the next time-step.
- [ ] (i) Use the probabilities output by the RNN to randomly sample a chosen word for that time-step as $\hat{y}^{<t>}$. (ii) Then pass the ground-truth word from the training set to the next time-step.
- [ ] (i) Use the probabilities output by the RNN to pick the highest probability word for that time-step as $\hat{y}^{<t>}$. (ii) Then pass this selected word to the next time-step.
- [x] (i) Use the probabilities output by the RNN to randomly sample a chosen word for that time-step as $\hat{y}^{<t>}$. (ii) Then pass this selected word to the next time-step.

6. You are training an RNN, and find that your weights and activations are all taking on the value of NaN (“Not a Number”). Which of these is the most likely cause of this problem?

- [ ] Vanishing gradient problem.
- [x] Exploding gradient problem.
- [ ] ReLU activation function g(.) used to compute g(z), where z is too large.
- [ ] Sigmoid activation function g(.) used to compute g(z), where z is too large.

7. Suppose you are training a LSTM. You have a 10000 word vocabulary, and are using an LSTM with 100-dimensional activations a<t>. What is the dimension of Γu at each time step?
- [ ] 1
- [x] 100
- [ ] 300
- [ ] 10000

Correct, $\Gamma_u$ is a vector of dimension equal to the number of hidden units in the LSTM.

8. Here’re the update equations for the GRU.
  ![](images/rnn8.png)
  Alice proposes to simplify the GRU by always removing the $\Gamma_u$. I.e., setting $\Gamma_u$ = 1. Betty proposes to simplify the GRU by removing the $\Gamma_r$. I. e., setting $\Gamma_r$ = 1 always. Which of these models is more likely to work without vanishing gradient problems even when trained on very long input sequences?

- [ ] Alice’s model (removing $\Gamma_u$), because if $\Gamma_r$≈0 for a timestep, the gradient can propagate back through that timestep without much decay.
- [ ] Alice’s model (removing $\Gamma_u$), because if $\Gamma_r$≈1 for a timestep, the gradient can propagate back through that timestep without much decay.
- [x] Betty’s model (removing $\Gamma_r$), because if $\Gamma_u$≈0 for a timestep, the gradient can propagate back through that timestep without much decay.
- [ ] Betty’s model (removing $\Gamma_r$), because if $\Gamma_u$≈1 for a timestep, the gradient can propagate back through that timestep without much decay.

Yes, For the signal to backpropagate without vanishing, we need $c^{<t>}$ to be highly dependant on $c^{<t-1>}$

9. Here are the equations for the GRU and the LSTM:
  ![](images/rnn9.png)
  From these, we can see that the Update Gate and Forget Gate in the LSTM play a role similar to _______ and ______ in the GRU. What should go in the the blanks?

- [x] $\Gamma_u$ and 1−$\Gamma_u$
- [ ] $\Gamma_u$ and $\Gamma_r$
- [ ] 1−$\Gamma_u$ and $\Gamma_u$
- [ ] $\Gamma_r$ and $\Gamma_u$

10. You have a pet dog whose mood is heavily dependent on the current and past few days’ weather. You’ve collected data for the past 365 days on the weather, which you represent as a sequence as $x^{<1>}, …, x^{<365>}$. You’ve also collected data on your dog’s mood, which you represent as $y^{<1>}, …, y^{<365>}$. You’d like to build a model to map from x→y. Should you use a Unidirectional RNN or Bidirectional RNN for this problem?

- [ ] Bidirectional RNN, because this allows the prediction of mood on day t to take into account more information.
- [ ] Bidirectional RNN, because this allows backpropagation to compute more accurate gradients.
- [x] Unidirectional RNN, because the value of $y^{<t>}$ depends only on $x^{<1>}, …, x^{<t>}$, but not on $x^{<t+1>}, …, x^{<365>}$
- [ ] Unidirectional RNN, because the value of $y^{<t>}$ depends only on $x^{<t>}$, and not other days’ weather.
