# Create & Run a TensorFlow App in 10 Minutes

We will install and use tools such as Anaconda and Jupyter Notebooks to create and run a deep learning app written in python.

## 1. Anaconda Installation

Go to Anaconda's install site and choose the version that fits your operating system.  I used the 2.X for MacOS for this tutorial.

[docs.anaconda.com/anaconda/install/](https://docs.anaconda.com/anaconda/install/)

## 2. Using Anaconda

Create a new environment by going to environments > create > python 3.X.


## 3. Add Required Libraries/Frameworks to the Environment

- ```conda install -c conda-forge tensorflow ```
- ```conda install jupyter```

## 4. Running & Using Jupyter Notebooks
Look over the Jupyter documentation - Jupyter notebooks are basically a way of running apps by using a client-side server with a browser-based UI.  We can view things like what notebooks are running, create new notebooks, and edit and step through each line of code.

[Jupyter Basics](https://jupyter-notebook.readthedocs.io/en/stable/examples/Notebook/Notebook%20Basics.html)

- Press the play button next to the environment we created in Anaconda, and choose "terminal"
- Run ```jupyter notebook```

## 5. Creating a Jupyter Notebook
- On the Jupyter home page in your browser, go to New > Python3
- The program we will create analyzes "handwritten" characters and attempts to guess which character it is.
- Copy this into the new notebook:
```
import tensorflow as tf
mnist = tf.keras.datasets.mnist

(x_train, y_train),(x_test, y_test) = mnist.load_data()
x_train, x_test = x_train / 255.0, x_test / 255.0

model = tf.keras.models.Sequential([
  tf.keras.layers.Flatten(input_shape=(28, 28)),
  tf.keras.layers.Dense(512, activation=tf.nn.relu),
  tf.keras.layers.Dropout(0.2),
  tf.keras.layers.Dense(10, activation=tf.nn.softmax)
])

model.compile(optimizer='adam',
              loss='sparse_categorical_crossentropy',
              metrics=['accuracy'])

model.fit(x_train, y_train, epochs=5)
model.evaluate(x_test, y_test)
```

## 6. Running the Notebook
- We're almost done!! 
- Click run at the top - hopefully you're on a decently fast system and you'll see the program execute in less than 5 minutes. On my i7 Macbook Pro I believe I was around 2 minutes when I ran the app. 

## 7. Congrats!
- You just created and ran a deep learning app, installed the necessary tools, and have insights on the data set we analyzed.  You'll see the results in the notebook - where you see information about each "epoch" or pass on the data.  You should see an increase in accuracy with each epoch that we ran.


- Let me know what other tutorials you'd like to see by emailing me: kziegler17@gmail.com

## License
[MIT](https://choosealicense.com/licenses/mit/)
