# NeurologIQ_Data Task for cell detection

## Introduction:

The program starts with the basic concept of circle detection using Tensorflow, keras and OpenCV. The model used within this program consists of 3 conv2D layers and a batch-normalization layer.  

## How has labels been created?

Within the create_data_set function all the training images have been cropped (256x256) uing openCV to expand the training data. These snippets are used as inputs. Further, these inputs are grey-scaled and a threshold has been used to find the countours within these images. Later, these countours were drawn on a black background. The final labels look like a black background with cells highlighted in white.  

## Results:

The model has initailly only been trained on parts of an image (256x256) from the training folder. Since the model only work with an input image of dimension (256x256), it only predicts cells within that region and only counts those predicted cells. 

Hence, a sliding window (256x256) is used, when testing on given test images. **Necessary padding** has been applied on the test image before using sliding window. The model identifies the region of cells, and gives the prediction visually which are similar to the label images. Using OpenCV, the number of cells were counted on the identified region of the cropped image.

Once all the cells have been counted in the test image (1500x1500), the final count is stored in a variable called num_of_cells. These cells are marked with a green boundary on the images and saved in the 'CellSample/Results' folder. The final cell count of each image has also been saved as results.csv within the same folder.

