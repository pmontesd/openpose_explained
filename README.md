# OpenPose Explained

_This work would be impossible without_ [_Ildoo Kim_](https://github.com/ildoonet/tf-pose-estimation).

Material regarding my talks at EuroSciPy 2018 and PyConES 2018.

There are 4 notebooks:
* 3 notebooks start 3 different ROS nodes: 1 that reads frames from your webcam, 1 that process those frames using OpenPose and 1 that displays the output image in a window.
* 1 notebook allows you to compare the different versions of OpenPose (which I've called VGG and Mobile). One of them uses standard convolutions while the other depthwise convolutions.

(0) Install Docker.

(1) Build the image.

`sudo docker build openpose_ros .`

(2) Run a container.

```
sudo docker run --rm -it \
   --ipc=host -p 8888:8888 \
   --device=/dev/video0:/dev/video0 \
   --env="DISPLAY" \
   --env="QT_X11_NO_MITSHM=1" \
   --volume="/tmp/.X11-unix:/tmp/.X11-unix:rw" \
   openpose_ros bash
```

(3) Run `roscore` on background.
`roscore &`
Once `roscore` is all set (this will take a few seconds), Ctrl+C to return to the command line while `roscore` still runs on background.

(4) Run Jupyter.

`jupyter-notebook --ip 0.0.0.0 --no-browser --allow-root`

Now you can go to your browser and access the notebook through `http://localhost:8888/?token=HERECOMESYOURTOKEN`. **Important**: modify the last address adding the token generated by Jupyter at start.

(5) Needed to see in your screen the windows generated in the docker container.

`xhost +local:root`