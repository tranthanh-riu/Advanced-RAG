# Form Data – Hệ thống hồ sơ mua bán bất động sản

Thư mục chứa 239 biểu mẫu, chia theo 5 giai đoạn của một giao dịch mua bán. Mỗi giai đoạn có **hồ sơ chung** (luôn phải có) và **hồ sơ bổ sung** (chỉ dùng khi giao dịch rơi vào trường hợp đó).

Chú thích màu trong sơ đồ:

- 🟩 Hồ sơ chung, bắt buộc
- 🟧 Mua qua môi giới / đại lý
- 🟦 Vay ngân hàng
- 🟪 Theo loại người mua / loại nhà / phát sinh

## 1. Sơ đồ tổng quan

```mermaid
flowchart LR
    G1["<b>Giai đoạn 1</b><br/>Giữ chỗ và đặt cọc<br/>48 tệp"]
    G2["<b>Giai đoạn 2</b><br/>Ký hợp đồng mua bán<br/>137 tệp"]
    G3["<b>Giai đoạn 3</b><br/>Thanh toán theo tiến độ<br/>23 tệp"]
    G4["<b>Giai đoạn 4</b><br/>Bàn giao nhà<br/>19 tệp"]
    G5["<b>Giai đoạn 5</b><br/>Nhận sổ hồng<br/>12 tệp"]
    G1 ==> G2 ==> G3 ==> G4 ==> G5

    B1["TH-01 Mua qua môi giới"]
    B2["Hồ sơ bổ sung<br/>khi mua qua môi giới"]
    B1 -.-> B2
    G1 --- B1
    G2 --- B2

    N1["TH-02 Vay ngân hàng"]
    N2["Hồ sơ bổ sung<br/>khi vay ngân hàng"]
    N3["TH-01 Ngân hàng giải ngân"]
    N1 -.-> N2 -.-> N3
    G1 --- N1
    G2 --- N2
    G3 --- N3

    C2["Hồ sơ theo loại người mua<br/>CH-001 → CH-005"]
    C3["TH-02 Khách thanh toán chậm"]
    C4["Bổ sung theo loại nhà<br/>Căn hộ / Nhà thấp tầng"]
    G2 --- C2
    G3 --- C3
    G4 --- C4

    classDef stage fill:#18232f,color:#ffffff,stroke:#18232f
    classDef broker fill:#fbefdf,color:#7a4300,stroke:#a35a00
    classDef bank fill:#e4ecf8,color:#1b4180,stroke:#2456a6
    classDef case fill:#f2e8f5,color:#5e2d6f,stroke:#7a3d8f
    class G1,G2,G3,G4,G5 stage
    class B1,B2 broker
    class N1,N2,N3 bank
    class C2,C3,C4 case
```

## 2. Chi tiết từng giai đoạn

### Giai đoạn 1 – Giữ chỗ và đặt cọc

