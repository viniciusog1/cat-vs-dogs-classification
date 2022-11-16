# 🐱 Cat vs Dogs 🐶
## 📝 About the project
Machine Learning model that receives an image and classifies it as cat or dog. The image dataset is available [here](https://www.kaggle.com/c/dogs-vs-cats).

Used tecnologies:
- Python
- Google Colab
- Pre-trained model
- TensorFlow

## 🧠 Project Steps
### Dataset
The first step is chose which dataset is gonna be used for make the machine learning model, as said before we use [this](https://www.kaggle.com/c/dogs-vs-cats) dataset that contains 25,000 images from dogs and cats

### Image processing
In our dataset we have several images but they are not equal and we need to create a pattern and make all images equal in dimensions, then we'll do it in code.

```
# Creating a directory for resized images
os.mkdir('/content/image resized')

# Resize all images for 224x224
original_folder = '/content/train/'
resized_folder = '/content/image resized/'

for i in range(2000):

  filename = os.listdir(original_folder)[i]
  img_path = original_folder+filename

  img = Image.open(img_path)
  img = img.resize((224, 224))
  img = img.convert('RGB')

  newImgPath = resized_folder+filename
  img.save(newImgPath)
```
### Train/Test
Now we need do train our model with the resized images! but before this we need to say to our model what is cat and what is dog, for doing this we have to assume two labels cats = 0, dogs = 1

```
# Creating a for loop to assign labels
filenames = os.listdir('/content/image resized/')

labels = []

for i in range(2000):

  file_name = filenames[i]
  label = file_name[0:3]

  # dog = 1
  if label == 'dog':
    labels.append(1)
  # cat = 0
  else:
    labels.append(0)
```

Good! Now we gonna separate our dataset to train and test.

```
X_train, X_test, Y_train, Y_test = train_test_split(X, Y, test_size=0.2, random_state=2)
```

## 🤔 How i use this project?
### Kaggle Configuration
You need to have an account on [Kaggle](https://www.kaggle.com/) platform.
Once logged in you have to go on account settings.

![account](/kaggle%20configuration/account.png/)

Click on 'Create New API Token' and you get 'kaggle.json' file.

![api](/kaggle%20configuration/api.png/)

![kaggle](/kaggle%20configuration/kaggle.png/)

### Using .ipynb file
Download the 'dogs_and_cats_classification.ipynb' file on this github.

Open this file with Jupyter notebook or Google Colab!

Upload your 'kaggle.json' file on your project and run the code!
