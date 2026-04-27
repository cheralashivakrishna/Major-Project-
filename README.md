# 🚗 Lane Detection & Collision Prevention System

An AI-powered system for **lane detection and vehicle collision warning** using **LSTR (Transformer-based Lane Detection)** and **YOLOv8**.

This project performs **real-time inference** on road scenes to:

* Detect lane boundaries
* Identify vehicles
* Estimate **Time-To-Collision (TTC)**
* Generate visual warnings

---

## 📌 Features

* ✅ Transformer-based **Lane Detection (LSTR)**
* ✅ **YOLOv8** for vehicle detection
* ✅ Ego-lane filtering
* ✅ Collision risk estimation using TTC
* ✅ Visual overlays with warnings
* ✅ Evaluation metrics (Precision, Recall, F1, IoU)

---

## 🧠 Tech Stack

* Python
* PyTorch
* OpenCV
* YOLOv8
* Kaggle Notebook (GPU execution)

---

## 📂 Project Structure

```
├── majorprojectiou71-1__4_.ipynb   # Main notebook
├── lstr_checkpoint_latest.pth      # Pretrained model (downloaded)
├── README.md
└── sample_outputs/
```

---

## ⚙️ How to Run (Inference Only)

### 1️⃣ Open Kaggle Notebook

* Go to [https://www.kaggle.com](https://www.kaggle.com)
* Create a new notebook
* Upload:

```
majorprojectiou71-1__4_.ipynb
```

---

### 2️⃣ Enable GPU

* Go to **Settings (⋮)**
* Select:

```
GPU T4 x2
```

---

### 3️⃣ Add Dataset

* Click **Add Data**
* Search:

```
CULane (by manideep1108)
```

* Dataset path:

```
/kaggle/input/datasets/manideep1108/culane/CULane
```

---

### 4️⃣ Download Pretrained Model

Download the best trained model from Google Drive:

🔗 [https://drive.google.com/file/d/1q_Dy65wK_WE7m6b1S9Y8DkmJqYGFX_NX/view?usp=sharing](https://drive.google.com/file/d/1q_Dy65wK_WE7m6b1S9Y8DkmJqYGFX_NX/view?usp=sharing)

Or use the following command inside the notebook:

````python
!pip install -q gdown

!gdown --id 1q_Dy65wK_WE7m6b1S9Y8DkmJqYGFX_NX \
       -O /kaggle/working/lstr_checkpoint_latest.pth
```python
!pip install -q gdown

!gdown --id 1q_Dy65wK_WE7m6b1S9Y8DkmJqYGFX_NX \\
       -O /kaggle/working/lstr_checkpoint_latest.pth
````

---

### 5️⃣ Load Model (Inference Mode)

```python
import torch

ckpt = torch.load('/kaggle/working/lstr_checkpoint_latest.pth', map_location=device)

model.load_state_dict(ckpt['model_state_dict'])
model.to(device)
model.eval()

print(f'Loaded from epoch : {ckpt["epoch"]}')
print(f'Best F1           : {ckpt["best_score"]:.4f}')
```

---

### 6️⃣ Run Inference

The notebook will:

* Load test images
* Detect lanes using LSTR
* Detect vehicles using YOLOv8
* Compute TTC
* Display results with overlays

---

### 7️⃣ Save Output

```python
import cv2

cv2.imwrite('/kaggle/working/prediction_output.jpg', output_frame)
```

Download via:

```
Output → Download
```

---

## 📊 Output

* Lane detection overlays
* Vehicle bounding boxes
* Collision warning banners

### Metrics:

* Precision
* Recall
* F1 Score
* Mean IoU

---

## ⚠️ Important Notes

* Always run:

```python
model.eval()
```

* Do **NOT** run training cells
* GPU is required for smooth execution

---

## 🚀 Future Improvements

* Real-time deployment with camera feed
* Integration with ADAS systems
* Better TTC estimation using depth models
* Edge deployment optimization

---

## 👨‍💻 Author

**Cherala Shiva Krishna**

---

## 📄 License

This project is for academic and research purposes.
