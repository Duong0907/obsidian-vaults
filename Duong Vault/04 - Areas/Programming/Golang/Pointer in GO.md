## Lợi ích
- Chương trình sẽ nhanh và tiết kiệm bộ nhớ hơn, do không cần copy data
## Bất lợi
- Chậm hơn khi truyền con trỏ vào hàm thay vì truyền giá trị
	- Do garbage collector trong heap
	- Escape analysis xem xét xem biến còn trong stack hay nằm trong heap
## Stack and Heap
- Không nên quyết định sử dụng con trỏ dựa vào hiệu suất, mà dựa vào sự trong sạch và tính đúng đắn của code

> Sharing down stays on the **stack**
> Sharing up escapes to the **heap**

- **Sharing down** là truyền tham số vào hàm. Ví dụ:
```go
func main() {
	n := 10
	m := square(n)
	fmt.Println(m)
}

func square(n int) int {
	return n * n
}
```
hoặc
```go
func main() {
	n := 10
	m := square(&n)
	fmt.Println(m) // Result: 100
}

func square(n *int) int {
	return (*n) * (*n)
}
```
- **Sharing up** là hàm trả về con trỏ. Ví dụ: 
```go
func main() {
	n := 10
	m := square(&n)
	fmt.Println(*m) // Result: 100
}

func square(n *int) *int {
	ans := (*n) * (*n)
	return &ans
}
```

## Tóm lại
- Nếu compiler không thể chứng minh được biến sẽ không được tham chiếu sau khi hàm trả về, thì biến sẽ được lưu trong heap (sẽ được garbage collector thu hồi) để tránh các lỗi về sau.


## Khi nào sử dụng con trỏ
- Copy một struct lớn
- Dùng trong receiver
- Tính nhất quán: ta sử dụng tất cả receiver để tất cả các receiver được nhất quán và dễ đọc code.
- Dùng để đánh dấu một biến là không có giá trị (chứ không phải giá trị 0). Ví dụ:
```go
	var n int = 0 // Có giá trị nhưng = 0
	var m *int = nil // Không có giá trị
```
