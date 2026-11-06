# Facial-Expression-Classification

A three-class facial expression classifier built by tuning a pretrained efficientNet-b0 model in google colab. The notebook prepares image data, trains and evaluates the model, visualizes results, and generates predictions for an unlabed set.

RESULTS
85.37% best validation accuracy after 6 epochs.

DATASET
Each image is a flattened 48x48 grayscale image containing 3,304 pixel values

PREPROCESSING
Reshape each image to 48x48 and convert it to three-channel RGB
resize images to 224 x 224
apply random horizontal flips, roations of up to 10 degrees, and brightness/contrast adjustments during training
normalize inputs using ImageNet channel means and satndard deviations
Use resign and normalization without random augentation for validation and testing

MODEL AND TRAINING
model starts with imageNet-pretrained EfficientNet-B0 weights. its final classification layer is replaced with a three-class linear layer, and all model parameters are tuned

Framework: PyTorch/torchvision
Batch size; 32
Maximum epochs: 6
Optimizer: AdamW
Learning rate: 0.0002
Weight decay: 0.0001
Early stoppage: 5 epochs without improved validation accuracy

Running in Google Colag
Open Facial_Expression_Classification.ipynb in Colab
Select a gpu runtime for faster training
if dependencies are missing, install them
Upload the 4 dataset CSV files to content/facial_expression_data
Run the Notebook cells in order. Loading pretrained weights requires internet acces on the first run
Download generated files before ending the session

Limitations
Performance is measured on one random validation split
training accuracy exceeds calidation accuracy indicating a generalization gap
results may vary across hardware and runs depsite fixed seeds

FUTURE IMPROVEMENTS
report per-class precision, recall, and f1 scores
compare against a simple classifier or majority baseline
evaluate on an independant labeld test set