```mermaid
flowchart TD
    G1["Giai đoạn 1<br/>Giữ chỗ và đặt cọc"]

    G1 --> A1["1. Hồ sơ khách hàng (13)"]
    A1 --> A11["Phiếu thông tin khách hàng"]
    A1 --> A12["CCCD"]
    A1 --> A13["Giấy tờ hôn nhân<br/>• Xác nhận độc thân<br/>• Đăng ký kết hôn<br/>• Thỏa thuận tài sản riêng"]
    A1 --> A14["Văn bản ủy quyền"]

    G1 --> A2["2. Hồ sơ căn nhà / căn hộ (8)<br/>• Bản sao GCN riêng của căn<br/>• Bản vẽ mặt bằng, sơ đồ vị trí<br/>• Phiếu thông tin BĐS<br/>• Xác nhận không bán trùng"]
    G1 --> A3["3. Hồ sơ giá bán (3)<br/>• Bảng giá đã phê duyệt<br/>• Phiếu tính giá và tiến độ TT<br/>• Chính sách bán hàng, ưu đãi"]
    G1 --> A4["4. Hồ sơ giữ chỗ (3)<br/>• Đăng ký nguyện vọng<br/>• Đề nghị / thỏa thuận giữ chỗ<br/>• Xác nhận giữ chỗ thành công"]
    G1 --> A5["5. Hồ sơ đặt cọc (3)<br/>• Hợp đồng đặt cọc"]
    G1 --> A6["6. Chứng từ nhận tiền (8)<br/>• Ủy nhiệm chi<br/>• Phiếu thu tiền đặt cọc<br/>• Xác nhận đã nhận đủ cọc"]
    G1 --> A7["7. Phê duyệt nội bộ (4)<br/>• Kiểm tra hồ sơ KH, checklist<br/>• Phiếu trình phê duyệt đặt cọc<br/>• Biên bản bàn giao hồ sơ"]

    G1 -.-> T1["TH-01 Mua qua môi giới (4)<br/>• Hợp đồng môi giới<br/>• Chính sách hoa hồng<br/>• Phiếu giới thiệu khách hàng<br/>• Xác nhận nguồn khách"]
    G1 -.-> T2["TH-02 Vay ngân hàng (2)<br/>• Phiếu đăng ký nhu cầu vay<br/>• Hồ sơ đánh giá khả năng vay"]

    classDef stage fill:#18232f,color:#ffffff,stroke:#18232f
    classDef common fill:#e6f2f0,color:#0a524c,stroke:#0d6b63
    classDef broker fill:#fbefdf,color:#7a4300,stroke:#a35a00
    classDef bank fill:#e4ecf8,color:#1b4180,stroke:#2456a6
    class G1 stage
    class A1,A11,A12,A13,A14,A2,A3,A4,A5,A6,A7 common
    class T1 broker
    class T2 bank
```

### Giai đoạn 2 – Ký hợp đồng mua bán

