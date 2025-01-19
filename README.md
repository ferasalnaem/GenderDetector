# GenderDetector
This project was developed as a semester project for the lecture "Special Aspects of Mobile Autonomous Systems". The idea behind this project is to assist robots in better communicating with people by accurately detecting gender.

A key improvement in this project is the significant reduction in training time compared to traditional transfer learning methods. By using fine-tuning, we leverage high-value features while reducing the number of trainable parameters, leading to faster training and better performance.


## How to Run the Code 
We provide two models:

1. A model with Keras frozen layers (baseline version).
2. A fine-tuned solution.

To run the project, you can comment out the model you don't want to use and train the desired one by running:

                  $ python train.py


## Project Structure

The project is organized as follows:

- data_loader.py: Handles loading the data.
- preprocessor.py and inference.py: Responsible for preprocessing, augmenting, and normalizing the data.
- generator.py: Generates the data in batches for training.
- download.sh and utils: Prepares and downloads necessary dependencies.
- models/: Contains the models, including:
	- .hdf5 (weights)
	- .json (model architecture)
	- Additional files needed for training.
- weights/: Contains pre-trained weights.
- train.py: The main script to train the models.
- Dependencies: Requires the following libraries:
	- Python 3.5+
	- Keras 2.0+
	- TensorFlow (backend for Keras)
	- OpenCV
	- Scipy
	- Numpy
	- Pandas
	- tqdm
	- tables
	- h5py
	- dlib (used for the demo)

## Training the Model

To train the model, simply run:
                  $ python train.py

- By default, the InceptionV3 model (located in models/transfer_learning/inception_v3) will be used.
- You can switch to a different model by commenting out the InceptionV3 section in train.py and uncommenting the desired model.


## Previous Model Version

Our previous model version is located here: models/fine_tuning/inception_v3_finetune.

In this version:
1. The model was first trained on the Wiki dataset.
2. Then, certain layers were frozen, and the model was fine-tuned with the IMDB dataset.

To run the code using this version:
- Comment out sections in train.py related to compiling, data generation, callbacks, and checkpoints (these are already defined in the fine-tuned model's architecture).
- Then run the visualization part.

## Modifying Training Parameters

You can adjust training parameters to customize the process. Parameters can be modified either:

- In the argument section of the script.
- Or deeper in the code.

Here are the adjustable parameters:
- nb_epochs: Number of training epochs.
- patience: Number of epochs to wait without improvement in val_loss before stopping training.
- optimizer: Choose between SGD, Adam, or RMSprop.
- batch_size: Number of images per batch during training.
- input_shape: Image dimensions, which should match the model's architecture (e.g., 299, 224, 160).
- validation_split: Fraction of the data reserved for validation (e.g., 0.2 or 0.1).
- Metrics: Choose whether to monitor loss, val_loss, accuracy, or val_acc.

## Running the Model After Training

Live Prediction with Camera
To test live predictions using a webcam:

1. Run the following command:

                     $ python predictionlivevideo.py
2. In the script, set the gender_model_path parameter to point to the weights file.

   
