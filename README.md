# Search Engine for images


## Overview
A simple image search using keras and flask. It extracts the features from the
images stored in ‘img’ folder and saves them in ‘.npy’ file format in the ‘feature’ folder.
Transfer learning approach is used to utilize a VGG16 model with weights pretrained on
imagenet dataset. This model is used to extract features from the images. The server file
runs a web-server using flask. The query image is sent to the server via a Flask
web-interface. The server finds similar images to the query image by a linear scan and
returns top 10 similar images with a score. This score represents how close the query image
is to the result image.

### Files overview
- `offline.py`: This script extracts a deep-feature from each database image. To extract features a VGG16 model is used with ImageNet pre-trained weights.
- `server.py`: This script runs a web-server. You can send your query image to the server via a Flask web-interface. The server finds similar images to the query by a simple linear scan.
- GPUs are not required.
- Tested on Ubuntu 16.04


### To run the application on local machine:

1. Run the below command from terminal of your root directory to install requirements.

    ```sh
    $ pip install -r requirements.txt
    ```
1. Run offline python file to extract features. Note that it takes time for the first time because Keras downloads the VGG weights.

    ```sh
    $ python offline.py
    ```
1. Run the server file
    ```sh
    $ python server.py
    ```

1. Open application using url: `http://localhost:5000`.

### Results:
- Example 1
![alt text](https://github.com/Varun-08/image_search/blob/main/result1.png?raw=true)

- Example 2
![alt text](https://github.com/Varun-08/image_search/blob/main/result2.png?raw=true)


### Note:
- If you want to search with existing images, then no need to run offline file. Directly run the server file and search images.
- If you want to search with your own images dataset, then delete the existing images and its corresponding feature files from img and feature directory respectively.
- Add your images to img directory and run offline file to extract features and then run server file to search images.