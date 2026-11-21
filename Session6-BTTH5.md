# [Bài thực hành 5] Xây dựng Rubric để AI chấm điểm bài viết

## 1. Rubric dạng bảng (tổng 10 điểm)

| Tiêu chí | Điểm tối đa | Mức tốt (100%) | Mức khá (khoảng 70-80%) | Mức yếu (khoảng 30-50%) | Mức không đạt (0) |
|---|---|---|---|---|---|
| Đúng chủ đề | 2 | Toàn bộ bài bàn về vai trò của AI trong học tập của sinh viên đại học | Đúng chủ đề nhưng có 1-2 câu hoặc ý lạc sang vấn đề khác | Chỉ nhắc đến chủ đề thoáng qua, phần lớn nói chuyện khác | Lạc đề hoàn toàn |
| Nội dung và lập luận | 3 | Có luận điểm rõ, có luận cứ giải thích, phân tích cả lợi ích và hạn chế, kết luận từ lập luận | Có luận điểm và một số giải thích nhưng có ý chỉ nêu mà chưa phân tích | Chủ yếu liệt kê ý, thiếu giải thích hoặc mâu thuẫn | Không có luận điểm |
| Ví dụ minh họa | 2 | Ví dụ cụ thể, thực tế, gắn với học tập, minh họa đúng luận điểm | Có ví dụ nhưng chỉ cho một phần luận điểm hoặc còn chung chung | Ví dụ mơ hồ, không rõ liên quan | Không có ví dụ |
| Cấu trúc bài viết | 1,5 | Đủ mở - thân - kết, các ý sắp xếp logic, có từ nối chuyển ý | Có đủ ba phần nhưng chuyển ý chưa mượt hoặc phần kết yếu | Thiếu một phần hoặc ý sắp xếp lộn xộn | Không có cấu trúc |
| Ngữ pháp và diễn đạt | 1,5 | Gần như không lỗi, câu rõ ràng, văn phong phù hợp văn viết | Vài lỗi nhỏ (dùng từ khẩu ngữ, dấu câu) không cản trở việc hiểu | Nhiều lỗi làm khó hiểu | Lỗi dày đặc, không hiểu được |
| **Tổng** | **10** | | | | |

Quy tắc chấm: mỗi tiêu chí chấm theo bước 0,25 điểm; điểm không vượt điểm tối đa; tổng điểm bằng đúng tổng 5 điểm thành phần.

## 2. Prompt thiết lập vai trò người chấm

```text
# VAI TRÒ
Bạn là giảng viên chấm bài viết, công tâm và nhất quán. Bạn chấm theo Rubric, không chấm theo cảm tính.

# NHIỆM VỤ
Đọc bài viết của sinh viên trong thẻ <bai_viet> (đề bài: "Vai trò của AI trong hoạt động học tập của sinh viên đại học", khoảng 300 từ) và chấm theo Rubric trong thẻ <rubric>.

<rubric>
| Tiêu chí | Điểm tối đa |
| Đúng chủ đề | 2 |
| Nội dung và lập luận | 3 |
| Ví dụ minh họa | 2 |
| Cấu trúc bài viết | 1,5 |
| Ngữ pháp và diễn đạt | 1,5 |
| Tổng | 10 |
Mô tả mức điểm của từng tiêu chí: {dán bảng mức điểm ở mục 1}
</rubric>

# QUY TẮC BẮT BUỘC
1. KHÔNG thay đổi điểm tối đa (trọng số) của bất kỳ tiêu chí nào.
2. KHÔNG chấm theo cảm tính: mỗi điểm số phải dựa trên mô tả mức điểm trong Rubric.
3. MỖI điểm số phải kèm MINH CHỨNG: trích nguyên văn (một câu hoặc cụm từ ngắn) từ bài viết. Nếu không tìm được minh chứng cho điểm cao, phải hạ điểm và ghi "Không tìm thấy minh chứng".
4. KHÔNG đánh giá cao chỉ vì bài dài; độ dài không phải là tiêu chí và không cộng điểm.
5. Với mỗi lỗi hoặc điểm yếu: chỉ rõ vị trí và ĐỀ XUẤT cách sửa cụ thể.
6. Chấm theo bước 0,25 điểm; điểm không được vượt điểm tối đa; kiểm tra lại tổng trước khi trả lời.
7. Chỉ dựa vào nội dung bài viết, không suy đoán ý định của sinh viên, không viết lại toàn bộ bài.

# ĐỊNH DẠNG ĐẦU RA (đúng thứ tự)
1. Bảng chấm điểm: | Tiêu chí | Điểm tối đa | Điểm đạt | Mức |
2. Bảng đối chiếu: | Tiêu chí | Điểm | Minh chứng (trích nguyên văn) | Lý do |
3. Điểm mạnh (gạch đầu dòng, mỗi ý kèm minh chứng)
4. Điểm yếu và lỗi: | Lỗi | Vị trí | Cách sửa |
5. Đề xuất cải thiện (tối đa 3 gợi ý ưu tiên)
6. TỔNG ĐIỂM: X/10

<bai_viet>
{Dán bài viết của sinh viên}
</bai_viet>
```

