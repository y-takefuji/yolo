# yolo mushi(woodlice) object
This is an example to demonstrate the single object (mushi) positioning.

You should download and install darknet:

$ git clone https://github.com/pjreddie/darknet.git
<pre>
Modify two files in examples/yolo.c and src/image.c:
---examples/yolo.c
#include "darknet.h"
char *voc_names[] = {"mushi"};
---
---src/image.c one line added in void draw_detections---
fprintf(p,"%d,%d \n",(left+right)/2,(top+bot)/2);
---
</pre>
Modify Makefile and make

# prepare a video for preparing data
First, you must prepare a video (test.mp4) to identify the object (woodlice).

Second, the video (test.mp4) will be used for generating multiple jpg or png files.

video2jpg will generate mushiXXX.jpg or png files using test.mp4.

Install labelImg for labeling mushixxx.jpg or png. Labeling (annotation) is to identify the location of the object in every image file. mushiXXX.txt will be generated.

In order to generate mushiXXX.txt for YOLO, you must click PascalVOC to change to YOLO for annotation. And click Use default label and enter mushi to generate mushiXXX.txt.

Now, you have mushiXXX.jpg or png files and mushiXXX.txt files.

Change process.py, train.txt will be generated by process.py.

$ cat train.txt
mushi/mushi0.png

...

mushi/mushi78.png

structure of darknet
<pre>
darknet
|_mushi/images/mushi0.png
...
|_mushi/train.txt
|_mushi/labels/mushi0.txt
...
|_mushi/mushi.data
|_mushi/mushi.names
</pre>
<pre>
$ cat train.txt
mushi/mushi0.png
...

$ cat mushi.data
classes=1
train=train.txt
valid=test.txt
labels=mushi.names
backup=backup/

$ cat mushi/mushi.names
mushi

</pre>
