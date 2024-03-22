Data Collection
=======================

This page describes the data collection procedure for all the modules. We used 
`DJI Mavic Mini <https://www.dji.com/mavic-mini>`_ for conducting the research experiments. The specifications 
of the UAV can be found at the `official website <https://www.dji.com/mavic-mini/specs>`_ . 


Distance Between Adjacent Buildings
-------------------------------------

For estimating the distance between adjacent structures, the images are collected in 3 different modes: Frontal Mode, In-Between Mode and Roof Mode.

.. list-table::
    
    * - .. _frontalmode:
        .. figure:: images/frontalviewdronepov.jpg
            :align: center

            Frontal Mode

        
      - .. _inbetweenmode:
        .. figure:: images/inbetweenviewdronepov.jpg
            :align: center

            In-Between Mode

      - .. _roofmode:
        .. figure:: images/rooftopdronepov.jpg
            :align: center

            Roof Mode




Frontal Mode
^^^^^^^^^^^^
:numref:`frontalmode` Shows the frontal face of two adjacent buildings for which data was collected. In this mode, we focused on 
estimating the distance between the two buildings by analyzing only their frontal faces while flying a UAV with a 
forward-facing camera. This view is particularly helpful when there are impediments between the subject buildings 
and flying a UAV between them is challenging.

.. raw:: html

    <p align = "center"> <iframe width="560" height="315" src="https://drive.google.com/file/d/1Rda3Xyh59lFqYp1AHLMu9nxtGgesTs74/preview" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen name="Data Collection for Roof Mode and In-Between Mode"></iframe> </p> 
    <p align = "center"> The video describes the workflow of data collection for Frontal Mode. The UAV was operated with a forward facing camera. </p>

 
In-Between Mode
^^^^^^^^^^^^^^^

:numref:`inbetweenmode` Shows that the UAV's point-of-view for the In-between Mode. The UAV is navigated in between the subject 
buildings along a path parallel to the facade with a forward-facing camera. This mode enables the operators to 
calculate distances when the subject buildings have irregular shapes. 

.. raw:: html

    <p align = "center"> <iframe width="560" height="315" src="https://drive.google.com/file/d/1xueFiKkA2lTOOzO1BYzTopE_LNFC6RUI/preview" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen name="Data Collection for Roof Mode and In-Between Mode"></iframe> </p> 
    <p align = "center"> The video describes the workflow of data collection for In-Between Mode. </p>

Roof Mode
^^^^^^^^^

:numref:`roofmode` Shows the UAV's point-of-view for the Roof Mode. The UAV was navigated at a fixed altitude with a 
downward-facing camera so as to capture the rooftops of the subject buildings. The roof mode helps in tackling 
occlusions due to vegetation and other physical structures.



.. raw:: html

    <p align = "center"> <iframe width="560" height="315" src="https://drive.google.com/file/d/1xueFiKkA2lTOOzO1BYzTopE_LNFC6RUI/preview" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen name="Data Collection for Roof Mode and In-Between Mode"></iframe> </p> 
    <p align = "center"> The video describes the workflow of data collection for Roof Mode. </p>



Plan Shape and Roof Area Estimation
-------------------------------------
For estimating the plan shape and roof area, the UAV was flown with a downward-facing camera over the roof at 
constant height. Our algorithm accounts for both orthoginal and non-orthogonal views of the roof.

.. _intermediateresults:
.. figure:: images/planshape.jpg
    :align: center
    :height: 315
    :width: 560
    :figclass: w
    :alt: intermediateresults

    Data Collection for Plan Shape and Roof Area Estimation

Roof Layout Estimation
-------------------------------------
For estimating the roof layout, the UAV was flown with a downward-facing camera over the roof at constant height.

.. raw:: html
    
    <p align = "center"><iframe src="https://drive.google.com/file/d/1Gu5oBJhCOV7ZOCrYVbju0ubeuobGXeur/preview" width="560" height="315" allow="autoplay"></iframe></p>
    <p align = "center"> Data Collection for Roof Layout Estimation </p>