## 3. Bài viết mẫu (khoảng 300 từ)

**Vai trò của AI trong hoạt động học tập của sinh viên đại học**

Trong những năm gần đây, trí tuệ nhân tạo (AI) đã trở thành một phần quen thuộc trong đời sống sinh viên đại học. Vậy AI đóng vai trò gì trong hoạt động học tập? Theo tôi, AI vừa là trợ lý hữu ích, vừa là công cụ cần sử dụng thận trọng.

Trước hết, AI giúp sinh viên tiết kiệm thời gian và tiếp cận kiến thức nhanh hơn. Khi gặp một khái niệm khó, sinh viên có thể nhờ AI giải thích bằng ngôn ngữ đơn giản hoặc đưa thêm ví dụ. Chẳng hạn, một sinh viên năm nhất ngành Công nghệ thông tin chưa hiểu con trỏ trong ngôn ngữ C có thể yêu cầu AI so sánh con trỏ với địa chỉ của một ngôi nhà, rồi hỏi tiếp cho đến khi hiểu. Ngoài ra, AI còn hỗ trợ kiểm tra lỗi chính tả, gợi ý dàn ý cho bài thuyết trình và tóm tắt tài liệu dài, nhờ vậy sinh viên có nhiều thời gian hơn cho việc suy nghĩ và thực hành.

Tuy nhiên, việc lạm dụng AI cũng để lại không ít hệ quả. Nếu chỉ sao chép câu trả lời, sinh viên sẽ dần mất khả năng tự suy nghĩ và tự giải quyết vấn đề. Nhiều bạn xài AI để làm bài hộ luôn, điều này dễ dẫn đến gian lận học thuật. Bên cạnh đó, AI đôi khi đưa ra thông tin sai nhưng trình bày rất tự tin, vì vậy sinh viên cần kiểm chứng lại bằng giáo trình hoặc nguồn đáng tin cậy. Nhiều bạn cũng dùng mạng xã hội quá nhiều nên bị phân tán sự chú ý.

Tóm lại, AI nên được xem là người hướng dẫn chứ không phải người làm bài thay. Sinh viên cần sử dụng AI có mục đích rõ ràng, luôn tự kiểm tra kết quả và giữ thói quen tự học. Chỉ khi đó AI mới thật sự phát huy vai trò tích cực trong học tập.

## 4. Kết quả AI chấm điểm

### 4.1. Bảng chấm điểm

| Tiêu chí | Điểm tối đa | Điểm đạt | Mức |
|---|---|---|---|
| Đúng chủ đề | 2 | 1,5 | Khá |
| Nội dung và lập luận | 3 | 2,5 | Khá |
| Ví dụ minh họa | 2 | 1,5 | Khá |
| Cấu trúc bài viết | 1,5 | 1,5 | Tốt |
| Ngữ pháp và diễn đạt | 1,5 | 1,0 | Khá |
| **Tổng** | **10** | **8,0** | |

### 4.2. Bảng đối chiếu tiêu chí - điểm số - minh chứng

