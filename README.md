# D2HL · Trợ lý đổi chuyến bay

Prototype tương tác mô phỏng cách trợ lý AI hỗ trợ khách đổi chuyến bay. Giao diện minh họa các mức tự chủ của AI, cách xử lý yêu cầu chưa rõ, bước xác nhận của khách và phương án khắc phục khi đổi nhầm.

> Đây là prototype dùng dữ liệu dựng. Ứng dụng không gọi AI, không kết nối hãng bay và không thực hiện giao dịch thật.

## Tính năng

- Chuyển đổi giữa ba mức tự chủ:
  1. **Chỉ gợi ý:** khách tự đổi chuyến.
  2. **Cần khách xác nhận:** trợ lý giữ chỗ và chỉ đổi sau khi khách xác nhận.
  3. **Tự làm và hoàn tác:** trợ lý đổi chuyến ngay, có thời hạn để hoàn tác.
- Chuyển đổi giữa hai kịch bản:
  - **K4 – Yêu cầu chưa rõ:** khách nói “sáng mai” khi có nhiều chuyến phù hợp.
  - **K6 – Đổi nhầm:** minh họa rủi ro khi trợ lý hành động trước khi làm rõ ý khách.
- Hiển thị chuyến bay, tình trạng chỗ, bộ đếm thời gian giữ chỗ và thông tin xác nhận.
- Mô phỏng hoàn tác, gửi yêu cầu hoàn vé và chuyển hồ sơ cho nhân viên hỗ trợ.
- Hiển thị lời hứa với khách, mức tự chủ của các tool và chú thích nguyên tắc HAX/PAIR.

## Chạy prototype

Không cần cài đặt thư viện hoặc máy chủ. Mở tệp `prototype/index.html` trực tiếp bằng trình duyệt.

Hoặc dùng VS Code với tiện ích Live Server để xem prototype trên máy chủ cục bộ.

## Cách dùng

1. Mở `prototype/index.html`.
2. Chọn một trong ba **Mức tự chủ** ở đầu trang.
3. Chọn kịch bản **K4** hoặc **K6**.
4. Dùng các nút trong khung hội thoại để đi qua luồng mô phỏng.
5. Bật hoặc tắt **Hiện số HAX/PAIR** để xem chú thích nguyên tắc thiết kế.

## Cấu trúc

```text
.
├── prototype/
│   └── index.html   
├── spec.md          
└── README.md