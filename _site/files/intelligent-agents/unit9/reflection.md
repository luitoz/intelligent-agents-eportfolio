# Unit 9 Reflection

## What

This unit presents adaptive algorithms, which modify their behaviour based on data and environmental feedback. Neural networks are among the most influential machine learning approaches today, although many non-neural methods remain effective, especially for structured data.

The simplest artificial neural network is the feed-forward neural network (FFNN), in which information flows from input nodes through one or more hidden layers to output nodes during inference. During training, however, the network performs backpropagation to update weights and biases based on prediction errors.

Deep learning models, which typically consist of large neural networks, often outperform classical machine learning approaches on large-scale problems involving unstructured data such as images, speech, and text. A major advantage of deep learning is its ability to learn feature representations automatically, reducing the need for manual feature engineering.

This capability is particularly important in computer vision. Traditional image-recognition systems relied on handcrafted features designed by human experts, whereas convolutional neural networks (CNNs) learn relevant features directly from data. Through convolutional filters and activation functions, CNNs build hierarchical representations, with early layers detecting simple patterns such as edges and textures, intermediate layers identifying object parts, and deeper layers combining these features to recognize complex objects and scenes. This hierarchical feature learning enables CNNs to detect complex visual concepts as compositions of simpler visual components.

## So what

This unit compared the performance of deep learning and classical machine learning algorithms. In general, deep learning tends to outperform classical approaches when large amounts of training data are available, particularly for unstructured data such as images, text, and speech. However, the exact crossover point varies depending on the task, data type, dataset size, and competing algorithms. For tabular prediction problems and datasets that are not extremely large, algorithms such as Gradient Boosted Trees frequently match or outperform deep neural networks.

Initially, I was impressed by the performance gains that deep learning can achieve on complex tasks such as image recognition. However, I also found it interesting that deep learning is not universally superior and that classical machine learning algorithms can still outperform neural networks on certain problems, particularly those involving structured or tabular data. This reinforced the importance of selecting algorithms based on the characteristics of the problem rather than following current trends.

## Now what


In this unit, I revisited and explored in greater depth topics from previous modules, particularly Convolutional Neural Networks (CNNs). I examined how feature learning is performed and gained a deeper understanding of the role of kernels in detecting useful patterns within data. During training, kernel weights are automatically adjusted to recognize increasingly informative features. I also learned that CNN kernels are conceptually related to the weights of neurons in artificial neural networks (ANNs) (gonzalez, 2018). In a simple ANN, a neuron's weights determine the pattern to which it responds, while in a CNN, a kernel's weights determine the visual features that a convolution operation detects.


This unit changed my perspective on deep learning by helping me understand that its effectiveness stems not merely from having large neural networks, but from its ability to learn hierarchical feature representations automatically. I now appreciate the importance of considering factors such as data type, dataset size, computational cost, and model complexity when choosing between deep learning and classical machine learning approaches.

In future machine learning projects, I will evaluate the characteristics of the dataset before selecting a modelling approach. For unstructured data such as images, text, or audio, I would consider deep learning techniques, particularly CNNs for computer vision tasks. For structured tabular datasets, I would also investigate classical algorithms such as Gradient Boosted Trees as strong baseline models. Furthermore, understanding how kernels learn visual features will help me better interpret CNN architectures and make more informed decisions when designing, training, and evaluating deep learning models.