```mermaid
flowchart TD
    G2["Giai đoạn 2<br/>Ký hợp đồng mua bán"]

    G2 --> P["Giấy tờ chung (43)"]
    P --> P1["Kiểm tra KH và sản phẩm<br/>1. Phiếu thông tin KH<br/>2. Xác nhận thông tin sản phẩm<br/>3. Bản sao GCN của căn<br/>4. Kiểm tra pháp lý của căn<br/>5. Xác nhận không bán trùng<br/>6. Phiếu tính giá bán<br/>7. Chính sách ưu đãi, chiết khấu"]
    P1 --> P2["Phê duyệt và thẩm quyền<br/>11. Kiểm tra hồ sơ KH<br/>12. Tờ trình phê duyệt<br/>13. Quyết định phê duyệt bán<br/>14. Thẩm quyền người ký của CĐT"]
    P2 --> P3["Hợp đồng và phụ lục<br/>15. Hợp đồng mua bán<br/>16–21. Phụ lục sản phẩm, giá,<br/>tiến độ TT, bản vẽ, thiết bị, bảo hành"]
    P3 --> P4["Hoàn tất ký<br/>22. Biên bản giao nhận hợp đồng<br/>23. Checklist chữ ký và hồ sơ"]

    G2 -.-> M["Bổ sung khi mua qua môi giới (20)"]
    M --> M1["Tư cách đại lý<br/>• HĐ phân phối CĐT – đại lý<br/>• Phụ lục sản phẩm phân phối<br/>• Giấy giới thiệu, chứng chỉ môi giới<br/>• Ủy quyền thu tiền"]
    M --> M2["Giao dịch với khách<br/>• Phiếu tư vấn, dẫn khách xem nhà<br/>• Xác nhận nguồn khách<br/>• Bảng giá, chính sách cho đại lý<br/>• Xác nhận SP do CĐT phát hành"]
    M --> M3["Đối soát và chuyển hồ sơ<br/>• Đối soát tiền cọc<br/>• CĐT xác nhận đã nhận tiền<br/>• Xác nhận giao dịch thành công<br/>• Phiếu chuyển hồ sơ đại lý → CĐT"]

    G2 -.-> V["Bổ sung khi vay ngân hàng (19)"]
    V --> V1["Xin vay<br/>• Đơn đề nghị vay vốn<br/>• Chứng minh thu nhập<br/>• Đề nghị CĐT xác nhận thông tin căn"]
    V1 --> V2["Ngân hàng chấp thuận<br/>• Thông báo chấp thuận tín dụng<br/>• Thư cam kết cho vay"]
    V2 --> V3["Ký kết<br/>• Hợp đồng tín dụng<br/>• HĐ / cam kết thế chấp<br/>• Thỏa thuận ba bên<br/>• Cam kết giao GCN cho ngân hàng<br/>• Tiến độ TT vốn tự có + vốn vay"]

    G2 -.-> K["Bổ sung theo loại người mua (55)"]
    K --> K1["CH-001 Vợ chồng đồng sở hữu<br/>• CCCD, đăng ký kết hôn, cư trú<br/>• Xác nhận đồng sở hữu<br/>• Ủy quyền, phạm vi ủy quyền"]
    K --> K2["CH-002 Người độc thân<br/>• CCCD, cư trú<br/>• Xác nhận tình trạng hôn nhân<br/>• Cam kết về thông tin hôn nhân"]
    K --> K3["CH-003 Nhiều người đồng sở hữu<br/>• Nhân thân từng người<br/>• Thỏa thuận đồng sở hữu, tỷ lệ<br/>• Thỏa thuận thanh toán, làm GCN<br/>• Ủy quyền, hợp đồng chính"]
    K --> K4["CH-004 Đã kết hôn, mua bằng tài sản riêng<br/>• CCCD, đăng ký kết hôn<br/>• Thỏa thuận tài sản riêng<br/>• Xác nhận của người còn lại<br/>• Cam kết nguồn tiền, thỏa thuận bàn giao"]
    K --> K5["CH-005 Doanh nghiệp mua<br/>• GCN ĐKDN, điều lệ<br/>• Quyết định / nghị quyết mua BĐS<br/>• Thẩm quyền phê duyệt, ủy quyền người ký<br/>• Tài khoản thanh toán DN"]

    classDef stage fill:#18232f,color:#ffffff,stroke:#18232f
    classDef common fill:#e6f2f0,color:#0a524c,stroke:#0d6b63
    classDef broker fill:#fbefdf,color:#7a4300,stroke:#a35a00
    classDef bank fill:#e4ecf8,color:#1b4180,stroke:#2456a6
    classDef case fill:#f2e8f5,color:#5e2d6f,stroke:#7a3d8f
    class G2 stage
    class P,P1,P2,P3,P4 common
    class M,M1,M2,M3 broker
    class V,V1,V2,V3 bank
    class K,K1,K2,K3,K4,K5 case
```

### Giai đoạn 3 – Thanh toán theo tiến độ

```mermaid
flowchart TD
    G3["Giai đoạn 3<br/>Thanh toán theo tiến độ"]
    G3 --> D["Hồ sơ mỗi đợt thanh toán (9)<br/>• Thông báo thanh toán<br/>• Bảng tính nghĩa vụ thanh toán<br/>• Ủy nhiệm chi mẫu 16c1–16c4<br/>• Giấy xác nhận tiền<br/>• Xác nhận thanh toán<br/>• Hóa đơn điện tử"]
    D -->|lặp lại từng đợt| D
    G3 -.-> T1["TH-01 Ngân hàng giải ngân (4)<br/>• Đề nghị giải ngân<br/>• Khế ước nhận nợ"]
    G3 -.-> T2["TH-02 Khách thanh toán chậm (9)<br/>• Thông báo nhắc thanh toán<br/>• Đơn xin gia hạn"]

    classDef stage fill:#18232f,color:#ffffff,stroke:#18232f
    classDef common fill:#e6f2f0,color:#0a524c,stroke:#0d6b63
    classDef bank fill:#e4ecf8,color:#1b4180,stroke:#2456a6
    classDef case fill:#f2e8f5,color:#5e2d6f,stroke:#7a3d8f
    class G3 stage
    class D common
    class T1 bank
    class T2 case
```

