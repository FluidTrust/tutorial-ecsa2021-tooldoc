Confidentiality Query Definition
================================

Confidentiality analyses are specified by queries. A query defines data flow patterns in the system that shall not occur. Detecting such a pattern means detecting a violation.

Creation of Confidentiality Query
---------------------------------

.. _fig_ui_toolbar_palladio2:
.. figure:: ../modeling/_images/palladio-toolbar.png
   :align: right
   :width: 100 %
   :figwidth: 33 %
   :alt: Toolbar containing actions to create Palladio models

   Palladio toolbar

In order to create a query, you can use the Palladio toolbar located in the top of the tooling window that is shown in :numref:`fig_ui_toolbar_palladio2`. To create a query, press the button containing the magnifying glass next to the data dictionary button.

.. _fig_querydsl_createwizard_0:
.. figure:: _images/querydsl-createwizard-0.png
   :align: right
   :width: 100 %
   :figwidth: 33 %
   :alt: Dialog for creating a query definition that asks to put in a file name ending with ".DCPDSL"

   Dialog page asking for a file name for query definition

.. _fig_querydsl_createwizard_1:
.. figure:: _images/querydsl-createwizard-1.png
   :align: right
   :width: 100 %
   :figwidth: 33 %
   :alt: Dialog for creating a query definition that asks for a data dictionary

   Dialog page for selecting a dictionary

In the upcoming dialog shown in :numref:`fig_querydsl_createwizard_0`, you have to select the project, into which you would like to put the query definition. The file name of the definition can be chosen freely but has to end with :file:`.DCPDSL`. A validation message in the top of the dialog reports if the file name is valid.

After pressing :guilabel:`Next`, the dialog asks for a data dictionary as shown in :numref:`fig_querydsl_createwizard_1`. You have to select the same dictionary that you used while specifying characteristics for :doc:`transmitted variables </modeling/confidentiality-variableusages>`, :ref:`usage scenarios <modeling/sirius-usage:Specification of Characteristics for Usage Scenarios>` or :ref:`resource containers <modeling/sirius-resource:Specification of Characteristics for Resource Containers>`. After pressing :guilabel:`Finish`, the query file will be created and an editor will be opened.

.. rst-class::  clear-both

Syntax of Query Definition
--------------------------

We only cover a small excerpt of the full syntax. For more detailed explanations, please refer to the corresponding publications :cite:p:`b-DBLP:conf/icsa/HahnerSHWBH21` :cite:p:`b-hahner2020a`.

Every query definition starts with an import of the data dictionary that has been used in specifying the software architecture. You can use relative or platform URIs to replace the ``<PATH>`` placeholder in the excerpt below. The line below gives an example on how to refer to :file:`dataDictionary.pddc` 

.. code-block:: php

   import <PATH>
   import dataDictionary.pddc

After the import, you have to specify the elements of the data dictionary that you would like to use. You do this by type statements. In a type statement, you define a name, through which you can refer to the characteristic type from the dictionary. In the following, the general syntax to introduce a ``<NAME>`` for a particular characteristic type ``<CT_NAME>`` is shown. Afterwards, an example for renaming the characteristic type ``BackgroundColor`` to ``BGColor`` is shown.

.. code-block:: php

   type <NAME>:<CT_NAME>
   type BGColor:BackgroundColor

A query is built automatically from a formulated constraint. A constraint describes a situation that shall not happen. A constraint always has a name ``<NAME>``, a data selector ``<DATA_SELECOTOR>``, a node selector ``<NODE_SELECTOR>`` and an optional condition ``<CONDITION>`` introduced by the ``WHERE`` keyword. The general idea is to look for data, which meets the criteria of the data selector, that arrives at a node, which meets the criteria of the node selector, and report on that combination. The general syntax of a constraint is shown below.

.. code-block:: php

   constraint <NAME> {
       <DATA_SELECTOR> NEVER FLOWS <NODE_SELECTOR> WHERE <CONDITION>
   }

Data Selector
^^^^^^^^^^^^^
A data selector consists of one or multiple selection criteria based on the particular characteristics of transmitted data. The characteristics of data are derived from the characteristics specified in variable usages. If multiple criteria are given, the conjunction of all criteria has to apply. The excerpt shown below consisting of three selection criteria could be used as data selector. In all criteria a previously defined type ``TYPE_NAME`` is used. In the first line, we state that the data has to have the value ``VALUE`` of the given type applied. The following line states that the data must not have the value ``VALUE`` be applied. The third line introduces a variable ``VAR`` that represents all values that are applied to the data that match the specified type. This variable can be used in :ref:`conditions <analysis/confidentiality-query-definition:Condition>` later to test more powerfull criteria.

.. code-block:: php
   :linenos:
   
   data.attribute.<TYPE_NAME>.<VALUE> &
   data.attribute.<TYPE_NAME>.!<VALUE> &
   data.attribute.<TYPE_NAME>.$<VAR>{}

Node Selector
^^^^^^^^^^^^^
A node selector consists of one or multiple selection criteria based on the particular characteristics of a node. The characteristics of nodes are derived from the characteristics specified for usage scenarios or resource containers. In context of Palladio, a node is always a component. Components can be selected by characteristics using the same criteria as for data. It as possible to define multiple criteria, which all have to apply in order to get the component selected. The following excerpt visualizes the selection by a particular value (line 1) or by not having a particular value (line 2), as well as the definition of a variable that captures all values for a given type (line 3).

.. code-block:: php
   :linenos:
   
   component.property.<TYPE_NAME>.<VALUE> &
   component.property.<TYPE_NAME>.!<VALUE> &
   component.property.<TYPE_NAME>.$<VAR>{}

Condition
^^^^^^^^^
The condition always yields a truth value after its evaluation against a given software architecture. If the condition evaluated to true, the constraint matched, which means that a violation has been detected.

A condition consists of the operations shown in :numref:`list_condition_booloperations` that yield truth values and that can be connected via disjunction (``|``) or conjunction (``&``). They can also be negated (``!``). A characteristic is always given as a variable name as illustrated in the examples. A set can be given as variable or as one of the set operations shown in :numref:`list_condition_setoperations`.

.. _list_condition_booloperations:
.. list-table:: Boolean operations available to be used in conditions
   :header-rows: 1

   * - Operation
     - Arguments
     - Result Type
     - Example
   * - Equality
     - Characteristic, Characteristic
     - Boolean
     - ``FG_COLOR == BG_COLOR``
   * - Inequality
     - Characteristic, Characteristic
     - Boolean
     - ``FG_COLOR !== BG_COLOR``
   * - Member Check
     - Characteristic, Set
     - Boolean
     - ``elementOf(COLOR, COLORS)``
   * - Empty Check
     - Set
     - Boolean
     - ``isEmpty(COLORS)``

.. _list_condition_setoperations:
.. list-table:: Set operations available to be used in conditions
   :header-rows: 1

   * - Operation
     - Arguments
     - Result Type
     - Example
   * - Intersection
     - Set, Set
     - Set
     - ``intersection(FG_COLORS, BG_COLORS)``
   * - Union
     - Set, Set
     - Set
     - ``union(FG_COLORS, BG_COLORS)``
   * - Subtract
     - Set, Set
     - Set
     - ``subtract(FG_COLORS, BG_COLORS)``
   * - Set Creation
     - Characteristic
     - Set
     - ``{FG_COLOR}``


References
----------

.. bibliography::
   :keyprefix: b-

   DBLP:conf/icsa/HahnerSHWBH21
   hahner2020a