Installation
===================================

**SetUp of the Codebase** 
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

**Installing Conda**

We are providing a conda env yaml file for easy installation of all the dependencies. Therefore, `Miniconda installation <https://docs.conda.io/en/latest/miniconda.html>`_ is recommended for using the UVRSABI package.

**Installing Colmap**

Another dependency for the package is colmap which needs to be installed as follows for the 3D reconstruction : `Colmap Installation <https://colmap.github.io/install.html>`_

**Installing the codebase for all the modules :** 

Clone the `Github repository <https://github.com/charvi-077/civil-structure-inspection>`_ by running the following commands:

..  code-block:: bash 

	$ git clone https://github.com/charvi-077/civil-structure-inspection

Once all the above dependencies have been installed, create a conda environment by running the following commands:

..  code-block:: bash

	$ cd civil-structure-inspection
	$ conda env create -f civil_code.yaml
	$ conda activate civil_code


**Running the Modules:**
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Note : All the detailed instructions are given inside README.md of every module on the above github link. 

**Distance Between Adjacent Buildings** 

1. First we have to 3D reconstruct the scene from the data collected in 3 different modes using "Colmap tool"
2. Run the below command to get sampled images from Video (from Uvrsabi directory)

..  code-block:: bash

	$ python3 ./utils/VideoToImage.py

3. Follow the Colmap tutorial page to 3D resconstruct the scene from respective mode.
4. With respect to the mode, run the below command
   
..  code-block:: bash

	$ cd DistanceModuleFrontalMode
	$ python3 FrontalMode.py
	or 
	$ cd DistanceModuleBetweenMode
	$ pytho3 InBetweenMode.py
	or 
	$ cd DistanceModuleRoofMode
	$ python3 TopViewFinal.py

**Roof Occupancy Estimation**  

1. Sample the images from video using above script
2. Traverse to code directory and run LEDNET Model on input images to get the roof masks 
   
..  code-block:: bash 

	$ cd RoofLayoutestimation/utils/LEDNet/test
	$ python test.py --datadir <path to input image directory > --resultdir < path to output directory >

3. Next is getting the object masks using Detic model
   
