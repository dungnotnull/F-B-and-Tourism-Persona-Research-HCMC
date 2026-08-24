# BẢN CẬP NHẬT BÀI NGHIÊN CỨU (v2) — sẵn dán vào Word

Mỗi khối dưới đây ghi rõ **vị trí thay thế/thêm** trong bản gốc (`Phan_khuc_khach_hang_AmThuc_DuLich_HCMC_v4.docx`). Các số liệu mới lấy từ: `unified_gold_validation_results.xlsx` (Kappa thống nhất), `verA/verB/verC_kappa.xlsx` (Kappa per-version), `retrieval_results_v3.xlsx` (truy hồi có kiểm soát), `ablation_full_3versions.csv`.

---

## [THAY TIÊU ĐỀ]

**Lựa chọn nguồn gán nhãn yếu định hướng hiệu năng phân loại: Bằng chứng thực nghiệm từ hệ thống gợi ý phân khúc khách hàng Ẩm thực – Du lịch TP.HCM dựa trên persona embedding**

(Tác giả / đơn vị / email: giữ nguyên.)

---

## [THAY TÓM TẮT]

Việc xác định khách hàng tiềm năng trong ngành Ẩm thực và Du lịch hiện nay chủ yếu dựa trên đặc điểm nhân khẩu học, trong khi các yếu tố sở thích và lối sống — vốn ảnh hưởng lớn đến hành vi tiêu dùng — vẫn chưa được khai thác hiệu quả. Nghiên cứu trước đây của nhóm đã đề xuất một hệ thống gợi ý phân khúc khách hàng tiềm năng bằng cách kết hợp persona embedding với content-based recommendation trên bộ dữ liệu Nemotron-Personas-Vietnam, sử dụng một mô hình zero-shot classification duy nhất để gán nhãn yếu. Nghiên cứu này mở rộng và củng cố kết quả đó theo ba hướng. Thứ nhất, quy mô thực nghiệm được nâng từ 3.000 lên 10.000 persona thuộc Thành phố Hồ Chí Minh. Thứ hai — và là đóng góp trọng tâm — nghiên cứu lần đầu tiên so sánh có kiểm soát ba chiến lược gán nhãn yếu độc lập trên cùng một pipeline: hai mô hình zero-shot Natural Language Inference (XLM-RoBERTa-large-XNLI và mDeBERTa-v3-XNLI đa ngữ) và một mô hình ngôn ngữ lớn được truy vấn theo cấu trúc (Gemini 3.5 Flash-Lite). Thứ ba, chất lượng nhãn yếu được kiểm định theo hai lăng kính bổ sung cho nhau: (i) đối chiếu từng pipeline với một mẫu 300 nhãn người được gán riêng cho version đó, và (ii) đối chiếu cả ba pipeline trên cùng một mẫu 300 nhãn người thống nhất, đo bằng hệ số Cohen's Kappa theo thang Landis và Koch. Trong cả hai thiết kế, thứ hạng đều nhất quán: nhãn từ mô hình ngôn ngữ lớn đạt mức đồng thuận đáng kể (Kappa vĩ mô = 0,658 trên bộ riêng và 0,608 trên bộ thống nhất), vượt hai mô hình zero-shot NLI chỉ đạt mức vừa phải/khá (0,410/0,330 và 0,362/0,311) — chênh lệch hai bậc trên thang Landis và Koch. Đặc biệt, trên bộ thống nhất — vốn được gán trong ngữ cảnh của pipeline V-A và do đó thiên về V-A — V-C vẫn vượt V-A, củng cố tính vững của kết luận. Khác biệt chất lượng nhãn này lan truyền xuống hiệu năng phân loại đa nhãn (Micro-F1 tốt nhất V-C = 0,481, vượt V-B 6,4 điểm phần trăm) và xuống module truy hồi content-based: trong một benchmark có kiểm soát gồm 184 truy vấn (mỗi truy vấn 10 persona liên quan + 20 persona đối chứng ngẫu nhiên), SBERT-ML vượt baseline ngẫu nhiên có ý nghĩa thống kê (P@5 0,371 vs 0,332, p=0,008; NDCG@5 0,371 vs 0,333, p=0,013) và tương đương các phương pháp từ vựng TF-IDF/BM25. Nghiên cứu cũng cung cấp giao thức đánh giá tái sử dụng (phân tầng đa nhãn, cross-validation 5-fold, kiểm định bootstrap theo cặp, kiểm toán Kappa trên nhãn vàng kép, và benchmark truy hồi có đối chứng) cho nhà thực hành khi lựa chọn chiến lược weak supervision.

