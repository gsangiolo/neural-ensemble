# neural-ensemble
Simple Ensemble of Neural Networks 

This repository is meant to demonstrate a very simple ensemble of Dense Feed-Forward neural networks. It contains two notebooks: BuildProcess.ipynb and Ensemble.ipynb.

BuildProcess.ipynb: This is a very "stream of consciousness" notebook where the initial neural network setup and testing was performed. Its inclusion is just for reference of my thought/build process

Ensemble.ipynb: This is the meat of the repository, and contains the main classes that are demonstrated: NeuralNetworkFactory and CategoricalEnsemble.

NeuralNetworkFactory attempts to replicate the factory build pattern seen often in Java, and provides a way to dynamically build any number of Dense Feed-Forward networks. For each network, an array of integers representing node counts for each layer (nodes), an array of strings representing the activation functions for each layer (activations), and the initial input size (input_size) are required to build the networks.

CategoricalEnsemble will create for itself a number of neural networks (using the NeuralNetworkFactory) and perform training and testing on them. While many functions are simple wrappers for built-in Keras functions (summary(), evalutate(), etc), the key piece is the Polling function. This function takes a set of test data, and performs a prediction with each model in the ensemble. From there, it takes the majority opinion to categorize each datapoint. It tallies votes by two methods: the first is Sum, which simply adds the probabilities together for each model, and selects the largest totals. The second is Count, which selects the highest probability for each model, and then tallies up votes from there.

