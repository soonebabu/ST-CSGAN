# Conditional Stacked GAN with Skip-thought Vectors
### Text to Image Synthesis
---
#### Dependencies
```
tensorflow
numpy
progressbar
python-dateutil
easydict
pandas
torchfile
requests
Theano
gensim
pydot
pandas
Pillow
nltk
skipthoughts
```
### Setup
```
- The project is done in google colaboratory.
- The text embedding of data is downloaded from https://drive.google.com/u/0/uc?id=0B3y_msrWZaXLT1BZdVdycDY5TEE&export=download
and saved in Data folder.
- Unzip the data to Data/birds.
- The dataset CUB-200 is downloaded from the site http://www.vision.caltech.edu/visipedia/CUB-200.html.
- The downloaded dataset is saved in the folder Data/birds.
```
#### Downloads
- To download all the dependencies, simply execute 
```
pip install -r requirements.txt
```
### Preprocess
```
Run preprocess.py to preprocess the dataset.
```

#### Training
```
- The exp1.py file is used to train the stage 1 network.
- The exp2.py file is used to train the stage 2 network.
- Save the model inside models folder.
```
#### Testing
```
-Describe the text description of the bird to be generated in Data/birds/example_captions.txt 
- Run demo.py file to generate the image from the provided text.
```


