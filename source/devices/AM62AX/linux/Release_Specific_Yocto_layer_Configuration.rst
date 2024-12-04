.. _yocto-layer-configuration:

**************************
Yocto Layer Configuration
**************************

.. http://processors.wiki.ti.com/index.php/Processor_SDK_Building_The_SDK#Layer_Configuration

Processor SDK uses the following oe-layersetup configs to configure the
meta layers. These are the <config> used in the command:

``$ ./oe-layertool-setup.sh -f <config>``

The following config files are located in the **configs/processor-sdk-analytics**
directory of the `oe-layersetup git repo <https://git.ti.com/cgit/arago-project/oe-layersetup/>`_.

+--------------------------------------------------+---------------------------------------------+------------------------------------------------------+
| Config File                                      | Description                                 | Supported machines/platforms                         |
+==================================================+=============================================+======================================================+
| processor-sdk-analytics-10.01.00-config.txt      | Processor SDK Analytics 10.01.00 Release    | am62axx-evm                                          |
+--------------------------------------------------+---------------------------------------------+------------------------------------------------------+

