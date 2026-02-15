# Real-Time Background Blurring with DeepLabV3

Deep learning-powered real-time background blurring for video calls using TensorFlow 2 and OpenCV.

![Python](https://img.shields.io/badge/Python-3.13+-blue.svg)
![TensorFlow](https://img.shields.io/badge/TensorFlow-2.20+-orange.svg)
![License](https://img.shields.io/badge/License-MIT-green.svg)

## Overview

This project implements real-time background blurring using the DeepLabV3+ semantic segmentation model. Perfect for video conferencing, interviews, or any situation where you need to blur your background professionally.

### Features

- 🎥 **Real-time Processing** - Process webcam feed at ~200-250ms per frame
- 🧠 **Deep Learning** - Uses DeepLabV3+ with MobileNetV2 backbone
- 🎯 **Pre-trained Weights** - Trained on PASCAL VOC dataset
- 🚀 **Modern Stack** - Updated for Python 3.13+ and TensorFlow 2.20+
- 💻 **Easy Setup** - Simple installation with virtual environment

## Installation

### Prerequisites

- Python 3.8 or higher (tested with Python 3.13)
- Webcam or camera device
- Windows/Linux/macOS

### Setup Instructions

1. **Clone the repository**
```bash
git clone <repository-url>
cd realtime_bg_blurring
```

2. **Create and activate virtual environment**

Windows:
```bash
python -m venv .venv
.venv\Scripts\activate
```

Linux/macOS:
```bash
python -m venv .venv
source .venv/bin/activate
```

3. **Install dependencies**
```bash
pip install tensorflow opencv-python matplotlib imutils numpy
```

## Usage

Run the application:
```bash
python main.py
```

The application will:
1. Load the DeepLabV3+ model (first run downloads ~9MB weights)
2. Access your default webcam
3. Display two windows: original feed and blurred background
4. Press **'q'** to quit

## Technology Stack

| Component | Technology |
|-----------|-----------|
| **Language** | Python 3.13+ |
| **Deep Learning** | TensorFlow 2.20+ with Keras API |
| **Computer Vision** | OpenCV (cv2) |
| **Model Architecture** | DeepLabV3+ |
| **Backbone** | MobileNetV2 |
| **Dataset** | PASCAL VOC (pre-trained) |
| **Dependencies** | NumPy, Matplotlib, imutils |

## Project Structure

```
realtime_bg_blurring/
├── main.py              # Main application entry point
├── model.py             # DeepLabV3+ model implementation
├── extract_weights.py   # Weight extraction utility
├── load_weights.py      # Weight loading utility
├── README.md            # This file
├── LICENSE              # License information
└── imgs/                # Sample images and results
```

## How It Works

1. **Capture Frame** - Webcam captures video frame
2. **Preprocess** - Resize and normalize image for model input
3. **Segmentation** - DeepLabV3+ predicts person mask
4. **Apply Blur** - Background is blurred using Gaussian blur
5. **Composite** - Person foreground + blurred background
6. **Display** - Show results in real-time

## Model Details

- **Architecture**: DeepLabV3+ with Atrous Spatial Pyramid Pooling (ASPP)
- **Backbone**: MobileNetV2 (lightweight and fast)
- **Output Stride**: 8 (configurable to 16)
- **Input Size**: 512x512x3
- **Output Classes**: 21 (PASCAL VOC classes)
- **Performance**: ~200-250ms per frame on CPU

## Requirements

### Python Packages
```txt
tensorflow>=2.20.0
opencv-python>=4.5.0
matplotlib>=3.3.0
imutils>=0.5.4
numpy>=1.19.0
```

### Hardware
- **CPU**: Any modern multi-core processor
- **RAM**: 4GB minimum, 8GB recommended
- **GPU**: Optional (will improve performance significantly)
- **Camera**: Any USB or built-in webcam

## Troubleshooting

### Common Issues

**Camera not detected:**
```python
# Check available cameras
import cv2
cap = cv2.VideoCapture(0)  # Try different indices: 1, 2, etc.
```

**Out of memory:**
- Close other applications
- Reduce frame resolution in code
- Use OS=16 for lower memory usage

**Slow performance:**
- Ensure no other heavy processes running
- Consider using GPU-enabled TensorFlow
- Reduce input image size

## Updates (February 2026)

This project has been completely modernized:

### Compatibility Updates
✅ **Python 3.13 Support** - Upgraded from Python 3.5  
✅ **TensorFlow 2.x Migration** - Migrated from TensorFlow 1.4  
✅ **API Fixes** - Updated all deprecated Keras APIs  
✅ **Virtual Environment** - Added proper dependency isolation  

### Code Improvements
- Replaced `_keras_shape` with `K.int_shape()`
- Updated `conv_utils` import path
- Fixed model naming for TensorFlow 2.x compliance
- Improved error handling

## References

1. **Encoder-Decoder with Atrous Separable Convolution for Semantic Image Segmentation**  
   Liang-Chieh Chen, Yukun Zhu, George Papandreou, Florian Schroff, Hartwig Adam  
   [Paper](https://arxiv.org/abs/1802.02611) | ECCV 2018

2. **MobileNetV2: Inverted Residuals and Linear Bottlenecks**  
   Mark Sandler, Andrew Howard, Menglong Zhu, Andrey Zhmoginov, Liang-Chieh Chen  
   [Paper](https://arxiv.org/abs/1801.04381) | CVPR 2018

3. **Keras DeepLab V3+ Implementation**  
   [GitHub Repository](https://github.com/bonlime/keras-deeplab-v3-plus)

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgments

- Original DeepLabV3 research by Google Research
- Keras implementation by [bonlime](https://github.com/bonlime)
- Pre-trained weights from PASCAL VOC dataset
- Updated and maintained for modern TensorFlow 2.x

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## Support

For issues, questions, or contributions, please open an issue on GitHub.

---

**Last Updated**: February 15, 2026  
**Status**: ✅ Fully functional with Python 3.13 and TensorFlow 2.20+
