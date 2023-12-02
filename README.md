# Human Pose Estimation and Analysis for Neuro Rehabilitation

Tech demo for rehabilitation education, instruction, and assessment via real-time 3D pose estimation in low resource environments. This repository contains 3D multi-person pose estimation demo in PyTorch. Pose estimation code uses [Lightweight OpenPose](https://arxiv.org/pdf/1811.12004.pdf) and [Single-Shot Multi-Person 3D Pose Estimation From Monocular RGB](https://arxiv.org/pdf/1712.03453.pdf) papers. It detects 2D coordinates of up to 18 types of keypoints: ears, eyes, nose, neck, shoulders, elbows, wrists, hips, knees, and ankles, as well as their 3D coordinates. It was trained on [MS COCO](http://cocodataset.org/#home) and [CMU Panoptic](http://domedb.perception.cs.cmu.edu/) datasets and achieves 100 mm MPJPE (mean per joint position error) on CMU Panoptic subset. *This repository significantly overlaps with https://github.com/opencv/open_model_zoo/, however contains just the necessary code for 3D human pose estimation demo.*

<p align="center">
  <video width="320" height="240" controls>
    <source src="outputs/LR_agreement_impaired_wireframe.avi" type="video/avi">
  </video>

  <video width="320" height="240" controls>
    <source src="outputs/LR_agreement_impaired_overlay.avi" type="video/avi">
  </video>
</p>

## Table of Contents

* [Requirements](#requirements)
* [Prerequisites](#prerequisites)
* [Pre-trained model](#pre-trained-model)
* [Running](#running)

## Requirements
* Python 3.5 (or above)
* CMake 3.10 (or above)
* C++ Compiler (g++ or MSVC)
* OpenCV 4.0 (or above)

## Prerequisites
1. Install requirements:
```
pip install -r requirements.txt
```
2. Build `pose_extractor` module:
```
python setup.py build_ext
```
3. Add build folder to `PYTHONPATH`:
```
export PYTHONPATH=pose_extractor/build/:$PYTHONPATH
```

## Pre-trained model <a name="pre-trained-model"/>

Pre-trained model is available at [Google Drive](https://drive.google.com/file/d/1niBUbUecPhKt3GyeDNukobL4OQ3jqssH/view?usp=sharing).

## Running

To run the demo, pass path to the pre-trained checkpoint and camera id (or path to video file):
```
python demo.py --model human-pose-estimation-3d.pth --video 0
```
> Camera can capture scene under different view angles, so for correct scene visualization, please pass camera extrinsics and focal length with `--extrinsics` and `--fx` options correspondingly (extrinsics sample format can be found in data folder). In case no camera parameters provided, demo will use the default ones.
