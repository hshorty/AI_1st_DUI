# AI_1st_DUI
# 1. Setup environment and others

## 1.1 Setup environment 

### 1.1.1 Open mini conda
### 1.1.2 conda create -n yolov8_custom python=3.9
### 1.1.3 activate the environment 

## 1.2 Install a library to Downloading images from google

### 1.2.1 $ip install simple_image_download==0.4
### 1.2.2 once the download is completed, create a new file called "download_images.py"
### 1.2.3 download images 
    $python download_images.py
### 1.2.4 Create a new folder called images. Put 50 good images form the downloaded images.
### 1.2.5 now you can delate the old folder contains downloaded images

## 1.3 Anotating the data and creating a data set

### 1.3.1 Download an anotaion tool 
        $pip install labelImg
### 1.3.2 run the tool
        $lableImg
### 1.3.3 file->open dir->select our 'image' folder
### 1.3.4 file->change save dir-> create a new folder called labels and select that folder
### 1.3.5 set to 'yolo' not to 'pasXX' 
### 1.3.6 make rectanges and label them 
### 1.3.7 once all the images are labeled you will see a list of labels for each image in the labels folder
### 1.3.8 Create a new folder called 'val'  
            * inside val create a folder 'images'  and 'labels' (for testing)
            cut and past 6 images form the original image folder to new image folder and corrosponding labels to new label folder.

            * create new folder called 'train' along with 'val' folder and put original 'images' and 'label' folders to this folder.
### 1.3.9 Now we have our training and testing data sets.

# 2. Training the model
### 2.1 Create the data_custom.yaml file
### 2.2 setup yolov8 (this will install all the libraries you need to run yolov8) this is the cpu version
    $pip install ultralytics
### 2.3 train the model
    $yolo task=detect mode=train epochs=100 data=data_custom.yaml model=yolov8m.pt imgsz=640 batch=4
### 2.4 once the tranning is over you can find your trained model in 
    runs\detect\train\weights\best.pt (best.pt is your model)
### 2.5 copy 'best.pt' and past in your root folder and rename it to yolov8m_custom.pt

# 3. Test the model
$yolo task=detect mode=predict model=yolov8m_coustom.pt source=1.jpeg conf=0.5 show=True

# Reference
https://www.youtube.com/watch?v=gRAyOPjQ9_s 











