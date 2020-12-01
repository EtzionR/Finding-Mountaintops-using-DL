# Finding-Mountaintops-using-DL
Identification of mountain peaks using a Neural Network.

![alps](https://github.com/EtzionR/Finding-Mountaintops-using-DL/blob/main/pictures/Valais_mountain.jpg)
Image source: [Wikimedia](https://commons.wikimedia.org/wiki/Matterhorn#/media/File:Valais_mountains.jpg)

## Introduction
We want to automatically identify the mountain peaks and for this we will use code [**Find_Mountaintops.ipynb**](https://github.com/EtzionR/Finding-Mountaintops-using-DL/blob/main/Find_Mountaintops.ipynb) based on a **Neural Network Model**.

In order to build the model, we will select proper area for **training and testing** the model. The area chosed located in the **Alps Mountains**, on the border between Italy and Switzerland. These are the boundaries of the defined area (wgs84 geo dd):
- **north:** 46.864583
- **South:** 45.687083 
- **East:** 8.878750
- **West:** 7.250417

To build the model, we will use **DTM**, which was produced as part of the [SRTM](https://en.wikipedia.org/wiki/Shuttle_Radar_Topography_Mission) project. The data downloaded from this website [srtmdata](http://srtm.csi.cgiar.org/srtmdata/) and transferred to a **numpy matrix**. The file contain a grid of points which each point value indicates its **height** in meters above sea level. The **tops** matrix, contain 1955 rows, 1414 columns and a total of **2,764,370** height points. The file save as [**tops.npy**](https://github.com/EtzionR/Finding-Mountaintops-using-DL/blob/main/Data/tops.npy). Now, we plot the tops matrix:

![contour](https://github.com/EtzionR/Finding-Mountaintops-using-DL/blob/main/pictures/contour.png)

In order to illustrate the height values of the various points, we chose to present in 3D the **Matterhorn Mountain** area. The data present using a customized version of code **3d-graph-gif**, the full documentation can be found here: [**create-3d-graph-gif**](https://github.com/EtzionR/create-3d-graph-gif):
![Matterhorn](https://github.com/EtzionR/Finding-Mountaintops-using-DL/blob/main/pictures/Matterhorn.gif)

The file [**tags.csv**](https://github.com/EtzionR/Finding-Mountaintops-using-DL/blob/main/Data/tags.csv) contains the labels of each point: **'top'=1** for a mountain peak and **'top'=0** not a mountain peak. Using this tagging, we will extract the location of each point in the matrix [**tops.npy**](https://github.com/EtzionR/Finding-Mountaintops-using-DL/blob/main/Data/tops.npy). In order to identify whether each point is a peak or not, we will process each point together with The height points that surround it, so we get for each tagged point a **19X19 matrix**. An example of such a matrix (showing a mountaintop point) can be seen here:
![example 1](https://github.com/EtzionR/Finding-Mountaintops-using-DL/blob/main/pictures/exm1.png)

Now, based on the labels (Y) and the collection of matrices (X), we will perform the model training, based on 90% of the data we have. This is the model structure we built:
![model](https://github.com/EtzionR/Finding-Mountaintops-using-DL/blob/main/pictures/model.png)

We will now evaluate the forecast quality of the model, based on the remaining 10% of the data. The percentage of correct results of the model seems to be 97.3%, and we will also present the results of the loss values and accuracy along the different epochs of the model:
<>

Examining the errors we received from the model results, it can be seen that in some cases these are borderline situations, in some of which it seems that the incorrect result of the model sometimes seems to make sense:
<>

We will export and save the model so that we can use it for future needs. The model is available at this link: D

## libraries

## Application
An application of the code is attached to this page under the name: 

[**"implementation.ipynb"**](https://github.com/EtzionR/Finding-Mountaintops-using-DL/blob/main/implementation.ipynb)

the examples outputs are also attached here.

## Using the code
To use this code, you just need to import it as follows:
``` sh

```


## Variables

**X:** some.

## License
MIT © [Etzion Harari](https://github.com/EtzionData)


Area


train 90%
test 10%

srtm


Matterhorn
https://www.google.com/maps/place/Matterhorn/@45.973403,7.6841342,5771m/

Rheinwaldhorn
https://www.google.com/maps/place/Rheinwaldhorn/@46.4940234,9.0335184,6473m




implementation
https://github.com/EtzionR/Finding-Mountaintops-using-DL/blob/main/implementation.ipynb

data

https://github.com/EtzionR/Finding-Mountaintops-using-DL/blob/main/Data/Rheinwaldhorn.npy


eval
https://github.com/EtzionR/Finding-Mountaintops-using-DL/blob/main/pictures/eval.png

should be mt, by look like vallay
https://github.com/EtzionR/Finding-Mountaintops-using-DL/blob/main/pictures/error3.png

model
https://github.com/EtzionR/Finding-Mountaintops-using-DL/blob/main/Model/Mountaintops_model.h5

gifs
https://github.com/EtzionR/Finding-Mountaintops-using-DL/blob/main/pictures/Matterhorn.gif
https://github.com/EtzionR/Finding-Mountaintops-using-DL/blob/main/pictures/Rheinwaldhorn.gif
https://github.com/EtzionR/create-3d-graph-gif