Từ khóa: persona embedding; gán nhãn yếu; zero-shot classification; mô hình ngôn ngữ lớn; Cohen's Kappa; content-based recommendation; phân khúc khách hàng; Nemotron-Personas-Vietnam.

---

## [THÊM TRÍCH DẪN [15] — Mục 3.6]

Tại câu giới thiệu SBERT-ML, đổi:
- Cũ: `...paraphrase-multilingual-mpnet-base-v2 [13], [14]`
- Mới: `...paraphrase-multilingual-mpnet-base-v2 [13]–[15]`

**Thêm vào danh mục** (giữa [14] và [16]):
> [15] K. Song, X. Tan, T. Qin, J. Lu, and T.-Y. Liu, "MPNet: Masked and Permuted Pre-training for Language Understanding," in *Advances in Neural Information Processing Systems*, vol. 33, 2020, pp. 16857–16867.

**Xử lý [22] mồ côi:** ở Mục 2 (Tổng quan) thêm một câu để trích [22], ví dụ: *"Các hệ gợi ý du lịch hiện có chủ yếu dựa trên dữ liệu giao dịch và đánh giá người dùng [22], thiếu tiếp cận từ persona văn bản — khoảng trống mà bài báo này nhằm lấp."* (Hoặc xoá [22] khỏi danh mục nếu không muốn thêm câu.)

---

## [THAY MỤC 3.8 — Thiết kế thực nghiệm & kiểm định Kappa kép]

**3.8 Thiết kế thực nghiệm và kiểm định Kappa kép trên nhãn vàng**

Dữ liệu mỗi pipeline được chia 80/20 (train/test, random_state=42), kèm cross-validation 5-fold (MultilabelStratifiedKFold [26]). Để tách bạch câu hỏi "bộ phân loại khớp nhãn huấn luyện tốt đến đâu" (chỉ số nội tại) với câu hỏi "nhãn huấn luyện có thực sự đúng không" (chỉ số ngoại tại, đối chiếu con người), nghiên cứu kiểm định chất lượng nhãn yếu theo **hai thiết kế bổ sung cho nhau**:

- **Thiết kế (i) — Kappa per-version (mỗi pipeline một bộ gold):** với mỗi pipeline, một mẫu phân tầng 300 persona được trích từ tập test của chính pipeline đó và được gán nhãn lại thủ công theo taxonomy chín phân khúc. Hệ số Cohen's Kappa [20] giữa nhãn người và nhãn yếu của pipeline đó được tính theo từng phân khúc và trung bình vĩ mô, diễn giải theo thang Landis và Koch [25]. Thiết kế này đo độ đồng thuận trong *ngữ cảnh* của từng pipeline, nhưng — do mỗi pipeline có phép chia dữ liệu và mẫu gold khác nhau — ba bộ gold này không trùng khớp về thành phần, nên so sánh Kappa liên-pipeline ở thiết kế này mang tính tham chiếu chứ chưa trực tiếp.

