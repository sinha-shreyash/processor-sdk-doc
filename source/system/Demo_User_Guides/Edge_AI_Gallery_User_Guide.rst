.. include:: /_replacevars.rst

.. _Edge-AI-Gallery-User-Guide-label:

Edge AI Gallery - User Guide
============================

Overview
--------

The |__PART_FAMILY_DEVICE_NAMES__| SK board has a QT based Out of Box application setup so that user can test the prepackaged models, with sample images, videos and optionally with a connected camera. The Demo also allows users to add their custom models, images, and videos to extend the functionality.

All of the necessary equipment requirement and instructions are provided here.

Hardware Prerequisites
----------------------

- TI |__PART_FAMILY_DEVICE_NAMES__| SK

- PC (Windows or Linux, to use serial terminal console)

- HDMI Monitor (to view the Demo on Display)

- IMX219 Camera

- USB Mouse

- SD card (minimum 16GB)

- Ethernet connection (if serial terminal console is not accessible)

Launching and Using the edge AI gallery
---------------------------------------

The edge AI gallery launches on Linux startup. Follow the below instructions to use it.

1. Connect the Display, IMX219 Camera, Mouse, Ethernet and Power on the board. The application will launch when the Device is fully booted.

.. Image:: /images/am62a_edge_ai_gallery_home.jpg
   :width: 407
   :height: 400

|

2. Once started, You can click on one of the ``Image Classification``, ``Object Detection`` or ``Semantic Segmentation`` to validate the models with a fixed GStreamer pipeline.

.. Image:: /images/am62a_edge_ai_gallery_cl.jpg
   :width: 407
   :height: 400

.. Image:: /images/am62a_edge_ai_gallery_od.jpg
   :width: 407
   :height: 400

.. Image:: /images/am62a_edge_ai_gallery_ss.jpg
   :width: 407
   :height: 400

|

3. To switch to a new pipeline, click on the same button again to stop the currently running pipeline.

4. To create and run a custom pipeline, click on ``Custom`` button. You'll be provided with a popup menu to choose the below options.

   - Input Type: Image, Video or Camera

   - Input: Image/Video file or Camera Device (For Image or Video files, the path displayed next to the dropdown heading is where you can add your custom files)

   - Model: Models available in the file system (The path displayed next to the dropdown heading is where you can add your custom models)

.. Image:: /images/am62a_edge_ai_gallery_popup.jpg
   :width: 407
   :height: 400

|

5. Select the 4 options as described above and click on ``Start`` to generate and start the pipeline.

   .. note:: As the note suggests, it might take a while for custom pipeline to start.

.. Image:: /images/am62a_edge_ai_gallery_custom.jpg
   :width: 407
   :height: 400

|

6. Click on ``Custom`` button again to stop the custom pipeline.

7. For ease of use, the IP addr of the device is displayed at the bottom right when Network is connected.

   .. note:: The IP addr is polled only for the first 100 seconds after the application has started.

8. To close the application and go to the Wallpaper screen, use the close button on the top right corner.

.. Image:: /images/am62a_edge_ai_gallery_wallpaper.jpg
   :width: 407
   :height: 400

|


9. To add new images, videos and models, you should add them in the below directories respectively

   - Images - /opt/edgeai-test-data/images/

   - Videos - /opt/edgeai-test-data/videos/

   - Models - /opt/model_zoo/


10. To change the videos in the prebuilt pipelines used for ``Image Classification``, ``Object Detection``, ``Semantic Segmentation`` & ``Multi Channel``, you can replace the video files ``oob-gui-video*.h264`` under ``/opt/oob-demo-assets/``.


11. To relaunch the application, you should run
   ::

        /etc/init.d/edgeai-launcher.sh start

12. And to stop the application again, you should run
   ::

        /etc/init.d/edgeai-launcher.sh stop

.. ifconfig:: CONFIG_part_family in ('AM62AX_family')

   13. To add new models to the ``Model`` dropdown list in Custom popup menu, Add the names of the models in ``/opt/oob-demo-assets/allowedModels.txt``.

   .. note:: For the above changes to take affect, close and relaunch the application.

   14. For more information on edge AI software stack, refer `Edge AI Documentation <https://software-dl.ti.com/jacinto7/esd/processor-sdk-linux-edgeai/AM62AX/10_01_00/exports/edgeai_docs/common/sdk_overview.html>`_

.. ifconfig:: CONFIG_part_variant in ('J721E')

   13. For more information on edge AI software stack, refer `Edge AI Documentation <https://software-dl.ti.com/jacinto7/esd/processor-sdk-linux-edgeai/TDA4VM/10_01_00/exports/docs/common/sdk_overview.html>`_

.. ifconfig:: CONFIG_part_variant in ('J721S2')

   13. For more information on edge AI software stack, refer `Edge AI Documentation <https://software-dl.ti.com/jacinto7/esd/processor-sdk-linux-edgeai/AM68A/10_01_00/exports/docs/common/sdk_overview.html>`_

.. ifconfig:: CONFIG_part_variant in ('J784S4')

   13. For more information on edge AI software stack, refer `Edge AI Documentation <https://software-dl.ti.com/jacinto7/esd/processor-sdk-linux-edgeai/AM69A/10_01_00/exports/docs/common/sdk_overview.html>`_

Building the edge AI gallery
----------------------------

The edge AI gallery application is enabled by default in yocto for |__PART_FAMILY_DEVICE_NAMES__| Linux and RT-Linux.

The source code is available at `edgeai-gui-app <https://git.ti.com/cgit/apps/edgeai-gui-app>`__ and can be recompiled with the following steps

1. To setup the environment, from the root of the SDK installation directory, source `environment-setup` script.
   ::

        $ source linux-devkit/environment-setup

2. Go to the root of edgeai-gui-app repository and run the following command to build the application.
   ::

        $ qmake; make

3. Copy the compiled binary to /usr/bin directory of the device
   ::

        $ scp edgeai-gui-app root@<ip-addr-of-device>:/usr/bin/


