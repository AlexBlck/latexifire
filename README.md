LaTeXiFire
===

### TODO

 - [ ] Set up Kaggle notebook for data generation for part 3
     - [ ] Find datasets to use as base [(Search google)](https://toolbox.google.com/datasetsearch)
 - [ ] Keep all NNs private, other stuff can go on repo
 - [ ] Set up README on Github
 - [ ] First test & classification data uses subset of characters:
     - [ ] MNIST only

### TODO Dom
 - [ ] https://www.kaggle.com/domhenjes/latexifire-generate-images/edit
 - [ ] Research Python image manipulation libraries etc.
 - [ ] Set up data generation script for MNIST subset of EMNIST
     - [ ] Convert images into PNG format
     - [ ] Create full-page images that contain multiple MNIST characters
 - [ ] Create data generation script for full formulae
     - [ ] Set up syntactically correct phrases
     - [ ] Convert phrases to image chains and add into A4 page - wait with this until later

### Meeting 1

Small number of characters to start with (5-8)
EMNIST or some maths character dataset
Read in A4 page in png format (A4 page is 595x845 px at 72 dpi)
Set up data generation script for making training data

### Overview of project

Do in following order: Stage 3, Stage 4, Stage 2, Stage 1

- [Stage 1: detect paper sheet](#Stage-1)
- [Stage 2: unskew paper & format input for analysis](#Stage-2)
- [Stage 3: detect formulae and add bounding boxes + labels](#Stage-3)
- [Stage 4: convert to LaTeX](#Stage-4)

### Stage 1

**Input:** Picture, PNG format, taken by user, containing an A4 sheet of paper.

**Output:** Coordinates of four corners of the paper sheet.

**Process:** CNN? Simple edge detection? Contrast?

### Stage 2

**Input:** Skewed paper + co-ordinates of 4 corners of paper sheet

**Output:** Corrected, 'PDF-like' page in PNG format

**Process:** Image transformations of some sort - research more when working on this part

### Stage 3

**Input:** PNG image of A4 page (+ whitespace padding for YOLO - dimensions 864x864px), adjusted to remove skew & scaling issues

**Output:** PNG image with bounding boxes, labels & confidence rating so for the characters inside

**Process:** Use an NN of some sort to identify bounding boxes and specify the characters inside

### Ideas - Data Generation
 - EMNIST
 - Maths character datasets off google dataset search
 - Start with fewer characters and work our way up - use MNIST-only to begin

1. Create .txt-file for each .png-image-file - in the same directory and with the same name, but with .txt-extension, and put to file: object number and object coordinates on this image, for each object in new line: <object-class> <x> <y> <width> <height>

Where:

 - <object-class> - integer object number from 0 to (classes-1)
 - <x_center> <y_center> <width> <height> - float values relative to width and height of image, it can be equal from (0.0 to 1.0)
 - for example: <x> = <absolute_x> / <image_width> or <height> = <absolute_height> / <image_height>
 - attention: <x_center> <y_center> - are center of rectangle (are not top-left corner)

For example for img1.jpg you will be created img1.txt containing:

```
    1 0.716797 0.395833 0.216406 0.147222
    0 0.687109 0.379167 0.255469 0.158333
    1 0.420312 0.395833 0.140625 0.166667
```

    
2. Create train.txt and test.txt, containing the paths to all train and test images, respectively. Eg:

```
    data/obj/img1.jpg
    data/obj/img2.jpg
    data/obj/img3.jpg
```

#### Ideas - Classifying
 - YoLo
 - RCCNs
 - Whitespace bounding boxes + character analysis
 - Original network

#### Attempt 1 - Data Generation


#### Attempt 1 - Classifying
YoLo

### Stage 4

**Input:** Labelled boxes with confidence ratings on PNG image - some boxes will overlap/refer to the same character

**Output:** LaTeX syntax for formula on page

**Process:** Image is converted into 

#### Ideas
- TensorFlow
- PyTorch
- Keras
- Pandas
- SciPy

