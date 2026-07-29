# HẮC VÂN KIẾM — Vượt Ải Diệt Quái

Game hành động 2D chạy thẳng trên trình duyệt, **không framework, không thư viện, không file ảnh**.
Toàn bộ nhân vật, quái, boss và bối cảnh được vẽ bằng `path` / `gradient` của Canvas 2D.

## Điều khiển

| Phím | Hành động |
|---|---|
| `A` `D` hoặc `←` `→` | Di chuyển |
| `W` / `Space` | Nhảy (nhảy đôi) |
| `S` + `Space` | Rơi xuyên qua bệ đá |
| `J` hoặc **chuột trái** | Liên trảm 3 nhát (nhát cuối hất tung) |
| `Shift` | Ảnh Bộ — lướt né, miễn thương trong lúc lướt |
| `K` hoặc **chuột phải** | **Khí Thuẫn** — giữ để đỡ |
| `L` | Băng Phù — bắn kiếm khí theo hướng chuột (24 MP) |
| `E` | Thiên Kiếm Trảm — tuyệt kỹ toàn màn hình khi ULT đầy |
| `Esc` | Tạm dừng |
| `G` hoặc `F2` | **GOD MODE** — bật/tắt chế độ test nhanh |
| `M` | Tắt / bật toàn bộ âm thanh |
| `N` | Tắt / bật riêng nhạc nền (vẫn giữ tiếng đánh) |
| `1` – `4` | Chọn nhanh độ khó khi đang ở bảng chọn |
| `` ` `` hoặc `F1` | Mở bảng lệnh cheat |

Trên điện thoại sẽ tự hiện cụm nút cảm ứng.

### Khí thuẫn hoạt động thế nào

* **Đỡ thường** — chặn 100% sát thương từ *phía trước*, trừ vào thanh KHIÊN thay vì máu. Bị đánh sau lưng thì không đỡ được.
* **Đỡ hoàn mỹ** — bấm đỡ trong vòng **0,22 giây** trước khi trúng đòn: không mất khiên, cộng ULT, và **bắn ngược viên đạn về phía địch với 190% sát thương**.
* **Vỡ khiên** — hết thanh khiên thì choáng 0,55 giây và cấm đỡ 1,4 giây. Khiên tự hồi 26/giây khi không đỡ.

### Nhạc nền

Sáu bản nhạc, **mỗi ải một chủ đề riêng khớp với bối cảnh** — không nạp file nhạc nào, toàn bộ
nốt do WebAudio dựng tại chỗ, đúng tinh thần "không thư viện, không file" của cả dự án:

| Bản | Dùng ở | Tính chất |
|---|---|---|
| `menu` | Màn hình chính | 62 BPM, thưa và huyền bí |
| `forest` | Ải I · Rừng Tử Khí | 76 BPM, ngũ cung, sáo gỗ, rất thoáng |
| `cave` | Ải II · Hang Nham Thạch | 98 BPM, trống nặng, bè trầm dồn dập |
| `palace` | Ải III · Điện Hắc Ám | 104 BPM, hành khúc thứ hoà thanh, uy nghi |
| `boss` | Khi Hắc Long Vương xuất hiện | 138 BPM, nhanh và dày |
| `victory` | Khi phá đảo | 84 BPM, vang và mở |

Mỗi bản là một mảng 16 bước (bè trầm · giai điệu · trống) cộng một nền hợp âm giữ liên tục.
Bộ lập lịch nhìn trước 120 ms bằng `setInterval`, **không phụ thuộc `requestAnimationFrame`**
nên nhạc không lệch nhịp khi khung hình tụt. Riêng Ác Mộng chèn thêm một tầng trầm rền (E1)
phía dưới cho nặng không khí.

---

## Nội dung game

**Ba ải:** Rừng Tử Khí → Hang Nham Thạch → Điện Hắc Ám.

**Sáu loại quái**, mỗi con một bản sắc và lối đánh riêng:

| Quái | Đặc điểm |
|---|---|
| **Nhớt Độc** | Khối nhớt trong suốt đã nuốt chửng một cái sọ, nhảy chồm tới, nhỏ giọt và bốc hơi độc |
| **Oán Linh** | Hồn ma đeo mặt nạ sứ nứt, thân tan thành khói, kéo theo xích gãy — tích rồi lao bổ |
| **Cốt Kiếm Sĩ** | Bộ xương mặc giáp rỉ, mũ trụ có chỏm lông, cờ trận rách, giáo gãy xuyên ngực; có khiên và vung kiếm |
| **Tà Đạo Sĩ** | Đạo sĩ bay lơ lửng, mũ đạo, râu dài, gương bát quái trước ngực, bùa vàng bay quanh; bắn ba cầu tối |
| **Thạch Vệ** | Tượng hộ pháp mặt sư tử bị phong ấn, bùa trên trán đã nứt; giậm đất tạo sóng xung kích |
| **Cung Thủ Ma** | Xạ thủ áo choàng rách, giương cung phát sáng, **có tia ngắm cảnh báo** trước khi bắn |

**Boss — Hắc Long Vương**, 3 giai đoạn, bộ chiêu mở rộng dần theo độ khó:

* Vuốt lao, phun lửa toả, nhảy giậm kèm mưa đá, triệu hồi lính, tia laser truy đuổi
* **Lao ngang toàn màn** — hiện dải đỏ cảnh báo và chữ “⚠ NHẢY TRÁNH” trước 0,85 giây *(Khó trở lên)*
* **Né đạn** — chớp sang bên khi kiếm khí bay tới, tỉ lệ 45% ở Khó và 72% ở Ác Mộng
* **Biến mất → lùi về hậu cảnh → oanh tạc** — cứ mất một mốc máu (80%, 60%, 42%, 25%, 12%) là biến mất, hiện mờ ở nền rồi **ném thiên thạch** hoặc **phun lửa** xuống người chơi. Số lượt oanh tạc tăng theo độ khó: 3 → 5 → 8 → 12. Trong lúc này boss bất khả xâm phạm, quay lại kèm sóng xung kích.
* **Giậm từ trên trời** — bay lên khỏi màn, tâm ngắm bám theo người chơi rồi khoá, lao xuống gây **động đất**: sát thương lớn và **choáng 1,2 giây nếu đang đứng dưới đất** (nhảy lên đúng lúc thì né được). Ở Ác Mộng boss giậm hai lần liên tiếp. *(Khó trở lên)*

---

## Độ khó

| | HP quái | Sát thương | Số quái | HP mình | Rơi đồ | Điểm & vàng |
|---|---|---|---|---|---|---|
| **Dễ** · Nhàn Du | ×0,72 | ×0,65 | ×0,70 | 150 | 42% | ×0,7 |
| **Bình thường** · Chính Đạo | ×1 | ×1 | ×1 | 120 | 26% | ×1 |
| **Khó** · Huyết Chiến | ×1,50 | ×1,45 | ×1,45 | 100 | 17% | ×1,7 |
| **Ác mộng** · Cửu U Ngục | ×1,80 | ×1,62 | ×1,55 | 100 | 17% | ×2,6 |

### Bẫy địa hình — mỗi ải một loại

Ác Mộng **không dồn cả ba bẫy vào cùng một ải**. Mỗi ải chỉ có đúng một loại, độ phức tạp
tăng dần để người chơi học xong bẫy này mới phải học bẫy sau. Vào ải luôn có **3,2 giây yên
thân** trước khi bẫy bắt đầu chạy, và mỗi ải nhuộm một tông màu địa hình riêng.

| Ải | Bẫy | Cách hoạt động |
|---|---|---|
| **I · Rừng Tử Khí** | ⩗ Bẫy chông | Rải dọc màn, chu kỳ 3,6 giây: ẩn → **nứt sáng cảnh báo 0,55 giây** → trồi lên, 16 sát thương. Bẫy tĩnh, chỉ cần đọc vết nứt rồi nhảy hoặc lướt qua. |
| **II · Hang Nham Thạch** | ☄ Thiên thạch | Mỗi 4,2–7,2 giây, 2–3 quả: vòng đỏ cảnh báo **1,35 giây** → rơi → nổ 22 sát thương bán kính 82 → để lại vũng lửa 2,8 giây (8 sát thương mỗi 0,6 giây). Bẫy động, buộc di chuyển liên tục. |
| **III · Điện Hắc Ám** | ≈ Nham thạch | Chu kỳ 23,3 giây (thấp 12s → dâng 3s → ngập 5,5s → rút 2,8s). Khi ngập, mặt đất là tử địa (12 sát thương mỗi 0,55 giây) — phải leo lên bệ. Có banner và tiếng gầm báo trước. |

Riêng **ải nham thạch** đổi sang bộ bệ đá cao `platN` (bệ hẹp treo cao thay nền đất rộng) vì
đó là ải duy nhất cần chỗ trú. Hai ải kia giữ nguyên địa hình gốc.

---

## Vàng và nâng cấp

Nhặt đồng tiền rơi từ quái, cộng tiền thưởng khi vượt ải
(`150 + số quái × 7 + điểm ÷ 22`, nhân hệ số độ khó). Sau mỗi ải sẽ mở bảng **Luyện Công**:

| Nâng cấp | Bậc | Hiệu quả mỗi bậc |
|---|---|---|
| ⚔ Kiếm Pháp | 5 | Sát thương kiếm +15% |
| ❤ Thể Phách | 5 | Máu tối đa +25 |
| ◈ Khí Thuẫn | 5 | Khiên tối đa +25 |
| ✦ Nội Lực | 5 | MP tối đa +20, hồi nhanh hơn |
| » Thân Pháp | 5 | Tốc chạy +8%, hồi lướt nhanh hơn |
| ✚ Hồi Sinh Đan | 1 | Gục ngã một lần sẽ tự đứng dậy với 60% máu |

---

## Cheat để test

### GOD MODE — cách nhanh nhất

Bấm **`G`** (hoặc `F2`) là xong, không cần mở bảng lệnh, không cần gõ gì. Bật/tắt được **mọi lúc**,
kể cả giữa trận. Một công tắc gộp bốn thứ:

* **Bất tử** — quái, boss và cả ba loại bẫy địa hình đều không trừ máu
* **Nội lực vô hạn** — bắn Băng Phù thoải mái
* **Máu · khiên · ULT luôn đầy** — không phải dừng lại hồi phục, tuyệt kỹ lúc nào cũng dùng được
* **Sát thương ×5** — lướt nhanh qua nội dung để tới chỗ cần xem

Khi bật sẽ có huy hiệu ⛨ vàng nhấp nháy ở góc phải màn hình. Trạng thái **giữ nguyên qua mỗi lần
chơi lại**, nên bật một lần rồi test bao nhiêu ván cũng được. Nút bấm có sẵn ở màn hình chính,
bảng chọn độ khó và bảng tạm dừng.

Cần bất tử *không kèm* mấy thứ kia thì dùng lệnh `inv`.

### Bảng lệnh đầy đủ

Nhấn `` ` `` hoặc `F1` để mở. Phím tắt nhanh: `F3` hồi máu · `F4` đầy ULT ·
`F5` diệt sạch quái · `F6` qua ải · `F7` gọi boss · `F8` bay xuyên địa hình.

