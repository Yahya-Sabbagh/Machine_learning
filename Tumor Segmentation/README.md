Description:
This Python script automates the processing, labeling, and organization of 3D CT scan volumes (.nii.gz) and their segmentation masks into a YOLO-compatible 2D dataset for training deep learning models.

 Main Steps:

Load and Process NIfTI Volumes

Reads CT and segmentation .nii.gz files using nibabel.

Extracts each 2D slice (axial plane) from 3D volumes.

Skips empty slices without any tumor pixels.

Normalize and Save CT Slices

Normalizes intensity values to the 0–255 range and saves them as .png images.

Remap and Generate Segmentation Labels

Remaps class IDs:

1 → 0 (Primary Tumor)

2 → 1 (Metastasis)

Extracts contours from masks and converts them into YOLO-style .txt label files containing:

class_id x_center y_center width height [polygon points...]


Organize the Dataset

Automatically splits data into train (80%), validation (10%), and test (10%) sets.

Moves corresponding image and label files into their respective folders under:

dataset/
  ├── images/
  │   ├── train/
  │   ├── val/
  │   └── test/
  └── labels/
      ├── train/
      ├── val/
      └── test/

 Output Summary:

Extracted and normalized CT slices

YOLO-formatted segmentation labels

Fully organized dataset ready for model training

This preprocessing pipeline is ideal for preparing medical image segmentation datasets for training YOLOv8/YOLOv9 or similar object detection models.
