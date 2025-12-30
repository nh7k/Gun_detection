# 🔫 Real-Time Weapon Detection System using YOLOv5

A live weapon detection system that uses YOLOv5 to detect guns in real-time through webcam. Built for Google Colab with instant alerts and visual indicators.

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![YOLOv5](https://img.shields.io/badge/YOLOv5-Latest-green)
![License](https://img.shields.io/badge/License-MIT-orange)

---

## 🎯 What Does This Do?

- **Detects guns in real-time** from webcam feed
- **Shows RED box** around detected weapons
- **Displays "WANTED" alert** when gun detected
- **Shows "SAFE AREA"** when no weapon found
- **Trains in 5-10 minutes** on Google Colab
- **Works on any webcam** - laptop, phone, external

---

## 🚀 Quick Setup (3 Steps)

### Step 1: Open Google Colab
Go to [colab.research.google.com](https://colab.research.google.com)

### Step 2: Run Training Code
Copy-paste the training notebook and run all cells (takes 5-10 minutes)

### Step 3: Run Detection
```python
detect_once()  # Test with single capture
```

**That's it!** 🎉

---

## 📸 How It Works

### When NO GUN:
```
┌──────────────────────────────────┐
│                    ┌───────────┐ │
│   [Your face]      │ ✓ SAFE   │ │
│                    │   AREA    │ │
│                    └───────────┘ │
└──────────────────────────────────┘
Status: 🟢 SAFE - NO WEAPON DETECTED
```

### When GUN DETECTED:
```
┌──────────────────────────────────┐
│   ╔═══════════╗    ┌───────────┐ │
│   ║ GUN 85%  ║     │ ⚠WARNING │ │
│   ║  [Gun]   ║     │  WANTED   │ │
│   ╚═══════════╝    └───────────┘ │
└──────────────────────────────────┘
Status: 🔴 GUN DETECTED - WANTED PERSON!
```

---

## 💻 Usage

### Single Detection
```python
detect_once()
```
Opens webcam → Click capture → Shows result

### Continuous Detection
```python
detect_continuous(5)  # 5 captures
```
Captures 5 frames continuously with results

---

## 📊 Training Options

### Quick Training (For Testing)
```python
Epochs: 7
Batch: 5
Time: 5-10 minutes
Accuracy: ~84%
```
**Good for:** Quick testing and prototyping

### Production Training (Recommended)
```python
Epochs: 50-100
Batch: 16
Time: 30-45 minutes  
Accuracy: ~90-93%
```
**Good for:** Real deployment and better accuracy

---

## 🔧 Common Issues & Fixes

### Issue 1: Always Shows "SAFE" (Not Detecting Gun)

**Cause:** Model not trained enough (7 epochs too low)

**Fix:**
```python
# Option 1: Lower confidence
CONFIDENCE_THRESHOLD = 0.10  # From 0.15

# Option 2: Retrain with more epochs
--epochs 50  # Instead of 7
```

### Issue 2: Webcam Not Opening

**Fix:**
- Allow camera permission in browser
- Click the green capture button
- Try refreshing the page

### Issue 3: Model Not Found

**Fix:**
```python
# Copy model after training
!cp /content/yolov5/weapon_detection/weapon_model/weights/best.pt /content/best.pt
```

---

## 📦 Installation

### For Google Colab (Easiest)
```python
!pip install -q ultralytics opencv-python-headless
```

### For Local Computer
```bash
pip install -r requirements.txt
```

---

## 📈 Performance

| Training | Time | Accuracy | Best For |
|----------|------|----------|----------|
| 7 epochs | 5-10 min | 84% | Testing |
| 50 epochs | 30 min | 90% | Production |
| 100 epochs | 45 min | 93% | High accuracy |

---

## 🎓 Dataset Used

**Source:** Kaggle Gun & Knife Detection Dataset  
**Images:** 1,000+  
**Classes:** weapon, person  
**Link:** [kaggle.com/datasets/nikhilajani/gun-knife](https://www.kaggle.com/datasets/nikhilajani/gun-knife)

---

## 🛠️ Configuration

### Change Detection Sensitivity
```python
CONFIDENCE_THRESHOLD = 0.15  # Lower = more sensitive
```

### Change Colors
```python
COLOR_SAFE = (0, 255, 0)      # Green
COLOR_DANGER = (0, 0, 255)    # Red
```

---

## 📁 Files Included

```
📦 Project
├── 📓 training_notebook.ipynb      # Train the model
├── 📓 detection_notebook.ipynb     # Run detection
├── 📄 requirements.txt             # Dependencies
├── 📄 README.md                    # This file
└── 📦 best.pt                      # Trained model (after training)
```

---

## ⚡ Quick Commands

```python
# Train model
!python train.py --img 640 --batch 5 --epochs 7

# Single detection
detect_once()

# Continuous detection
detect_continuous(10)

# Check model info
print(model.names)
print(f"Confidence: {CONFIDENCE_THRESHOLD}")
```

---

## 💡 Pro Tips

1. **Good Lighting** - Use bright room for better detection
2. **Clear Image** - Hold weapon clearly in frame
3. **Medium Distance** - Not too close or far
4. **Train More** - Use 50+ epochs for production
5. **Lower Threshold** - If missing detections, lower to 0.10

---

## 🎯 Use Cases

- ✅ Security monitoring
- ✅ Public safety systems
- ✅ Educational projects
- ✅ Research & development
- ✅ Proof of concept demos

---

## 🤝 Contributing

Want to improve this? 
1. Fork the repo
2. Make changes
3. Submit pull request

---

## ⚠️ Important Notes

### This System:
- ✅ Detects only visible weapons
- ✅ Requires good lighting
- ✅ Works best with clear images
- ✅ Needs training for high accuracy

### Limitations:
- ❌ Won't detect concealed weapons
- ❌ May miss in poor lighting
- ❌ Needs retraining for new weapon types
- ❌ 7 epochs = low accuracy (use 50+)

---

## 🐛 Debug Mode

See what's being detected:
```python
detect_once()  # Check console output

# You'll see:
# 📊 Total detections found: X
# 🔎 All detected objects:
#   - Class: 'weapon' | Confidence: XX%
```

---

## 📞 Need Help?

**Not detecting weapons?**
1. Check console output during detection
2. Lower confidence threshold to 0.10
3. Retrain with 50+ epochs
4. Ensure good lighting
5. Hold weapon clearly visible

**Still issues?**
- Open an issue on GitHub
- Check console for error messages

---

## 📄 License

MIT License - Free to use for educational purposes

---

## 🙏 Credits

- **YOLOv5** - Ultralytics
- **Dataset** - Nikhil Ajani (Kaggle)
- **Platform** - Google Colab

---

## ⭐ Star This Repo!

If this helped you, please star ⭐ the repository!

---

**Made for Security & Safety Applications** 🛡️

*Last Updated: December 2024*