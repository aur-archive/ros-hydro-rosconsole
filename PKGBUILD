# Script generated with import_catkin_packages.py
# For more information: https://github.com/bchretien/arch-ros-stacks
pkgdesc="ROS - ROS console output library."
url='http://www.ros.org/wiki/rosconsole'

pkgname='ros-hydro-rosconsole'
pkgver='1.10.11'
_pkgver_patch=0
arch=('any')
pkgrel=1
license=('BSD')

ros_makedepends=(ros-hydro-rostime
  ros-hydro-catkin
  ros-hydro-cpp-common
  ros-hydro-rosunit)
makedepends=('cmake' 'git' 'ros-build-tools'
  ${ros_makedepends[@]}
  apr
  apr-util
  boost
  log4cxx)

ros_depends=(ros-hydro-rostime
  ros-hydro-rosbuild
  ros-hydro-cpp-common)
depends=(${ros_depends[@]}
  apr
  apr-util
  log4cxx)

_tag=release/hydro/rosconsole/${pkgver}-${_pkgver_patch}
_dir=rosconsole
source=("${_dir}"::"git+https://github.com/ros-gbp/ros_comm-release.git"#tag=${_tag})
md5sums=('SKIP')

build() {
  # Use ROS environment variables
  source /usr/share/ros-build-tools/clear-ros-env.sh
  [ -f /opt/ros/hydro/setup.bash ] && source /opt/ros/hydro/setup.bash

  # Create build directory
  [ -d ${srcdir}/build ] || mkdir ${srcdir}/build
  cd ${srcdir}/build

  # Fix Python2/Python3 conflicts
  /usr/share/ros-build-tools/fix-python-scripts.sh -v 2 ${srcdir}/${_dir}

  # Build project
  cmake ${srcdir}/${_dir} \
        -DCMAKE_BUILD_TYPE=Release \
        -DCATKIN_BUILD_BINARY_PACKAGE=ON \
        -DCMAKE_INSTALL_PREFIX=/opt/ros/hydro \
        -DPYTHON_EXECUTABLE=/usr/bin/python2 \
        -DPYTHON_INCLUDE_DIR=/usr/include/python2.7 \
        -DPYTHON_LIBRARY=/usr/lib/libpython2.7.so \
        -DSETUPTOOLS_DEB_LAYOUT=OFF
  make
}

package() {
  cd "${srcdir}/build"
  make DESTDIR="${pkgdir}/" install
}
