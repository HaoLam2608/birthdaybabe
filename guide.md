# Đề xuất hoàn thiện Birthday Microsite

## Đánh giá bản hiện tại

Bản hiện tại đã đẹp hơn khá nhiều so với lúc đầu, đặc biệt ở chỗ scene đã bắt đầu có cảm giác được art-direct thay vì chỉ là một demo Three.js. Phần banner cũ đã được thay bằng dây fairy light + charm, hợp bối cảnh hơn nhiều và tạo cảm giác nhẹ, thơ hơn. Phần thiệp cũng đã nằm sẵn trên bàn, có shadow riêng, có ánh sáng lướt nhẹ và bố cục hợp lý hơn trước. Ngoài ra, việc thêm cánh hoa, ngọc trai, bokeh nền, sparkle, light dust và khói nến đã giúp scene đầy hơn mà chưa bị quá rối.

Phần camera cũng được xử lý tốt hơn vì không còn đứng hoàn toàn yên mà có cinematic drift nhẹ, đồng thời thay đổi focus khi chuyển sang hộp quà hoặc thiệp. Điều này làm trải nghiệm có cảm giác cao cấp hơn rõ rệt.

## Những điểm hiện tại đã tốt

- Fairy light thay banner hợp hơn rất nhiều.
- Thiệp bây giờ hòa vào scene tốt hơn.
- Dải ảnh có depth, scale và opacity theo vị trí nên vòng xoay có chiều sâu hơn.
- Mặt sau Polaroid đã được làm riêng nên không còn cảm giác lộ mặt trắng thô.
- Bánh, hộp quà và thiệp đã có spotlight riêng theo từng giai đoạn.
- Hiệu ứng khói nến, dust và bokeh phù hợp với birthday scene.
- Các decoration nhỏ như petal và pearl giúp phần bàn bớt trống.

## Những phần nên bổ sung thêm

### 1. Tạo background layer mềm hơn phía sau fairy light

Hiện tại fairy light đẹp nhưng phía sau nó vẫn hơi trống. Có thể thêm một lớp rất nhẹ như curtain voile mờ, gradient wall panel hoặc một mảng blur glow lớn. Không cần là vật thể rõ ràng, chỉ cần tạo cảm giác có một background set phía sau để tránh cảm giác fairy light đang treo giữa không khí.

### 2. Thêm shadow riêng cho bánh kem sau khi xuất hiện

Hiện tại hộp quà có contact shadow khá rõ và thiệp cũng có shadow riêng, nhưng bánh kem sau khi xuất hiện vẫn có thể trông hơi float. Nên tạo một contact shadow riêng cho cake và fade shadow này theo animation.

Flow mong muốn:

```text
Cake xuất hiện
↓
Shadow fade in
↓
Cake settle xuống
↓
Shadow đậm dần nhẹ
```

Điều này sẽ làm bánh trông có trọng lượng và thật hơn.

### 3. Làm bánh kem bớt geometric

Bánh hiện tại ổn nhưng vẫn hơi procedural vì các tier khá tròn và đều. Có thể bổ sung:

- Frosting edge không đều một chút.
- Một vài cream swirl nhỏ trên mặt bánh.
- Strawberry hoặc berry lớn hơn ở một vài vị trí.
- Một topper nhỏ như `Happy Birthday`.
- Một ít gold flakes hoặc sugar pearl.

Không nên thêm quá nhiều, chỉ cần 3–5 chi tiết nhỏ để bánh bớt cảm giác dựng bằng primitive geometry.

### 4. Cải thiện flame của nến

Nến đã có glow nhưng có thể làm flame đẹp hơn bằng cách:

- Flame gồm hai lớp màu, bên ngoài vàng/cam và lõi gần trắng.
- Halo lớn hơn nhưng opacity thấp.
- Point light flicker nhẹ hơn và không quá đều.
- Khi tắt nến, giữ glow giảm dần rồi mới biến mất hoàn toàn.

### 5. Làm fairy light thật hơn

Có thể thêm vài đoạn dây rất mảnh từ dây chính xuống các charm để charm trông như đang thật sự được treo.

Ví dụ:

