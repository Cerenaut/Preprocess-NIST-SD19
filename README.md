# Preprocessing for NIST Special Dataset #19 (handwritten character recognition)

This repository contains Java code without any dependencies to preprocess NIST Special Dataset #19 (characters A..Z) to the same format as used in the famous MNIST handwritten digit (0..9) recognition dataset. The MNIST dataset was preprocessed by Yann LeCun as described here:

http://yann.lecun.com/exdb/mnist/

The intended purpose of this is to be able to combine this dataset with MNIST to have a combined alphanumeric handwritten digit dataset.

# Where to get the input data
This code will preprocess the MNIST SD-19 "by_class" dataset of alphabetic characters.

Note the dataset belongs to NIST, and was not created by us.

Download "by_class.zip" from this link and unzip it to a directory:

https://www.nist.gov/srd/nist-special-database-19

# How to use the code
The program consists of a single Java file with a main() method.

Build and invoke the main method with 3 arguments:

1. The location of the unzipped input images
2. The folder you'd like the preprocessed images to be written to
3. A prefix for the output image filenames

# What it does
This program applies exactly the same operations as LeCun did to MNIST digits, to the NIST SD19 characters.

In theory you can then use these as part of a combined alphanumeric dataset.

The steps performed are described here:

http://yann.lecun.com/exdb/mnist/

Specifically, we find the bounding box and centre of mass of non-background pixels, and then crop the smallest square centred on the centre of mass that fits the entire foreground bounding box. 

The croped image part is resized to 20x20 pixels and pasted into a 28x28 image at origin 4,4. This creates a 4 pixel margin on all sides (just like MNIST). Greyscale values result from interpolation of pixel intensities.

# Output image labels
The dataset includes uppercase characters A-Z (ascii 0x41 to 0x5a / 65 to 90). We use the two-digit ASCII codes to label the images with integer values:

https://en.wikipedia.org/wiki/ASCII

# Dependencies
This program has no dependencies except standard Java libraries.