Bảng lệnh chia hai cột: **nhật ký** bên trái, **danh sách lệnh bấm được** bên phải (nhóm theo
màu — nhân vật, màn chơi, bẫy địa hình, chỉ số). Bấm thẳng vào lệnh để chạy, lệnh cần tham số
thì tự điền sẵn vào ô nhập. Trong ô nhập: `Enter` chạy · `Tab` hoàn thành lệnh đang gõ dở ·
`↑` `↓` lịch sử · `Esc` đóng. Dải trạng thái trên đầu luôn hiện cheat nào đang bật.

```
god / gm            GOD MODE (gộp cả 4)       inv         chỉ bất tử, không kèm gì
heal                hồi đầy HP + MP           ult         nạp đầy tuyệt kỹ
mp                  nội lực vô hạn
kill                xoá sạch quái             skip        qua ải hiện tại
lv 1..3             nhảy thẳng tới một ải     boss        triệu hồi boss ngay
nuke                hạ boss tức thì           win         phá đảo luôn
spawn golem 3       sinh quái (slime / wraith / skeleton / mage / golem / archer)
diff 1..4           đổi độ khó giữa ván       dmg 5       nhân sát thương kiếm
speed 0.3           chỉnh tốc độ game         score 5000  cộng điểm
gold 2000           cộng vàng                 shop        mở bảng nâng cấp
noclip              bay xuyên địa hình        stun        tự gây choáng để xem hiệu ứng
spike               bật bẫy chông (ải I)      meteor      gọi 3 thiên thạch (ải II)
lava                kích nham thạch dâng (ải III)
hazard              bật/tắt bẫy ở mọi độ khó — bật lại theo đúng bẫy của ải hiện tại
reset               tắt toàn bộ cheat         clear       xoá log       help  danh sách đầy đủ
```

Ba lệnh `spike` / `meteor` / `lava` **đổi hẳn loại bẫy đang chạy**, nên có thể thử bất kỳ bẫy
nào ở bất kỳ ải nào mà không cần chơi lại.

Combo hay dùng khi test boss: bấm `G` rồi gõ `lv 3` → `boss`, thêm `speed 0.3` để xem chậm từng chiêu.
