# opencv4.5_gstreamer-script
A Script : Headless Opencv4.5 setup with Gstreamer for Ubuntu 18.04, Jetson Nano
### Create Temp
_I recommended this script with new environment in Python3.8(Support 18.04)_
```
OPENCV_VER="master"
TMPDIR=$(mktemp -d)
cd "${TMPDIR}"
```
### Get Opencv From git
`git clone --branch ${OPENCV_VER} --depth 1 --recurse-submodules --shallow-submodules https://github.com/opencv/opencv-python.git opencv-python-${OPENCV_VER}`
and 
`cd opencv-python-${OPENCV_VER}
`
### Set Cmake file parameters
```
export ENABLE_CONTRIB=0
export ENABLE_HEADLESS=1
export CMAKE_ARGS="-DWITH_GSTREAMER=ON"
```
_important note : in my case i need additionally need "GTK" check you need or not, if you need use this code block ;_
`export CMAKE_ARGS="-DWITH_GTK=ON"`

### And finally pip with wheel
_may take 1-2 hours depending on your system_
`python3 -m pip wheel . --verbose`

### And Just pip install
`python3 -m pip install opencv_python*.whl
`



