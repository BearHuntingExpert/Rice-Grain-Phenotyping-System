# Rice-Grain-Phenotyping-System

A lightweight desktop system for automated detection, counting, and phenotypic analysis of densely distributed rice grains.

This repository provides the trained model, standalone desktop application, and supporting resources developed for the study:

**An integrated high-throughput rice grain phenotyping method for breeding applications**

The system integrates rice grain detection, automatic counting, spatial calibration, grain size measurement, thousand-grain weight estimation, visualization, and result export into a unified desktop interface.

---

## Overview

Accurate and efficient acquisition of rice grain phenotypic traits is important for variety evaluation, breeding selection, and germplasm characterization. However, dense grain distribution, severe adhesion, and variations in imaging scale can reduce the accuracy of conventional vision-based methods.

This project provides a lightweight multi-scale rice grain detection and phenotyping framework based on YOLOv8n. The proposed model incorporates:

- **C2f-DyGhost** for lightweight feature extraction
- **LWCGA** for enhanced local feature interaction in densely distributed grain regions
- **MSPN** for multi-scale feature fusion and small-object representation
- **Focaler-PIoU** for improved bounding-box regression

A PySide6-based desktop application was further developed to support practical phenotyping analysis.

---

## Main Features

The system currently supports:

- Rice grain image import
- Automatic grain detection
- Automatic grain counting
- Confidence and IoU threshold adjustment
- Visualization of bounding boxes, IDs, and confidence scores
- Spatial calibration using a reference object
- Manual pixel-to-length calibration
- Grain length measurement
- Grain width measurement
- Average grain length and width calculation
- Thousand-grain weight estimation
- Individual grain image extraction
- CSV result export

---

## Model Performance

The proposed lightweight model achieved:

| Metric          | Result  |
| ---             | ---:    |
| Precision       | 99.83%  |
| Recall          | 99.82%  |
| mAP@0.5         | 99.48%  |
| mAP@0.5:0.95    | 86.63%  |
| Parameters      | 1.17 M  |
| GFLOPs          | 6.7 G   |
| Inference speed | 197 FPS |

Independent counting experiments were conducted under acquisition heights of 28, 36, and 44 cm with grain numbers ranging from 300 to 1000 per image.

The mean counting error rates of the proposed model were:

| Acquisition height | Mean error |
| ---                | ---:       |
| 28 cm              | 0.01%      |
| 36 cm              | 0.06%      |
| 44 cm              | 0.25%      |

---

## Desktop Phenotyping System

The graphical user interface was developed using **Python** and **PySide6**.

The system provides two main analysis modes:

1. **Rapid counting and thousand-grain weight estimation**
2. **Morphological measurement**

### Interface

<img width="1728" height="1341" alt="image" src="https://github.com/user-attachments/assets/c42c834a-5a63-40ae-9718-2aa5194a3d4d" />


### Rapid Counting Mode

The rapid counting mode detects individual rice grains and automatically outputs the total grain number. Users can adjust confidence and IoU thresholds according to image conditions.

When the total grain weight is provided, the system can also estimate thousand-grain weight.

### Morphological Measurement Mode

The morphological measurement mode performs spatial calibration and converts pixel-based measurements into physical dimensions.

The system outputs phenotypic parameters including:

- Grain length
- Grain width
- Average grain length
- Average grain width
- Total grain number

The measurement results can be exported as CSV files for subsequent statistical analysis.

---

## Repository Structure

```text
Rice-Grain-Phenotyping-System/
│
├── High-Throughput Rice Grain Phenotyping System.exe
│   └── Standalone desktop application
│
├── best.pt
│   └── Trained lightweight rice grain detection model
│
├── hnu_logo.png
│   └── Logo resource used by the graphical user interface
│
├── Example Image 1.jpg
│   └── Example rice grain image for software demonstration
│
├── Example Image 2.jpg
│   └── Example rice grain image for software demonstration
│
├── detected_grain.jpg
│   └── Example detection result
│
├── results.csv
│   └── Example exported phenotypic measurement results
│
└── results_crops/
    └── Example individual grain images automatically extracted during CSV export
```

The executable application has been packaged as a standalone program. Therefore, users do not need to install Python, PyTorch, PySide6, Ultralytics, or other development dependencies to run the software.

---
## Software Requirements

No Python environment or additional package installation is required for normal use.

The current version is distributed as a standalone Windows executable. The packaged application can be downloaded from the Releases section of this repository.

The executable, trained model weight (best.pt), and required resource files should be kept in the same directory during use.

## Usage

1.Download the files in this repository.

2.Keep the executable file, best.pt, and hnu_logo.png in the same directory.

3.Double-click:

High-Throughput Rice Grain Phenotyping System.exe

4.Import a rice grain image using Import Image.

5.Adjust the confidence and NMS IoU thresholds if necessary.

6.Click Run Inference to perform rice grain detection and counting.

7.For dimensional phenotyping, perform spatial calibration using the reference object or manually specify the pixel-to-length conversion ratio.

8.The software automatically calculates grain number, grain length, grain width, and mean morphological parameters.

9.If the total sample weight is entered, the system can estimate thousand-grain weight.

10.Detection images and phenotypic results can be exported for subsequent analysis.

## Output Files

The software can generate the following output files:

detected_grain.jpg

Detection result image containing the predicted rice grain bounding boxes and optional grain IDs or confidence scores.

results.csv

Phenotypic measurement results for individual rice grains.

Typical fields include:

- Grain ID

- Grain length

- Grain width

- Pixel-based measurements

- Calibrated physical measurements

results_crops/

Individual detected grain regions automatically cropped from the original image. Each grain image is saved using its corresponding grain ID.

## Source Code

The current repository primarily provides the standalone executable version of the rice grain phenotyping system for reproducible application and demonstration.

The source code is being organized and verified because multiple development versions were generated during system development. A verified source-code version corresponding to the released application will be provided in a future repository release.


## Dataset

The model was developed using rice grain images from four rice varieties representing both japonica and indica types.

The dataset contains densely distributed and adhered rice grains acquired under different imaging heights.

Due to data management and intellectual property considerations, the complete training dataset is not currently included in this repository.

Example images are provided in the repository.

---

## Citation

If this software or model is useful in your research, please cite the corresponding paper:

```bibtex
@article{Chen_RiceGrainPhenotyping,
  title   = {An integrated high-throughput rice grain phenotyping method for breeding applications},
  author  = {To be updated},
  journal = {To be updated},
  year    = {To be updated}
}
```

The citation information will be updated after publication.

---

## Software Availability

The current repository provides the trained detection model, example images, example output files, and a standalone executable version of the rice grain phenotyping system.

The Windows executable is distributed through the Releases section of this repository.

The source code is currently being organized and verified because multiple development versions were generated during system development. A verified source-code version corresponding to the released application will be provided in a future release.

---

## License

This project is released under the **MIT License**.

See the `LICENSE` file for details.

---

## Contact

For questions regarding the software or research, please contact the authors through the corresponding paper or GitHub Issues.

---

## Acknowledgements

This work was supported by research projects related to intelligent agricultural equipment and automated crop phenotyping.

The authors thank all collaborators who contributed to rice grain image acquisition, annotation, experimental validation, and system development.