..  code-block:: bash 

	$ cd Detic
	$ python demo.py --config-file detic/configs/Detic_LCOCOI21k_CLIP_SwinB_896b32_4x_ft4x_max-size.yaml --input ../images/*.jpg --output ../ObjectMasks --vocabulary custom --custom_vocabulary solar_array,air_conditioner,vent,box,sink --confidence-threshold 0.5 --opts MODEL.WEIGHTS Detic_LCOCOI21k_CLIP_SwinB_896b32_4x_ft4x_max-size.pth


1. Next, to do stitiching of input images and masks
   
..  code-block:: bash 

	$ python stitch.py -i images -o ObjectMasks -r RoofMasks -s $results_path/stitching_results

2. Estimating the roof occupancy
   
..  code-block:: bash  

   $ python calculateoccupancy.py -r ../RoofLayoutEstimationResults/stitching_results/stitched_roof_mask.jpg -o ../RoofLayoutEstimationResults/stitching_results/stitched_object_mask.jpg -t ../RoofLayoutEstimationResults/final_results/final_results_roof_layout_estimation.txt

**Roof Area Estimation**

1. Follow the same steps as in Roof Occupancy Estimation to get the roof masks from LEDNet Model 
2. Estimate the Roof Area 
   
..  code-block:: bash 

	$ cd RoofAreaCalculation
	$ python find_area.py --roofmasks RoofMasks --log_file $2 --save_dir_intermediate $results_path/intermediate_results --save_dir_final $results_path/final_results 

**Window Detection and Storey Count Estimation** 

1. Traverse to the wind_det_heatmaps and also download the weights of the model provided link in codebase Readme
2. Run the inference script 
   
..  code-block:: bash 

	$ python infer.py --cfg /path/to/yaml/config \
                --model /path/to/model \
                --infer /path/to/image/directory

3. This generates 2 dirs: infer_result and post_process_result and need to prepare respective log file as provided in codebase
4. Configure the parameters in below file and to run using below command to perform NMS and get the storey count from the 
   images folder  
   
..  code-block:: bash 

	$ cd mapToVerticalPlane 
	$ python main.py

**Crack Detection**

1. Using above script get the sampled images from the video
2. Model weights are provided in the codebase
3. Here for evaluation metrics we are labeling the data using v7 lab annotation tool and saving the images with 
   same name as input image in label folder ( sample data folder is provided in the code )
4. Configure the data paths in the script and run the script using command as below 
   
..  code-block:: bash 

	$ python3 test_target_label.py ( if labels are available )
	or 
	$ python3 test_target.py ( if no labels are available, instead only input images )
   
.. We also require pre-trained weights to segment rooftops, detect objects. These can be downloaded by running the following command:
    
.. ..  code-block:: bash

.. 	$ cd UVRSABI-Code/
.. 	$ ./weights.sh

**Building Tilt Estimation**

**Approach 1 : Sensor Based Slope Estimation**

1. We are using 2d Lidar and RTK GPS for getting the slope data for setup. 

Instructions to run the code : 
1. Clone and build the px4 and rplidar ros packages from source

..  code-block:: bash 

	$ roscore
	$ roslaunch mavros px4.launch (buid )
	$ roslaunch rplidar_ros rplidar_a2m12.launch
	$ cd main_code/slope_estimation/scripts/
	$ python3 slope_estimation.py


2. Set the rosparam to record the specific reading at the slope

..  code-block:: bash  

	$ rosparam set /reading_trigger true


**Approach 2 :  Base Slope Estimation**

Instructions to run the code : 
1. Run the script 

..  code-block:: bash  

	$ python3 fit_plane.py

**Approach 3 : Clustering-Based Plane Segmentation Neural Network for Urban Scene Modeling**

Requirements
   * Python 3.8
   * Pytorch 1.7.1
   * scikit-learn 0.24.2
   * Open3d 0.13.0

**Dataset**

We used Virtual KITTI Dataset from <a href="https://github.com/VisualComputingInstitute/vkitti3D-dataset" target="_blank">here</a>. 

We used voxel downsampling to filter the dataset and extract man-made structures such as roads and buildings.

Sample datasets are stored in the dataset folder

**Installation** 

..  code-block:: bash 

	$ git clone https://github.com/jimmy9704/plane-segmentation-network.git
	$ cd plane-segmentation-network/


**Training**
	Run the following command to start training

..  code-block:: bash 

	$ python train.py 

Description of options

..  code-block:: bash 

	$ train(pointnet, dataset,train_loss, epochs=100,make_label=False, save=True)
	$ make_labels(dataset,max_k=15,iteration=10)

You can create a label for training PointNet by setting the ```make_label``` option to 'True'.

You can change ```max_k``` and ```iteration```.

```max_k``` is the maximum number that PointNet will estimate

```iteration``` is the number of Hybrid-Kmeans iterations

```iteration``` can be reduced to reduce time consumption but it might cause unstable results.

**Test**
Run the following command to start test

..  code-block:: bash 

	$ python test.py

Description of options

..  code-block:: bash 

	$ valid(pointnet, dataset, save_num=99,iteration=5)

```save_num``` is the check point to load for PointNet.


Pre-trained checkpoints can be loaded by setting 'save_num' to 99.


**Installation of GUI (Under Development)** 
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The GUI can be launched by running the following command:

..  code-block:: bash

	$ cd UVRSABI-Code/
	$ python gui.py


The :doc:`instructions` page can be referred to for more details on how to use the GUI.

.. Follow the instructions mentioned on the `official website <https://docs.docker.com/get-docker>`_ 
.. to install Docker on your system. The installation can be verified by running the following commands in the terminal
 (Linux Systems and macOS) or in the command line (Windows)::
    
    docker --version
    docker-compose --version

.. For getting hands-on-experience with Docker, you can refer to some `basic tutorials .. <https://www.freecodecamp.org/news/the-docker-handbook/>`_.