# Script generated with Bloom
pkgdesc="ROS - A rosout GUI viewer developed at Southwest Research Insititute as an alternative to rqt_console."
url='http://ros.org/wiki/swri_console'

pkgname='ros-kinetic-swri-console'
pkgver='1.0.0_1'
pkgrel=1
arch=('any')
license=('BSD'
)

makedepends=('qt5-base'
'ros-kinetic-catkin'
'ros-kinetic-rosbag-storage'
'ros-kinetic-roscpp'
'ros-kinetic-rosgraph-msgs'
)

depends=('qt5-base'
'ros-kinetic-rosbag-storage'
'ros-kinetic-roscpp'
'ros-kinetic-rosgraph-msgs'
)

conflicts=()
replaces=()

_dir=swri_console
source=()
md5sums=()

prepare() {
    cp -R $startdir/swri_console $srcdir/swri_console
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

