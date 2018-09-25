# Installation Guide of Python 2.7.9

Installation Guide of Python 2.7.9 for Augmented Reality lab sessions.

## On Windows

### Download and install Python 2.7.0

From [here](https://www.python.org/downloads/release/python-279). You can try to install python in the user filesystem to avoid having to deal with administrator permissions.

### Update PiP tool

Open a CMD shell (as administrator if Python was installed in the root filesystem). Go to the directory with the python executable and type:

```
python.exe -m pip install --upgrade pip
```

### Install numpy and matplotlib

From the same directory, type:

```
python.exe -m pip install numpy
python.exe -m pip install matplotlib
```

### Install OpenCV

Download OpenCV from [here](https://sourceforge.net/projects/opencvlibrary/files/opencv-win).

Copy the file at 'opencv\build\python\2.7\x86\cv2.yd' into the Python directory 'Python2.7.9\Lib\site-packages'.

### That's all

After installing and IDE tool such as PyCharm, we should have Python with those three modules available.
