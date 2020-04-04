# Ops Experiments Deconvolution

Ops Experiments is an experimental repository used to play around with new ideas.  Thus far it has mainly been used to work out how to connect ImageJ to native math libraries like [MKL](https://software.intel.com/en-us/mkl), [IPP](https://software.intel.com/en-us/ipp), [Cuda](https://developer.nvidia.com/cuda-zone) and [CLFFT](https://github.com/clMathLibraries/clFFT).  Currently ops-experiments has been used to implement some GPU deconvolution algorithms.  

The code can be found [here](https://github.com/imagej/ops-experiments)  

## Installation

[windows files can be found here](https://www.dropbox.com/sh/6hlplqgfkbd5p1n/AAAc4MqtGfrNdRyqjbbcIgnOa?dl=0)

[Linux Files can be found here](https://www.dropbox.com/sh/yijt2swbbgo2rqu/AAAX4dYCGiXYRozAOHZ3icxMa?dl=0)

Mac version is being discussed on [ImageSC](https://forum.image.sc/)

Copy all jar files into the 'Fiji.app/jars' directory.  You may want to install a fresh 'experimental' version of Fiji, because you need to overwrite ```javacpp``` and ```imglib2``` with newer versions. 

## Test Images

Test images are [here](https://www.dropbox.com/sh/owh83l3isipv3xy/AABx_qZ69uLU5jnbNw1gVkx-a?dl=0)

## Update site

An official update site is quite possible soon.  It's not here yet because a couple of the dependencies (javacpp specifically) need to be updated in Fiji.  It's also unclear to me how to handle Windows vs Linux distribution as different native libs need to be distributed in each case. 

## OpenCL CLIJ friendly version 

Add the CLIJ update site.  

In the dropbox directory there is a script called 'CLIJDecon.py'.  The script is also [here](https://github.com/imagej/ops-experiments/blob/master/ops-experiments-opencl/ijscripts/CLIJDecon.py).   Load and run this script in the Fiji script editor.  A dialog will appear and you choose an image and PSF.  

<img src="CLIJDecon.jpg" width="742">  

After running the script a message should appear indicating which GPU device is used.  Verify it is using the GPU (CLIJ sometimes defaults to the CPU)  

<img src="CLIJDeconOutput.jpg" width="742">  

And a deconvolved image should appear too... something like this...  

<img src="OutputImage.jpg" width="200">  

## CUDA (YacuDecu) plugins

There are also some plugins available that derive from Bob Pepin's [YacuDecu](https://github.com/bobpepin/YacuDecu).  Some changes have made for ImageJ integration, non-circulant deconvolution, and assymetrical PSFs.  The updated code base is [here](https://github.com/imagej/ops-experiments/tree/master/ops-experiments-cuda).  

After adding the jars from the dropbox folder the following menu should appear 

<img src="OpsExperimentsMenu.jpg" width="500">  

These plugins require updated NVIDIA drivers and [Cuda 10+](https://developer.nvidia.com/cuda-downloads)

1.  YacuDecu Deconvolution - choose an image and PSF and deconvolve.
4.  YacuDecu Theoretical PSF - Deconvolve an image with a theoretical PSF.   
2.  YacuDecu Deconvolution Batch - experimental interface for batch processing several files.  
3.  YacuDecu Refractive Index Tester - Deconvolved an image several times over, using a range of sample refractice indexes.  Useful for evaluating the true RI of a sample.  

Any questions about these plugins?? Or problems running these plugins ??  Ask on [ImageSC Message Board](https://forum.image.sc/)
