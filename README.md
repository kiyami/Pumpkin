# Pumpkin
Code for Principal Component and Random Forest Classification to study Galaxy Cluster X-ray Emission

In order create the synthetic data the *ciao* software package is required. It can be found here: https://cxc.cfa.harvard.edu/ciao/

In order to create the synthetic data, update the StN150_Single.py and StN150_Double.py files with the appropriate directories. Then run the following command,
`python StN150_Single.py && python StN150_Double.py`

We then need to shuffle the data (again please update the directories in the StN150_shuffle.py file)...
Then run `python StN150_shuffle.py`

With the synthetic data created, we can now move to training and testing the algorithm. To do so open ***PCA_ML-StN150.ipynb***.


## Perseus Cluster
This repository contains all the code required to recreate the Perseus cluster map (figure 8) in our 2020 paper. There are several steps needed to recreate the map:


1. Download the ObsIDs 3209 and 4289
2. Merge the two ObsIDs using CIAO, determine region of choice in ds9, and finally use dmcopy to extract a fits image of the region (I called it source.img)
3. Update ComponentMap/Perseus.i --> namely image\_fits and base\_dir
4. Run "python ComponentMap/ExtractSpectra.py ComponentMap/Perseus.i"
	- This will create a WVT map of your region and extract the spectra of each region for each ObsID (it takes a while)
5. Run "python ComponentMap/Components.py ComponentMap/Perseus.i"
	- This will take your WVT map and assign a number of underlying components to each region using our trained algorithm and the extracted spectra
6. Update Temperatures/Perseus.i with the correct base\_dir and output\_dir
7. Run "python Temperatures/Temperature_Maps.py Perseus.i"
 	- This will calculate the temperatures of each component in each region and create maps of each temperature



This is Pumpkin
![alt text](https://scontent.fykz2-1.fna.fbcdn.net/v/t1.0-9/92460203_10157331845593892_1711534790894682112_o.jpg?_nc_cat=106&_nc_sid=84a396&_nc_ohc=aNAKpmS6fgQAX9K2vgB&_nc_ht=scontent.fykz2-1.fna&oh=c69224b5f7fce1a282286ffe68f42ecd&oe=5F80D829 "Pumpkin")
