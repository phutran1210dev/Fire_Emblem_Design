# Review: Làm gameplay khác biệt hơn

> Ngày: 2026-11-21 · Phạm vi: toàn bộ `design/gdd/` và `production/roadmap.md`
> Trạng thái: **ĐÃ DUYỆT TOÀN BỘ (2026-11-21)**: P1–P4, mọi mục ở bảng 3, cả hai chế độ
> Classic + Wounded, và đổi tên thuật ngữ. Các GDD liên quan đã có ghi chú "Approved change";
> nội dung chi tiết sẽ được viết vào GDD bằng `/design-system`.

## 1. Kết luận nhanh

Thiết kế hiện tại là một khung SRPG đầy đủ và gọn, nhưng **gần như mọi luật
đều là luật chuẩn của thể loại**: tam giác vũ khí, lượt theo phe, thăng cấp bằng
vật phẩm ở level cap, công thức hit/crit kiểu cổ điển, kỹ năng Miracle / Canto.
Người chơi quen thể loại sẽ thấy "đã chơi rồi" ngay ở màn đầu.

Điểm thực sự riêng hiện có:
- **5 tier class** (thể loại thường chỉ 2–3). Đây là móc tốt nhưng chưa có cơ chế nào làm nó có ý nghĩa.
- **Hệ địa hình chi tiết**, nhưng Environment Phase gần như trống.

Đề xuất: giữ khung cũ, thêm **3 trụ cột** gắn chặt với nhau, mỗi trụ dùng lại hệ
đã có thay vì thêm hệ mới:

| # | Trụ cột | Dùng lại hệ | Giải quyết câu hỏi mở |
|---|---------|-------------|----------------------|
| P1 | **Chiến trường sống**: phép nguyên tố biến đổi địa hình | Terrain, Tome, Environment Phase | Q6, Q25, Q28 |
| P2 | **Vị trí là vũ khí**: kẹp đánh (Pincer) + đẩy/kéo | Combat, Movement | Q3, Q4 |
| P3 | **Đà chiến (Momentum)**: tài nguyên chung của đội để dùng kỹ năng | Skill, Combat | Q17 |
| P4 | **Lời thề thăng cấp (Oath)**: rẽ nhánh mỗi lần thăng tier | Class, Promotion | Q10, Q11, Q14 |

Vòng chơi mới: *đặt quân để Kẹp (P2) → đánh lợi thế / đẩy vào địa hình đang
cháy (P1) → tích Momentum (P3) → tung kỹ năng mạnh → lên tier theo Lời thề mình
chọn (P4)*. Mỗi lượt có một câu hỏi chiến thuật rõ: **"lượt này mình tạo ra bao
nhiêu Momentum?"**

---

## 2. Bốn trụ cột đề xuất

### P1 · Chiến trường sống (Living Battlefield)

Phép nguyên tố tác động lên ô, không chỉ lên đơn vị. Environment Phase lan và
kết thúc hiệu ứng.

| Nguyên tố | Lên ô | Kết quả | Thời gian |
|-----------|-------|---------|-----------|
| Lửa | Forest / Plain cỏ | **Burning**: 3 sát thương/lượt cho ai đứng trên; lan sang 1 ô Forest kề mỗi Environment Phase | 2 vòng → thành **Ash** (như Plain, mất +20% Avoid) |
| Băng | Shallow / Deep water | **Ice**: đi được, chi phí 1; cavalry trượt thêm 1 ô theo hướng đi | 3 vòng |
| Sét | Đơn vị đứng trên nước | Lan sang mọi đơn vị trên các ô nước nối liền (50% sát thương) | Tức thì |
| Gió | Đơn vị | Đẩy 1 ô; dập ô Burning thành Ash | Tức thì |

- Bổ sung luật cho Tome: Tome có `element` (fire / ice / thunder / wind), giải quyết "Wind Tome" chưa định nghĩa (Q6).
- Status **Burn** (Q25) = đứng trên ô Burning hoặc trúng phép lửa crit.
- Q28: chốt luôn là status và địa hình **tick ở Environment Phase**.
- AI cần biết né ô Burning và biết dùng nó (thêm hệ số vào `priorityScore`).