### Giai đoạn 4 – Bàn giao nhà

```mermaid
flowchart TD
    G4["Giai đoạn 4<br/>Bàn giao nhà"]
    G4 --> C["Dùng chung cho căn hộ và nhà thấp tầng (12)"]
    C --> C1["Thông báo bàn giao nhà"]
    C1 --> C2["Phiếu xác nhận đủ điều kiện bàn giao<br/>Kiểm tra hiện trạng nhà đất"]
    C2 --> C3["Biên bản kiểm tra, nghiệm thu và bàn giao<br/>Biên bản bàn giao thiết bị"]
    C3 --> C4["Biên bản yêu cầu sửa chữa<br/>→ Xác nhận hoàn tất sửa chữa"]
    C4 --> C5["Phiếu bảo hành<br/>Tiếp nhận quản lý của BQL"]

    G4 -.-> A["Căn hộ chung cư (3)<br/>• Biên bản tiếp nhận căn hộ<br/>• Đo đạc diện tích sử dụng thực tế<br/>• Chứng từ nộp kinh phí bảo trì"]
    G4 -.-> L["Biệt thự, liền kề, nhà phố, shophouse (4)<br/>• Xác nhận mốc giới, ranh giới lô đất<br/>• Bàn giao sân vườn, cổng, hàng rào<br/>• Hướng dẫn cải tạo nội thất<br/>• Bản cam kết"]

    classDef stage fill:#18232f,color:#ffffff,stroke:#18232f
    classDef common fill:#e6f2f0,color:#0a524c,stroke:#0d6b63
    classDef case fill:#f2e8f5,color:#5e2d6f,stroke:#7a3d8f
    class G4 stage
    class C,C1,C2,C3,C4,C5 common
    class A,L case
```

### Giai đoạn 5 – Nhận sổ hồng

```mermaid
flowchart TD
    G5["Giai đoạn 5<br/>Nhận sổ hồng"]
    G5 --> F["Nghĩa vụ tài chính (3)<br/>• Hồ sơ nghĩa vụ tài chính<br/>• Chứng từ đã nộp thuế, phí, lệ phí"]
    F --> R["Đăng ký sang tên (6)<br/>• Đơn đăng ký biến động đất đai<br/>• Đơn / giấy ủy quyền sang tên sổ<br/>• Giấy tiếp nhận hồ sơ, hẹn trả kết quả"]
    R --> H["Giao sổ (3)<br/>• Biên bản giao nhận Giấy chứng nhận"]
    H -.->|nếu vay ngân hàng| BK["Giao GCN cho ngân hàng<br/>theo cam kết ở Giai đoạn 2"]

    classDef stage fill:#18232f,color:#ffffff,stroke:#18232f
    classDef common fill:#e6f2f0,color:#0a524c,stroke:#0d6b63
    classDef bank fill:#e4ecf8,color:#1b4180,stroke:#2456a6
    class G5 stage
    class F,R,H common
    class BK bank
```

## 3. Cách chọn hồ sơ cho một giao dịch

1. Ngay ở giai đoạn 1, trả lời 3 câu hỏi: khách đến qua môi giới không? Có vay ngân hàng không? Khách thuộc nhóm người mua nào (CH-001 đến CH-005)?
2. Ở mỗi giai đoạn, luôn lấy đủ **hồ sơ chung**, rồi cộng thêm nhánh bổ sung tương ứng với câu trả lời ở bước 1.
3. Nhánh **môi giới** kết thúc ở giai đoạn 2 bằng phiếu chuyển hồ sơ từ đại lý sang chủ đầu tư.
4. Nhánh **vay ngân hàng** kéo dài từ giai đoạn 1 đến giai đoạn 3 (đăng ký vay → ký tín dụng, thế chấp → giải ngân). Ở giai đoạn 5, Giấy chứng nhận giao cho ngân hàng theo cam kết.
5. Giai đoạn 4 chia nhánh theo **loại nhà**: căn hộ chung cư hoặc nhà thấp tầng, cộng với bộ giấy tờ dùng chung.
