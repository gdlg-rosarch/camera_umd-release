# Script generated with Bloom
pkgdesc="ROS - A collection of node(let)s that stream images from USB cameras (UVC) and provide CameraInfo messages to consumers. Includes a two-camera node that provides rough synchronization for stereo vision. Currently uses the base driver from Morgan Quigley's uvc_cam package."
url='http://ros.org/wiki/uvc_camera'

pkgname='ros-kinetic-uvc-camera'
pkgver='0.2.5_1'
pkgrel=1
arch=('any')
license=('GPLv2'
)

makedepends=('ros-kinetic-camera-info-manager'
'ros-kinetic-catkin'
'ros-kinetic-image-transport'
'ros-kinetic-nodelet'
'ros-kinetic-roscpp'
'ros-kinetic-sensor-msgs'
'v4l-utils'
)

depends=('ros-kinetic-camera-info-manager'
'ros-kinetic-image-transport'
'ros-kinetic-nodelet'
'ros-kinetic-roscpp'
'ros-kinetic-sensor-msgs'
'v4l-utils'
)

conflicts=()
replaces=()

_dir=uvc_camera
source=()
md5sums=()

prepare() {
    cp -R $startdir/uvc_camera $srcdir/uvc_camera
}

build() {
  # Use ROS environment variables
  source /usr/share/ros-build-tools/clear-ros-env.sh
  [ -f /opt/ros/kinetic/setup.bash ] && source /opt/ros/kinetic/setup.bash

  # Create build directory
  [ -d ${srcdir}/build ] || mkdir ${srcdir}/build
  cd ${srcdir}/build

  # Fix Python2/Python3 conflicts
  /usr/share/ros-build-tools/fix-python-scripts.sh -v 2 ${srcdir}/${_dir}

  # Build project
  cmake ${srcdir}/${_dir} \
        -DCMAKE_BUILD_TYPE=Release \
        -DCATKIN_BUILD_BINARY_PACKAGE=ON \
        -DCMAKE_INSTALL_PREFIX=/opt/ros/kinetic \
        -DPYTHON_EXECUTABLE=/usr/bin/python2 \
        -DPYTHON_INCLUDE_DIR=/usr/include/python2.7 \
        -DPYTHON_LIBRARY=/usr/lib/libpython2.7.so \
        -DPYTHON_BASENAME=-python2.7 \
        -DSETUPTOOLS_DEB_LAYOUT=OFF
  make
}

package() {
  cd "${srcdir}/build"
  make DESTDIR="${pkgdir}/" install
}