### P2 · Vị trí là vũ khí (Position matters)

1. **Phản đòn (Q3)**: người bị đánh phản đòn nếu người tấn công nằm trong tầm vũ khí của mình. Đây là luật chuẩn, cần ghi rõ.
2. **Đánh hai lần (Q4)**: `AS = SPD − max(0, weapon.weight − STR/2)`. Nếu `AS ≥ AS đối phương + 4` thì đánh thêm một đòn. Weight có tác dụng (Q20) và SPD có giá trị.
3. **Kẹp đánh (Pincer), luật mới chính**: nếu một đồng minh đứng **đối diện** mục tiêu qua người nó (trái–phải hoặc trên–dưới):
   - +15% Hit, +2 sát thương
   - **mục tiêu không được phản đòn**
   - +1 Momentum
   Không cần hệ hướng mặt (facing), dễ đọc trên lưới, thưởng cho việc dàn đội hình.
4. **Đẩy / Kéo / Đổi chỗ**: mỗi class Tier 1 có một lệnh di chuyển ép:

   | Class | Lệnh | Ghi chú |
   |-------|------|---------|
   | Knight, Fighter | Shove (đẩy 1 ô) | Va vào vật cản / đơn vị khác: 2 sát thương cho cả hai |
   | Mercenary, Thief | Swap (đổi chỗ đồng minh kề) | Cứu đồng minh ra khỏi vòng vây |
   | Cleric, Mage | Pull (kéo 1 ô, tầm 2) | |

   Đẩy địch vào ô Burning / nước sâu / vực = kết hợp với P1. Đẩy rơi xuống vực **không** giết ngay: địch bị **Stun** 1 lượt và 5 sát thương, tránh luật gây ức chế.

### P3 · Đà chiến (Momentum)

Thay MP/SP riêng từng nhân vật (đang mâu thuẫn, Q17) bằng **một thanh dùng chung 0–10 cho cả đội**.

| Nhận | Momentum |
|------|----------|
| Đánh trúng với lợi thế tam giác | +1 |
| Đòn Kẹp | +1 |
| Hạ một địch | +2 |
| Hạ địch bằng địa hình (Burning, đẩy, sét lan) | +3 |

| Mất | Momentum |
|-----|----------|
| Một đồng minh gục | −3 |
| Bắt đầu Player Phase | −1 (tránh tích trữ vô hạn) |

- Kỹ năng Active tốn 2–6; kỹ năng tối thượng Tier 5 tốn 10.
- Passive và Reaction vẫn miễn phí.
- Thanh hiện trên HUD cạnh số lượt; dự báo trận đánh (combat forecast) cho biết đòn này sẽ cho bao nhiêu Momentum.
- Cooldown giữ nguyên để chống spam một kỹ năng.

Kết quả: tam giác vũ khí, đội hình và địa hình cùng đổ vào **một** tài nguyên. Người chơi có lý do để chơi khéo thay vì chỉ "đánh thằng yếu nhất".

### P4 · Lời thề thăng cấp (Oath promotion)

Năm tier chỉ có ý nghĩa khi mỗi lần lên tier là **một lựa chọn**.

- Mỗi lần thăng tier, chọn 1 trong 2 **Lời thề**. Ví dụ dòng Mercenary:
  - *Oath of the Shield*: thiên phản đòn, bảo vệ đồng minh kề, cho Momentum khi đỡ đòn
  - *Oath of the Edge*: thiên đánh hai lần, crit, cho Momentum khi Kẹp
- Bảng class hiện tại thành nhánh "mặc định"; mỗi tier thêm một nhánh thay thế.
  Để giữ phạm vi, **chỉ làm rẽ nhánh ở Tier 2 và Tier 4**.
- **Sửa nhịp độ**: 5 tier × 20 level = 100 level là quá dài cho một chiến dịch 25–30 màn.
  Đề xuất **10 level mỗi tier**, thăng cấp khoảng 5 màn/lần.
