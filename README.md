# **Phân loại tin nhắn spam với Naive Bayes**

## 1. Giới thiệu bài toán   
- **Text Classification (Phân loại văn bản)** là một trong những bài toán phổ biến trong lĩnh vực Machine Learning và Natural Language Processing. Trong đó, nhiệm vụ của chúng ta là xây dựng một chương trình có khả năng phân loại văn bản vào các phân lớp do chúng ta quy định. Các ứng dụng phổ biến liên quan đến loại chương trình này có thể kể đến phát hiện
 các bình luận tiêu cực trên không gian mạng, các đánh giá tích cực của sản phẩm...
- Project này xây dựng 1 chương trình classification liên quan đến việc phân loại một tin nhắn là spam hay không, sử dụng thuật toán ***Naive Bayes*** 

    - **Input**: 1 đoạn tin nhắn bất kì (text)
    - **Output**: Tin nhắn có là spam hay không spam

## 2. Tải bộ dữ liệu
- Có thể tại bộ dữ liệu tại [đây](https://drive.google.com/file/d/1N7rk-kfnDFIGMeX0ROVTjKh71gcgx-7R/view?usp=sharing) hoặc chạy lệnh sau *(google colab)*
```
    !gdown--id 1N7rk-kfnDFIGMeX0ROVTjKh71gcgx-7R
```
- Bộ dữ liệu gồm 2 cột:
    1. Category: gồm 2 nhãn là Ham và Spam, với ý nghĩa như sau:

        • Ham: Là những tin nhắn bình thường, không có mục đích quảng cáo hoặc lừa đảo hoặc nói cách khác là người nhận mong muốn nhận được.

        • Spam: Là những tin nhắn không mong muốn, thường có mục đích quảng cáo sản phẩm, dịch vụ, hoặc lừa đảo.

    2. Message: là những nội dung bên trong một Messages.

## 3. Import các thư viện cần thiết và đọc dữ liệu
*(Xem tại các mục 1 và 2 trong file text_classification.ipynb)*

## 4. Tiền xử lý dữ liệu
#### 4.1 Tiền xử lý dữ liệu đặc trưng
- ***Lowercase***: chuyển tất cả message thành chữ thường
- ***Punctuation Removal***: xóa dấu câu
- ***Tokenize***: chuyển message thành token
- ***Remove Stopword***: xóa các từ không quan trọng (trong tiếng anh)
- ***Stemming***: chuyển các từ về dạng nguyên thể
#### 4.2. Tiền xử lý dữ liệu nhãn
- chuyển 2 nhãn *ham*, *spam* về dạng 0, 1 bằng:
```
    le = LabelEncoder()
    y = le.fit_transform(labels)
```

## 5. Chia bộ dữ liệu train/val/test:
- Chia bộ dữ liệu thành các tập train/val/test với tỉ lệ tương ứng 7/2/1

## 6. Huấn luyện mô hình
## 7. Đánh giá mô hình
## 8. Thực hiện dự đoán
- Dự đoán cho các message mới là spam hay không spam. Cần thực hiện lại các bước *Tiền xử lý, tạo đặc trưng* cho message mới. Truyền message mới vào cho mô hình. Mô hình sẽ trả về kết quả dạng 0, 1. Do đó, gọi hàm *inverse_transform()* để chuyển về nhãn *Ham* hoặc *Spam*