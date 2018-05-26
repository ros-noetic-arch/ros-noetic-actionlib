# Script generated with import_catkin_packages.py
# For more information: https://github.com/bchretien/arch-ros-stacks
pkgdesc="ROS - The actionlib stack provides a standardized interface for interfacing with preemptable tasks."
url='http://www.ros.org/wiki/actionlib'

pkgname='ros-melodic-actionlib'
pkgver='1.11.14'
_pkgver_patch=0
arch=('any')
pkgrel=1
license=('BSD')

ros_makedepends=(ros-melodic-std-msgs
  ros-melodic-actionlib-msgs
  ros-melodic-roscpp
  ros-melodic-catkin
  ros-melodic-message-generation
  ros-melodic-rostest
  ros-melodic-rospy)
makedepends=('cmake' 'ros-build-tools'
  ${ros_makedepends[@]}
  boost)

ros_depends=(ros-melodic-rostopic
  ros-melodic-std-msgs
  ros-melodic-actionlib-msgs
  ros-melodic-message-runtime
  ros-melodic-roscpp
  ros-melodic-roslib
  ros-melodic-rostest
  ros-melodic-rospy)
depends=(${ros_depends[@]}
  wxpython
  boost)

# Git version (e.g. for debugging)
# _tag=release/melodic/actionlib/${pkgver}-${_pkgver_patch}
# _dir=${pkgname}
# source=("${_dir}"::"git+https://github.com/ros-gbp/actionlib-release.git"#tag=${_tag})
# sha256sums=('SKIP')

# Tarball version (faster download)
_dir="actionlib-release-release-melodic-actionlib-${pkgver}-${_pkgver_patch}"
source=("${pkgname}-${pkgver}-${_pkgver_patch}.tar.gz"::"https://github.com/ros-gbp/actionlib-release/archive/release/melodic/actionlib/${pkgver}-${_pkgver_patch}.tar.gz")
sha256sums=('6fe3fdad940d570f8a1c0c6ebd4f2f847b015097301003ab8f9f81990f837108')

build() {
  # Use ROS environment variables
  source /usr/share/ros-build-tools/clear-ros-env.sh
  [ -f /opt/ros/melodic/setup.bash ] && source /opt/ros/melodic/setup.bash

  # Create build directory
  [ -d ${srcdir}/build ] || mkdir ${srcdir}/build
  cd ${srcdir}/build

  # Fix Python2/Python3 conflicts
  /usr/share/ros-build-tools/fix-python-scripts.sh -v 2 ${srcdir}/${_dir}

  # Build project
  cmake ${srcdir}/${_dir} \
        -DCMAKE_BUILD_TYPE=Release \
        -DCATKIN_BUILD_BINARY_PACKAGE=ON \
        -DCMAKE_INSTALL_PREFIX=/opt/ros/melodic \
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
