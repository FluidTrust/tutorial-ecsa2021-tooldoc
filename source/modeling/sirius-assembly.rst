Usage of Assembly Editor
========================

The assembly editor allows to assemble multiple building blocks from the :doc:`repository <sirius-repository>` to new building blocks or systems. Consequently, the editor can produce composite components as well as systems.

Contents of Editor
------------------

.. _fig_sirius_assembly:
.. figure:: _images/sirius-assembly.svg
   :align: right
   :width: 100 %
   :figwidth: 33 %
   :alt: Assembly diagram showing a system providing two interfaces and consisting of two component instances.

   Simple assembly diagram

The editor consists of a composed structure, i.e. a composite component or a system, the provided and required roles of the composed structure, as well as connected assemblies, i.e. instances, of existing building blocks from the repository.

Every provided and required role of the composed structure has to be connected to an assembly. The same holds for all required roles of the contained assemblies.