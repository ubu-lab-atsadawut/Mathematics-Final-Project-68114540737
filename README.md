# ⚽ Premier League Match Analysis & Goal Prediction
> **Course:** 1145 201 Mathematics for Data Science | UBU
> **Author:** Atsadawut Phansalee (68114540737)

## 📌 Problem Statement
การแข่งขันฟุตบอลพรีเมียร์ลีกมีปัจจัยทางสถิติระหว่างเกมที่หลากหลาย (เช่น โอกาสยิง, ยิงเข้ากรอบ, เตะมุม, ฟาวล์) โครงงานนี้จัดทำขึ้นเพื่อวิเคราะห์ความสัมพันธ์ของตัวแปรทางสถิติเหล่านี้ด้วยหลักการทางคณิตศาสตร์และพีชคณิตเชิงเส้น รวมถึงสร้างแบบจำลอง Machine Learning (Regression) เพื่อพยากรณ์ความดุเดือดของเกมในรูปแบบ **"จำนวนประตูรวม" (Total Goals)** 

## 📊 Dataset
- **Source:** [football-data.co.uk](https://football-data.co.uk/englandm.php)
- **Scope:** English Premier League (EPL) 5 ฤดูกาล (2021/2022 ถึง 2025/2026)
- **Size:** 1,900 แมตช์ 

## 🚀 Project Workflow & CLOs
โปรเจกต์นี้ถูกออกแบบมาให้สอดคล้องกับวัตถุประสงค์การเรียนรู้ (Course Learning Outcomes) ดังนี้:

### 1. Linear Algebra Analysis (CLO1)
- นำเทคนิค **PCA (Principal Component Analysis)** ผ่านการคำนวณ Covariance Matrix มาใช้เพื่อลดมิติข้อมูล (Dimensionality Reduction) 
- **ผลลัพธ์:** สกัด Feature หลักที่อธิบายความแปรปรวน (Variance) ของรูปเกม และแสดงผลความแตกต่างของผลการแข่งขันผ่าน 2D Visualization

### 2. Statistical Learning (CLO2)
- วิเคราะห์การกระจายตัวของข้อมูล (Distribution) และหาความสัมพันธ์ (Correlation)
- ศึกษา **Bias-Variance Tradeoff** ผ่านการทำ Polynomial Regression เพื่อหา Model Complexity ที่เหมาะสม (U-Curve)
- **ผลลัพธ์:** พบว่า `Total_Shots_On_Target` มีความสัมพันธ์กับจำนวนประตูรวมมากที่สุด และโมเดลที่มีความซับซ้อนต่ำ (Low Degree) ป้องกันการเกิด Overfitting ได้ดีที่สุด

### 3. Model Building (CLO3)
- สร้างและเทรนโมเดล Regression 2 รูปแบบเพื่อเปรียบเทียบประสิทธิภาพ:
  1. **Simple Linear Regression:** ใช้เพียง 1 Feature ที่มีสหสัมพันธ์สูงสุด
  2. **Ridge Regression:** ใช้สถิติแบบพหุคูณ (Multiple Features) พร้อมเพิ่ม L2 Regularization (Penalty) เพื่อควบคุมขนาดของน้ำหนักสมการ

### 4. Model Selection (CLO4)
- ประเมินผลโมเดลอย่างเป็นธรรมด้วยเทคนิค **5-Fold Cross-Validation**
- **ผลลัพธ์:** Ridge Regression ทำผลงานได้เสถียรที่สุดบนข้อมูลที่ไม่เคยเห็นมาก่อน (Unseen Data) โดยให้ค่าเฉลี่ย Mean Squared Error (MSE) ที่ต่ำและลดปัญหาความแปรปรวนของโมเดล

## 🛠️ Tech Stack
- `Python`
- `Pandas`, `NumPy` (Data Manipulation & Linear Algebra)
- `Matplotlib`, `Seaborn` (Data Visualization)
- `Scikit-learn` (Machine Learning, PCA, Cross-Validation)

## 💡 Future Work
- ทำ Feature Engineering เพิ่มเติม เช่น การหาค่าเฉลี่ยฟอร์มย้อนหลัง (Rolling Averages) 5 นัดล่าสุดของแต่ละทีม เพื่อให้โมเดลเข้าใจโมเมนตัมของทีม ณ ขณะนั้น
- นำสถิติขั้นสูงอย่าง xG (Expected Goals) มาประยุกต์ใช้เพื่อยกระดับความแม่นยำ (R²) ของการพยากรณ์