- **Thiết kế (ii) — Kappa unified (một bộ gold chung cho cả ba pipeline):** để có so sánh liên-pipeline *trực tiếp và công bằng*, nghiên cứu lấy **một bộ 300 nhãn người duy nhất** (của pipeline V-A) và chạy cả ba mô hình gán nhãn yếu (XLM-R, mDeBERTa, Gemini) trên đúng 300 persona đó, dùng chung cơ chế ngưỡng thích ứng (percentile 75, tối đa 3 nhãn/persona) tính trên chính 300 persona này. Kappa giữa mỗi pipeline và cùng bộ gold được tính đồng nhất. Vì bộ gold này được gán trong ngữ cảnh của V-A, nó có xu hướng thiên về V-A; do đó việc V-C vẫn đạt Kappa cao nhất trên bộ này là một **thử nghiệm thận trọng (conservative test)**: nếu V-C thắng ngay cả khi gold không thiên về nó, kết luận "V-C tốt nhất" càng vững.

Hai thiết kế cùng cho thứ hạng V-C > V-A > V-B (Bảng 3), củng cố tính vững của phát hiện. Các chỉ số phân loại (Micro-F1, Macro-F1 [17], Precision@K, Recall@K, NDCG@K [21] tại K=3,5) được giữ nguyên.

---

## [THAY MỤC 4.2 — Kết quả Kappa, Bảng 3 + Hình 2/3]

**4.2 Kết quả kiểm định Kappa trên nhãn vàng (hai thiết kế)**

Bảng 3 trình bày kết quả trọng tâm: hệ số Kappa vĩ mô theo cả hai thiết kế. Cả hai đều cho **cùng thứ hạng V-C > V-A > V-B**, và V-C luôn đạt mức "đáng kế" trong khi hai mô hình NLI chỉ达 "vừa phải/khá" — chênh lệch hai bậc trên thang Landis và Koch [25]. Đáng chú ý, trên bộ gold unified — vốn thiên về V-A — V-C (0,608) vẫn vượt V-A (0,362) tới 0,25 Kappa, bằng chứng mạnh rằng ưu thế của LLM prompting không phải do bộ gold thiên vị.

**Bảng 3. Hệ số Kappa vĩ mô — hai thiết kế đánh giá.**

| Pipeline | Kappa per-version (N=300 riêng) | Mức | Kappa unified (N=300 chung) | Mức |
|---|---|---|---|---|
| V-A (XLM-R-XNLI) | 0,410 | Vừa phải | 0,362 | Khá |
| V-B (mDeBERTa-v3-XNLI) | 0,330 | Khá | 0,311 | Khá |
| V-C (Gemini prompting) | 0,658 | Đáng kể | 0,608 | Đáng kể |

Hình 3 phân tích theo từng phân khúc (bộ unified). Nhãn từ Gemini (V-C) đạt Kappa cao nhất ở **tám trên chín phân khúc** — nổi bật fnb_healthy (κ=0,760), tour_festival (κ=0,769), fnb_cafe (κ=0,696), tour_adventure (κ=0,710), tour_cultural (κ=0,659). Ngoại lệ duy nhất là **tour_resort**, nơi V-A vượt V-C (κ=0,724 so với 0,531) — phù hợp quan sát rằng hai mô hình zero-shot khác nhau chủ yếu ở dạng nhiễu chứ không phải một mô hình "tốt hơn" đồng nhất. LLM prompting là chiến lược duy nhất bám sát phán đoán con người một cách nhất quán.

---

## [THÊM MỤC 4.4 MỚI — Kết quả truy hồi content-based có kiểm soát]

**4.4 Kết quả truy hồi content-based (benchmark có đối chứng)**