- **Sửa công thức chỉ số (Q10)**: tăng theo % trên chỉ số gốc 3–5 gần như bằng 0
  (LCK 5 × 5% = 0,25). Đổi thành **bonus cố định theo class**, ví dụ Mercenary → Hero: HP +5, STR +2, SKL +2, SPD +1, DEF +2.

---

## 3. Lỗ hổng gameplay cần sửa (dù có làm trụ cột hay không)

| Mức | Vấn đề | Đề xuất |
|-----|--------|---------|
| Cao | Không có **combat forecast** (bảng dự báo Hit / Dmg / Crit trước khi đánh) | Bắt buộc với SRPG; thêm vào UI action menu |
| Cao | Không quyết định **chết vĩnh viễn hay không** | Hai chế độ: *Classic* (chết vĩnh viễn) và *Wounded* (gục = nghỉ 1 màn, giảm 1 chỉ số tạm thời) |
| Cao | Chỉ số gốc Tier 1 giống hệt nhau cho mọi class (Q12) | Bảng base stats riêng cho 9 class |
| Cao | Thắng chỉ kiểm tra cuối vòng (Q2) | Seize / Boss Kill thắng ngay lập tức |
| Trung bình | Crit ×3 với Dagger 15% + SKL/2 → sát thủ một đòn quá sớm | Crit ×2.5 hoặc Dagger crit 10% |
| Trung bình | Không có trần hit / crit (Q9) | Clamp 0–100; hiển thị số đã clamp trên forecast |
| Trung bình | AI không có tie-break (Q34) | Ưu tiên: giết được → HP thấp → gần nhất → id nhỏ |
| Thấp | Boss dễ đoán | Boss **báo trước** vùng kỹ năng lượt sau (vùng đỏ trên lưới) |

---

## 4. Nhận xét về tài liệu

1. **Chưa có game concept**: không có bối cảnh, cốt truyện, phe phái, cảm giác người chơi (Player Fantasy).
   Mọi GDD đều thiếu mục này. Nên làm `design/game-concept.md` với 3–4 pillar trước khi viết tiếp GDD.
2. **Tên gọi trùng với một dòng game nổi tiếng**: tên repo, *Master Seal*, *Canto*, *Miracle*, *Falcon Knight*,
   *Pegasus Knight*, *Wyvern Rider*, *Great Knight*, *Paladin*, *Sniper*... Nên đặt lại tên theo thế giới riêng của bạn,
   vừa để game có bản sắc vừa tránh rủi ro thương hiệu khi phát hành.
   Ví dụ đổi Master Seal → *Oath Sigil* (khớp với P4).
3. **Phạm vi quá lớn cho bản đầu**: 9 dòng × 5 tier = 45 class.
   Vertical slice nên có **4 dòng (Mercenary, Knight, Archer, Mage) × Tier 1–2**.
4. Các GDD còn thiếu Edge Cases, Tuning Knobs, Acceptance Criteria. Ưu tiên viết cho `combat-system.md` trước.

---

## 5. Thứ tự đề xuất

1. Bạn chốt: đồng ý / sửa / bỏ từng trụ cột P1–P4 và các mục ở bảng 3.
2. Viết `design/game-concept.md` (bối cảnh + pillars + đặt lại tên).
3. Cập nhật `combat-system.md` (P2 + P3 + forecast), rồi `terrain-and-maps.md` (P1), rồi `class-system.md` (P4).
4. Làm prototype giấy hoặc greybox trong Godot: 1 bản đồ 10×10, 4 vs 6, có rừng và nước, để thử P1–P3 trước khi dựng nhiều model 3D.

## Diagrams

Các flow đề xuất (vẽ lại bằng archify):

- [Combat resolution (proposed)](../diagrams/combat-resolution.html)
- [Battle round loop (proposed)](../diagrams/battle-round.html)
- [Unit progression (proposed)](../diagrams/unit-progression.html)
