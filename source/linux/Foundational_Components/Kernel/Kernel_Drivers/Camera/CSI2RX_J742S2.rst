.. include:: _CSI2RX_common.rst

***********************
Enabling camera sensors
***********************

J742S2 has three instances of CSI2RX capture subsystem and can support upto
twelve **IMX390** cameras using FPDLink fusion EVM. J742S2-EVM also supports
**OV5640** module connected to MIPI connector.

Applying sensor overlays
========================

To enable FPDLink cameras you will need to apply the device tree overlays
for both the fusion board and the sensor at U-boot prompt:

.. code-block:: text

   # For single RCM IMX390 connected to RX port 0 on Fusion board EVM on J742S2 EVM:
   # FPDLink IMX390 camera overlays are named according to the port connected in the following
   # format : ti/k3-fpdlink-imx390-rcm-<csi_port>-<fusion_rx_port>.dtbo
   => setenv name_overlays ti/k3-j721s2-evm-fusion.dtbo ti/k3-fpdlink-imx390-rcm-0-0.dtbo
   => boot

   # For single RCM IMX390 connected to port 0 on FPDLink IV Fusion 2 board on J742S2 EVM:
   => setenv name_overlays ti/k3-j784s4-evm-fpdlink-iv-fusion.dtbo ti/k3-fpdlink-imx390-rcm-0-0.dtbo
   => boot

   # For single RCM IMX390 connected to RX port 0 on DS90UB954-Q1 EVM on J742S2 EVM:
   => setenv name_overlays ti/k3-j721s2-evm-ub954.dtbo ti/k3-fpdlink-imx390-rcm-0-0.dtbo
   => boot

For more details on building or applying overlays permanently, refer to the
:ref:`How to enable DT overlays in linux <howto_dt_overlays>` guide.

CSI2RX testing details
======================

The following combinations of sensors are tested in the latest sdk.

+--------------+---------------------------------------+-----------------------------------+
| Hardware     | Sensor                                | Default format and resolution     |
+==============+=======================================+===================================+
| J742S2       | FPDLink fusion 1 EVM, IMX390          | SRGGB12_1X12/1936x1100 at 30 fps  |
+--------------+---------------------------------------+-----------------------------------+
