Data Collection
==================

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
    
    <p align = "center"><iframe src="https://drive.google.com/file/d/1fxskLs4S_HThzdnOvRX_PgcrjrbKYM08/preview" width="560" height="315" allow="autoplay"></iframe></p>
    <p align = "center"> The video describes the workflow of data collection for Frontal Mode </p>

 
In-Between Mode
^^^^^^^^^^^^^^^

:numref:`inbetweenmode` Shows that the UAV's point-of-view for the In-between Mode. The UAV is navigated in between the subject 
buildings along a path parallel to the facade with a forward-facing camera. This mode enables the operators to 
calculate distances when the subject buildings have irregular shapes. 

.. raw:: html

    <p align = "center"> <iframe width="560" height="315" src="https://drive.google.com/file/d/1rx2SoTVmqqgvL1F9eZ6DJnVPkksj18bI/preview" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen name="Data Collection for Roof Mode and In-Between Mode"></iframe> </p> 
    <p align = "center"> The video describes the workflow of data collection for In-Between Mode </p>

Roof Mode
^^^^^^^^^

:numref:`roofmode` Shows the UAV's point-of-view for the Roof Mode. The UAV was navigated at a fixed altitude with a 
downward-facing camera so as to capture the rooftops of the subject buildings. The roof mode helps in tackling 
occlusions due to vegetation and other physical structures.

.. raw:: html

    <p align = "center"> <iframe width="560" height="315" src="https://drive.google.com/file/d/1iStwFSqVPI3HL2zJSfXSUPZ85bipBKhS/preview" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen name="Data Collection for Roof Mode and In-Between Mode"></iframe> </p> 
    <p align = "center"> The video describes the workflow of data collection for Roof Mode </p>


Plan Shape and Roof Area Estimation
-------------------------------------
For estimating the plan shape and roof area, the UAV was flown with a downward-facing camera over the roof at 
constant height. Our algorithm accounts for both orthoginal and non-orthogonal views of the roof.

.. _intermediateresults_all:
.. figure:: images/planshape.jpg
    :align: center
    :height: 315
    :width: 560
    :figclass: w
    :alt: intermediateresults

    Data Collection for Plan Shape and Roof Area Estimation

Roof Layout Estimation
-------------------------
For estimating the roof layout, the UAV was flown with a downward-facing camera over the roof at constant height.

.. raw:: html
    
    <p align = "center"><iframe src="https://drive.google.com/file/d/1scB-GjORxmCNVjrZGO-3S4wUrEoGrgg9/preview" width="560" height="315" allow="autoplay"></iframe></p>
    <p align = "center"> Data Collection for Roof Layout Estimation </p>


Crack Detection 
------------------
For crack detection the UAV was flown with the forward facing camera near to cracks of the buildings. Our 
stack is able to segment the cracks from the images including shadows, occulsions or different viewpoints.

.. raw :: html

   <p align = "center"><iframe src="https://drive.google.com/file/d/1u6QjUOTofAWEYOb6pfb-dRxHGIUJuuDG/preview" width="560" height="315" allow="autoplay"></iframe></p>
   <p align = "center"> Data Collection for Crack Detection in buildings </p>

Window Detection and Storey Height Estimation  
------------------------------------------------
For window detection and Storey Height Estimation the UAV was flown from ground floor to the top floor of the buildings.
Depending upon the distance between building, we could fly the drone away from building to get large fov to cover two window_result1 
in single frame. 

.. raw :: html

   <p align = "center"><iframe src="https://drive.google.com/file/d/1ZAD9vMlQg0jFs3LdQxzdz09LvD03KkWY/preview" width="560" height="315" allow="autoplay"></iframe></p>
   <p align = "center"> Data Collection for Window Detection and Storey Height Estimation </p>

.. Building Tilt Estimation 
.. ---------------------------
.. For Building Tilt Estimation we are calculating the tilt in the buildings 





