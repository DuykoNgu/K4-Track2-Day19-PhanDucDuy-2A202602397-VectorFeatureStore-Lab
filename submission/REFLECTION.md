# Reflection — Lab 19

**Tên:** Phan Đức Duy

**Cohort:** A20-K4

**Path:** Lite

Trên 50 truy vấn, hybrid đạt Precision@10 78,6%, cao hơn BM25 (77,8%) và vector (73,2%). Với `exact`, BM25 và hybrid cùng đạt 96,7%; với `mixed`, hybrid đạt 100%. Trên `paraphrase`, embedding Lite `bge-small-en` yếu với tiếng Việt: vector đạt 24%, BM25 33,3%, hybrid 32%. Vì vậy cần chọn embedding theo ngôn ngữ và đo trên dữ liệu thực.

Không cần hybrid khi query chứa thuật ngữ chính xác và BM25 đã đủ tốt, hoặc khi một retriever đơn lẻ đạt chất lượng với chi phí và độ trễ thấp hơn. Với paraphrase tiếng Việt, nên thử embedding đa ngôn ngữ rồi đo lại.

Điều bất ngờ nhất: post-filter chỉ đạt recall 0,00 khi filter còn 3,8% corpus, còn filtered-ANN giữ 1,00. Cache thiếu namespace cũng làm lộ câu trả lời giữa tenant.
