Usage of Usage Model Editor
===========================

The usage model editor allows specifying the interaction of users with the system. In order to do that, it is necessary to have a system specified via the :doc:`assembly editor <sirius-assembly>`.

.. _fig_sirius_usagemodel_overview:
.. figure:: _images/sirius-usagemodel.svg
   :align: right
   :width: 100 %
   :figwidth: 33 %
   :alt: Usage model describing the interaction of a flight planner with the system by doing one call to the system.

   Simple usage model diagram

Contents of Editor
------------------


The editor contains multiple usage scenarios. A usage scenario describes the interaction of a certain type of users with the system. The scenario contains a behavior description. The description consists of a sequence of activies. The most important activities are calls to the system.

.. rst-class::  clear-both

Specification of Characteristics for Usage Scenarios
----------------------------------------------------

Usage scenarios can have characteristics assigned. To assign characteristics, a :doc:`data dictionary <xtext-datadictionary>` has to exist and contain characteristic types. This is essentially because the characteristics are typed by the characteristic types in the data dictionary.

.. _fig_sirius_tool_enumcharacteristic2:
.. figure:: _images/sirius-tool-enumcharacteristic.png
   :align: right
   :width: 100 %
   :figwidth: 20 %
   :alt: Tool located in palette to create a characteristic

   Tool for creating a characteristic

.. _fig_sirius_tool_enumcharacteristic_dialog2:
.. figure:: _images/sirius-tool-enumcharacteristic-dialog.png
   :align: right
   :width: 100 %
   :figwidth: 33 %
   :alt: Dialog asking to select a characteristic type

   Selection dialog for characteristic type

In order to create a characteristic, you have to select the corresponding tool shown in :numref:`fig_sirius_tool_enumcharacteristic` and click into a usage scenario. This will open the dialog shown in :numref:`fig_sirius_tool_enumcharacteristic_dialog` that asks for a characteristic type. Select the characteristic type, for which you would like to select values later. After you selected a type, press :guilabel:`OK`.

.. _fig_sirius_usagemodel_enumcharacteristic:
.. figure:: _images/sirius-usagemodel-enumcharacteristic.png
   :align: right
   :width: 100 %
   :figwidth: 33 %
   :alt: Properties view that allows to select values for a characteristic via the semantic tab

   Value selection for characteristics

A green rectangle will be added to the resource container as shown in :numref:`fig_sirius_usagemodel_enumcharacteristic`. Initially, there are no values selected. You can change this by using the semantic tab of the properties view. Click into the cell in the :guilabel:`Value` column next to the :guilabel:`Values` property and press the :guilabel:`...` button. In the opened dialog, you can select the values to be applied by double-clicking on them or selecting them and pressing :guilabel:`Add`. You can remove them again by double-clicking them or using the :guilabel:`Remove` button. After closing the dialog by pressing :guilabel:`OK`, the new values are visualized in the green rectangle.

Specification of Entry Level System Calls
-----------------------------------------

Entry level system calls make calls to system services. The effect of a call on quality properties is specified by so called :dfn:`variable usages`. A variable usage describes how a variable, which can essentially be a parameter or return value, is characterized. The variable is defined by a name shown in the top of the grey rectangles that visualize variable usages. The definition of characteristics shown below the name can refer to other characteristics, which enables the propagation of characteristics through the system.

Call actions allow to specify two types of variable usages: usages for parameters of the called service (i.e. characterizations of the sent parameters) and usages for the return value of the called service (i.e. characterizations of the received return value). To specify characteristics for a parameter, the variable usages has to have the very same name as the parameter in the signature of the called service. To specify characteristics of the return value, a variable usage with any name can be defined. However, when referring to the characteristics of the particular return value from the called service, the keyword ``RETURN`` has to be used.

We explain how to create variable usages for analyzing confidentiality on a :doc:`separate page <confidentiality-variableusages>`.