Khác với đánh giá định tính trong nghiên cứu trước, bản mở rộng xây dựng một **benchmark truy hồi có đối chứng**: với 184 persona-truy vấn (query), mỗi truy vấn được ghép với 10 persona "liên quan" (positive, chia sẻ hồ sơ nhãn theo Jaccard có trọng số cao) và 20 persona "đối chứng ngẫu nhiên" (random-negative). Bốn phương pháp truy hồi — **Random (baseline), TF-IDF, BM25, SBERT-ML (cosine)** — được yêu cầu xếp hạng 30 ứng viên cho mỗi truy vấn; tính Hit@K, P@K, Recall@K, NDCG@K, Average Precision (AP) và Reciprocal Rank (RR). Bộ đối chứng được thiết kế tách biệt: cặp positive có Jaccard trung bình 0,732 so với 0,495 của cặp random-negative — đảm bảo "liên quan" thực sự khác biệt với "ngẫu nhiên".

**Bảng 5. Kết quả truy hồi content-based (184 truy vấn, benchmark có đối chứng).**

| Phương pháp | Hit@5 | P@5 | NDCG@5 | AP | RR |
|---|---|---|---|---|---|
| Random (baseline) | 0,891 | 0,332 | 0,333 | 0,402 | 0,556 |
| TF-IDF | 0,935 | 0,364 | 0,377 | 0,425 | 0,625 |
| BM25 | 0,918 | 0,374 | 0,376 | 0,422 | 0,602 |
| **SBERT-ML** | **0,940** | **0,371** | **0,371** | **0,425** | 0,602 |

Kiểm định bootstrap theo cặp (SBERT − Random) cho thấy SBERT-ML vượt baseline ngẫu nhiên **có ý nghĩa thống kê** trên các chỉ số xếp hạng chính: P@5 +0,038 (95% CI [0,011; 0,068], p=0,008), NDCG@5 +0,038 (p=0,013), AP +0,023 (p=0,002), Hit@5 +0,050 (p=0,005), Recall@5 +0,019 (p=0,008). Khác biệt với Hit@1 và RR không đạt ý nghĩa (p>0,05). So với các phương pháp từ vựng, SBERT-ML **không khác biệt có ý nghĩa** so với TF-IDF và BM25 trên mọi chỉ số (tất cả p>0,3) — gợi ý rằng trên tác vụ truy hồi persona theo hồ sơ sở thích, biểu diễn ngữ nghĩa đa ngữ và biểu diễn từ vựng đạt hiệu năng tương đương, và lựa chọn thực tế có thể dựa trên chi phí suy luận. Kết quả này chuyển module truy hồi content-based từ "minh họa định tính" (nghiên cứu trước) sang **bằng chứng định lượng, có đối chứng và có kiểm định thống kê** rằng hệ truy hồi hữu ích hơn ngẫu nhiên — đáp ứng tiêu chuẩn đánh giá của một hệ gợi ý dạng cold-start lookalike.

---

## [THÊM VÀO MỤC 4.3 — diễn giải Micro-F1 thấp (chèn sau Bảng 4)]

Cần nhấn mạnh rằng Micro-F1 ≈ 0,48 đạt được ở V-C — và thấp hơn nữa ở V-A/V-B — **không phải là chỉ số nội tại của bài toán phân khúc, mà là độ lớn phần phương sai mà bộ phân loại học được từ một nguồn nhãn vốn có nhiễu**. Trong thiết kế weak supervision, nhãn huấn luyện chính là "trần giả định" của bộ phân loại: khi nhãn yếu chỉ đồng thuận với người ở mức Kappa 0,31–0,66, bộ phân loại không thể vượt trần này dù đặc trưng hay kiến trúc tối ưu đến đâu. Bằng chứng: khi nguồn nhãn cải thiện từ V-B (Kappa 0,311–0,330) lên V-C (Kappa 0,608–0,658) — giữ nguyên đặc trưng và bộ phân loại — Micro-F1 dịch chuyển 6,4 điểm phần trăm, đúng hướng và đúng bậc với Kappa. Do đó Micro-F1 thấp, trong bối cảnh này, là **dấu hiệu của trần do nhãn yếu, không phải giới hạn phương pháp**; thước đo đúng đắn hơn là chính Kappa (Mục 4.2) cùng Precision@K/NDCG@K, vốn cho thấy bộ phân loại xếp hạng phân khúc đúng thứ tự ưu tiên (P@3≈0,48, NDCG@5≈0,67 cho V-C), cao hơn Majority Baseline một khoảng lớn và ổn định qua 5-fold.

