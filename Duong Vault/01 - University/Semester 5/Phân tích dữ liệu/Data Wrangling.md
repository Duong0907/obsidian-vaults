
## Data Wrangling
- Gom nhóm:
	- Theo một chiều: `df.group_by()`
	- Theo dạng bảng: `df.pivot()`
- Tìm tương quan:
	- Giữa 1 biến liên tục và 1 biến rời rạc: `sns.boxplot`, overlap càng ít thì tương quan càng nhiều
	- Giữa 2 biến liên tục: scatter plot (`sns.regplot()`), pearson correlation
		- pearson_coef (-1 < pearson_coef < 1): tính thuận nghịch của tương quan
		- p_value (-1 < p_value < 1): tính mạnh yếu của tương quan (càng gần 0 càng mạnh)
	- Giữa 2 biến rời rạc và 1 biến liên tục: `plt.colorbar()`
	- Giữa 2 biến rời rạc: X<sup>2</sup>
	- Giữa tất cả các biến (liên tục): `df.corr()`
```python
pearson_coef, p_value = scipy.stats.pearsonr() # truyền vào 2 series
```

- Phân tích ANOVA: xem xét khả năng ảnh hưởng của các nhóm trong cùng 1 **biến phân loại**
	- f_value: khả năng ảnh hưởng mạnh yếu giữa các biến phân loại và mục tiêu (càng lớn càng mạnh)
	- p_value: mức độ tự tin, kết quả thu được có thể dùng trong thống kê không
```python
fvalue, pvalue = scipy.stats.f_oneway() # truyền vào các group
```
- Đếm số lượng của từng giá trị của biến rời rạc: `pd.Series.value_counts()`
- So sánh `sns.boxplot` và `plt.boxplot`
	- `sns.boxplot()` truyền vào df và 2 tên cột của df
	- `plt.boxplot()` truyền vào 2 Series

