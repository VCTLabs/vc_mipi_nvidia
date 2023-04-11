Yocto migration plan
====================

Initial effort
--------------

* start with current Jetpack version => 32.5.0
* start with corresponding meta-tegra branch => dunfell-l4t-r32.5.0
  (which really seems to be 32.5.2)
* rebase vc-mipi camera patches on linux-tegra-4.9 branch oe4t-patches-l4t-r32.5
* add rebased patches to yocto kernel recipe (bbappend)
* make new recipe for user-space application
* document yocto workflow for kernel/user-app

week 1
------

* flashable (test) yocto image with vc_mipi and application support

week 2
------

* fork and update any necessary upstream repos
* document yocto build/deploy workflows
* make sure dev workflow/build is clean and repeatable

stretch goals
-------------

* do the proper meta-tegra dev things

  + create yocto layer and define custom machine bits for production HW
  + define project/product distro for release versioning


Future-proofing
---------------

* forward-port vc_mipi_camera patches to latest LTS branches

  + latest dunfell LTS => dunfell-l4t-r32.6.1
  + latest kirkstone LTS => kirkstone-l4t-r32.7.x
  + verify camera/user-app on each LTS branch

* the above branches should be reasonably clean on current antmicro/capable_robot hardware
* moving to newer meta-tegra and/or kernel branches *requires* either migrating
  or dropping TX2-class machine support


Reference links
===============

https://github.com/OE4T/tegra-demo-distro/tree/dunfell-l4t-r32.5.0
https://github.com/OE4T/linux-tegra-4.9/tree/oe4t-patches-l4t-r32.5)
https://docs.yoctoproject.org/3.1.20/dev-manual/dev-manual-common-tasks.html