```text
────●────●────●────
         │
         ♢

              │
              ♡
```

Chỉ cần khoảng 4–5 charm rủ xuống là đủ. Không nên treo ở mọi bóng đèn.

### 6. Thêm một vài cánh hoa ở foreground

Hiện đã có cánh hoa nằm trên bàn, nhưng có thể thêm khoảng 3–5 cánh hoa đi ngang foreground cực chậm. Các cánh gần camera nên lớn hơn, opacity thấp hơn và chuyển động không lặp quá thường xuyên.

Ví dụ:

```text
top-right
   ↓
      center
          ↓
      bottom-left
```

Hiệu ứng này sẽ giúp scene có chiều sâu tốt hơn rất nhiều.

### 7. Polaroid nên nghiêng nhẹ theo chuyển động carousel

Không nên để tất cả ảnh luôn hướng thẳng hoàn toàn vào camera vì sẽ hơi mechanical. Có thể cho ảnh nghiêng nhẹ theo vị trí trong vòng quay:

```text
Ảnh phía trái:  -8°
Ảnh giữa:        0°
Ảnh phía phải:  +8°
```

Nên giới hạn khoảng 8–12° để vẫn luôn nhìn rõ mặt trước của ảnh.

### 8. Khi click ảnh nên có focus mode

Khi một ảnh được chọn:

- Background giảm brightness khoảng 5–8%.
- Fairy light giảm attention nhẹ.
- Sparkle phía sau giảm opacity.
- Các ảnh còn lại giảm scale hoặc opacity.
- Ảnh được chọn có shadow mềm và glow rất nhẹ.

Sau khi đóng ảnh, toàn bộ scene trở về trạng thái bình thường.

### 9. Thiệp khi mở nên có perspective tự nhiên hơn

Thiệp hiện tại đã mở theo hai nhịp, đây là hướng tốt. Khi mở hoàn toàn không nên để thiệp phẳng hoàn toàn so với camera. Có thể giữ một chút perspective:

```text
rotationY ≈ -3° đến -6°
rotationZ ≈ 1° đến 2°
```

Như vậy sẽ có cảm giác giống một tấm thiệp thật đang được cầm trước mặt.

### 10. Thêm một final moment khi thiệp mở xong

Sau khi thiệp mở hoàn toàn nên có một đoạn kết ngắn khoảng 1–1.5 giây:

```text
Thiệp mở hoàn toàn
↓
Fairy light sáng hơn nhẹ
↓
Một vài sparkle nhỏ xuất hiện quanh thiệp
↓
Camera gần như đứng yên
↓
Các animation khác chậm lại
```

Không cần thêm confetti ở bước này. Chỉ cần ánh sáng ấm hơn một chút và khoảng 6–10 sparkle nhỏ quanh thiệp là đủ.

## Những thứ không nên thêm nữa

Không nên tiếp tục thêm quá nhiều object lớn như:

- Bóng bay lớn.
- Nhiều hộp quà.
- Gấu bông lớn.
- Chữ 3D.
- Quá nhiều hoa lớn.
- Quá nhiều confetti.

Scene hiện tại đã gần đủ chi tiết. Nếu tiếp tục thêm nhiều object lớn sẽ dễ quay lại cảm giác rối.

Từ thời điểm này nên ưu tiên:

```text
Lighting
→ Shadow
→ Micro-animation
→ Depth
→ Transition
→ Timing
```

thay vì tiếp tục thêm nhiều model.

## Thứ tự ưu tiên chỉnh tiếp

1. Thêm contact shadow riêng cho bánh.
2. Polish bánh kem để bớt geometric.
3. Làm fairy light và charm thật hơn.
4. Thêm vài petal foreground.
5. Cải thiện chuyển động Polaroid.
6. Thêm focus mode khi click ảnh.
7. Polish góc mở và perspective của thiệp.
8. Thêm final lighting moment sau khi mở thiệp.

Sau khi hoàn thành các phần trên, scene nên chuyển sang giai đoạn polish cuối, tập trung chủ yếu vào timing, scale, spacing, camera và lighting thay vì tiếp tục thêm nhiều object mới.
