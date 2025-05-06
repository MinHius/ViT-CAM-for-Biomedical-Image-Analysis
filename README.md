# Dự án Seminar - Vision Transformers for Biomedical Image Analysis and Diagnostics.
### Thông tin chung. 
- Dự án sử dụng mô hình ViT để chẩn đoán 4 bệnh về phổi phổ biến bằng ảnh chụp X-quang, và sử dụng thuật toán ReciproCAM để cải thiện tính diễn giải và độ tin cậy của kết luận.
- Vì kích thước ~327MB, model đã được lưu trữ trên Kaggle: [https://www.kaggle.com/models/minhius/vit_lungxray_bestval]
- Các thành viên **nhóm 18**:
  + Trịnh Minh Hiếu
  + Trần Kim Thành
  + Trần Hồng Đăng
### Về dự án:
1. Mô hình.
- Mô hình ViT base đã được pretrain trên tập dữ liệu Image21k, và được fine-tune trên bộ dữ liệu **COVID-19 Radiography Database** của Tawsifur Rahman, Tiến sĩ Muhammad Chowdhury và Amith Khandakar trên Kaggle.
- Được train trên Kaggle với GPU T4 x 2 trong hơn 3 tiếng, kiểm thử trên Google Colab với GPU T4.
- Mô hình tốt nhất (epoch 7 early stopping) đạt accuracy trên tập train là 99%, trên tập validation và tập test là 98%.
<p align="center">
  <img src="https://github.com/user-attachments/assets/9537f3c0-a841-40cf-8dfd-f55fe2ddfda5">
</p>

2. Kiểm thử.
<p align="center">
  <img src="https://github.com/user-attachments/assets/efe51425-329a-4dbb-921a-107799e81427">
</p>

  + **Accuracy**: 96.06%<br>
  + **F1 Score**: 0.9601161442894759<br>
  + **Precision**: 0.9617316249617643<br>
  + **Recall**: 0.9602083333333333<br>
  + **AUC-ROC**: 0.9965431134259259<br>

3. Bộ dữ liệu huấn luyện.
- Bộ dữ liệu có kích thước khoảng 42.3 nghìn ảnh định dạng .png, với 4 labels: Covid, Lung Opacity, Normal, và Viral Pneumonia. Trong đó, một nửa bộ dữ liệu là ảnh đã được xử lý sẵn tách masks của hai lá phổi.
- Link bộ dữ liệu: https://www.kaggle.com/datasets/tawsifurrahman/covid19-radiography-database/data.
- Train/val/test = 70/15/15.

4. Bộ dữ liệu kiểm thử.
- Bộ dữ liệu kiểm thử được tổng hợp từ 7 bộ dữ liệu khác nhau trên Kaggle, không bao gồm bộ đã dùng để huấn luyện.
- Bộ bao gồm 4800 ảnh với 1200 COVID, 1200 Lung Opacity, 1200 Normal và 1200 Viral Pneumonia.
  + #1: https://www.kaggle.com/datasets/pranavraikokte/covid19-image-dataset
  + #2: https://www.kaggle.com/datasets/pcbreviglieri/pneumonia-xray-images
  + #3: https://www.kaggle.com/datasets/thomasnibb/image-classification-covid19-xray
  + #4: https://www.kaggle.com/datasets/fsang2692/lung-area-specific-covid19-xray-dataset
  + #5: https://www.kaggle.com/datasets/nourmahmoud/covid19-digital-xrays-forgery-dataset
  + #6: https://www.kaggle.com/datasets/yazanqiblawey/sars-mers-xray-images-dataset
  + #7: https://www.kaggle.com/datasets/kamildinleyici/covid-normal-viral-opacity-v2

5. Các loại file.
- **train.ipynb**: File mã nguồn fine-tune mô hình.
- **ViT_reciproCAM.ipynb**: File mã nguồn kiểm thử có áp dụng reciproCAM trên sample nhỏ từ bộ kiểm thử và bộ huấn luyện.
- **Test_final.ipynb**: File mã nguồn kiểm thử trên bộ kiểm thử đầy đủ.

### Cách cài đặt.
- Chạy pip install -r requirements.txt
- Dataset sử dụng phải có cấu trúc như sau:
  - Dataset/
    + COVID/
      + image1.png
      + image2.png
      + ...
    + Lung Opacity/
      + image1.png
      + image2.png
      + ...
    + Normal/
      + image1.png
      + image2.png
      + ...
    + Viral Pneumonia/
      + image1.png
      + image2.png
      + ...
- Tải model từ Kaggle rồi chạy.

### Disclaimer.
- Code train được tham khảo và điều chỉnh từ: https://github.com/stevenlimcorn/Covid-Classification
- Code ReciproCAM được tham khảo và điều chỉnh từ: https://github.com/sybyun/vitcam
