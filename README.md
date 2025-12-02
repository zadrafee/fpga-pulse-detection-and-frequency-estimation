# ⚡ FPGA-Based Pulse Detector & Frequency Estimator  
# 🎯 آشکارساز پالس و تخمین فرکانس مبتنی بر FPGA

## 📘 خلاصه پروژه  
این پروژه یک سیستم کامل آشکارسازی پالس و تخمین دقیق فرکانس روی پلتفرم FPGA است که برای سیگنال‌های IF با فرکانس مرکزی **160MHz** طراحی شده است. سیستم ابتدا دامنه سیگنال Baseband را استخراج کرده، پالس‌های ورودی را با Threshold شناسایی می‌کند و در نهایت با اجرای **FFT 128-Point** و **Quadratic Interpolation** فرکانس دقیق پالس را تخمین می‌زند. ⚙️📡

This project implements a complete pulse detection and frequency estimation system on an FPGA platform. It processes **160MHz IF signals**, extracts the Baseband envelope, detects pulses using adaptive thresholding, and computes precise frequency using a **128-point FFT** and **quadratic interpolation**. 🚀🎛️

---

## 🌟 ویژگی‌های اصلی سیستم  
- دمدولاسیون **I/Q** و استخراج سیگنال Baseband  
- محاسبه دامنه با **CORDIC SQRT**  
- تولید Threshold با نویز میانگین  
- تشخیص شروع و پایان پالس  
- فعال‌سازی هماهنگ FFT  
- اجرای **128-Point FFT**  
- تخمین فرکانس دقیق با **Quadratic Interpolation**  
- دقت فرکانسی **1MHz** و زیر-باین  

✨ English Highlights  
- **I/Q demodulation** and envelope extraction  
- Magnitude computation via **CORDIC SQRT**  
- Noise averaging and threshold generation  
- Pulse start/stop detection  
- FFT trigger alignment  
- **128-point pipelined FFT**  
- Sub-bin frequency estimation using **quadratic interpolation**  
- **1MHz** frequency resolution

---

## 🧩 معماری سیستم  

### 1. 🔻 IQ_Demodulator  
تبدیل IF 160MHz به Baseband و فیلتر FIR/IIR  
Down-conversion to Baseband with band-limited filtering.

### 2. 📐 CORDIC SQRT  
محاسبه دامنه لحظه‌ای  
Computes instantaneous magnitude.

### 3. 🎚️ Noise_Mean_Calculator  
استخراج میانگین نویز و Threshold  
Noise averaging and threshold generation.

### 4. 🎯 Pulse Detector  
تشخیص شروع و پایان پالس و فعال‌سازی FFT  
Detects pulse window and triggers FFT.

### 5. 📊 FFT_128p  
محاسبه دامنه باین‌ها و یافتن حداکثر  
Computes bin magnitudes and identifies peak bin.

### 6. 🔬 Quadratic Interpolation  
تخمین دقیق فرکانس با سه مقدار A، B و C  
Refines frequency using A/B/C bin interpolation.

---

## 📁 ساختار فایل‌ها  

```
PulseDetector_FrequencyEstimator/
│
├── ISE_Project/
│   ├── IF_FFT_Top.vhd
│   ├── IQ_Demodulator.vhd
│   ├── Noise_Mean_Calc.vhd
│   ├── Low_Pass_Filter.vhd
│   └── IF_IFF_Top_tb.vhd
│
├── MATLAB_Simulink/
│   ├── ifm.slx
│   └── input_write_file.m
│
└── Docs/
    ├── Report_Persian.pdf
    └── Report_English.pdf
```

---

## ▶️ نحوه اجرا  
- نرم‌افزار: **Xilinx ISE 14.7** 🧰  
- انتخاب `IF_FFT_Top.vhd` به عنوان Top  
- اجرای Testbench برای شبیه‌سازی 🧪  
- خروجی فرکانس با `FFT_Max_Index` و `Bin_Offset` استخراج می‌شود  

Required software: **Xilinx ISE 14.7**  
Set `Pulse_Top.vhd` as top module.  
Use the testbench for simulation.  
Frequency is obtained using `FFT_Max_Index` and `Bin_Offset`.

---

## 🏁 جمع‌بندی  
این پروژه یک نمونه کامل و عملی از پیاده‌سازی آشکارساز پالس و تخمین فرکانس روی FPGA است. 💼🔧

This project demonstrates a practical FPGA-based pulse detection and frequency estimation system. 🌐⚙️
