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
| `` ` `` hoặc `F1` | Mở bảng lệnh cheat |

Trên điện thoại sẽ tự hiện cụm nút cảm ứng.

### Khí thuẫn hoạt động thế nào

* **Đỡ thường** — chặn 100% sát thương từ *phía trước*, trừ vào thanh KHIÊN thay vì máu. Bị đánh sau lưng thì không đỡ được.
* **Đỡ hoàn mỹ** — bấm đỡ trong vòng **0,22 giây** trước khi trúng đòn: không mất khiên, cộng ULT, và **bắn ngược viên đạn về phía địch với 190% sát thương**.
* **Vỡ khiên** — hết thanh khiên thì choáng 0,55 giây và cấm đỡ 1,4 giây. Khiên tự hồi 26/giây khi không đỡ.

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
| **Ác mộng** · Cửu U Ngục | ×2,05 | ×1,90 | ×1,85 | 85 | 11% | ×2,6 |

**Riêng Ác Mộng đổi hẳn địa hình** — mỗi ải dùng bộ bệ đá riêng (`platN`): 6–8 bệ hẹp treo cao thay cho nền đất rộng, mặt đất nứt nham thạch, tàn lửa bay khắp màn. Kèm ba hiểm hoạ:

* **Nham thạch dâng** theo chu kỳ 22,7 giây (thấp 11s → dâng 2,6s → ngập 6,5s → rút 2,6s). Khi ngập, mặt đất là tử địa, phải leo lên bệ. Có banner báo trước.
* **Thiên thạch** mỗi 3,6–6,4 giây, 2–4 quả: vòng đỏ cảnh báo 1,2 giây → rơi → nổ 30 sát thương bán kính 86 → để lại vũng lửa 2,8 giây.
* **Bẫy chông** rải dọc màn, chu kỳ 3,6 giây: ẩn → nứt sáng cảnh báo 0,5 giây → trồi lên 20 sát thương.

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

Nhấn `` ` `` hoặc `F1` để mở bảng lệnh. Phím tắt nhanh: `F2` bất tử · `F3` hồi máu · `F4` đầy ULT ·
`F5` diệt sạch quái · `F6` qua ải · `F7` gọi boss · `F8` bay xuyên địa hình.

```
god                 bất tử                    heal        hồi đầy HP + MP
mp                  nội lực vô hạn            ult         nạp đầy tuyệt kỹ
kill                xoá sạch quái             skip        qua ải hiện tại
lv 1..3             nhảy thẳng tới một ải     boss        triệu hồi boss ngay
nuke                hạ boss tức thì           win         phá đảo luôn
spawn golem 3       sinh quái (slime / wraith / skeleton / mage / golem / archer)
diff 1..4           đổi độ khó giữa ván       dmg 5       nhân sát thương kiếm
speed 0.3           chỉnh tốc độ game         score 5000  cộng điểm
gold 2000           cộng vàng                 shop        mở bảng nâng cấp
noclip              bay xuyên địa hình        stun        tự gây choáng để xem hiệu ứng
lava                kích nham thạch dâng      meteor      gọi 4 thiên thạch
hazard              bật/tắt bẫy Ác Mộng ở mọi độ khó
reset               tắt toàn bộ cheat         clear       xoá log       help  danh sách đầy đủ
```

Combo hay dùng khi test boss: `diff 4` → `lv 3` → `god` → `boss` → `dmg 20`, rồi `speed 0.3` để xem chậm từng chiêu.
