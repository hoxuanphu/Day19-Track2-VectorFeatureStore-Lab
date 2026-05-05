# Reflection — Lab 19

**Tên:** _<Hồ Xuân Phú>_
**Cohort:** _<A20-K1>_
**Path đã chạy:** _<lite>_

---

## Câu hỏi (≤ 200 chữ)

Trên bộ golden set 50 queries:
- **Exact**: BM25 thường thắng hoặc ngang ngửa Hybrid vì query chứa từ khóa kỹ thuật chính xác có trong corpus.
- **Paraphrase**: Vector (Semantic) thắng vì BM25 không tìm thấy từ khóa trùng khớp. Tuy nhiên, với model `bge-small-en` ở bản Lite, độ chính xác có thể chưa cao do hạn chế về ngôn ngữ Tiếng Việt.
- **Mixed**: Hybrid thắng rõ rệt nhờ kết hợp được cả tín hiệu từ khóa và ngữ nghĩa, mang lại kết quả hội tụ nhất.

**Tại sao?** Hybrid (RRF) giúp bù đắp điểm yếu của từng mode đơn lẻ: BM25 giải quyết bài toán "từ hiếm/tên riêng", còn Vector giải quyết bài toán "đồng nghĩa/diễn đạt khác".

**Khi nào không dùng hybrid?** 
1. Hệ thống yêu cầu độ trễ cực thấp (ultra-low latency) mà việc chạy song song hai engine là quá tốn kém.
2. Dữ liệu tìm kiếm rất đặc thù (ví dụ: tìm mã lỗi, mã sản phẩm) chỉ cần BM25 là đủ.
3. Khi giới hạn tài nguyên (vận hành Vector DB tốn kém hơn so với Full-text search đơn giản).

---

## Điều ngạc nhiên nhất khi làm lab này

Sự đơn giản nhưng hiệu quả bất ngờ của thuật toán RRF $1/(k+rank)$ — không cần huấn luyện lại model mà vẫn cải thiện rõ rệt chất lượng tìm kiếm tổng thể.


---

## Bonus challenge

- [ ] Đã làm bonus (xem `bonus/`)
- [ ] Pair work với: _<tên đồng đội nếu có>_