| Tiêu chí | Điểm | Minh chứng (trích từ bài) | Lý do |
|---|---|---|---|
| Đúng chủ đề | 1,5/2 | Câu mở: "Vậy AI đóng vai trò gì trong hoạt động học tập?" (bài bám đề). Câu lạc đề: "Nhiều bạn cũng dùng mạng xã hội quá nhiều nên bị phân tán sự chú ý." | Gần như toàn bài đúng chủ đề, trừ 0,5 vì một câu chuyển sang mạng xã hội, không liên quan đến AI |
| Nội dung và lập luận | 2,5/3 | "AI giúp sinh viên tiết kiệm thời gian..." (lợi ích); "sinh viên sẽ dần mất khả năng tự suy nghĩ..." (hạn chế); "AI nên được xem là người hướng dẫn chứ không phải người làm bài thay" (kết luận) | Có luận điểm hai mặt và kết luận rút ra từ lập luận; trừ 0,5 vì ý "gian lận học thuật" chỉ nêu mà chưa giải thích hay phân tích |
| Ví dụ minh họa | 1,5/2 | "một sinh viên năm nhất ngành Công nghệ thông tin chưa hiểu con trỏ trong ngôn ngữ C có thể yêu cầu AI so sánh con trỏ với địa chỉ của một ngôi nhà" | Ví dụ cụ thể, đúng luận điểm lợi ích; trừ 0,5 vì phần hạn chế (thông tin sai, mất khả năng tự suy nghĩ) không có ví dụ |
| Cấu trúc bài viết | 1,5/1,5 | Mở bài ("Trong những năm gần đây..."), từ nối "Trước hết", "Tuy nhiên", "Bên cạnh đó", kết bài "Tóm lại..." | Đủ mở - thân - kết, chuyển ý mượt; câu lạc đề đã bị trừ ở tiêu chí chủ đề nên không trừ lặp ở đây |
| Ngữ pháp và diễn đạt | 1,0/1,5 | "Nhiều bạn xài AI để làm bài hộ luôn, điều này dễ dẫn đến gian lận học thuật." | Dùng khẩu ngữ ("xài", "luôn", "làm bài hộ") không phù hợp văn viết, và hai ý nối bằng dấu phẩy (lỗi dính câu); các câu còn lại rõ ràng, đúng ngữ pháp |
| **Tổng** | **8,0/10** | | 1,5 + 2,5 + 1,5 + 1,5 + 1,0 = 8,0 |

## 5. Nhận xét và đề xuất cải thiện

**Điểm mạnh**
- Lập luận hai mặt rõ ràng (lợi ích và hạn chế), kết luận gắn với lập luận: "AI nên được xem là người hướng dẫn chứ không phải người làm bài thay".
- Ví dụ về con trỏ trong ngôn ngữ C cụ thể, gần gũi với sinh viên.
- Cấu trúc ba phần mạch lạc, dùng từ nối hợp lý.

**Điểm yếu và cách sửa**

| Lỗi | Vị trí | Cách sửa |
|---|---|---|
| Câu lạc đề | Đoạn 3, câu cuối: "Nhiều bạn cũng dùng mạng xã hội..." | Xóa câu này hoặc thay bằng ý về AI, ví dụ: "Dùng AI thường xuyên để tra cứu cũng khiến sinh viên ngại tự tìm tài liệu." |
| Ý chưa được phân tích | Đoạn 3: "điều này dễ dẫn đến gian lận học thuật" | Thêm một câu giải thích hậu quả, ví dụ: bài nộp không phản ánh năng lực thật nên sinh viên có thể bị xử lý kỷ luật và hụt kiến thức nền |
| Thiếu ví dụ cho phần hạn chế | Đoạn 3 | Thêm ví dụ: AI đưa ra công thức sai, sinh viên chép vào bài và bị trừ điểm |
| Khẩu ngữ và dính câu | Đoạn 3: "xài AI để làm bài hộ luôn, điều này..." | Sửa thành: "Nhiều bạn sử dụng AI để làm bài thay mình. Điều này dễ dẫn đến gian lận học thuật." |

**Đề xuất ưu tiên:** (1) loại bỏ ý lạc đề và thay bằng ý về AI; (2) bổ sung một ví dụ cho phần hạn chế; (3) viết lại câu khẩu ngữ theo văn phong trang trọng.
