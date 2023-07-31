春季
=================================


.. tip:: Check this section to see if there are specific prerequisites for your 
   Linux/Unix distribution.

Before you can build Ceph source code, you need to install several libraries
and tools::

	./install-deps.sh

.. note:: Some distributions that support Google's memory profiler tool may use
   a different package name (e.g., ``libgoogle-perftools4``).

Build Ceph
==========

Ceph is built using cmake. To build Ceph, navigate to your cloned Ceph
repository and execute the following::

    cd ceph
    ./do_cmake.sh
    cd build
    make

.. note:: By default do_cmake.sh will build a debug version of ceph that may
   perform up to 5 times slower with certain workloads. Pass 
   '-DCMAKE_BUILD_TYPE=RelWithDebInfo' to do_cmake.sh if you would like to
   build a release version of the ceph executables instead.

.. topic:: Hyperthreading

	You can use ``make -j`` to execute multiple jobs depending upon your system. For 
	example, ``make -j4`` for a dual core processor may build faster.


Build Ceph Packages
===================


.. tip:: When building on a multi-core CPU, use the ``-j`` and the number of 
   cores * 2. For example, use ``-j4`` for a dual-core processor to accelerate 
   the build.


Advanced Package Tool (APT)
---------------------------


	sudo apt-get install debhelper

Once you have installed debhelper, you can build the packages::

	sudo dpkg-buildpackage

For multi-processor CPUs use the ``-j`` option to accelerate the build.

