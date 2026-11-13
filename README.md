# 📊 Product Performance & CR Optimization: TeddyWorld Case Study

## 🎯 1. Bối cảnh & Mục tiêu dự án

Dự án phân tích hiệu suất 4 sản phẩm của TeddyWorld (thương mại điện tử gấu bông) trên dữ liệu đơn hàng, hoàn tiền và hành vi duyệt web. Thay vì chỉ nhìn doanh thu gộp, dự án đo doanh thu thực tế sau hoàn tiền và tìm điểm nghẽn trong phễu chuyển đổi của từng sản phẩm.

**Mục tiêu chính:**

* 💰 **Phân tích doanh thu và hoàn tiền:** Tính doanh thu gộp, doanh thu thuần và tỷ lệ hoàn tiền theo sản phẩm.
* 📉 **So sánh phễu chuyển đổi theo sản phẩm:** Đối chiếu trải nghiệm khách hàng giữa `The Original Mr. Fuzzy` và `The Forever Love Bear`, từ trang `/products` đến khi mua hàng.
* 🚀 **Đề xuất tối ưu CR:** Gợi ý phân bổ ngân sách quảng cáo và cải thiện trang danh mục, giỏ hàng.

## 💻 2. Techstack (Công cụ sử dụng)

* **Ngôn ngữ:** `Python` 🐍
* **Xử lý dữ liệu:** `pandas`, `numpy`, `datetime`
* **Trực quan hóa dữ liệu:** `matplotlib` & `seaborn`
* **Môi trường:** `Google Colab`, `Jupyter Notebook` 📓

## 🗂️ 3. Dữ liệu

* `products.csv`: mã sản phẩm, ngày ra mắt, tên sản phẩm (4 sản phẩm).
* `order_items.csv`: từng dòng hàng với giá bán (`price_usd`) và giá vốn (`cogs_usd`).
* `order_item_refunds.csv`: số tiền hoàn theo từng dòng hàng.
* `website_pageviews.csv` và `website_sessions.csv`: lượt xem trang theo phiên truy cập.

## ⚙️ 4. Phương pháp

### Phần 1 – Doanh thu và hoàn tiền

* Gộp đơn hàng, sản phẩm và hoàn tiền; dòng hàng không hoàn tiền được gán số tiền hoàn bằng 0.
* **Gross Revenue** = tổng `price_usd`. **Net Revenue** = `price_usd` − `refund_amount_usd`.
* **Refund Rate** = số dòng hàng bị hoàn tiền / tổng số dòng hàng.

### Phần 2 – Phễu theo sản phẩm

* Hàm `get_funnel` đếm số session qua 4 bước: `/products` → trang chi tiết sản phẩm → `/cart` → `/thank-you-for-your-order`.
* Chỉ lấy các lượt xem sau ngày Love Bear ra mắt (2013-01-06 13:00:00) để so sánh công bằng, vì Mr. Fuzzy ra mắt trước.
* Chỉ số: CR lũy kế, Drop-off Rate và Step CR (so với bước liền trước).

## 💡 5. Insight chiến lược (Key Insights)

### 💰 5.1. Doanh thu và hoàn tiền

* Doanh thu gộp **$1.94M**, hoàn tiền **$85.3K**, doanh thu thuần **$1.85M**.
* **The Original Mr. Fuzzy** có doanh thu thuần cao nhất ($1.15M), vượt xa các sản phẩm còn lại, nhưng tỷ lệ hoàn tiền cao thứ 2 (**5.11%**).
* **The Birthday Sugar Panda** có tỷ lệ hoàn tiền cao nhất (**6.04%**) trong khi doanh thu thấp ⇒ cần xem lại chất lượng sản phẩm.
* **The Hudson River Mini bear** có tỷ lệ hoàn tiền thấp nhất (1.28%).

### 📉 5.2. Phễu chuyển đổi: Mr. Fuzzy vs Love Bear

* Cả hai cùng xuất phát từ 231,193 sessions tại `/products`.
* **Products → Xem chi tiết:** Mr. Fuzzy đạt **60.92%**, Love Bear chỉ **11.26%** ⇒ đây là điểm nghẽn khiến Love Bear có doanh thu thấp.
* **Xem chi tiết → Giỏ hàng:** Love Bear đạt **55.64%**, cao hơn Mr. Fuzzy (**42.98%**).
* **Giỏ hàng → Mua hàng:** Mr. Fuzzy **35.04%**, Love Bear **33.16%**. Cả hai đều thấp ⇒ cần kiểm tra quy trình checkout, chi phí vận chuyển, phương thức thanh toán và các yếu tố gây bỏ giỏ hàng.
* **CR lũy kế (Products → Mua hàng):** Mr. Fuzzy **9.17%**, Love Bear **2.08%**.

## 🚀 6. Khuyến nghị chiến lược (Recommendations)

### 🎯 1. Tập trung ngân sách quảng cáo vào Mr. Fuzzy

* Sản phẩm có doanh thu vượt trội và tỷ lệ chuyển đổi từ trang danh mục vào trang chi tiết cao, chứng tỏ sức hút khi khách lướt xem danh mục.

### 🖼️ 2. Cải thiện hiển thị Love Bear tại trang danh mục

* Thêm ưu đãi nổi bật hoặc hình ảnh bắt mắt hơn để giảm tỷ lệ thoát.

### 🛒 3. Giảm bỏ giỏ hàng và thử nghiệm giao diện

* Kiểm tra checkout, phí vận chuyển, phương thức thanh toán.
* Nghiên cứu các yếu tố giúp trang Love Bear có tỷ lệ thêm giỏ hàng cao, sau đó A/B testing giao diện cho Mr. Fuzzy.
* Xem lại chất lượng The Birthday Sugar Panda do tỷ lệ hoàn tiền cao.

## 📁 7. Cấu trúc notebook

* **Phần 1:** Phân tích doanh thu và hoàn tiền (Revenue & Refund Analysis).
* **Phần 2:** Phân tích phễu theo sản phẩm (Product-Specific Funnel).
* **Recommendation:** Đề xuất hành động.
