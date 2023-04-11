Yocto migration plan
====================

Initial effort
--------------

* start with current Jetpack version => 32.5.0
* start with corresponding meta-tegra branch => dunfell-l4t-r32.5.0
  (which really seems to be 32.5.2)
* rebase vc-mipi camera patches on corresponding linux-tegra-4.9 jetpack branch
* add rebased patches to yocto kernel recipe
* make new recipe for user-space application
* document yocto workflow for kernel/user-app

.. note:: Turns out l4t-graphics-demos_32.5.1 pkg is broken on the dunfell-l4t-r32.5.0
  branch, however, kirkstone-l4t-r32.7.x branch builds fine (and probably latest
  dunfell 32.6 as well).  Since camera driver is supported on 32.5 - 32.7 we will
  bump straight to the latest LTS branch => kirkstone-l4t-r32.7.x


week 1
------

* fork and update any necessary upstream repos
* flashable (test) yocto image with vc_mipi driver and application support

week 2
------

* document yocto build/deploy workflows
* make sure dev workflow/build is clean and repeatable

stretch goals
-------------

* do the proper meta-tegra dev things

  + create yocto layer and define custom machine bits for production HW
  + define project/product distro for release versioning


New jetpack/yocto baseline
--------------------------

* forward-port vc_mipi_camera patches to latest LTS branch with TX2 support

  + latest dunfell LTS => dunfell-l4t-r32.6.1 (should work, but getting old)
  + latest kirkstone LTS => kirkstone-l4t-r32.7.x (pkgs good, newer kernel rev)
  + verify camera/user-app on  LTS branch

* the above branches should be reasonably clean on current antmicro/capable_robot hardware
* kirkstone-l4t-r32.7.x is preferred, unless we find a requirement for rolling back to
  dunfell-l4t-r32.6.1 branch
* moving to newer (than kirkstone-l4t-r32.7.x) meta-tegra and/or kernel branches
  *requires* either migrating or dropping TX2-class machine support


Reference links
===============

https://github.com/OE4T/tegra-demo-distro/tree/dunfell-l4t-r32.5.0
https://github.com/OE4T/linux-tegra-4.9/tree/oe4t-patches-l4t-r32.5)
https://docs.yoctoproject.org/3.1.20/dev-manual/dev-manual-common-tasks.html