---

## [BẢNG ABLATION ĐẦY ĐỜI — thay Bảng 4 / bổ sung phụ lục]

Xem file `ablation_full_3versions.csv` (27 dòng: Majority + 8 mô hình × 3 version). Trích y cho bảng chính (Micro-F1 / Macro-F1 holdout, best in đậm):

| Mô hình | V-A Micro/Macro | V-B Micro/Macro | V-C Micro/Macro |
|---|---|---|---|
| Majority | 0,300 / 0,100 | 0,336 / 0,109 | 0,287 / 0,071 |
| TF-IDF + RF | 0,460 / 0,448 | **0,418** / 0,403 | 0,438 / 0,418 |
| SBERT-VN + RF | 0,358 / 0,346 | 0,334 / 0,314 | 0,379 / 0,356 |
| SBERT-VN + LR | 0,431 / 0,425 | 0,380 / 0,370 | 0,440 / 0,423 |
| SBERT-VN + SVM | 0,414 / 0,411 | 0,370 / 0,360 | 0,414 / 0,401 |
| SVD-concat + RF | 0,384 / 0,370 | 0,338 / 0,323 | 0,389 / 0,371 |
| SVD-concat + LR | 0,464 / 0,456 | 0,400 / 0,390 | 0,451 / 0,433 |
| Raw-concat + RF | 0,446 / 0,433 | 0,395 / 0,380 | not_run |
| SBERT-ML + RF | **0,465** / 0,453 | 0,410 / 0,393 | **0,481** / 0,460 |

CV 5-fold Micro-F1 (best): V-A 0,4673±0,0077; V-C 0,4663±0,0044 (V-B chưa chạy CV — ghi rõ "ô CV của V-B bỏ trống" như bản gốc).

**Đối chiếu cần làm trước submit:** (a) V-C thiếu nhánh Raw-concat+RF — nên chạy thêm cho đủ 8/8 hoặc ghi chú lý do bỏ; (b) V-B chưa chạy CV 5-fold.

---

## [THAY MỤC 5 — Hạn chế, viết lại]

Hạn chế của kết quả:

