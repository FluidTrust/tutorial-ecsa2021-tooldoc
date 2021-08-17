Usage of Repository Editor
==========================

The repository editor allows to specify the building blocks for creating a system.

Contents of Editor
------------------

The editor consists of components, interfaces and data types, as well as of edges between these elements.

.. _fig_sirius_repository_componentroles:
.. figure:: _images/sirius-repository-component-roles.png
   :align: right
   :width: 100 %
   :figwidth: 33 %
   :alt: Component having one provided role and one required role shown by edges to interfaces.

   Roles of component

A component always has at least one edge to an interface that describes the provided services, a so-called :dfn:`provided role`. As shown in :numref:`fig_sirius_repository_componentroles`, this is shown by an accordingly labeled edge. A component can have edges to interfaces that describe required services, a so-called :dfn:`required role`. This is also shown by an accordingly labeled edge.

Within the components, there are :abbr:`SEFFs (Service Effect Specifications)` for every provided service, i.e. every signature of an interface that has been referenced as provided role.

.. rst-class::  clear-both

Opening the SEFF Editor
-----------------------

In order to open the graphical editor describing the :abbr:`SEFF (Service Effect Specification)` of the component, you can do any of the following:

* double-click on the corresponding entry
* right-click on the entry and select :guilabel:`Open` and the shown diagram entry afterwards

Please see the description of the :doc:`SEFF editor <sirius-seff>` for details on that particular editor.