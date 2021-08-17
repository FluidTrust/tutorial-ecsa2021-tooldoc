Confidentiality Analysis Execution
==================================

.. _fig_run_config_button:
.. figure:: _images/run-config-button.png
   :align: right
   :width: 100 %
   :figwidth: 33 %
   :alt: Toolbar with context menu to create run configurations

   Run configuration toolbar

To execute a confidentiality analysis, you have to :doc:`define it <confidentiality-query-definition>` first. After that, you can create a run configuration, through which you can execute the analysis.

To create a run configuration, you have to select the context menu of the green play button in the upper toolbar and choose :guilabel:`Run Configurations...` as shown in :numref:`fig_run_config_button`.

.. rst-class::  clear-both

.. _fig_run_config_create:
.. figure:: _images/run-config-create.png
   :align: right
   :width: 100 %
   :figwidth: 33 %
   :alt: Context menu in the run configuration dialog to create a new configuration

   Run configuration dialog

In the upcoming dialog shown in :numref:`fig_run_config_create`, look for the :guilabel:`PCM Confidentiality (DSL)` entry and select :guilabel:`New Configuration` to create a blank run configuration.

.. rst-class::  clear-both

.. _fig_run_config_dsl:
.. figure:: _images/run-config-dsl.png
   :align: right
   :width: 100 %
   :figwidth: 33 %
   :alt: Wizard for creating the run configuration that requires a usage model, allocation model, the query and a result file to be selected.

   Run configuration wizard

In the following wizard, you have to select a usage model, an allocation model, the created query and a result file. The former three files have to exist already, so you can select them via the :guilabel:`...` button next to the corresponding text fields. The result file does not exist yet, so you can only select the containing project via the :guilabel:`...` button and have to enter the file name manually. It is beneficial to have a filename ending with :file:`.txt` but this is not mandatory.

After you provided all information, you can press :guilabel:`Run` to execute the run configuration. The dialog will close and the run configuration will be saved. If you want to reexecute it later, you can just select the run configuration in the dialog and press :guilabel:`Run` again.

After the execution of the analysis, the result file will be created and can be inspected.