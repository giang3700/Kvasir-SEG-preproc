
# Tiền xử lý dữ liệu Kvasir-SEG

Project tiền xử lý đối với bộ dữ liệu Kvasir-SEG - Bộ dữ liệu Kvasir-SEG  bao gồm 1000 ảnh polyp và label tương ứng từ bộ dữ liệu Kvasir Dataset v2. Kích thước hình ảnh trong Kvasir-SEG thay đổi từ 332x487 đến 1920x1072 pixel. Các tệp hình ảnh và mask tương ứng được lưu trữ trong hai thư mục images/masks với cùng tên tệp. Các tệp hình ảnh được lưu dưới dạng file JPEG.

- Link tải bộ dữ liệu [Kvasir-SEG](https://datasets.simula.no/downloads/kvasir-seg.zip)

- Link dữ liệu Kaggle [Kvasir-SEG-Kaggle](https://www.kaggle.com/datasets/ipythonx/kvasirseg/data)
## 🧐 Tiền xử lý dữ liệu

### Các bước tiền xử lý dữ liệu

- Load dữ liệu hình ảnh và mask tương ứng
- Data augmentation 
- Tạo tf Dataset để train model

### 🚀 Chi tiết

#### Phần 1: Load dữ liệu:

- Dữ liệu hình ảnh và mask được đọc dưới dạng dữ liệu có kích thước là ```target_size``` đầu vào

- Dữ liệu hình ảnh và mask sẽ được chuẩn hóa về giá trị thập phân từ ```0``` đến ```1```

- Dữ liệu hình ảnh sẽ có shape là ```[target_size, target_size, 3]```

- Dữ liệu mask sẽ có shape là ```[target_size, target_size]``` bởi vì mask là hình ảnh dưới dạng màu xám.

![IMG](https://github.com/ficstkeyfx/Kvasir-SEG-preproc/blob/dev/image/img.png?raw=true)

#### Phần 2: Data augmentation

- Dữ liệu sẽ được gia tăng bằng phương pháp data augmentation

- Dữ liệu hình ảnh và mask đầu vào sẽ được thay đổi độ sáng, độ tương phản, độ bão hòa và độ màu ```hue``` để gia tăng thêm dữ liệu dành để huấn luyện mô hình

#### Phần 3: Tạo tf Dataset 

- Từ các phương pháp ở trên sau đó tạo dữ liệu ```tf.Dataset``` để huấn luyện mô hình