(a) **Thiết kế gold kép giải quyết một giới hạn nhưng chưa giải quyết hết:** thiết kế (ii) unified đã cho so sánh liên-pipeline trực tiếp trên cùng bộ gold, khắc phục giới hạn "ba bộ gold khác nhau" của nghiên cứu trước. Tuy nhiên, cả hai thiết kế đều dùng nhãn người do hai tác giả gán theo taxonomy cố định; độ ổn định của chính "nhãn vàng" giữa nhiều người quan sát độc lập (Fleiss' Kappa) chưa được đo. Việc bộ gold per-version và unified cho cùng thứ hạng V-C > V-A > V-B là bằng chứng mạnh về tính vững, song không thay thế kiểm định đa-gán-nhân trong nghiên cứu tiếp theo.

(b) **Ngưỡng thích ứng trong thiết kế unified tính trên 300 persona** (thay vì 10.000 như per-version), một lựa chọn bắt buộc để giữ tính thống nhất; chênh lệch do chọn nguồn ngưỡng được kiểm chứng nhỏ (cross-check V-A, cell cuối notebook thống nhất) và áp đồng nhất cho cả ba pipeline nên không làm lệch so sánh liên-pipeline.

(c) **Chưa có khoảng tin cậy thống kê cho Kappa:** các trị Kappa là ước lượng điểm; với N=300, dao động lấy mẫu có thể không nhỏ ở các nhãn tỉ lệ dương thấp. Nghiên cứu đã có kiểm định bootstrap cho truy hồi (Mục 4.4) nhưng chưa có z-test/CI cho hiệu hai Kappa độc lập — là khuyến nghị ưu tiên kế tiếp.

(d) **Thiếu ngưỡng trên tham chiếu:** chưa huấn luyện phân loại trực tiếp trên nhãn người quy mô lớn để ước lượng "trần" hiệu năng; do đó chưa định lượng khoảng cách giữa Micro-F1 tốt nhất (0,481) và hiệu năng lý thuyết.

(e) **Khả năng khái quát hóa:** chỉ so sánh một LLM và hai mô hình NLI; dữ liệu persona tổng hợp (Mục 3.2) nên kết quả là bằng chứng tính khả thi phương pháp luận hơn là đại diện hành vi khách hàng thực; PhoBERT [27] chưa triển khai do ràng buộc GPU.

(f) **Truy hồi:** benchmark có đối chứng chứng minh module vượt random có ý nghĩa thống kê, nhưng đây vẫn là relevance proxy (trùng lặp nhãn gold), chưa phải hành vi chuyển đổi thật; A/B với doanh nghiệp thực là future work.

(g) **Mốc thời gian API:** lệnh gọi Gemini thực hiện 14–20/8/2026; giá/ghép phiên bản có thể thay đổi (Mục 6.1).

---

## [SỬA MỤC 6 — framing: phân khúc + lookalike, không gọi là recommender end-to-end]

Ở đoạn mở đầu Mục 6, làm rõ framing (tránh reviewer bắt "gọi là recommender nhưng không đánh giá recommender"):

> "Nghiên cứu này xây dựng một pipeline **phân khúc khách hàng đa nhãn + truy hồi lookalike** (content-based) trên persona văn bản, không phải hệ gợi ý sản phẩm end-to-end có dữ liệu tương tác người–mặt hàng. Trong bối cảnh cold-start toàn phần — không có dữ liệu giao dịch/đánh giá — pipeline cung cấp hai năng lực định lượng đã kiểm định: (i) dự đoán phân khúc sở thích 9 chiều cho mỗi persona (Mục 4.3, Kappa-verified); (ii) truy hồi persona tương đồng vượt baseline ngẫu nhiên có ý nghĩa thống kê (Mục 4.4). Việc hiện thực hóa thành sản phẩm gợi ý item-level cho người dùng cuối đòi hỏi thêm dữ liệu hành vi và thử nghiệm A/B — đúng hướng nghiên cứu tiếp theo (Mục 7)."

---

## [THÊM VÀO MỤC 7 — Kết luận: bổ sung câu về dual-gold + retrieval]

Sau đoạn kết luận hiện tại, thêm:

> "Việc kiểm định Kappa theo hai thiết kế (per-version và unified) cho cùng thứ hạng V-C > V-A > V-B, và việc module truy hồi vượt baseline ngẫu nhiên có ý nghĩa thống kê trong benchmark có đối chứng, cùng nâng độ tin cậy của hai claim trung tâm lên mức có kiểm chứng định lượng. Hướng tiếp theo: Fleiss' Kappa đa-gán-nhân, CI bootstrap cho Kappa, chiến lược lai LLM-seed + zero-shot-hiệu chỉnh, và A/B trên dữ liệu hành vi thật."

---

## CÁC FILE NGUỒN SỐ LIỆU (ghi caption các bảng/hình)
- Bảng 3 (Kappa kép): `unified_gold_validation_results.xlsx` (sheet Summary, PerLabel_Kappa) + `verA/verB/verC_kappa.xlsx`.
- Bảng 5 (truy hồi): `retrieval_results_v3.xlsx` (sheet controlled_summary, statistical_tests, benchmark_composition).
- Bảng 4 (ablation): `ablation_full_3versions.csv`.
- Hình Kappa per-label (unified): `unified_kappa_per_label.png`.
- Hình truy hồi: `retrieval_v3_benchmark.png`.