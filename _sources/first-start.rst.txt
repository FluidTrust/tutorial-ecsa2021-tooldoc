===========
First Start
===========

You can launch the tooling by running the :file:`PalladioBench` executable (Windows/Linux) or by running the :file:`Eclipse.app` (MacOSX). After a short splash screen, the user interface will be shown. The most important view is the Model Explorer.

.. _fig_modelexplorer:
.. figure:: _static/modelexplorer.png
   :scale: 50 %
   :align: right
   :alt: Screenshot of the Model Explorer view within the Palladio tooling.

   Model Explorer

The Model Explorer shown in :numref:`fig_modelexplorer` visualizes all available projects. There will be multiple projects that contain various states of the running example system. You can view the content of the projects by expanding them via the triangle on the left side of the project icon. In :numref:`fig_modelexplorer`, this has been done for the first project.

A project consists of

* system description models that can be edited using various :doc:`graphical editors <modeling/index>`
* models holding :doc:`confidentiality primitives <modeling/xtext-datadictionary>` and :doc:`analyses <analysis/confidentiality-query-definition>`
* launch configurations that ca be edited and used using the :doc:`run configuration dialogues <analysis/confidentiality-analysis-execution>`

Depending on your further interests, you can continue reading the :doc:`foundations <foundations/index>` or learn more about :doc:`modeling <modeling/index>` and :doc:`analyzing <analysis/index>` confidentiality using Palladio.