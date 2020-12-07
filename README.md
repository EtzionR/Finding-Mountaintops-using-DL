# Finding-Mountaintops-using-DL
Identification of mountain peaks using a Neural Network.

![alps](https://github.com/EtzionR/Finding-Mountaintops-using-DL/blob/main/pictures/Valais_mountain.jpg)
Image source: [Wikimedia](https://commons.wikimedia.org/wiki/Matterhorn#/media/File:Valais_mountains.jpg)

## Introduction
In order to automatically identify mountain peaks and ranges. To do so, we will use the code [**Find_Mountaintops.ipynb**](https://github.com/EtzionR/Finding-Mountaintops-using-DL/blob/main/Find_Mountaintops.ipynb) to create **Neural Network Model**. Our goal is to identify using this model whatever some point desrcibe mountain range or peak.

In order to build the model, we will select proper area for **training and testing** the model. The area chosed located in the **Alps Mountains**, on the border between Italy and Switzerland. These are the boundaries of the defined area (wgs84 geo dd):
- **north:** 46.864583
- **South:** 45.687083 
- **East:** 8.878750
- **West:** 7.250417

To build the model, we will use **DTM**, which was produced as part of the [SRTM](https://en.wikipedia.org/wiki/Shuttle_Radar_Topography_Mission) project. The data downloaded from this website [srtmdata](http://srtm.csi.cgiar.org/srtmdata/) and transferred to a **numpy matrix**. The martix contain a grid of points which each point value indicates its **height** in meters above sea level. The **tops** matrix, contain 1955 rows, 1414 columns and a total of **2,764,370** height points. The file save as [**tops.npy**](https://github.com/EtzionR/Finding-Mountaintops-using-DL/blob/main/Data/tops.npy). Now, we plot the tops matrix:

![contour](https://github.com/EtzionR/Finding-Mountaintops-using-DL/blob/main/pictures/contour.png)

In order to illustrate the height values of the points, we chose to present in 3D the specific area from the matrix. The selcted area is [**Matterhorn Mountain**](https://www.google.com/maps/place/Matterhorn/@45.973403,7.6841342,5771m/) area. The data present using a adapt version of the **3d-graph-gif** code, full documentation can be found here: [**create-3d-graph-gif**](https://github.com/EtzionR/create-3d-graph-gif):

![Matterhorn](https://github.com/EtzionR/Finding-Mountaintops-using-DL/blob/main/pictures/Matterhorn.gif)

The file [**tags.csv**](https://github.com/EtzionR/Finding-Mountaintops-using-DL/blob/main/Data/tags.csv) contains **75508 labels** of each point: **'top'=1** means mountain peak and **'top'=0** means not a mountain peak. Using this tagging, we will extract the location (row + column) of each point in the matrix [**tops.npy**](https://github.com/EtzionR/Finding-Mountaintops-using-DL/blob/main/Data/tops.npy). In order to identify whether each point is a peak or not, we will process each point together with The height points that surround it, so we get for each tagged point a **19X19 matrix**. An example of such a matrix (showing a mountaintop point) can be seen here:

![example 1](https://github.com/EtzionR/Finding-Mountaintops-using-DL/blob/main/pictures/exm1.png)

Now, based on the tagged labels (Y) and the array of matrices (X), we will perform the model training, based on 90% of the data we have. This is the model structure:

![model](https://github.com/EtzionR/Finding-Mountaintops-using-DL/blob/main/pictures/model.png)

To **evaluate** the prediction quality of the model, we based on the remaining 10% test records. The percentage of correct results of the model seems to be **97.3%**. In addition, we will present the results of the loss values and accuracy along the epochs of the model:

![eval](https://github.com/EtzionR/Finding-Mountaintops-using-DL/blob/main/pictures/evl.png)

While examining the errors received from the model, it can be seen that in some cases might consider as controversial situations: in some of this cases its seems that the  result consider incorrect sometimes seems to make sense:

![error9](https://github.com/EtzionR/Finding-Mountaintops-using-DL/blob/main/pictures/error9.png)

Now, we would like to export the model so we can use it for future needs. The model is available at this link: [**Mountaintops_model.h5**](https://github.com/EtzionR/Finding-Mountaintops-using-DL/blob/main/Model/Mountaintops_model.h5)

## Model Application
Now, we want to use the model on new data. To do this, we will select as an example the area of [**Rheinwaldhorn Mountain**](https://www.google.com/maps/place/Rheinwaldhorn/@46.4940234,9.0335184,6473m). This new area not included in the boundaries of the old area which we used to build the model. As with the data we dealt with earlier, the information about the new area also should stored as a numpy matrix: [Rheinwaldhorn.npy](https://github.com/EtzionR/Finding-Mountaintops-using-DL/blob/main/Data/Rheinwaldhorn.npy). We will examine the data:

![Rheinwaldhorn area](https://github.com/EtzionR/Finding-Mountaintops-using-DL/blob/main/pictures/rhn.png)

After using the model prediction, we will paint in red the peaks and mountain ranges identified, and present the result in 3D:

![Rheinwaldhorn_gif](https://github.com/EtzionR/Finding-Mountaintops-using-DL/blob/main/pictures/Rheinwaldhorn.gif)

As can be seen, the model was able to successfully identify the peaks along the mountain ranges.

Full code for the model application process can be seen here: [**"implementation.ipynb"**](https://github.com/EtzionR/Finding-Mountaintops-using-DL/blob/main/implementation.ipynb)

## Using the model
To use this model, you just need to import it as follows:
``` sh
# import tensorflow
from tensorflow import keras

# load model
model = keras.models.load_model(r'Model\Mountaintops_model.h5')

# load X
X = ...

# application
Y_prediction = np.round(model.predict(X),0)
```

## Variables

**X:** numpy.array which contain 19x19 matrices of np.floats


## Libraries

**tensorflow**

**matplotlib**

**pandas**

**numpy**


## License
MIT © [Etzion Harari](https://github.com/EtzionData)
