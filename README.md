# Video Analytics on Intel GPU

## Introduction

 * This shows how to do video analytics integraton on Intel GPU with best peformance, including multiple streams decoding, video processing and inference with OpenVINO. some of codes was borrowed from Intel's VAIT code. thanks for their great work!!!    you can refer more on VAIT(https://software.intel.com/en-us/articles/vaitpreview)

### Key Features:

 * Decoding and video processing with MSDK
 * Inference with GPU with OpenVINO
 * scale from 1 stream to multiple streams.  the maximum supported is 48 for now.
 * RGBP color format supported with latest MSDK + Open Source media driver
 * Docker based environment for user easy to setup the environment

### WIP features:
 * add display
 * workload balance between CPU + GPU
 * batch cross different streams

### Expected Usages:

 * Reference to learn CVSDK, MSDK, and OpenCL
 * Reference source code about how to use MediaSDK pipe/plugin

## Requirements

 * Intel MediaSDK
 * Intel Computer Vision SDK 
 * Intel OpenCL driver needs to be installed correctly. 

## pre-requisites installation without Docker

 * Ubuntu 16.04.3
   Install OS and finish "sudo apt-get update; sudo apt-get upgrade; reboot"
   Copy "vait_prerequisites_install_ubuntu.py" and "silent.cfg" to other folder (ex: ~/tmp)
   
   - SKL/BXT     
	   Script will create many folders and download packages in current folder, so you'd be better run this from other directory, not in the VAIT folder.

	   tmp$ sudo vait_prerequisites_install_ubuntu.py
	   tmp$ reboot
## installation with Docker

 * Ubuntu 16.04.3
   Install OS and finish "sudo apt-get update; sudo apt-get upgrade; reboot"
 
 * docker build -t <any name>:<any:version> .
 * docker run -ti --device /dev/dri:/dev/dri IMAGEID /bin/bash
 

## build

 * Ubuntu 16.04.3

   $ source env.sh
   $ mkdir build
   $ cd build
   $ cmake ..
   $ make

      
## VAIT execution

 * Ubuntu 16.04.3
 
   
   .\build\video_analytics_example\video_analytics_example -i ../../test_content/video\cars_768x768.h264 -d GPU -m ../test_content/IR/SSD/SSD_GoogleNet_v2_fp16.xml -l ../test_content/IR/SSD/pascal_voc_classes.txt -fr 50
       

