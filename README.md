# Fast 3D Object Detection in the Wild

## Setup environment

Make sure you have CUDA version 11.3 installed locally and in the virtual environment. Also make sure you are using `python 3.8`, or else there would be dependency issues.

```
conda create -n fast3d python=3.8 pytorch cudatoolkit=11.3 torchvision -c pytorch -y
conda activate fast3d
pip3 install openmim
mim install mmcv-full
mim install mmdet
mim install mmsegmentation
git clone https://github.com/open-mmlab/mmdetection3d.git
cd mmdetection3d
pip3 install -e .
```

If there are issues with installation, downgrade the necessary packages. For example, the `click` package might throw a version issue, because it's a dependency for `black` (a python code formatter).

Remove the mmdetection3d folder (optional)

```
rm -rf mmdetection3d
```
## Clone the Project Repository

Once the package installation is succesful, clone the project repository.
```
git clone https://github.com/adityamwagh/fast3d.git
cd fast3d
```

## Download Dataset & Weights
Download the data folder and the weights folder (Must use an NYU Affiliated Email): [Dataset and Weights](https://drive.google.com/drive/folders/1Msf2P5aSV1Xha-DPwiJ9K24v5gAdqxpG). The dataset has been proprocessed to generate the required file format.

### Dataset
- Make a folder named `data` in the root of `fast3d`.
- Unzip the `kitti.zip` folder into `data`. The folder structure should look like this:

```

└── data
    ├── kitti
       ├── training    
       |   ├── image_2 
       |   ├── calib
       |   ├── label_2
       |   ├── velodyne
       |   └── velodyne_reduced
       └── testing     
           ├── image_2
           ├── calib
           ├── velodyne
           └── velodyne_reduced
       ├── kitti_dbinfos_train.pkl
       ├── kitti_infos_test.pkl
       ├── kitti_infos_train.pkl
       ├── kitti_infos_trainval.pkl
       ├── kitti_infos_val.pkl
       ├── gt_database
       
```
### Weights
- Download the checkpoints folder from Google Drive.
- Unzip checkpoints.zip
- Copy the `checkpoints` folder into the root of `fast3d` folder.

## Evaluation

Run the `test.py` script in the `tools` folder in `fast3d`.

```bash
python tools/test.py \ 
configs/pointpillars/hv_pointpillars_secfpn_6x8_160e_kitti-3d-car.py \
checkpoints/epoch_2.pth \
--show --show-dir ./data/kitti/show_results
```
