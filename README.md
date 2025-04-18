# Dự án Seminar - Vision Transformers for Biomedical Image Analysis and Diagnostics.
### Thông tin chung. 
- Dự án sử dụng mô hình ViT để chẩn đoán 4 bệnh về phổi phổ biến bằng ảnh chụp X-quang, và sử dụng thuật toán ReciproCAM để cải thiện tính xác thực và độ tin cậy của kết luận.
- Vì kích thước >330mb, model đã được lưu trữ trên Kaggle: https://www.kaggle.com/models/minhius/vit_final_model/
- Các thành viên nhóm:
  + Trịnh Minh Hiếu
  + Trần Kim Thành
  + Trần Hồng Đăng
### Công cụ và công nghệ:
1. Mô hình.
- Mô hình ViT base đã được pretrain trên tập dữ liệu Image21k, và được fine-tune trên bộ dữ liệu **COVID-19 Radiography Database** của Tawsifur Rahman, Tiến sĩ Muhammad Chowdhury và Amith Khandakar trên Kaggle.
- Mô hình đã đạt accuracy trên tập train là 99%, trên tập validation là 95%.
2. Bộ dữ liệu huấn luyện.
- Bộ dữ liệu có kích thước khoảng 42.3 nghìn ảnh định dạng .png, với 4 labels: Covid, Lung Opacity, Normal, và Viral Pneumonia. Trong đó, một nửa bộ dữ liệu là ảnh đã được xử lý để tách masks của hai lá phổi.
- Link bộ dữ liệu: https://www.kaggle.com/datasets/tawsifurrahman/covid19-radiography-database/data
- Train/val/test = 70/15/15.
3. Bộ dữ liệu kiểm thử.
- Bộ dữ liệu kiểm thử được tổng hợp từ 6 bộ dữ liệu khác nhau trên Kaggle, không bao gồm bộ đã dùng để huấn luyện.
  + #1: https://www.kaggle.com/datasets/pranavraikokte/covid19-image-dataset
  + #2: https://www.kaggle.com/datasets/pcbreviglieri/pneumonia-xray-images
  + #3: https://www.kaggle.com/datasets/thomasnibb/image-classification-covid19-xray
  + #4: https://www.kaggle.com/datasets/fsang2692/lung-area-specific-covid19-xray-dataset
  + #5: https://www.kaggle.com/datasets/nourmahmoud/covid19-digital-xrays-forgery-dataset
  + #6: https://www.kaggle.com/datasets/yazanqiblawey/sars-mers-xray-images-dataset
4. Công cụ và cài đặt.
- Train trên Kaggle với GPU T4 x 2 trong hơn 3 tiếng.
- Code train được tham khảo từ: https://github.com/stevenlimcorn/Covid-Classification
- Code ReciproCAM: https://github.com/sybyun/vitcam
  
