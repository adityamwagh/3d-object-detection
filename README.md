# Fast 3D Object Detection in the Wild

## Setup environment


## Download Dataset & Weights
Download the data folder and the weights folder from the link mentioned below - </br>

- Dataset - Kitti.zip </br>
- weights - checkpoints </br>

[Dataset and Weights](https://drive.google.com/drive/folders/1Msf2P5aSV1Xha-DPwiJ9K24v5gAdqxpG)

- Create a directory named data inside the cloned repository and copy the dataset. Your directory strucutre should look as mentioned below - </br>
```plain

└── data
    ├── Kitti
       ├── training    
       |   ├── image_2 
       |   ├── calib
       |   ├── label_2
       |   ├── velodyne
       |   └── velodyne_reduced <-- empty directory
       └── testing     
           ├── image_2
           ├── calib
           ├── velodyne
           └── velodyne_reduced <-- empty directory
       ├── kitti_dbinfos_train.pkl
       ├── kitti_infos_test.pkl
       ├── kitti_infos_train.pkl
       ├── kitti_infos_trainval.pkl
       ├── kitti_infos_val.pkl
       ├── Imagesets
       ├── gt_database
       
```
- Create a new directory named checkpoints and copy the weights(.pth files) inside the checkpoints folder.

## Evaluation
```shell
    python tools/test.py configs/pointpillars/hv_pointpillars_secfpn_6x8_160e_kitti-3d-car.py checkpoints/epoch_2.pth --show --show-dir ./data/kitti/show_results
```
