# Install Tensorflow



```
pip install --upgrade "tensorflow==1.7.*"


```

# Fork the git repository


# Clone the git repository


```
git clone https://github.com/Navan0/build-your-first-imageClassifier.git
```


```
cd build-your-first-imageClassifier 

```
# Download the training images



```
download your datasets
    
```

# Put the images into the classes

```
ls tf_files/data

```



```
yourclass1/
yourclass2/
yourclass3/
yourclass4/
yourclass5/
LICENSE.txt

```

# (Re)training the network



**In this exercise, we will retrain a MobileNet. MobileNet is a a small efficient convolutional neural network. "Convolutional" just means that the same calculations are performed at each location in the image.**

Set those variables in your shell

```
IMAGE_SIZE=224
ARCHITECTURE="mobilenet_0.50_${IMAGE_SIZE}"

```

# Investigate the retraining script



```
python -m scripts.retrain -h
```
# Run the training




```
python -m scripts.retrain \
  --bottleneck_dir=tf_files/bottlenecks \
  --how_many_training_steps=4000\
  --model_dir=tf_files/models/ \
  --summaries_dir=tf_files/training_summaries/"${ARCHITECTURE}" \
  --output_graph=tf_files/retrained_graph.pb \
  --output_labels=tf_files/retrained_labels.txt \
  --architecture="${ARCHITECTURE}" \
  --image_dir=tf_files/flower_photos
```

# Classifying an image



```
python -m scripts.label_image \
    --graph=tf_files/retrained_graph.pb  \
    --image=tf_files/test/test_m.jpg
```

