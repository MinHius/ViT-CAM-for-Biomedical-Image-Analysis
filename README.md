# Dự án Seminar - Vision Transformers for Biomedical Image Analysis and Diagnostics.
### Thông tin chung. 
- Dự án sử dụng mô hình ViT để chẩn đoán 4 bệnh về phổi phổ biến bằng ảnh chụp X-quang, và sử dụng thuật toán ReciproCAM để cải thiện tính diễn giải và độ tin cậy của kết luận.
- Vì kích thước ~327MB, model đã được lưu trữ trên Kaggle: [https://www.kaggle.com/models/minhius/vit_lungxray_bestval]
- Các thành viên nhóm:
  + Trịnh Minh Hiếu
  + Trần Kim Thành
  + Trần Hồng Đăng
### Về dự án:
1. Mô hình.
- Mô hình ViT base đã được pretrain trên tập dữ liệu Image21k, và được fine-tune trên bộ dữ liệu **COVID-19 Radiography Database** của Tawsifur Rahman, Tiến sĩ Muhammad Chowdhury và Amith Khandakar trên Kaggle.
- Mô hình tốt nhất (epoch 7 early stopping) đạt accuracy trên tập train là 99%, trên tập validation và tập test là 98%.
<p align="center">
  <img src="https://github.com/user-attachments/assets/9537f3c0-a841-40cf-8dfd-f55fe2ddfda5">
</p>

2. Kiểm thử.
<p align="center">
  <img src="https://github.com/user-attachments/assets/57930a4e-fb62-42d0-8c0d-545a7040a8cc">
</p>
- Accuracy: 94.90%
- F1 Score: 0.7292832447036676
- Precision: 0.7270522396694347
- Recall: 0.9634361515391286
- AUC-ROC: 0.9951287983667494

3. Bộ dữ liệu huấn luyện.
- Bộ dữ liệu có kích thước khoảng 42.3 nghìn ảnh định dạng .png, với 4 labels: Covid, Lung Opacity, Normal, và Viral Pneumonia. Trong đó, một nửa bộ dữ liệu là ảnh đã được xử lý để tách masks của hai lá phổi.
- Link bộ dữ liệu: https://www.kaggle.com/datasets/tawsifurrahman/covid19-radiography-database/data
- Train/val/test = 70/15/15.

4. Bộ dữ liệu kiểm thử.
- Bộ dữ liệu kiểm thử được tổng hợp từ 6 bộ dữ liệu khác nhau trên Kaggle, không bao gồm bộ đã dùng để huấn luyện.
- Bộ bao gồm 4430 ảnh với 1192 COVID, 1703 Normal, 1435 Viral Pneumonia và không có Lung Opacity.
  + #1: https://www.kaggle.com/datasets/pranavraikokte/covid19-image-dataset
  + #2: https://www.kaggle.com/datasets/pcbreviglieri/pneumonia-xray-images
  + #3: https://www.kaggle.com/datasets/thomasnibb/image-classification-covid19-xray
  + #4: https://www.kaggle.com/datasets/fsang2692/lung-area-specific-covid19-xray-dataset
  + #5: https://www.kaggle.com/datasets/nourmahmoud/covid19-digital-xrays-forgery-dataset
  + #6: https://www.kaggle.com/datasets/yazanqiblawey/sars-mers-xray-images-dataset

5. Công cụ và cài đặt.
- Train trên Kaggle với GPU T4 x 2 trong hơn 3 tiếng.
- Code train được tham khảo từ: https://github.com/stevenlimcorn/Covid-Classification
- Code ReciproCAM: https://github.com/sybyun/vitcam
  
