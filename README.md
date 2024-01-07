# Identification of COVID-19 in lung X-ray images

Machine Learning II - University of Minho

* Célia Manuela Fernandes Ferreira

* Mohammad Reza Tabrizi

This repository includes proposals for <b>machine learning</b> and <b>deep learning</b> models that aim to identify COVID-19 in lung images.

### Motivation
* COVID-19 tests are difficult to obtain: there are not enough to test the entire population, which makes timely diagnosis and mitigation of contagion difficult. This scenario can also increase the occurrence of opportunistic situations, with the creation of false tests.

* These limitations can be mitigated by using other forms of diagnosis. Because COVID-19 attacks the epithelial cells lining the respiratory tract, X-rays can be used to analyze a patient's lung health and identify COVID-19 without the usual test kits.

* However, X-ray analysis consumes precious human resources and time, so the development of an automatic X-ray analysis system represents an added value. This is the objective of this project.

### Goals

- Automatically identify pneumonia in X-rays
- Due to the current scarcity of data on Covid events, use generative models
- Compare the performance of traditional machine learning and deep learning algorithms
- Interpret results


### Index

The repository is organized as follows:

* <b>Chapter 1</b>: [Data import](https://github.com/celiaferreira/Covid19_RX/blob/master/1_ImportarDados.ipynb)

  To ensure the greatest amount of data for adequate training, data was collected from several sources: Kaggle and github.

* <b>Chapter 2</b>: [Data Preprocessing](https://github.com/celiaferreira/Covid19_RX/blob/master/2_PreProcessamento.ipynb)

  This section reshapes and standardizes the images, processes the labels to be predicted and divides the data into training, validation and test sets.
  
* <b>Chapter 3</b>: [Exploratory data analysis](https://github.com/celiaferreira/Covid19_RX/blob/master/3_AnaliseDados.ipynb)
  
 In order to gain a greater understanding of the data, this section includes visualization of input images, counting of labels and analysis of COVID patients.

* <b>Chapter 4</b>: Data augmentation

  COVID-19 data is still poorly available. To overcome this limitation and allow better learning, two approaches will be tested to increase the number of data: oversampling and data generation.

  - 4.1 [Oversampling](https://github.com/celiaferreira/Covid19_RX/blob/master/4_1_Oversampling_SMOTE.ipynb)

  Using the SMOTE (Sythetic Minority Oversampling TEchnique) oversampling technique, images are generated in the training set so that the dataset is <b>balanced</b>.
    
    
  - 4.2 [Data Generation](https://github.com/celiaferreira/Covid19_RX/blob/master/4_2_DataGeneration.ipynb) 
  
  Using slight translations and rotations of the COVID-19 images in the training set, the COVID-19 cases in the training set are quadrupled. The greater computational effort of this technique stands out, compared to oversampling.

  In the following sections, models developed using these 2 techniques used to increase and balance the training dataset are presented and compared.


* <b>Chapter 5</b>: [Auxiliary functions](https://github.com/celiaferreira/Covid19_RX/blob/master/5_FuncoesAuxiliares.ipynb)

 In this chapter, functions are parameterized that will simplify the outputs of the developed models: metrics, confusion matrix, plots of the evolution of accuracy and loss per epoch and visualization of convolutional and fully connected layers.

* <b>Chapter 6</b>: Machine learning models

  This section presents and evaluates the predictive power of traditional machine learning models in identifying COVID-19 in images.
  Random forests, KNN, Boosting and model ensembles are tested, for training data augmented by oversampling and data generation.

  - 6.1 [Oversampling](https://github.com/celiaferreira/Covid19_RX/blob/master/6_1_MachineLearning_SMOTE.ipynb)

  - 6.2 [Data Generation](https://github.com/celiaferreira/Covid19_RX/blob/master/6_2_MachineLearning_DataGen.ipynb) 
  
* <b>Chapter 7</b>: Deep learning models

    This section presents <b>convolutional, sequential neural networks using the functional API</b>, as well as a <b>hyperparameter optimization process</b>, also for training data augmented by oversampling and data generation.
  
  - 7.1 [Oversampling](https://github.com/celiaferreira/Covid19_RX/blob/master/7_1_DeepLearning_SMOTE.ipynb)
  
    This section also includes an <b>analysis of the errors</b> made by the optimal model in predicting COVID-19 and the <b>visualization of the model's learning</b>.

  - 7.2 Data Generation
  
    This section presents models for targets with 3 labels and targets with 4 labels:
        
      [Data Generation: 3 labels](https://github.com/celiaferreira/Covid19_RX/blob/master/7_2_DeepLearning_DataGen_3lab.ipynb) 
      
      [Data Generation: 4 labels](https://github.com/celiaferreira/Covid19_RX/blob/master/7_3_DeepLearning_DataGen_4lab.ipynb) 
         
* <b>Chapter 8</b>: Transfer learning models

  In this section we evaluate the predictive capacity of two pre-trained networks in identifying COVID-19: InceptionResNetV2 and ResNet50.
  Three configurations for the convolutional layers are tested: Non-trainable weights (frozen), Weights of the last trainable layers (fine tuning) and Trainable weights (use of the network architecture).

  - 8.1 [Oversampling](https://github.com/celiaferreira/Covid19_RX/blob/master/8_1_TransferLearning_SMOTE.ipynb)

  - 8.2 [Data Generation](https://github.com/celiaferreira/Covid19_RX/blob/master/8_2_TransferLearning_DataGen.ipynb) 


* <b>Capítulo 9</b>: [Conclusion](https://github.com/celiaferreira/Covid19_RX/blob/master/9_Conclusoes.ipynb)

     - As a technique to increase records and balance the training dataset, oversampling is recommended, due to the better performance and less computational effort required.
    - Even in an image classification problem, traditional machine learning models present a competitive performance, greater than 90%.
    - In general, deep learning models are more predictive, with the optimized model standing out.
    - API models (more complex) present competitive performance, but do not surpass the optimal model.
    - Transfer learning models with frozen weights did not prove to be competitive. The best result was obtained by using the network architecture, but allowing the training of weights directed to the problem under analysis.
    - Taking into account the global performance, the recall of COVID cases and the absence of overfitting, **the model obtained through hyperparameter optimization** is proposed as ideal, which presents the following topology:

        model = models.Sequential()
        model.add(layers.Conv2D(128, (3, 3), activation='relu', input_shape=(200, 200, 1)))
        model.add(layers.MaxPooling2D((2, 2)))
        model.add(layers.Conv2D(128, (3, 3), activation='relu'))
        model.add(layers.MaxPooling2D((2, 2)))
        model.add(layers.Conv2D(128, (3, 3), activation='relu'))
        model.add(layers.MaxPooling2D((2, 2)))
        model.add(layers.Flatten())
        model.add(layers.Dense(64, activation='relu'))
        model.add(layers.Dense(16, activation='relu'))
        model.add(layers.Dense(3, activation='softmax'))
        model.compile(optimizers.Adam(lr=0.001),loss='sparse_categorical_crossentropy',metrics=['accuracy'])

  - This model distinguishes COVID-19 from other pneumonias and normal situations with an **accuracy of 97.3%** in the test set, with a **recall of 98.1% of COVID-19 cases**.
