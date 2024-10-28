Khi clone về mà composer install không được thì chạy:
```
composer install --ignore-platform-reqs
```
Nếu không chạy được php artisan thì là do version php không phù hợp


### Cloning laravel project from GitHub
1. Run git clone <my-cool-project>
2. Run composer install
3. Run cp .env.example .env
4. Run php artisan key:generate
5. Run php artisan migrate
6. Run php artisan serve
7. Go to link localhost:8000

/////// Các file php, js, ảnh: 

Khánh Hiển thị danh sách sản phẩm + Tìm, lọc sản phẩm: view/user/product_list 

Giỏ hàng + Thanh toán + Quản lí đơn hàng + Hiển thị chi tiết sản phẩm: view/user/cart.php, view/user/product_detail 

Giới thiệu + Hướng dẫn + Trang chủ: view/shared, view/user/guide.php, view/homePage.php, view/homePage_login.php 

Huy 
Quản lý sản phẩm + Quản lí hạng mục: view/admin/category, view/admin/product 

Quản lí khách hàng + Quản lí khuyến mãi + Quản lí doanh thu: view/admin/coupon, view/admin/customer, view/admin/report Đăng nhập, đăng kí: view/auth 

Dương: view/error, view/user/purchase_history, public/assets/js, public/assets/svg, public/assets/image 

Trung: view/layout, database/migration, app/http/controllers, app/http/models, routes/web.php 

////// Các file css: tương tự (trong thư mục public/assets/css)



12/12
Hoàn thành database
Sửa lại toàn bộ giao diện (update mới nhất)
User (Dương): 
	- Hiển thị danh sách sản phẩm + Tìm, lọc sản phẩm, Hiển thị chi tiết sản phẩm
	- Giới thiệu + Hướng dẫn + Trang chủ

Admin (Trung):
	- Quản lý sản phẩm 
	- Quản lí hạng mục
	- Quản lý đơn hàng