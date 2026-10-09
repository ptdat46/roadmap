# Java Software Engineer — Roadmap học từng ngày

> Mục tiêu: Fresher sau 4–5 tháng; Junior thực chiến và đủ năng lực apply Mid sau 12–14 tháng tiếp theo; Senior sau 1–2 năm tích lũy scope thật.
>
> Lịch chuẩn: Thứ 2–6 mỗi ngày 2 giờ; Thứ 7 5 giờ; Chủ nhật nghỉ hoặc bù tối đa 2 giờ. Tổng 15 giờ/tuần. Mỗi buổi: 45 phút học, 60 phút code, 15 phút ghi chú/test/commit.
>
> Quy tắc: học xong phải code; feature phải có test; mỗi tuần có commit; mỗi mốc có project demo. Salary/title không tự động theo thời gian; cần năng lực, output, phỏng vấn, thị trường.
>
> Buffer: trượt tuần nào dời gate tương ứng; không học nhanh hơn để kịp lịch. Gate trượt thì bù đúng phần trượt, không bỏ qua.

---

# GIAI ĐOẠN 1 — TUẦN 1–8
## Java 17 LTS + Spring Boot Foundation: Xây Dựng Base Dự Án Giao Vặt

**Mục tiêu cuối giai đoạn:** Tự tay dựng và làm chủ một Backend Spring Boot 3.x chuẩn sản xuất chạy trên **Java 17 LTS**; hiểu sâu kiến trúc phân tầng 3 layers; tự viết RESTful API kết nối Database quan hệ (PostgreSQL/MySQL); nắm vững cú pháp, câu điều kiện, vòng lặp, OOP, Java Collections, Domain Exceptions, Stream API và Concurrency Locking cơ bản trực tiếp trên codebase Giao Vặt; có test tự động MockMvc và Testcontainers.

> **NGUYÊN TẮC HỌC CỐT LÕI CỦA GIAI ĐOẠN 1 (PRACTICE-FIRST VIA GIAO VẶT):**
> - **Môi trường kỹ thuật chuẩn:** Sử dụng **Java 17 LTS** và phiên bản **Spring Boot 3.x tương thích** (Spring Boot 3.2+).
> - **Tuyệt đối không học qua ví dụ console rời rạc nhỏ lẻ:** Bỏ qua các bài toán máy tính cầm tay, quản lý sinh viên mảng console, quản lý thư viện console. Chúng gây phân mảnh và không phản ánh cách tư duy của kỹ sư phần mềm backend thực chiến.
> - **Học theo phương pháp thực hành trực tiếp làm app Giao Vặt:**
>   1. Ngay từ Tuần 1, khởi tạo base dự án Spring Boot cho Giao Vặt $\rightarrow$ Học được cấu trúc hoàn chỉnh của 1 Backend Java Spring Boot chuẩn doanh nghiệp (Maven/Gradle, `pom.xml`, các package `controller`, `service`, `repository`, `model`, `dto`, `config`, `exception`).
>   2. Code Controller và các REST API đầu tiên cho Giao Vặt (Ping API, Order Controller skeleton).
>   3. Khi bắt tay vào viết logic nghiệp vụ cho Giao Vặt (tính cước sàn theo khoảng cách, kiểm tra điều kiện tạo đơn, kiểm tra trạng thái máy đơn hàng, duyệt danh sách bảng tin, lọc đơn, thống kê thu nhập) $\rightarrow$ Học và làm chủ tự nhiên các logic cú pháp Java: kiểu dữ liệu, toán tử, câu điều kiện (`if/else`, switch-case / switch expression), vòng lặp (`for`, `while`), OOP đóng gói, Java Collections in-memory, Custom Exceptions và Stream API.

**Dự án chính: Giao Vặt** — On-Demand Crowdsourced Delivery Platform (Nền tảng tiện chuyến & giao việc vi mô)
- **Scope nghiệp vụ:** Hệ thống kết nối Người tạo đơn (Creator) và Người tiện chuyến / Tài xế (Runner). Khách đăng nhu cầu giao hàng/đi nhờ xe $\rightarrow$ Đơn hàng hiển thị trên Bảng tin công khai (`Order Feed`) $\rightarrow$ Runner duyệt bảng tin và nhận đơn (`claimOrder`).
- **Core Mechanism:** Bảng tin đơn hàng tập trung (`OPEN` orders), cơ chế khóa chống tranh chấp khi nhiều Runner cùng bấm nhận 1 đơn trong cùng tích tắc (Concurrency Locking với `@Version`), thông báo real-time cập nhật trạng thái đơn (Server-Sent Events / SSE).
- **Core features:** Creator đăng đơn (điểm đón, điểm trả, khoảng cách, cước phí), Bảng tin đơn mở công khai, Runner duyệt feed & nhận đơn (`OPEN` $\rightarrow$ `ACCEPTED`), cập nhật hành trình (`PICKED_UP` $\rightarrow$ `IN_TRANSIT` $\rightarrow$ `COMPLETED` / `CANCELLED`), tính giá linh hoạt (Strategy Pattern), phân quyền Creator vs Runner bằng JWT.
- **Architecture:** Monolith Spring Boot 3 chuẩn 3 layers (Controller–Service–Repository Seam), In-Memory Cache/Queue (Redis ở Giai đoạn 2), PostgreSQL/MySQL tập trung, thiết kế module hóa phân ranh giới rõ ràng.

### Danh mục 9 Module Chức năng Bắt buộc của App Giao Vặt (Khai thác 100% Roadmap)
1. **Module 1 — Authentication & RBAC (Tuần 9, 15):** Đăng ký/đăng nhập Creator & Runner; Spring Security 6 + JWT Stateless; Refresh Token Rotation; phân quyền `@PreAuthorize("hasRole('...')")`; cấu hình MDC Logging `traceId`; ẩn số điện thoại khách trên public feed (chỉ hiển thị sau khi Runner nhận đơn thành công).
2. **Module 2 — Đăng đơn & Định giá thông minh (Tuần 3, 6, 15, 17):** Jakarta Validation `@Valid`; GoF Strategy Pattern cho tính giá cước (`StandardPricingStrategy`, `SurgePricingStrategy` giờ cao điểm, `BadWeatherPricingStrategy` thời tiết xấu); Idempotency Key Pattern (Header `Idempotency-Key` lưu Redis chống bấm đúp tạo đơn trùng); chuẩn hóa lỗi theo RFC 7807 `ProblemDetail`.
3. **Module 3 — Redis In-Memory Priority Queue & Feed (Tuần 10):** Redis Sorted Set (ZSET) lưu `orders:open` theo score thời gian/giá cước; Cache-Aside pattern cho chi tiết đơn `order:{id}`; Sliding Window Rate Limiting bằng Redis để chống bot/spam refresh bảng tin.
4. **Module 4 — Runner Claim Order & Concurrency Control (Tuần 7, 8, 17, 24–26):** Giải quyết triệt để race condition khi nhiều Runner cùng bấm nhận 1 đơn bằng JPA Optimistic Locking (`@Version`); đối chứng so sánh với Pessimistic Locking (`PESSIMISTIC_WRITE`) hoặc Redisson Distributed Lock; cấu hình Spring `@Retryable` tự động retry với exponential backoff khi gặp deadlock.
5. **Module 5 — Real-time Feed & Notifications (Tuần 17):** Server-Sent Events (`SseEmitter`) quản lý luồng real-time một chiều nhẹ; Event-Driven Architecture (`ApplicationEventPublisher`); sử dụng Thread Pool bất đồng bộ (`ThreadPoolTaskExecutor`, `@Async`) trên Java 17 LTS cho tác vụ push notification (broadcast thêm đơn mới vào feed, gỡ đơn đã nhận, báo khách có Runner nhận).
6. **Module 6 — Quản lý vòng đời đơn & State Machine (Tuần 2, 4, 6, 8, 12):** Quản lý chu trình trạng thái: `DRAFT` $\rightarrow$ `OPEN` $\rightarrow$ `ACCEPTED` $\rightarrow$ `PICKED_UP` $\rightarrow$ `IN_TRANSIT` $\rightarrow$ `COMPLETED` / `CANCELLED`; Custom Exceptions (`InvalidOrderStateException`, `OrderNotFoundException`); Global Exception Handler `@RestControllerAdvice`; Unit & Integration tests với MockMvc.
7. **Module 7 — Thanh toán Sandbox & Webhook (Tuần 17, 49):** Tích hợp cổng thanh toán giả lập (VNPay/Stripe Sandbox); Webhook Receiver xác thực chữ ký số HMAC-SHA256; Idempotent Webhook Processing (chống duplicate webhook callback khi cổng gửi lại).
8. **Module 8 — Báo cáo định kỳ & Spring Batch (Tuần 4, 22):** `@Scheduled` hoặc Spring Batch tự động tổng kết doanh thu Runner lúc 00:00 hàng ngày; xuất file báo cáo Excel bằng Apache POI; tính toán thống kê bằng Java Stream API (`groupingBy`, `summarizingDouble`).
9. **Module 9 — Database Tuning, Testing & DevOps (Tuần 5, 7, 11, 12, 36):** Flyway Database Migrations (`V1`, `V2`); B-Tree Composite Index `(status, created_at)` kèm benchmark `EXPLAIN ANALYZE`; Testcontainers (PostgreSQL + Redis thật); Multi-thread stress test với JUnit 5 + `CountDownLatch`; Dockerfile multi-stage; Docker Compose full stack; GitHub Actions CI pipeline; Spring Actuator & Prometheus metrics.

---

## Tuần 1 — Khởi tạo Base Giao Vặt & Cấu trúc Backend Spring Boot (Java 17 LTS)

### Thứ 2 — Môi trường Java 17 LTS & Khởi tạo dự án Giao Vặt (2h)
- [ ] Cài đặt JDK 17 (Java 17 LTS), IntelliJ IDEA, Git, Maven (hoặc Gradle wrapper); kiểm tra `java -version`, `mvn -version`, `git --version`.
- [ ] Khởi tạo dự án Spring Boot 3.x (Java 17) cho Giao Vặt qua Spring Initializr (dependencies: `spring-boot-starter-web`, `lombok`, `spring-boot-starter-test`).
- [ ] Khám phá cấu trúc thư mục của 1 Backend Spring Boot chuẩn: `src/main/java`, `src/main/resources`, `pom.xml` (quản lý dependency, plugin compiler target 17).
- [ ] Tìm hiểu điểm khởi chạy ứng dụng: `@SpringBootApplication`, phương thức `main`, Spring ApplicationContext khởi động ra sao.
- [ ] Tạo repository `giao-vat-platform`; commit initial codebase chuẩn.

### Thứ 3 — Controller đầu tiên & Cấu trúc Phân tầng Package (2h)
- [ ] Học cấu trúc phân tầng (Package Structure) chuẩn của Spring Boot Backend: `controller`, `service`, `repository`, `model`/`entity`, `dto`, `config`, `exception`.
- [ ] Tạo Controller đầu tiên: `PingController` với endpoint `GET /api/v1/ping` trả về trạng thái hệ thống `"Giao Vat Platform v1 - Ready"`.
- [ ] Tìm hiểu cơ chế HTTP Request/Response, annotation `@RestController`, `@GetMapping`.
- [ ] Học cú pháp Java nền tảng: Biến, kiểu dữ liệu primitive vs reference, `String`, hằng số (`final`), quy ước đặt tên (CamelCase, Clean Code).
- [ ] Test endpoint qua trình duyệt hoặc curl/Postman; commit.

### Thứ 4 — Controller API Đơn Hàng Đầu Tiên (`OrderController` Skeleton) (2h)
- [ ] Tạo `OrderController` với 2 endpoint cơ bản: `POST /api/v1/orders` (tạo đơn hàng) và `GET /api/v1/orders` (lấy danh sách đơn hàng).
- [ ] Học cách nhận dữ liệu trong Spring Boot: `@PostMapping`, `@RequestBody`, `@RequestParam`, `@PathVariable`.
- [ ] Khái niệm DTO (Data Transfer Object): Tạo `CreateOrderRequest` và `OrderResponse`.
- [ ] Học Java 17 `record`: Viết DTO bằng Java `record` (immutable data carrier gọn gàng) vs class truyền thống.
- [ ] Test gửi request JSON qua Postman/curl; commit.

### Thứ 5 — Inversion of Control (IoC), Dependency Injection (DI) & Tầng Service (2h)
- [ ] Học nguyên lý Inversion of Control (IoC) và Dependency Injection (DI) trong Spring Boot.
- [ ] Phân tách trách nhiệm: Controller chỉ nhận HTTP và trả response; Logic nghiệp vụ thuộc về Service.
- [ ] Tạo `OrderService` (đánh dấu `@Service`), inject vào `OrderController` qua Constructor Injection (Spring Best Practice, tránh dùng `@Autowired` trên field).
- [ ] Viết method đầu tiên trong `OrderService`: tạo đơn hàng mock và trả về `OrderResponse`.
- [ ] Review luồng đi của dữ liệu: Client $\rightarrow$ Controller $\rightarrow$ Service $\rightarrow$ Response; commit.

### Thứ 6 — Configuration, Spring Profiles & Clean Logging (2h)
- [ ] Cấu hình ứng dụng qua `application.yml`: cấu hình `server.port=8080`, context-path `/api`.
- [ ] Học Spring Profiles (`local`, `dev`, `test`): tách file `application-local.yml` và kích hoạt qua `spring.profiles.active`.
- [ ] Sử dụng SLF4J / Logback (`@Slf4j`): Ghi log khi nhận request tạo đơn, tuyệt đối không dùng `System.out.println`.
- [ ] Tự review git diff; dọn dẹp mã nguồn; commit.

### Thứ 7 — Base Project Lab & API Verification (5h)
- [ ] 2h: Hoàn thiện khung base project Giao Vặt chạy mượt mà trên Java 17 LTS + Spring Boot 3.
- [ ] 1h: Viết test khởi động context (`@SpringBootTest` contextLoads) và test endpoint `/api/v1/ping`.
- [ ] 1h: Thiết lập tài liệu API cơ bản bằng SpringDoc OpenAPI / Swagger (`/swagger-ui.html`).
- [ ] 1h: Viết README giới thiệu kiến trúc base của Giao Vặt; commit và tag `giaovat-base-v0`.

**Chủ nhật:** Nghỉ; tự kiểm tra kiến trúc Spring Boot và request lifecycle.

---

## Tuần 2 — Nghiệp Vụ Đơn Hàng: Học Cú Pháp, Điều Kiện & Vòng Lặp Java Thực Chiến

### Thứ 2 — Model Nghiệp Vụ Giao Vặt, Kiểu Dữ Liệu & Enums (2h)
- [ ] Tạo class nghiệp vụ trung tâm: `Order` (chứa: `id`, `creatorId`, `runnerId`, `pickupAddress`, `dropoffAddress`, `distanceInKm`, `offeredPrice`, `minPrice`, `status`, `category`, `createdAt`).
- [ ] Học các kiểu dữ liệu số thực và tiền tệ trong Java: `BigDecimal` vs `long` (lý do không dùng `double`/`float` cho tiền tệ vì lỗi sai số dấu phẩy động).
- [ ] Học Java Enum: Tạo `OrderCategory` (`RIDE`, `FOOD`, `PARCEL`) và `OrderStatus` (`OPEN`, `ACCEPTED`, `PICKED_UP`, `IN_TRANSIT`, `COMPLETED`, `CANCELLED`).
- [ ] Viết logic khởi tạo đơn hàng với trạng thái mặc định ban đầu là `OPEN`; commit.

### Thứ 3 — Câu Điều Kiện (`if/else`, switch) & Logic Tính Cước Sàn (2h)
- [ ] Học câu điều kiện Java (`if/else`, ternary operator `?:`).
- [ ] Viết method tính cước sàn tối thiểu `calculateMinPrice(distanceInKm, category)`:
  - Nếu khoảng cách $\le 0$: báo lỗi logic không hợp lệ.
  - Cước phí cơ sở theo loại đơn: `RIDE` (10.000đ/km), `FOOD` (12.000đ/km), `PARCEL` (8.000đ/km).
  - Sử dụng `switch expression` (tính năng mạnh mẽ của Java 17) để trả về đơn giá theo `OrderCategory`.
- [ ] Kiểm tra điều kiện tạo đơn: `offeredPrice` do khách đưa ra phải $\ge$ `minPrice` hệ thống gợi ý.
- [ ] Viết bài test nhỏ kiểm tra các nhánh điều kiện tính giá; commit.

### Thứ 4 — Máy Trạng Thái Đơn Hàng & Switch Pattern Matching (2h)
- [ ] Học quản lý trạng thái đơn hàng (State Transitions):
  - Đơn chỉ có thể nhận (`ACCEPTED`) khi đang ở trạng thái `OPEN`.
  - Đơn chỉ có thể chuyển sang `PICKED_UP` khi đang ở trạng thái `ACCEPTED`.
  - Khách chỉ được hủy (`CANCELLED`) khi đơn chưa có Runner nhận (`OPEN`).
- [ ] Viết hàm kiểm tra và chuyển trạng thái `canTransitionTo(currentStatus, targetStatus)` bằng `switch`.
- [ ] Tránh nested `if/else` sâu; áp dụng kỹ thuật "Early Return / Guard Clauses" để code trong sáng, dễ đọc; commit.

### Thứ 5 — Vòng Lặp Java (`for`, `while`) & Duyệt Danh Sách Đơn Bảng Tin (2h)
- [ ] Học các loại vòng lặp trong Java: `for` truyền thống, enhanced `for-each`, `while`, `break`, `continue`.
- [ ] Quản lý danh sách đơn hàng in-memory: Duyệt qua danh sách đơn hàng để tìm kiếm:
  - Tìm các đơn hàng có địa chỉ đón trùng với từ khóa tìm kiếm của Runner.
  - Lọc ra các đơn hàng thỏa mãn điều kiện cước phí tối thiểu Runner mong muốn.
  - Dùng `while` mô phỏng việc sinh ID tự tăng an toàn không trùng lặp.
- [ ] Phân tích độ phức tạp thời gian (Big-O) của thao tác duyệt danh sách: $O(N)$; commit.

### Thứ 6 — Method Refactoring & Clean Business Logic (2h)
- [ ] Tối ưu hóa code trong `OrderService`: Một method chỉ làm một nhiệm vụ duy nhất (Single Responsibility Principle).
- [ ] Tách các hàm validate riêng biệt: `validateCreateOrderRequest()`, `validatePrice()`, `validateStateTransition()`.
- [ ] Đặt tên biến và method mang tính biểu đạt cao theo từ điển nghiệp vụ Giao Vặt (xem `CONTEXT.md`).
- [ ] Tự review diff; loại bỏ mã lặp (DRY - Don't Repeat Yourself); commit.

### Thứ 7 — Order Flow In-Memory Lab (5h)
- [ ] 2h: Hoàn thiện bộ API in-memory: Đăng đơn (`POST /api/v1/orders`), Xem bảng tin các đơn `OPEN` (`GET /api/v1/orders/feed`), Runner nhận đơn (`POST /api/v1/orders/{id}/claim`), Hủy đơn (`POST /api/v1/orders/{id}/cancel`).
- [ ] 1h: Kiểm tra kỹ toàn bộ logic điều kiện (biên khoảng cách, giá âm, nhận đơn đã bị claim...).
- [ ] 1h: Viết tài liệu mô tả luồng nghiệp vụ đơn hàng và máy trạng thái.
- [ ] 1h: Commit và dọn dẹp mã nguồn.

---

## Tuần 3 — Đóng Gói OOP, Strategy Pattern Tính Giá & Quản Lý In-Memory Bằng Java Collections

### Thứ 2 — Tính Đóng Gói (Encapsulation) & Immutability trong Giao Vặt (2h)
- [ ] Học 4 tính chất OOP: Encapsulation, Inheritance, Polymorphism, Abstraction.
- [ ] Encapsulation thực chiến trên class `Order`:
  - Đặt các field là `private`; không tạo setter bừa bãi làm hỏng tính toàn vẹn trạng thái đơn hàng.
  - Thay thế setter bằng các phương thức nghiệp vụ có chủ đích: `claimByRunner(runnerId)`, `markAsPickedUp()`, `complete()`.
  - Đảm bảo tính bất biến (Immutability): Tạo Value Object `Location` (`address`, `lat`, `lng`) bằng Java 17 `record`.
- [ ] Review các nguy cơ khi setter cho phép ghi đè trạng thái sai lệch; commit.

### Thứ 3 — Composition over Inheritance & Thiết Kế Thực Thể (2h)
- [ ] Học nguyên lý "Ưu tiên Composition hơn Inheritance" (Composition over Inheritance).
- [ ] Thiết kế quan hệ giữa các thực thể Giao Vặt:
  - `Order` sở hữu `PickupLocation` và `DropoffLocation` (Composition - Has-a relationship).
  - Tạo `User` đóng gói thông tin người dùng (`id`, `fullName`, `phoneNumber`, `role`), phân tách rõ Creator vs Runner.
  - Tránh bẫy kế thừa sai lầm (ví dụ: không kế thừa `Order` thành `FoodOrder`, mà dùng enum thuộc tính hoặc strategy).
- [ ] Viết test đảm bảo tính độc lập giữa các thực thể; commit.

### Thứ 4 — Interface, Polymorphism & GoF Strategy Pattern Tính Giá Cước (2h)
- [ ] Học Interface, Abstract Class, Polymorphism (Tính đa hình), Dependency Inversion.
- [ ] Áp dụng **Strategy Pattern** cho bài toán tính cước phí Giao Vặt (Module 2):
  - Tạo interface `PricingStrategy` với method `calculatePrice(distanceInKm)`.
  - Triển khai `StandardPricingStrategy` (giá cước ngày thường).
  - Triển khai `SurgePricingStrategy` (nhân hệ số giờ cao điểm 1.5x).
  - Triển khai `BadWeatherPricingStrategy` (nhân hệ số trời mưa 1.3x).
- [ ] Dùng Spring `@Component` và `@Qualifier` hoặc Factory để chọn strategy linh hoạt theo điều kiện; commit.

### Thứ 5 — Java Collections Nền Tảng: List & Map Quản Lý Bảng Tin Đơn Hàng (2h)
- [ ] Học Java Collections Framework: Hierarchy của `Collection`, `List`, `Set`, `Map`.
- [ ] `ArrayList` vs `LinkedList`: Hiệu năng truy xuất ngẫu nhiên $O(1)$ vs chèn/xóa $O(N)$ trong bảng tin đơn hàng.
- [ ] `HashMap` vs `ConcurrentHashMap`:
  - Lưu trữ danh sách đơn hàng in-memory dạng Key-Value (`Map<Long, Order>`).
  - Tìm kiếm đơn theo ID với độ phức tạp $O(1)$.
  - Hiểu sâu cơ chế bên trong của `HashMap`: Hash function, Array of Buckets, Hash Collision (Chaining bằng LinkedList / Red-Black Tree khi bucket $\ge 8$), Load Factor (0.75), Rehashing.
  - Hợp đồng bất biến: `equals()` và `hashCode()` contract — tại sao override `equals` bắt buộc phải override `hashCode`.
- [ ] Test tìm kiếm và thêm đơn hàng vào Map; commit.

### Thứ 6 — Java Collections Nâng Cao: Set & PriorityQueue (2h)
- [ ] `HashSet` / `LinkedHashSet`: Quản lý danh sách ID đơn đã hoàn tất hoặc danh sách mã khuyến mãi độc nhất (không trùng lặp).
- [ ] `PriorityQueue` (Hàng đợi ưu tiên):
  - Ứng dụng sắp xếp bảng tin đơn hàng: Đơn có cước phí đề xuất (`offeredPrice`) cao hơn hoặc thời gian chờ lâu hơn sẽ được ưu tiên xếp lên đầu queue.
  - Học cơ chế Binary Heap bên dưới `PriorityQueue`.
- [ ] Viết test so sánh thứ tự pick đơn khi dùng Queue thường vs PriorityQueue; commit.

### Thứ 7 — Collections & Strategy Lab (5h)
- [ ] 2h: Refactor toàn bộ tầng lưu trữ in-memory của Giao Vặt sang dùng `ConcurrentHashMap<Long, Order>` và `PriorityQueue`.
- [ ] 1h: Tích hợp Strategy Pattern tính giá cước động dựa trên thời gian request (giờ cao điểm).
- [ ] 1h: Viết test cho `PricingStrategy` và các thao tác CRUD in-memory.
- [ ] 1h: Commit và tổng kết bài học về cấu trúc dữ liệu.

---

## Tuần 4 — Xử Lý Lỗi Tập Trung (Domain Exceptions), Java Stream API & Báo Cáo Doanh Thu

### Thứ 2 — Phân Cấp Exception & Domain Exceptions Giao Vặt (2h)
- [ ] Học cơ chế xử lý ngoại lệ trong Java: `Throwable`, `Error`, `Exception` (Checked vs Unchecked / `RuntimeException`).
- [ ] Tại sao trong Spring Boot Backend hiện đại nên ưu tiên Unchecked Domain Exceptions?
- [ ] Tạo bộ Custom Domain Exceptions cho Giao Vặt:
  - `OrderNotFoundException` (khi không tìm thấy ID đơn hàng).
  - `InvalidOrderStateException` (khi chuyển trạng thái sai quy tắc, ví dụ đơn đã nhận rồi mà Runner khác đòi nhận lại).
  - `PriceBelowMinimumException` (khi khách trả giá thấp hơn giá sàn).
- [ ] Sử dụng từ khóa `throw`, `throws`, khối `try/catch/finally`; commit.

### Thứ 3 — Chuẩn Hóa Lỗi API với `@RestControllerAdvice` & RFC 7807 (2h)
- [ ] Xây dựng Global Exception Handler tập trung bằng `@RestControllerAdvice` và `@ExceptionHandler`.
- [ ] Chuyển đổi các Domain Exception thành HTTP Response tương ứng:
  - `OrderNotFoundException` $\rightarrow$ `404 Not Found`.
  - `InvalidOrderStateException` $\rightarrow$ `409 Conflict`.
  - `PriceBelowMinimumException` $\rightarrow$ `400 Bad Request`.
- [ ] Chuẩn hóa payload lỗi theo chuẩn quốc tế **RFC 7807 ProblemDetail** (Spring 6 / Spring Boot 3 hỗ trợ native: `status`, `title`, `detail`, `instance`, `timestamp`).
- [ ] Không bao giờ để lộ stack trace thô ra ngoài client vì lý do bảo mật; commit.

### Thứ 4 — Lambda Expressions & Functional Interfaces (2h)
- [ ] Học lập trình hàm trong Java: Anonymous class vs Lambda expressions `() -> {}`.
- [ ] Các Functional Interfaces cốt lõi trong `java.util.function`:
  - `Predicate<T>`: Kiểm tra điều kiện (ví dụ: `order -> order.getStatus() == OrderStatus.OPEN`).
  - `Function<T, R>`: Biến đổi dữ liệu (ví dụ: chuyển `Order` thành `OrderResponse`).
  - `Consumer<T>`: Tiêu thụ dữ liệu (ví dụ: gửi thông báo).
  - `Supplier<T>`: Cung cấp dữ liệu.
- [ ] Method References (`Order::getId`, `System.out::println`); commit.

### Thứ 5 — Java Stream API Thực Chiến (2h)
- [ ] Khái niệm luồng xử lý dữ liệu Stream (nguồn, intermediate operations, terminal operations).
- [ ] Các thao tác xử lý danh sách đơn hàng Giao Vặt bằng Stream:
  - `filter()`: Lọc các đơn đang ở trạng thái `OPEN` và có khoảng cách $\le 5$km.
  - `map()`: Biến đổi danh sách thực thể `Order` sang danh sách `OrderResponse` DTO.
  - `sorted()`: Sắp xếp đơn theo cước phí giảm dần (`Comparator.comparing(Order::getOfferedPrice).reversed()`).
  - `distinct()`, `limit()`, `skip()` (hỗ trợ phân trang in-memory).
  - `collect(Collectors.toList())` / Java 16+ `.toList()`.
- [ ] Test stream với danh sách rỗng và null; commit.

### Thứ 6 — Stream Collectors Nâng Cao & Java 17 Optional (2h)
- [ ] Thống kê doanh thu Runner bằng `Collectors`:
  - `groupingBy(Order::getCategory)`: Nhóm đơn hàng theo danh mục.
  - `summarizingDouble(Order::getOfferedPrice)`: Tính tổng doanh thu, cước phí trung bình, đơn giá cao nhất/thấp nhất.
  - `counting()`: Đếm số đơn hoàn tất theo từng Runner.
- [ ] Học `Optional<T>`: Tránh triệt để lỗi kinh điển `NullPointerException` (NPE).
- [ ] Viết method `findOrderById(Long id)` trả về `Optional<Order>`, sử dụng `.orElseThrow(() -> new OrderNotFoundException(id))`; commit.

### Thứ 7 — Reporting & Stream API Lab (5h)
- [ ] 2h: Viết API thống kê báo cáo cho Giao Vặt (`GET /api/v1/orders/reports/summary`) sử dụng toàn bộ sức mạnh của Stream API.
- [ ] 1h: Export dữ liệu báo cáo ra định dạng CSV/Text sử dụng try-with-resources an toàn tài nguyên.
- [ ] 1h: Viết unit tests kiểm tra toàn bộ luồng exception và logic thống kê Stream API.
- [ ] 1h: Commit và tổng kết tuần.

---

## Tuần 5 — Git, Maven, Unit Testing Thực Chiến & Nền Tảng JVM / Concurrency trên Java 17

### Thứ 2 — Git Workflow Thực Chiến Trong Team (2h)
- [ ] Học Git fundamentals: Working Directory, Staging Area, Local Repository, Remote.
- [ ] Branching model: `main`, `develop`, feature branches (`feature/order-lifecycle`, `feature/pricing-strategy`).
- [ ] Các lệnh thiết yếu: `branch`, `checkout`/`switch`, `merge`, `rebase`, `stash`, `cherry-pick`, `revert`.
- [ ] Quy ước commit chuẩn Conventional Commits (`feat:`, `fix:`, `refactor:`, `test:`, `docs:`).
- [ ] Thực hành cố ý tạo conflict trên code Giao Vặt và giải quyết conflict (merge conflict resolution); commit.

### Thứ 3 — Maven Build Tool & Dependency Management (2h)
- [ ] Cấu trúc `pom.xml`: `groupId`, `artifactId`, `version`, `packaging`.
- [ ] Quản lý dependency: Dependency Scopes (`compile`, `provided`, `runtime`, `test`).
- [ ] Maven Build Lifecycle: `validate` $\rightarrow$ `compile` $\rightarrow$ `test` $\rightarrow$ `package` $\rightarrow$ `verify` $\rightarrow$ `install`.
- [ ] Phân tích và xử lý xung đột dependency (Dependency Convergence & Exclusion); commit.

### Thứ 4 — Unit Testing Chuẩn với JUnit 5 (2h)
- [ ] Nguyên lý kiểm thử: Mô hình Arrange-Act-Assert (AAA), First-Class Tests, Red-Green-Refactor.
- [ ] JUnit 5 Annotations: `@Test`, `@BeforeEach`, `@AfterEach`, `@DisplayName`, `@ParameterizedTest` (kiểm thử tham số hóa nhiều trường hợp khoảng cách và giá cước).
- [ ] Viết unit test toàn diện cho logic tính cước sàn và chuyển trạng thái đơn hàng trong `OrderService`.
- [ ] Assertions: `assertEquals`, `assertThrows`, `assertNotNull`, AssertJ Fluent Assertions (`assertThat`); commit.

### Thứ 5 — Mocking Dependencies với Mockito (2h)
- [ ] Bản chất của Mocking: Phân biệt Dummy, Stub, Spy, Mock, Fake.
- [ ] Mockito annotations: `@Mock`, `@InjectMocks`, `@Spy`, `@ExtendWith(MockitoExtension.class)`.
- [ ] Cấu hình hành vi giả lập: `when(...).thenReturn(...)`, `when(...).thenThrow(...)`.
- [ ] Xác minh tương tác: `verify(mock, times(1)).doSomething(...)`.
- [ ] Viết unit test cho `OrderController` độc lập với Service; đánh giá trade-off giữa Unit Test độc lập vs Integration Test; commit.

### Thứ 6 — JVM Memory Layout & Concurrency Primitives trên Java 17 (2h)
- [ ] Học kiến trúc bộ nhớ JVM:
  - **Heap Memory**: Young Generation (Eden, Survivor 0/1), Old Generation.
  - **Stack Memory**: Stack Frame, lưu biến cục bộ (Local Variables) và tham chiếu phương thức; phân biệt rõ Pass-by-value trong Java.
  - **Metaspace**: Lưu metadata của class, static fields.
  - Cơ chế Garbage Collection (GC) căn bản: Mark & Sweep, Stop-The-World.
- [ ] Nền tảng Concurrency trên Java 17:
  - Java Memory Model (JMM): Visibility, Instruction Reordering, Happens-Before relationship.
  - Từ khóa `volatile` (đảm bảo visibility qua CPU cache) vs `synchronized` (đảm bảo atomicity & mutual exclusion).
  - `AtomicInteger`, `AtomicLong` và cơ chế phần cứng CAS (Compare-And-Swap).
  - Tạo bài lab đa luồng nhỏ: 10 threads cùng cộng dồn biến đếm đơn hàng để chứng minh Lost Update nếu không đồng bộ hóa; commit.

### Thứ 7 — Java Core & Quality Assessment (5h)
- [ ] 2h: Rà soát toàn bộ codebase Giao Vặt in-memory, đảm bảo Clean Code và test coverage đạt $\ge 80\%$ cho tầng Service.
- [ ] 1h: Tự giải 3 bài toán DSA căn bản liên quan đến Array, HashMap, Two Pointers.
- [ ] 1h: Mock interview tự vấn đáp 20 câu hỏi trọng tâm về Java Core, OOP, Collections, JVM Memory.
- [ ] 1h: Tag release Git: `giaovat-core-passed`.

---

## Tuần 6 — Tái Cấu Trúc Spring Core & Spring MVC Nâng Cao (Chuẩn Hóa 3 Layers)

### Thứ 2 — Spring IoC Container & Bean Lifecycle Internals (2h)
- [ ] Học sâu cơ chế Spring IoC: `ApplicationContext` vs `BeanFactory`.
- [ ] Bean Scopes: Singleton (mặc định), Prototype, Request, Session.
- [ ] Chi tiết vòng đời của một Spring Bean (**Spring Bean Lifecycle**):
  - `BeanDefinition` $\rightarrow$ Instantiation (khởi tạo instance) $\rightarrow$ Populate Properties (tiêm thuộc tính) $\rightarrow$ Aware Interfaces (`BeanNameAware`, `ApplicationContextAware`) $\rightarrow$ `BeanPostProcessor.postProcessBeforeInitialization` $\rightarrow$ `@PostConstruct` / `InitializingBean` $\rightarrow$ `BeanPostProcessor.postProcessAfterInitialization` $\rightarrow$ Bean sẵn sàng sử dụng $\rightarrow$ `@PreDestroy` / `DisposableBean`.
- [ ] Viết code thực nghiệm in log từng bước của Bean Lifecycle; commit.

### Thứ 3 — Spring AOP, Proxy Internals & Self-Invocation Trap (2h)
- [ ] Học nguyên lý Aspect-Oriented Programming (AOP): Pointcut, Advice, JoinPoint, Aspect.
- [ ] Cơ chế Spring Proxy:
  - **JDK Dynamic Proxy**: Dựa trên Interface (Java Reflection).
  - **CGLIB Proxy**: Tạo subclass bằng bytecode runtime (mặc định trong Spring Boot).
- [ ] Tái hiện và giải thích bẫy kinh điển: **`@Transactional` / `@Async` Self-Invocation Trap**:
  - Khi một method trong class tự gọi trực tiếp một method khác có `@Transactional` cùng class, proxy bị bypass hoàn toàn $\rightarrow$ Transaction không bao giờ được mở!
  - Thực hành 3 cách khắc phục chuẩn: (1) Tách sang Bean/Service khác, (2) Tự inject chính mình bằng `@Lazy`, (3) Dùng `TransactionTemplate`; commit.

### Thứ 4 — Spring MVC Architecture & Request Lifecycle (2h)
- [ ] Cơ chế hoạt động của `DispatcherServlet`: Client request $\rightarrow$ `HandlerMapping` $\rightarrow$ `HandlerAdapter` $\rightarrow$ Controller $\rightarrow$ `HttpMessageConverter` (Jackson JSON) $\rightarrow$ Response.
- [ ] Custom Filters và Interceptors:
  - Tạo `RequestLoggingFilter` để ghi nhận request time, URI và sinh `traceId`.
  - Phân biệt Filter (tầng Servlet container) vs Interceptor (tầng Spring MVC); commit.

### Thứ 5 — DTO Validation Nâng Cao với Jakarta Bean Validation (2h)
- [ ] Sử dụng `spring-boot-starter-validation`.
- [ ] Các validation annotations trên `CreateOrderRequest`: `@NotNull`, `@NotBlank`, `@Positive`, `@Min`, `@Size`.
- [ ] Viết Custom Validator: Tạo annotation `@ValidLocation` để kiểm tra tọa độ hợp lệ (latitude trong khoảng $[-90, 90]$, longitude trong khoảng $[-180, 180]$).
- [ ] Xử lý `MethodArgumentNotValidException` trong Global Exception Handler để trả về danh sách chi tiết từng trường bị lỗi kèm message rõ ràng; commit.

### Thứ 6 — Chuẩn Hóa Kiến Trúc 3 Tầng (Controller – Service – Repository Seam) (2h)
- [ ] Phân định ranh giới (Seam) kiến trúc:
  - **Controller Layer**: Chỉ chịu trách nhiệm tiếp nhận HTTP, validation cú pháp, mapping DTO.
  - **Service Layer**: Nắm giữ toàn bộ nghiệp vụ thuần túy của Giao Vặt, không phụ thuộc vào Web hay Servlet API.
  - **Repository Layer (Interface Seam)**: Tạo interface `OrderRepository` để trừu tượng hóa việc lưu trữ dữ liệu (tách rời khỏi cách lưu cụ thể).
- [ ] Viết một implementation tạm thời `InMemoryOrderRepository` implements `OrderRepository` để chuẩn bị cho việc tích hợp Database vào tuần sau; commit.

### Thứ 7 — REST API Standardization Lab (5h)
- [ ] 2h: Hoàn thiện toàn bộ bộ API Giao Vặt chuẩn hóa 3-layer: CRUD Đơn hàng, Feed bảng tin, Claim đơn hàng, Chuyển trạng thái, Báo cáo.
- [ ] 1h: Tích hợp đầy đủ tài liệu OpenAPI/Swagger 3 với `@Operation`, `@ApiResponse`, schema models.
- [ ] 1h: Viết test controller với `MockMvc` (kiểm tra status code 200, 201, 400 validation, 404 not found, 409 conflict).
- [ ] 1h: Commit và sẵn sàng bước sang tầng Database.

---

## Tuần 7 — SQL, Database Relational, B-Tree Index & Spring Data JPA

### Thứ 2 — Thiết Kế Database Relational & Migration Flyway (2h)
- [ ] Học thiết kế cơ sở dữ liệu quan hệ: Bảng, Primary Key (PK), Foreign Key (FK), Chuẩn hóa 1NF–3NF, Constraints.
- [ ] Thiết kế ERD chuẩn cho Giao Vặt:
  - Bảng `users`: `id`, `email`, `password_hash`, `full_name`, `phone_number`, `role` (`ROLE_CREATOR`, `ROLE_RUNNER`).
  - Bảng `orders`: `id`, `creator_id`, `runner_id`, `pickup_address`, `dropoff_address`, `distance_km`, `min_price`, `offered_price`, `status`, `version`, `created_at`, `updated_at`.
- [ ] Tạo file migration đầu tiên bằng Flyway: `src/main/resources/db/migration/V1__init_schema.sql`; commit.

### Thứ 3 — SQL CRUD, JOIN & Cấu Trúc B-Tree Index (2h)
- [ ] Học SQL nâng cao: INSERT, UPDATE, DELETE, SELECT, INNER/LEFT JOIN, GROUP BY, HAVING.
- [ ] Học cấu trúc **B-Tree Index**: Cấu trúc cây cân bằng $O(\log N)$, leaf nodes linked list cho range query, Clustered Index (Primary Key) vs Secondary Index; phân biệt Index Seek vs Index Scan vs Full Table Scan.
- [ ] Tạo composite index trên `(status, created_at)` để tối ưu câu truy vấn lấy danh sách đơn chờ nhận trên bảng tin.
- [ ] Viết 10 câu query thực chiến cho Giao Vặt: lấy danh sách đơn `OPEN` mới nhất, lịch sử đơn theo Creator, tổng thu nhập theo Runner; seed 1.000 dòng dữ liệu test; commit.

### Thứ 4 — Spring Data JPA Entity & Repository Mapping (2h)
- [ ] Học `@Entity`, `@Table`, `@Id`, `@GeneratedValue(strategy = GenerationType.IDENTITY)`, `JpaRepository`.
- [ ] Mapping entity `User` và `Order`; dùng `@Enumerated(EnumType.STRING)` cho `OrderStatus` và `OrderCategory`.
- [ ] Viết Repository methods: `findByStatusOrderByCreatedAtDesc(OrderStatus status, Pageable pageable)`.
- [ ] Viết repository test sử dụng Testcontainers (PostgreSQL container thật); commit.

### Thứ 5 — Relationships, Cascade & Xử Lý N+1 Query Problem (2h)
- [ ] Học `@ManyToOne`, `@OneToMany`, owning side, FetchType (`LAZY` vs `EAGER`), cascade options.
- [ ] Mapping quan hệ: Một `User` (Creator) có nhiều `Order`; một `User` (Runner) có thể thụ lý nhiều `Order`.
- [ ] Luôn đặt `FetchType.LAZY` cho quan hệ to-one; kiểm soát và reproduce lỗi **N+1 Query Problem** qua SQL log.
- [ ] Giải quyết N+1 bằng `JOIN FETCH` trong JPQL hoặc `@EntityGraph`; commit.

### Thứ 6 — Transactions, Isolation Levels, MVCC & Locking Nền Tảng (2h)
- [ ] Học `@Transactional`: Transaction boundaries, rollback rules (`rollbackFor = Exception.class`).
- [ ] Học **Transaction Isolation Levels**: READ UNCOMMITTED, READ COMMITTED, REPEATABLE READ, SERIALIZABLE; phân tích 4 hiện tượng dị thường: **Dirty Read**, **Non-repeatable Read**, **Phantom Read**, **Lost Update**.
- [ ] Cơ chế **MVCC** (Multi-Version Concurrency Control) trong PostgreSQL / MySQL InnoDB (Undo Log, Read View để đọc non-blocking snapshot).
- [ ] **Khóa Lạc Quan (Optimistic Locking) nền tảng:** Thêm trường `@Version private Long version;` trên thực thể `Order` để bảo vệ tranh chấp khi nhiều Runner cùng nhận 1 đơn; commit.

### Thứ 7 — Chuyển Toàn Bộ Giao Vặt API Sang Database (5h)
- [ ] 2h: Thay thế `InMemoryOrderRepository` bằng `JpaOrderRepository`; hoàn thiện mapping Entity $\leftrightarrow$ DTO.
- [ ] 1h: Thêm phân trang (Pagination) và sắp xếp (Sorting) cho API bảng tin đơn hàng bằng `Pageable`.
- [ ] 1h: Viết Integration Tests kiểm tra lưu trữ và truy vấn DB thật với Testcontainers.
- [ ] 1h: Commit và dọn dẹp mã nguồn.

---

## Tuần 8 — Hoàn Thiện Monolith v0 Giao Vặt & Quality Gate 1

### Thứ 2 — Order Lifecycle & Runner Claim Order Flow Hoàn Chỉnh (2h)
- [ ] Nối thông toàn bộ luồng từ DB:
  - Creator tạo đơn (`POST /api/v1/orders`) $\rightarrow$ Lưu DB trạng thái `OPEN`.
  - Runner duyệt bảng tin (`GET /api/v1/orders/feed`) $\rightarrow$ Query DB index `(status, created_at)`.
  - Runner nhận đơn (`POST /api/v1/orders/{id}/claim`) $\rightarrow$ Kiểm tra trạng thái và cập nhật `runner_id`, đổi status sang `ACCEPTED` dưới sự bảo vệ của `@Version`.
- [ ] Test validation nghiệp vụ: Chặn Runner nhận đơn không phải `OPEN`, chặn Creator tự nhận đơn của chính mình; commit.

### Thứ 3 — Error Handling Chuẩn Hóa & RFC 7807 (2h)
- [ ] Rà soát toàn bộ HTTP status code, format timestamp UTC, URL path.
- [ ] Xử lý `OptimisticLockingFailureException` $\rightarrow$ Trả về `409 Conflict` kèm message `"Đơn hàng đã được nhận bởi tài xế khác"`.
- [ ] Cập nhật tài liệu OpenAPI với toàn bộ mã lỗi chuẩn; commit.

### Thứ 4 — Integration Test Toàn Diện (2h)
- [ ] Viết test Controller bằng `MockMvc` kết hợp `@SpringBootTest` và PostgreSQL container thật.
- [ ] Viết test đa luồng cơ bản với `CountDownLatch` (2 threads cùng gọi claim 1 đơn $\rightarrow$ 1 thành công, 1 nhận 409).
- [ ] Chạy `mvn test` pass 100%; kiểm tra không có flaky test; commit.

### Thứ 5 — Performance Profiling & Query Optimization (2h)
- [ ] Chạy `EXPLAIN ANALYZE` trên câu query bảng tin đơn hàng; so sánh chi phí trước và sau khi có B-Tree index `(status, created_at)`.
- [ ] Kiểm tra dung lượng query, đảm bảo không bị N+1 khi trả về thông tin Creator kèm theo đơn hàng.
- [ ] Ghi lại kết quả benchmark vào file `docs/benchmarks/foundation-query.md`; commit.

### Thứ 6 — Technical Interview Gate 1 (2h)
- [ ] Tự vấn đáp 15 câu Java Core (OOP, Collections, Exceptions, Memory), 15 câu Spring Boot (IoC, Lifecycle, Proxy trap, MVC, JPA), 10 câu SQL/Transaction (Isolation, Index, MVCC).
- [ ] Làm 2 bài DSA Easy trong 45 phút.
- [ ] Ghi nhận các điểm còn chưa tự tin vào sổ tay kỹ thuật.

### Thứ 7 — Demo Gate 1: Sẵn Sàng Bước Sang Giai Đoạn 2 (5h)
- [ ] 2h: Thử thách tái tạo lại một CRUD entity độc lập từ đầu không nhìn tài liệu (để kiểm tra độ nhuần nhuyễn).
- [ ] 1h: Chạy demo toàn bộ luồng Monolith v0 và quay video demo ngắn.
- [ ] 1h: Hoàn thiện README, ERD, hướng dẫn chạy ứng dụng bằng `mvn spring-boot:run`.
- [ ] 1h: Tag release Git: `giaovat-foundation-ready`.

# GIAI ĐOẠN 2 — TUẦN 9–18
## Đủ Điều Kiện Apply Java Fresher & Mở Rộng Tư Duy Kiến Trúc Hệ Thống (Mục tiêu 12–15 triệu)

**Mục tiêu cốt lõi:** Hoàn thiện sản phẩm Giao Vặt v1 chuẩn sản xuất: Bảng tin đơn hàng `orders:open` trên Redis, cơ chế Runner claim đơn chống race condition bằng Concurrency Locking, phân quyền Creator vs Runner với Spring Security + JWT Stateless, Caching & Rate Limiting, Docker Compose, CI/CD GitHub Actions, deploy cloud và tài liệu chuẩn OpenAPI/ADR. Sau tuần 18 bắt đầu apply vị trí Java Fresher/Junior, không chờ học hết Senior.

> **TRIẾT LÝ PHƯƠNG PHÁP LUẬN TỪ GIAI ĐOẠN 2 TRỞ ĐI:**
>
> **1. Quy Trình 4 Bước: Học Lý Thuyết & Bức Tranh Tổng Thể ──► Phân Tích Trade-off ──► Chọn Phương Pháp Phù Hợp (ADR) ──► System Design & Thực Hành:**
> - Đối với các mảng kiến thức kỹ thuật lớn (Bảo mật/Auth, Caching, Concurrency/Locking, Asynchronous/Real-time, Message Queues, Microservices, Distributed Systems...):
>   - **Bước 1 — Lý thuyết & Bức tranh tổng quan (Landscape & Theory First):** Phải học lý thuyết trước để nắm được cái nhìn tổng quát về các phương pháp giải quyết bài toán đang có trong ngành (pattern catalog, protocol, under-the-hood mechanism). Không nhảy vào code một công nghệ khi chưa hiểu các phương pháp thay thế của nó.
>   - **Bước 2 — Phân tích Trade-off:** Không có giải pháp "tốt nhất", chỉ có giải pháp phù hợp với bài toán và ràng buộc kỹ thuật. Phân tích ma trận ưu/nhược điểm (Throughput, Latency, Data Consistency, Complexity, Resource Cost).
>   - **Bước 3 — Ra quyết định kiến trúc (Decision Making & ADR):** Chọn phương pháp phù hợp nhất cho bài toán cụ thể và viết Architectural Decision Record (ADR) giải thích rõ lý do chọn và lý do bác bỏ các phương án khác.
>   - **Bước 4 — System Design & Thực hành:** Hiện thực hóa giải pháp vào dự án hoặc lab thực nghiệm có đo lường đối chứng.
>
> **2. Nhận Định Sống Còn Về Phạm Vi Senior:**
> - Dự án **Giao Vặt** là một case study thực chiến tuyệt vời, là xương sống rèn luyện kỹ năng backend sâu (concurrency locking, in-memory queue, cache-aside, realtime SSE, idempotency, webhook).
> - **TUY NHIÊN, LÀM XONG PROJECT GIAO VẶT KHÔNG ĐẢM BẢO BAO QUÁT HẾT TOÀN BỘ ROADMAP!**
> - Roadmap này hướng tới **Senior Software Engineer**, và **Senior không bao giờ dừng lại ở một dự án duy nhất dù dự án đó đủ to**.
> - Senior đòi hỏi tư duy đa chiều, khả năng System Design cho nhiều loại hình hệ thống khác nhau (E-commerce Flash Sale, Chat System thời gian thực toàn cầu, Streaming/CDN, FinTech Ledger đối soát phân tán...), hiểu sâu bản chất Hệ thống phân tán (CAP, PACELC, Consensus Raft/Paxos, Multi-region Replication) và năng lực SRE/Leadership sản xuất.

---

## Tuần 9 — Authentication, RBAC & Security Architecture

### Thứ 2 — Lý Thuyết Tổng Quan Kiến Trúc Bảo Mật & Authentication (2h)
- [ ] Học lý thuyết tổng thể các mô hình xác thực trong ngành phần mềm:
  - Session-based Stateful Authentication (Cookie, Server Session, Redis Session Store) vs Token-based Stateless Authentication (JWT).
  - Phân tích ưu/nhược điểm: Khả năng scale ngang (horizontal scalability), rủi ro revoke token tức thì, kích thước header.
  - Phân biệt Authentication (Xác thực danh tính) vs Authorization (Phân quyền truy cập).
  - Khái niệm RBAC (Role-Based Access Control) vs ABAC (Attribute-Based Access Control).
- [ ] Lựa chọn kiến trúc cho Giao Vặt: Chọn JWT Stateless cho RESTful API, lưu refresh token trong Redis để hỗ trợ revoke; commit ADR.

### Thứ 3 — Password Hashing & Quản Lý Credential (2h)
- [ ] Học lý thuyết an toàn mật khẩu: Rainbow table attacks, cơ chế Salt, Key Stretching.
- [ ] So sánh các thuật toán mã hóa mật khẩu: MD5/SHA (bất an) vs BCrypt, PBKDF2, Argon2.
- [ ] Cấu hình Spring Security với `BCryptPasswordEncoder` (cost factor 10 hoặc 12).
- [ ] Tạo schema bảng `users` và migration Flyway `V2__security_users.sql`.
- [ ] Viết test đăng ký: chặn duplicate email/phone, password yếu, đảm bảo mật khẩu lưu trong DB đã hash 100%; commit.

### Thứ 4 — JWT Anatomy & Stateless Token Flow (2h)
- [ ] Học cấu trúc chuẩn JWT (JSON Web Token): Header (thuật toán ký), Payload (Claims: `sub`, `roles`, `exp`, `iat`), Signature.
- [ ] Cơ chế ký số HMAC-SHA256 vs RSA (Asymmetric).
- [ ] Xây dựng `JwtTokenProvider`: sinh Access Token (hạn 15–30 phút) chứa `user_id` và `role`.
- [ ] Xây dựng `JwtAuthenticationFilter` kế thừa `OncePerRequestFilter`: đọc Bearer token từ header, xác thực signature và nạp Principal vào `SecurityContextHolder`.
- [ ] Viết test: token hợp lệ, token sai chữ ký, token hết hạn; commit.

### Thứ 5 — Authorization & RBAC trong Giao Vặt (2h)
- [ ] Cấu hình Security Filter Chain và Method Security (`@PreAuthorize("hasRole('...')")`).
- [ ] Phân quyền nghiêm ngặt cho hai tác nhân chính:
  - **`ROLE_CREATOR` (Người tạo đơn):** Chỉ xem và hủy đơn của chính mình; tuyệt đối không thể gọi API nhận đơn (`claimOrder`).
  - **`ROLE_RUNNER` (Tài xế tiện chuyến):** Duyệt danh sách bảng tin đơn `OPEN`; nhận đơn và cập nhật tiến độ đơn mình đã nhận.
- [ ] Bảo mật dữ liệu nhạy cảm (Data Privacy): Ẩn số điện thoại khách hàng trên public feed; chỉ Runner nhận đơn thành công mới xem được số điện thoại Creator; commit.

### Thứ 6 — Refresh Token Rotation & Threat Modeling (2h)
- [ ] Học cơ chế **Refresh Token Rotation**: Mỗi lần dùng Refresh Token để lấy Access Token mới, hệ thống sẽ cấp một Refresh Token hoàn toàn mới và hủy Refresh Token cũ.
- [ ] Lưu trữ Refresh Token trong Redis với TTL (ví dụ 7 ngày); cơ chế phát hiện Replay Attack (nếu Refresh Token cũ bị dùng lại $\rightarrow$ thu hồi toàn bộ phiên của user).
- [ ] Xây dựng API `/api/v1/auth/refresh` và `/api/v1/auth/logout`.
- [ ] Viết tài liệu Threat Model ngắn gọn cho hệ thống auth; commit.

### Thứ 7 — Auth Integration & CORS/CSRF Hardening (5h)
- [ ] 2h: Hoàn thiện toàn bộ luồng Auth: Register $\rightarrow$ Login $\rightarrow$ Access Protected API $\rightarrow$ Refresh Token $\rightarrow$ Logout.
- [ ] 1h: Viết Integration Tests toàn diện cho các endpoint bảo mật với `@WithMockUser`.
- [ ] 1h: Cấu hình CORS an toàn (chỉ cho phép domain frontend được chỉ định), tắt CSRF vì API hoàn toàn stateless.
- [ ] 1h: Hoàn thiện README Security và commit code.

---

## Tuần 10 — Caching Architecture, Redis & Anti-Spam Rate Limiting

### Thứ 2 — Lý Thuyết Tổng Quan Caching Strategies trong System Design (2h)
- [ ] Học lý thuyết tổng thể về các chiến lược Caching trong kiến trúc phần mềm:
  - **Cache-Aside (Lazy Loading):** App đọc cache trước, miss thì đọc DB rồi ghi vào cache.
  - **Read-Through:** App chỉ nói chuyện với cache, cache tự nạp từ DB.
  - **Write-Through:** App ghi vào cache, cache ghi đồng bộ xuống DB.
  - **Write-Behind (Write-Back):** App ghi vào cache, cache ghi bất đồng bộ theo lô xuống DB (tốc độ cao nhưng rủi ro mất dữ liệu).
- [ ] Ba thảm họa Caching kinh điển và giải pháp:
  - **Cache Penetration:** Query key không tồn tại $\rightarrow$ hit thẳng DB $\rightarrow$ Giải pháp: Bloom Filter hoặc lưu Null Object có TTL ngắn.
  - **Cache Breakdown:** Hot key hết hạn $\rightarrow$ hàng nghìn request cùng dội xuống DB $\rightarrow$ Giải pháp: Mutex Lock hoặc Logical Expiration.
  - **Cache Avalanche:** Hàng loạt cache key cùng hết hạn cùng lúc $\rightarrow$ DB sập $\rightarrow$ Giải pháp: Thêm Random Jitter vào TTL.
- [ ] Cache Invalidation: *"Có hai điều khó nhất trong Khoa học Máy tính: đặt tên và xóa cache"*.

### Thứ 3 — Redis Data Structures & Thiết Kế Bảng Tin Giao Vặt (2h)
- [ ] Học sâu các cấu trúc dữ liệu Redis: String, Hash, List, Set, Sorted Set (ZSET), Bitmap, HyperLogLog.
- [ ] Thiết kế Bảng Tin Đơn Hàng (`Order Feed`) trên Redis:
  - Dùng **Sorted Set (ZSET)** key `orders:open`: Score là timestamp tạo đơn hoặc cước phí, Member là `orderId` $\rightarrow$ Hỗ trợ phân trang và sắp xếp siêu tốc $O(\log N + M)$.
  - Dùng **Hash** key `order:{id}`: Lưu snapshot chi tiết đơn hàng dạng JSON/Fields để Runner xem nhanh không cần chạm Database.
- [ ] Code API Runner lấy danh sách bảng tin trực tiếp từ Redis; commit.

### Thứ 4 — Đồng Bộ Trạng Thái Đơn Hàng & Cache-Aside (2h)
- [ ] Xử lý đồng bộ hai chiều (Redis $\leftrightarrow$ Database):
  - Khi Creator tạo đơn: Ghi DB $\rightarrow$ Đẩy `orderId` vào Redis ZSET `orders:open` $\rightarrow$ Lưu Hash `order:{id}`.
  - Khi Runner nhận đơn thành công (`OPEN` $\rightarrow$ `ACCEPTED`): Gỡ `orderId` khỏi Redis ZSET `orders:open` $\rightarrow$ Cập nhật trạng thái trong DB.
- [ ] Cơ chế Fallback an toàn: Nếu Redis tạm thời mất kết nối (Redis down), hệ thống tự động fallback query từ Database với index `(status, created_at)`.
- [ ] Viết test kết nối và test thao tác Redis với Docker Compose; commit.

### Thứ 5 — Docker Compose Redis & Serializer Chuẩn (2h)
- [ ] Khởi chạy Redis thông qua Docker Compose local.
- [ ] Cấu hình Spring Data Redis: `RedisTemplate<String, Object>`, cấu hình `GenericJackson2JsonRedisSerializer` hoặc `Jackson2JsonRedisSerializer` an toàn (tránh lỗ hổng Java Deserialization).
- [ ] Thiết lập Connection Pool với Lettuce: `max-active`, `max-idle`, `min-idle`.
- [ ] Viết test kiểm tra eviction policy và TTL; commit.

### Thứ 6 — Rate Limiting & Anti-Spam Bằng Thuật Toán Sliding Window (2h)
- [ ] Lý thuyết các thuật toán Rate Limiting: Fixed Window Counter, Sliding Window Log, Sliding Window Counter, Token Bucket, Leaky Bucket.
- [ ] Triển khai **Sliding Window Rate Limiter** bằng Redis ZSET (hoặc Lua script atomic):
  - Giới hạn Creator: Tối đa 5 request tạo đơn/phút (chống spam đơn ảo).
  - Giới hạn Runner: Tối đa 30 request refresh bảng tin/phút và tối đa 10 request claim đơn/phút (chống auto-clicker bot).
- [ ] Trả về mã lỗi HTTP `429 Too Many Requests` kèm header `Retry-After`; commit.

### Thứ 7 — Reliability, Latency Measurement & Concurrency Lab (5h)
- [ ] 2h: Hoàn thiện luồng Redis Feed + Cache-Aside + DB Fallback.
- [ ] 1h: Viết test đa luồng mô phỏng đồng thời 50 request vừa tạo đơn vừa pick đơn.
- [ ] 1h: Đo đạc và lập biểu đồ latency: So sánh thời gian phản hồi khi lấy bảng tin từ Redis ($<5$ms) so với query PostgreSQL trực tiếp ($30-50$ms).
- [ ] 1h: Ghi nhận bài học về Cache Consistency và commit code.

---

## Tuần 11 — Containerization, CI/CD Pipeline & Deployment

### Thứ 2 — Lý Thuyết Virtualization vs Containerization & 12-Factor App (2h)
- [ ] Học lý thuyết Containerization: Khác biệt giữa Virtual Machine (Hypervisor, Guest OS) vs Container (chia sẻ OS Kernel, cgroups, namespaces).
- [ ] 12-Factor App methodology cho Cloud-Native Backend: Config qua biến môi trường, Stateless processes, Port binding, Concurrency, Disposability.
- [ ] Viết Dockerfile Multi-stage tối ưu cho Spring Boot (Java 17 LTS):
  - Stage 1: Build source bằng Maven wrapper.
  - Stage 2: Chạy trên nền Eclipse Temurin 17 JRE Alpine nhỏ gọn ($<200$MB), tạo user non-root để tăng cường bảo mật.
- [ ] Build image và chạy container local; commit.

### Thứ 3 — Docker Compose Full-Stack Local Environment (2h)
- [ ] Viết file `docker-compose.yml` định nghĩa toàn bộ stack:
  - Dịch vụ backend: `app` (expose port 8080, healthcheck qua Spring Actuator).
  - Dịch vụ database: `postgres` (port 5432, persistent volume, init scripts).
  - Dịch vụ cache/queue: `redis` (port 6379).
- [ ] Cấu hình network bridge và dependencies (`depends_on` với condition `service_healthy`).
- [ ] Kiểm tra khả năng khởi động toàn bộ hệ thống bằng 1 lệnh duy nhất: `docker compose up -d`; commit.

### Thứ 4 — Lý Thuyết CI/CD & GitHub Actions Pipeline (2h)
- [ ] Học lý thuyết Continuous Integration & Continuous Delivery/Deployment.
- [ ] Cấu hình GitHub Actions workflow (`.github/workflows/ci.yml`):
  - Trigger: Mọi PR và Push vào nhánh `main`.
  - Các bước: Checkout code $\rightarrow$ Setup JDK 17 $\rightarrow$ Cache Maven dependencies $\rightarrow$ Run Unit & Integration Tests (`mvn test`) $\rightarrow$ Build Docker Image.
- [ ] Tạo status badge CI hiển thị trên README repo; commit.

### Thứ 5 — So Sánh Jenkins vs GitHub Actions vs GitLab CI (2h)
- [ ] Phân tích ưu nhược điểm giữa Self-hosted CI (Jenkins) vs Managed Cloud CI (GitHub Actions, GitLab CI).
- [ ] Tìm hiểu Jenkins Declarative Pipeline: `Jenkinsfile`, Stages, Agents, Artifact Archiving.
- [ ] Ghi lại bảng so sánh các công cụ CI/CD vào tài liệu kỹ thuật; commit.

### Thứ 6 — Deployment Cloud Thực Tế & Quản Lý Secret (2h)
- [ ] Học các mô hình Cloud Compute: IaaS (EC2) vs PaaS (Render, Railway, Fly.io) vs CaaS/K8s.
- [ ] Deploy backend Giao Vặt lên nền tảng Cloud phù hợp (PaaS hoặc VPS).
- [ ] Nguyên tắc bất biến về bảo mật: Tuyệt đối không commit secret lên Git; quản lý biến môi trường qua Cloud Dashboard / Secret Manager; tạo file `.env.example`.
- [ ] Kiểm tra kết nối từ bên ngoài tới API Cloud; commit.

### Thứ 7 — Hoàn Thiện CI/CD & Runbook Triển Khai (5h)
- [ ] 2h: Tự động hóa build và push Docker image lên GitHub Container Registry (GHCR) hoặc Docker Hub trong CI pipeline.
- [ ] 1h: Tích hợp bước kiểm tra code chất lượng (Linter / Spotless / Checkstyle) vào CI.
- [ ] 1h: Viết Runbook hướng dẫn chi tiết cách khởi động, kiểm tra log, backup và rollback hệ thống.
- [ ] 1h: Tag release Git: `giaovat-ci-cd-ready`.

---

## Tuần 12 — Testing Strategy, Observability & Performance Profiling

### Thứ 2 — Lý Thuyết Testing Pyramid & Lập Ma Trận Kiểm Thử (2h)
- [ ] Học lý thuyết **Testing Pyramid**: Unit Tests (chân tháp - nhiều nhất, nhanh nhất), Integration / Slice Tests (giữa tháp), End-to-End Tests (đỉnh tháp - ít nhất, chậm nhất).
- [ ] Phân biệt Unit Test (cô lập, mock ranh giới) vs Integration Test (thực tế với database/redis thật).
- [ ] Lập Test Matrix cho toàn bộ các module của Giao Vặt (Creator, Runner, Order Feed, Claim Lock, Pricing, Payment Webhook).
- [ ] Loại bỏ các test thừa thãi chỉ kiểm tra implementation detail; commit.

### Thứ 3 — Testcontainers Thực Chiến với PostgreSQL & Redis Thật (2h)
- [ ] Tại sao H2 Database là "bẫy giả lập" nguy hiểm (khác biệt về SQL dialect, locking behavior, JSON support so với PostgreSQL thật)?
- [ ] Cấu hình Testcontainers trong Spring Boot 3 (`@Testcontainers`, `@Container` PostgreSQL + Redis).
- [ ] Viết bộ integration test kiểm tra trọn vẹn luồng tạo đơn $\rightarrow$ lưu DB $\rightarrow$ đẩy Redis feed $\rightarrow$ claim đơn.
- [ ] Đảm bảo tính độc lập tuyệt đối giữa các bài test (Test Isolation & Clean Database); commit.

### Thứ 4 — Ba Trụ Cột Của Observability: Metrics, Logs & Traces (2h)
- [ ] Học lý thuyết Observability: Khác biệt giữa Monitoring (biết hệ thống hỏng) vs Observability (hiểu vì sao hệ thống hỏng từ bên trong).
- [ ] Ba trụ cột:
  - **Metrics:** Số liệu đo lường định lượng (CPU, RAM, Request Rate, Error Rate, Latency).
  - **Structured Logging:** Log có cấu trúc (JSON format), log level (`DEBUG`, `INFO`, `WARN`, `ERROR`), MDC (Mapped Diagnostic Context) chứa `traceId` và `userId` xuyên suốt vòng đời request.
  - **Traces:** Dấu vết đường đi của request qua các thành phần.
- [ ] Tích hợp Spring Boot Actuator: expose `/actuator/health`, `/actuator/metrics`, `/actuator/prometheus`.
- [ ] Cấu hình MDC Filter ghi nhận `traceId` cho mọi log entry của Giao Vặt; commit.

### Thứ 5 — Performance Profiling & Database Query Tuning (2h)
- [ ] Học cách đọc và phân tích **Query Execution Plan** (`EXPLAIN (ANALYZE, BUFFERS)` trong PostgreSQL).
- [ ] Phân biệt các toán tử truy vấn: Seq Scan (Full Table Scan), Index Scan, Index Only Scan, Bitmap Index Scan.
- [ ] Tối ưu hóa câu query bảng tin: Đánh Composite Index `(status, created_at)` hoặc Partial Index `WHERE status = 'OPEN'`.
- [ ] Đo lường chi phí truy vấn (Execution time và Buffers read) trước và sau khi đánh index; commit.

### Thứ 6 — Bug Hunting & Tái Hiện Lỗi Thực Tế (2h)
- [ ] Thực hành tái hiện và sửa 4 lỗi kinh điển:
  - (1) Bẫy N+1 Query khi load danh sách đơn hàng kèm thông tin Creator.
  - (2) Lộ số điện thoại Creator trên public feed trước khi Runner claim.
  - (3) Race condition khi 2 request cùng claim 1 đơn mà không có lock.
  - (4) Stale cache trên Redis khi Creator hủy đơn mà cache feed chưa xóa.
- [ ] Viết regression test chứng minh bug đã được vá triệt để; commit.

### Thứ 7 — Quality Gate & Stress Test Nền Tảng (5h)
- [ ] 2h: Chạy toàn bộ test suite (Unit + Integration), đảm bảo pass 100% không có flaky test.
- [ ] 1h: Chạy stress test đơn giản bằng tool (JMeter / k6 / ApacheBench) với 100 concurrent requests tới endpoint bảng tin.
- [ ] 1h: Tự review code theo checklist bảo mật và chất lượng code.
- [ ] 1h: Cập nhật tài liệu kỹ thuật và commit code.

---

## Tuần 13 — Agile, Engineering Processes, System Design Docs & AI Workflows

### Thứ 2 — Agile / Scrum & Quy Trình Phát Triển Phần Mềm (2h)
- [ ] Học quy trình Agile/Scrum: Product Backlog, Sprint Planning, Daily Standup, Sprint Review, Retrospective.
- [ ] Các khái niệm cốt lõi: Epic, User Story, Acceptance Criteria (AC), Definition of Done (DoD).
- [ ] Viết 1 Epic Giao Vặt và 8 User Stories chi tiết theo chuẩn Vertical Slice (mỗi story mang lại giá trị độc lập từ UI/API tới Database); commit.

### Thứ 3 — Mô Phỏng Jira Board & Quản Lý Công Việc (2h)
- [ ] Tạo board Kanban/Scrum cá nhân (GitHub Projects hoặc Jira Free).
- [ ] Tạo issue, gán label, độ ưu tiên (Priority), ước lượng thời gian.
- [ ] Thực hành quy trình làm việc theo task: Kéo card `In Progress` $\rightarrow$ tạo branch `feature/ticket-id` $\rightarrow$ code & test $\rightarrow$ mở Pull Request $\rightarrow$ review $\rightarrow$ merge vào `main`.
- [ ] Viết Daily Update mẫu bằng English: Yesterday / Today / Blockers; commit.

### Thứ 4 — Estimation & Sprint Retrospective (2h)
- [ ] Học kỹ thuật ước lượng công việc: Planning Poker, Story Points, 3-Point Estimation (Optimistic, Most Likely, Pessimistic).
- [ ] Học cách nhận diện rủi ro và các giả định (assumptions) kỹ thuật trước khi bắt tay vào code.
- [ ] Viết tài liệu Sprint Retrospective: Keep (điểm làm tốt), Stop (thói quen xấu cần bỏ), Start (hành động cải tiến tiếp theo); commit.

### Thứ 5 — Kỹ Thuật Viết Design Doc & Architectural Decision Records (ADR) (2h)
- [ ] Học tầm quan trọng của việc viết tài liệu kỹ thuật trong doanh nghiệp: *"Code là cái hệ thống làm, Design Doc là vì sao hệ thống làm như vậy"*.
- [ ] Cấu trúc chuẩn của một bản **ADR (Architectural Decision Record)**: Title, Status, Context, Decision, Consequences (Pros & Cons).
- [ ] Viết 2 bản ADR chính thức cho Giao Vặt lưu tại thư mục `docs/adr/`:
  - `ADR-001`: Lựa chọn cơ chế Concurrency Locking cho luồng Runner Claim Order (Optimistic Locking `@Version` vs Pessimistic Lock).
  - `ADR-002`: Lựa chọn Redis Sorted Set cho Bảng Tin Đơn Hàng thời gian thực.
- [ ] Commit tài liệu.

### Thứ 6 — AI-Assisted Engineering & Workflow Hiện Đại (2h)
- [ ] Thực hành tích hợp AI coding assistants (GitHub Copilot, Cursor, Antigravity) vào quy trình phát triển.
- [ ] Kỹ thuật Prompt Engineering cho lập trình: Cung cấp đủ context domain, yêu cầu viết test trước (TDD), yêu cầu giải thích trade-offs.
- [ ] Cố ý kiểm tra và bắt lỗi: Hallucination về thư viện không tồn tại, bỏ sót edge cases, vi phạm quy tắc bảo mật.
- [ ] Ghi lại bài học kinh nghiệm về việc làm chủ AI; commit.

### Thứ 7 — Code Review Workflow & PR Checklist (5h)
- [ ] 2h: Tạo một Pull Request hoàn chỉnh cho feature mới.
- [ ] 1h: Tự review PR dựa trên checklist nghiêm ngặt: Tính đúng đắn (Correctness), Bảo mật (Security), Khả năng quan sát (Observability), Độ bao phủ test (Test Coverage).
- [ ] 1h: Tinh chỉnh lại code theo các góp ý tự đánh giá.
- [ ] 1h: Merge PR và cập nhật changelog dự án.

---

## Tuần 14 — Cấu Trúc Dữ Liệu & Giải Thuật Ứng Dụng Trong System Design

### Thứ 2 — Recursion, Call Stack & Binary Search Biến Thể (2h)
- [ ] Học bản chất đệ quy (Call Stack, Base Case, Stack Overflow) vs Vòng lặp khử đệ quy.
- [ ] Binary Search ($O(\log N)$) và các biến thể tìm biên (Find First/Last Occurrence).
- [ ] Ứng dụng trong System Design: Tìm kiếm log timestamp, định vị partition key trong hệ thống phân tán.
- [ ] Luyện 3 bài: Binary Search, Search in Rotated Sorted Array, Koko Eating Bananas; commit.

### Thứ 3 — Trees, Binary Search Tree (BST) & Cấu Trúc Index (2h)
- [ ] Học Tree fundamentals: Depth, Height, DFS (Pre/In/Postorder), BFS (Level-order).
- [ ] Binary Search Tree (BST) và cân bằng cây (AVL, Red-Black Tree).
- [ ] Ứng dụng trong System Design: Vì sao Database dùng B-Tree / B+Tree cho index trên đĩa thay vì BST (tối ưu hóa I/O Block đĩa).
- [ ] Luyện 3 bài: Invert Binary Tree, Validate BST, Binary Tree Level Order Traversal; commit.

### Thứ 4 — Heap / Priority Queue & Top-K Problems (2h)
- [ ] Học cấu trúc dữ liệu Binary Heap: Min-Heap, Max-Heap, độ phức tạp thao tác ($O(1)$ peek, $O(\log N)$ push/pop).
- [ ] Ứng dụng trong System Design: Hàng đợi ưu tiên xử lý task, thuật toán Top-K phần tử thịnh hành trong khoảng thời gian (Top Trending).
- [ ] Luyện 2 bài: K Closest Points to Origin, Top K Frequent Elements; commit.

### Thứ 5 — Graph Algorithms & Bài Toán Định Tuyến Đơn Hàng Giao Vặt (2h)
- [ ] Học biểu diễn đồ thị: Adjacency List vs Adjacency Matrix; Duyệt đồ thị BFS vs DFS.
- [ ] Thuật toán đường đi ngắn nhất: Dijkstra Algorithm.
- [ ] **Ánh xạ vào bài toán thực tế của Giao Vặt:**
  - Tìm cuốc xe gần tọa độ hiện tại của Runner nhất (Nearest Driver Problem).
  - Ghép lộ trình tiện đường giữa đơn hàng A và đơn hàng B (Route Matching / Multi-order Batching).
- [ ] Luyện 2 bài: Number of Islands, Course Schedule (Topological Sort); commit.

### Thứ 6 — Dynamic Programming (Quy Hoạch Động) Nhập Môn (2h)
- [ ] Học bản chất Quy hoạch động: Overlapping Subproblems và Optimal Substructure.
- [ ] So sánh Top-down (Memoization) vs Bottom-up (Tabulation).
- [ ] Luyện 3 bài kinh điển: Climbing Stairs, House Robber, Coin Change.
- [ ] Ghi lại bảng chuyển trạng thái (State Transition Table) bằng lời trước khi code; commit.

### Thứ 7 — Timed Algorithm Assessment (5h)
- [ ] 2h: Giải 3 bài LeetCode Easy/Medium có bấm giờ (mỗi bài tối đa 35 phút).
- [ ] 1h: Tự giải thích thuật toán bằng tiếng Anh theo cấu trúc: Idea $\rightarrow$ Complexity $\rightarrow$ Edge Cases $\rightarrow$ Code.
- [ ] 1h: Tổng hợp các pattern giải thuật thường gặp trong phỏng vấn kỹ thuật.
- [ ] 1h: Commit bài giải và ghi chú.

---

## Tuần 15 — Software Design Patterns, Network Protocols & Security Audit

### Thứ 2 — GoF Design Patterns: Creational & Structural Patterns (2h)
- [ ] Học bản chất và ứng dụng thực tế của GoF Design Patterns:
  - **Strategy Pattern:** Tách rời thuật toán tính toán khỏi context sử dụng (đã áp dụng trong `PricingStrategy` của Giao Vặt).
  - **Factory Method:** Đóng gói logic khởi tạo object phức tạp.
  - **Builder Pattern:** Xây dựng object có nhiều thuộc tính tùy chọn, đảm bảo immutability (Java `@Builder`).
  - **Adapter & Decorator Pattern:** Chuyển đổi interface tương thích và bọc thêm tính năng.
- [ ] Cảnh báo chống "Over-engineering": Khi nào KHÔNG nên dùng pattern; commit.

### Thứ 3 — Behavioral Patterns & Event-Driven Architecture (2h)
- [ ] Học **Observer Pattern** và mô hình Event-Driven trong Spring Boot:
  - Sử dụng `ApplicationEventPublisher` phát sinh sự kiện nội bộ: `OrderCreatedEvent`, `OrderClaimedEvent`, `OrderCompletedEvent`.
  - Xây dựng `@EventListener` và `@TransactionalEventListener(phase = TransactionPhase.AFTER_COMMIT)`.
  - Phân tích sự khác biệt giữa xử lý sự kiện đồng bộ (Synchronous) vs bất đồng bộ (`@Async`).
- [ ] Viết test đảm bảo event listener chỉ kích hoạt sau khi database transaction đã commit thành công; commit.

### Thứ 4 — Lý Thuyết Networking & HTTP Protocols (2h)
- [ ] Học sâu mô hình mạng: TCP/IP stack 4 tầng, cơ chế TCP 3-Way Handshake và 4-Way Teardown.
- [ ] TLS/SSL Handshake: Mã hóa bất đối xứng (trao đổi khóa) kết hợp mã hóa đối xứng (truyền dữ liệu).
- [ ] So sánh các thế hệ HTTP:
  - HTTP/1.1: Keep-Alive, bẫy Head-of-Line (HoL) Blocking ở tầng ứng dụng.
  - HTTP/2: Binary Framing, Multiplexing qua 1 kết nối TCP duy nhất, Server Push, Header Compression (HPACK).
  - HTTP/3: Chạy trên nền giao thức QUIC (UDP), giải quyết triệt để HoL Blocking ở cả tầng transport.
- [ ] Dùng `curl -v` trace chi tiết một request tới Giao Vặt API; commit ghi chú.

### Thứ 5 — Linux Shell & Điều Tra Server Log (2h)
- [ ] Học các câu lệnh Linux thiết yếu cho Backend Engineer:
  - Tìm kiếm & lọc log: `grep`, `egrep`, `awk`, `sed`, `tail -n 100 -f app.log`.
  - Kiểm tra tiến trình & tài nguyên: `top`, `htop`, `ps aux | grep java`, `free -m`, `df -h`.
  - Kiểm tra mạng & cổng: `netstat -tulpn`, `ss -tulpn`, `lsof -i :8080`, `curl`, `dig`.
- [ ] Thực hành điều tra lỗi trong file server log giả lập: tìm kiếm exception stack trace theo `traceId`; commit.

### Thứ 6 — OWASP Top 10 Security Audit Cho Giao Vặt (2h)
- [ ] Học danh mục lỗ hổng bảo mật phổ biến **OWASP Top 10 API Security**:
  - BOLA / IDOR (Broken Object Level Authorization): Runner A cố tình cập nhật hoặc xem chi tiết đơn của Runner B $\rightarrow$ Cách phòng chống: Luôn kiểm tra quyền sở hữu đối tượng trước khi xử lý.
  - Broken Authentication & Token Theft.
  - SQL Injection & Mass Assignment.
  - Lack of Resources & Rate Limiting.
- [ ] Rà soát toàn bộ endpoint của Giao Vặt, viết bài test chứng minh hệ thống chặn đứng lỗi IDOR; commit.

### Thứ 7 — Comprehensive Technical Mock Interview (5h)
- [ ] 2h: Tự phỏng vấn vấn đáp 20 câu Design Patterns, Networking HTTP và Security.
- [ ] 1h: Trực tiếp vẽ sơ đồ và giải thích Strategy Pattern và Event-Driven Architecture trên codebase Giao Vặt.
- [ ] 1h: Vấn đáp SQL indexing, transaction isolation và query tuning.
- [ ] 1h: Tổng kết các điểm cần cải thiện và commit checklist.

---

## Tuần 16 — System Architecture Documentation, English Communication & Portfolio

### Thứ 2 — Chuẩn Hóa Toàn Diện RESTful API (2h)
- [ ] Rà soát toàn bộ API Contracts: Chuẩn hóa URI danh từ số nhiều (`/api/v1/orders`), quy chuẩn phân trang (`page`, `size`, `sort`).
- [ ] Cập nhật toàn bộ OpenAPI / Swagger examples cho request và response.
- [ ] Đảm bảo tính nhất quán của mã lỗi trả về theo RFC 7807 `ProblemDetail`; commit.

### Thứ 3 — Vẽ Kiến Trúc Hệ Thống Chuẩn C4 Model (2h)
- [ ] Học mô hình tài liệu kiến trúc **C4 Model**: Context, Container, Component, Code.
- [ ] Vẽ sơ đồ kiến trúc hệ thống Giao Vặt:
  - Sơ đồ Container: Client $\rightarrow$ Nginx / Cloud Proxy $\rightarrow$ Spring Boot Monolith $\rightarrow$ PostgreSQL & Redis.
  - Sơ đồ Request Flow chi tiết: Khách tạo đơn $\rightarrow$ Redis Feed ZSET $\rightarrow$ Runner Claim (Locking) $\rightarrow$ SSE Broadcast.
- [ ] Viết phần "Known Limitations & Future Architecture" vào README; commit.

### Thứ 4 — Technical English: Introduction & Storytelling (2h)
- [ ] Soạn thảo bản giới thiệu bản thân bằng tiếng Anh (Self-Introduction) trong 90 giây.
- [ ] Luyện tập ghi âm 3 lần; chỉnh sửa phát âm và ngữ pháp.
- [ ] Nắm vững vốn từ vựng kỹ thuật chuẩn: *concurrency, race condition, data consistency, trade-off, optimistic locking, latency, horizontal scaling, bottleneck, root cause*.
- [ ] Lưu bản script giới thiệu vào repo; commit.

### Thứ 5 — Technical English: Demo Dự Án Giao Vặt (2h)
- [ ] Chuẩn bị bài thuyết trình 5 phút bằng tiếng Anh về dự án Giao Vặt theo cấu trúc:
  - Problem & Context $\rightarrow$ Architecture Design $\rightarrow$ Technical Challenges (Concurrency Locking & Realtime Feed) $\rightarrow$ Trade-offs $\rightarrow$ Results & Metrics.
  - Tự trả lời 2 câu hỏi kỹ thuật hóc búa bằng tiếng Anh:
    1. *"How do you handle double-picking when multiple drivers claim the same order simultaneously?"*
    2. *"Why did you choose Redis Sorted Set instead of direct database polling for the order feed?"*
- [ ] Ghi âm và đánh giá độ lưu loát; commit.

### Thứ 6 — CV Kỹ Sư Backend Chuẩn Quốc Tế (2h)
- [ ] Soạn thảo CV tiếng Anh 1 trang chuẩn format ATS (Applicant Tracking System).
- [ ] Trình bày dự án Giao Vặt theo mô hình Action-Result (STAR): Nêu bật công nghệ sử dụng, thách thức kỹ thuật đã giải quyết và số đo đạt được (ví dụ: xử lý race condition đảm bảo 0% duplicate claim dưới tải 100 concurrent threads).
- [ ] Đưa đúng từ khóa kỹ thuật: *Java 17 LTS, Spring Boot 3, Spring Security, JWT, Redis, PostgreSQL, JPA/Hibernate, Optimistic Locking, Testcontainers, Docker, CI/CD, RFC 7807*.
- [ ] Rà soát ngữ pháp và chính tả; commit.

### Thứ 7 — Release Portfolio Sản Phẩm Giao Vặt v1 (5h)
- [ ] 2h: Dọn dẹp mã nguồn, kiểm tra lint, format code chuẩn Google Java Style.
- [ ] 1h: Quay video demo ngắn (3–5 phút) thể hiện toàn bộ tính năng và luồng chạy thực tế.
- [ ] 1h: Tạo Git Tag release chính thức: `v1.0.0-giaovat-release`.
- [ ] 1h: Kiểm tra quy trình Clean Clone: Clone repo về thư mục mới $\rightarrow$ Chạy `docker compose up` $\rightarrow$ Run test $\rightarrow$ Kiểm tra ứng dụng chạy trơn tru 100%.

---

## Tuần 17 — Production API Patterns, Real-time & High-Concurrency Locking

### Thứ 2 — Lý Thuyết RESTful Nâng Cao & Idempotency Key Pattern (2h)
- [ ] Học nguyên lý **Idempotent API**:
  - Tính chất Idempotency: Khả năng thực thi một thao tác nhiều lần mà kết quả cuối cùng trên hệ thống không thay đổi so với thực thi một lần.
  - Phân tích các phương thức HTTP: GET, PUT, DELETE, HEAD (vốn dĩ là idempotent) vs POST, PATCH (không idempotent).
- [ ] Bài toán thực tế: Khách bấm nút "Đặt đơn" hoặc "Thanh toán" hai lần liên tiếp do mạng lag $\rightarrow$ Nguy cơ tạo 2 đơn trùng lặp hoặc trừ tiền 2 lần.
- [ ] Thiết kế **Idempotency Key Pattern** cho API Tạo Đơn (`POST /api/v1/orders`):
  - Client gửi kèm Header `Idempotency-Key` (UUID ngẫu nhiên).
  - Backend sử dụng Redis lệnh `SET order:idempotency:{key} "PROCESSING" NX EX 120` (Atomic Set if Not Exists kèm TTL 2 phút).
  - Nếu key đã tồn tại: Chặn ngay lập tức và trả về `409 Conflict` hoặc kết quả cache trước đó.
  - Khi hoàn tất tạo đơn: Cập nhật value thành `"COMPLETED"` kèm ID đơn hàng.
- [ ] Viết bài test mô phỏng gửi đồng thời 2 request cùng Idempotency Key; commit.

### Thứ 3 — Lý Thuyết Webhook Architecture & Security (2h)
- [ ] Học mô hình Webhook trong tích hợp hệ thống:
  - Khác biệt giữa Polling (chủ động hỏi) vs Webhook (bị động nhận thông báo sự kiện qua HTTP callback).
  - Các rủi ro an ninh của Webhook: Giả mạo nguồn phát (Spoofing), Sửa đổi payload trên đường truyền (Tampering), Tấn công gửi lại (Replay Attacks).
- [ ] Xây dựng Webhook Receiver nhận kết quả thanh toán Sandbox (giả lập VNPay/Stripe):
  - Xác thực chữ ký số bằng thuật toán **HMAC-SHA256** dựa trên Shared Secret Key bí mật.
  - Kiểm tra tính hợp lệ của timestamp trong webhook để ngăn chặn Replay Attack quá thời hạn.
  - Thiết kế **Idempotent Webhook Processing**: Đảm bảo cổng thanh toán gửi lại webhook nhiều lần thì trạng thái đơn hàng vẫn chỉ cập nhật đúng 1 lần duy nhất.
- [ ] Viết test: gửi webhook sai chữ ký (phải trả 401 Unauthorized), gửi webhook hợp lệ thành công; commit.

### Thứ 4 — Lý Thuyết Real-Time Web & Server-Sent Events (SSE) (2h)
- [ ] Học và so sánh các cơ chế giao tiếp thời gian thực:
  - **Short Polling:** Client liên tục gửi request theo chu kỳ ngắn $\rightarrow$ Lãng phí tài nguyên máy chủ.
  - **Long Polling:** Server giữ kết nối cho đến khi có dữ liệu mới $\rightarrow$ Nặng nề, quản lý connection phức tạp.
  - **WebSocket (STOMP):** Kết nối 2 chiều toàn phần (Full-duplex), giao thức binary/text riêng $\rightarrow$ Tối ưu cho game/chat, nhưng nặng và khó scale qua HTTP proxies.
  - **Server-Sent Events (SSE):** Giao tiếp 1 chiều từ Server xuống Client (Server-to-Client), chạy trên nền HTTP chuẩn (`text/event-stream`), tự động reconnect native trong trình duyệt $\rightarrow$ **Lựa chọn hoàn hảo nhất cho bảng tin đơn hàng và thông báo trạng thái**.
- [ ] Triển khai SSE với Spring Boot `SseEmitter`:
  - API `GET /api/v1/orders/feed/stream`: Runner đăng ký nhận stream bảng tin thời gian thực.
  - Khi Creator tạo đơn mới: Push event `NEW_ORDER_AVAILABLE` tới toàn bộ Runner đang kết nối.
  - Khi một Runner nhận đơn thành công: Push event `ORDER_CLAIMED` để các Runner khác tự động xóa đơn khỏi màn hình, đồng thời push event `RUNNER_ACCEPTED` cho Creator.
- [ ] Xử lý quản lý vòng đời connection: Timeout, client disconnect, heartbeat ping định kỳ 15 giây; commit.

### Thứ 5 — Lý Thuyết Concurrency & Database Locking Thực Chiến (2h)
- [ ] Phân tích bài toán kinh điển: **Double-Picking / Race Condition**:
  - Khi 10 Runner cùng nhìn thấy 1 đơn hàng giá hời trên bảng tin và cùng bấm "Nhận đơn" trong cùng 1 phần nghìn giây.
  - Nếu không có cơ chế kiểm soát đồng thời $\rightarrow$ Cả 10 Runner đều nhận thành công $\rightarrow$ Thảm họa nghiệp vụ!
- [ ] So sánh chuyên sâu các giải pháp khóa trong ngành:
  - **Pessimistic Locking (`SELECT ... FOR UPDATE`):** Khóa dòng trực tiếp trong Database $\rightarrow$ An toàn tuyệt đối nhưng block tài nguyên, throughput thấp, dễ dẫn đến deadlock.
  - **Optimistic Locking (`@Version` trong JPA):** Không khóa ở DB, dựa trên số version để phát hiện xung đột $\rightarrow$ Throughput cực cao, không block đọc, phù hợp hệ thống có tỷ lệ đọc nhiều hơn ghi.
  - **Distributed Locking (Redis Redlock / Redisson):** Dùng khi hệ thống phân tán nhiều instance độc lập.
- [ ] Triển khai Optimistic Locking trên entity `Order`:
  - Thêm trường `@Version private Long version;`.
  - Viết test stress concurrency bằng JUnit 5 kết hợp `CountDownLatch` và `ExecutorService` (10 thread cùng gọi `claimOrder`): Chứng minh duy nhất 1 Runner nhận thành công, 9 Runner còn lại nhận ngoại lệ `OptimisticLockingFailureException` và trả về `409 Conflict`; commit.

### Thứ 6 — Deadlock Simulation & Resolution Drill (2h)
- [ ] Phân tích nguyên nhân gốc rễ sinh ra **Deadlock**: 4 điều kiện của Coffman (Mutual Exclusion, Hold and Wait, No Preemption, Circular Wait).
- [ ] Tạo bài lab tái hiện Deadlock thực tế: Hai transaction chạy song song cập nhật chéo tài nguyên (Tx 1: lock User rồi lock Order; Tx 2: lock Order rồi lock User).
- [ ] Đọc và phân tích Deadlock Graph trong Database log (`SHOW ENGINE INNODB STATUS` trong MySQL hoặc Postgres log).
- [ ] Hai giải pháp khắc phục triệt để:
  - (1) Chuẩn hóa thứ tự khóa tài nguyên (Lock Ordering Rule).
  - (2) Cấu hình cơ chế tự động thử lại bằng Spring `@Retryable` với Exponential Backoff khi gặp transient deadlock.
- [ ] Viết test chứng minh `@Retryable` vượt qua deadlock tạm thời; commit.

### Thứ 7 — End-to-End Payment & Notification Lab (5h)
- [ ] 2h: Ghép nối trọn vẹn luồng sản xuất hoàn chỉnh: Creator tạo đơn (kèm Idempotency Key) $\rightarrow$ Đẩy Redis Feed $\rightarrow$ Push SSE cho các Runner $\rightarrow$ Runner claim đơn (Optimistic Lock) $\rightarrow$ Gỡ đơn khỏi feed và báo cho Creator $\rightarrow$ Thanh toán Sandbox qua Webhook.
- [ ] 1h: Viết integration tests toàn luồng với Testcontainers và MockMvc.
- [ ] 1h: Hoàn thiện tài liệu ADR về các quyết định Idempotency, SSE và Locking.
- [ ] 1h: Commit và tổng kết tuần.

---

## Tuần 18 — Fresher Gate & Sẵn Sàng Ứng Tuyển Thực Tế

### Thứ 2 — Mock Technical Interview: Java Core Deep Dive (2h)
- [ ] Vấn đáp chuyên sâu 30 câu hỏi Java Core: OOP principles, Immutability, Collections Framework internals, JVM Memory (Heap, Stack, Metaspace), GC, Java Memory Model, Concurrency primitives.
- [ ] Sửa chữa 5 điểm thiếu sót lớn nhất ghi nhận được; commit ghi chú.

### Thứ 3 — Mock Technical Interview: Spring Boot, JPA & Database (2h)
- [ ] Vấn đáp 30 câu Spring Boot & Data: IoC/DI, Bean Lifecycle, Proxy mechanism & self-invocation trap, `@Transactional` isolation & propagation, N+1 query fix, B-Tree index structure, MVCC snapshot.
- [ ] Vẽ sơ đồ luồng đi của request từ Client tới Database không nhìn tài liệu; commit.

### Thứ 4 — Mock System & Project Presentation (2h)
- [ ] Trình bày dự án Giao Vặt theo cấu trúc chuẩn: Bối cảnh $\rightarrow$ Vấn đề $\rightarrow$ Giải pháp kiến trúc $\rightarrow$ Trade-offs $\rightarrow$ Kết quả đạt được.
- [ ] Trả lời phản biện các câu hỏi xoay quanh Concurrency Locking, Redis Feed, SSE connection leak, Idempotency pattern.

### Thứ 5 — Mock Interview bằng Tiếng Anh (English Technical Round) (2h)
- [ ] Mô phỏng vòng phỏng vấn tiếng Anh: Self-introduction, Project walk-through, Behavioral questions (STAR method), Career aspiration.
- [ ] Ghi âm lại và chấm điểm dựa trên: Độ rõ ràng (Clarity), Cấu trúc câu trả lời (Structure), Từ vựng kỹ thuật chính xác (Technical Vocabulary).

### Thứ 6 — Thiết Lập Hệ Thống Ứng Tuyển & Tìm Kiếm Việc Làm (2h)
- [ ] Tạo bảng Job Application Tracker: Công ty, Vị trí, Link JD, Ngày nộp, Trạng thái, Điểm còn thiếu, Kế hoạch follow-up.
- [ ] Lựa chọn 10 Job Descriptions (JD) Fresher / Junior Java phù hợp trên thị trường (ITviec, TopCV, LinkedIn).
- [ ] Đối chiếu từ khóa trên JD với kinh nghiệm thực tế từ dự án Giao Vặt; chuẩn bị thư xin việc (Cover Letter) cá nhân hóa cho từng vị trí.
- [ ] Học kỹ năng đàm phán lương ban đầu: Tìm hiểu dải lương Fresher tại thị trường Việt Nam (12–15 triệu), cách trả lời câu hỏi "Mức lương mong muốn của bạn là bao nhiêu?".

### Thứ 7 — Final Gate Assessment: Đạt Chuẩn Apply Fresher (5h)
- [ ] 2h: Thử thách Live Coding: Tự tay dựng một tính năng CRUD có validation, exception handler, auth và test trong vòng 120 phút không xem tài liệu cũ.
- [ ] 1h: Chạy full test suite và demo toàn diện hệ thống.
- [ ] 1h: Gửi 3 bộ hồ sơ ứng tuyển chất lượng đầu tiên.
- [ ] 1h: Đánh giá Retrospective toàn bộ Giai đoạn 1 & 2, lập kế hoạch bước vào Giai đoạn 3 (Junior $\rightarrow$ Mid).

**Tiêu chuẩn hoàn thành Gate Fresher (DoD Fresher):**
- Có repository Git chuẩn mực; clone về máy mới chạy được ngay bằng `docker compose up`.
- Nắm vững kiến trúc Backend 3 layers, code thành thạo CRUD + Auth trong 2–3 giờ.
- Giải thích rành rọt bản chất OOP, Collections, Concurrency primitives, SQL Index, Spring Proxy và Locking.
- Trình bày được dự án và trả lời phỏng vấn kỹ thuật bằng tiếng Anh cơ bản.
- **Đạt gate này là BẮT ĐẦU NỘP HỒ SƠ ỨNG TUYỂN NGAY, không chờ đợi phải học hết kiến trúc Senior.**

> *Trường hợp chưa đạt điểm tự tin:* Bù đắp đúng phần bị hổng trong 2 tuần tiếp theo, đồng thời mở rộng dải ứng tuyển sang Intern/Fresher dải 8–12 triệu hoặc thực tập sinh có lương; tuyệt đối không đứng ngoài thị trường lao động.

# GIAI ĐOẠN 3 — THÁNG 5–17
## Junior Thực Chiến → Đủ Điều Kiện Apply Mid Java Software Engineer (Mục tiêu 25–30 triệu)

> Giai đoạn này ưu tiên kinh nghiệm tại công ty thật. Mỗi tuần giữ lịch học đều đặn nhưng gắn chặt với task sản xuất thực tế. Nếu chưa có việc ngay, tiếp tục dùng **Giao Vặt** làm môi trường mô phỏng mở rộng (On-Demand Crowdsourced Delivery Platform) và ghi rõ là Personal Production Project.

> **NGUYÊN TẮC CHIẾN LƯỢC: VƯỢT RA NGOÀI GIỚI HẠN CỦA MỘT DỰ ÁN — BƯỚC ĐỆM TIẾN TỚI SENIOR**
> 
> **1. Phương Pháp Học Các Mảng Kiến Thức Lớn: Lý Thuyết & Bức Tranh Tổng Thể ──► Phân Tích Trade-off ──► Ra Quyết Định Kiến Trúc (ADR) ──► System Design:**
> - Khi bước vào các mảng kiến thức quy mô lớn (Microservices, Message Brokers Kafka/RabbitMQ, Distributed Consistency, Database Sharding/Replication, Observability APM, Cloud/DevOps...):
>   - **Học lý thuyết trước để nắm được cái nhìn tổng quát (Landscape & Foundations First):** Bắt buộc phải hiểu bản chất nguồn gốc bài toán, các trường phái giải pháp trong ngành phần mềm, cơ chế hoạt động bên dưới (under the hood), ưu và nhược điểm. Tuyệt đối không học theo kiểu "cắm đầu vào cấu hình công cụ" mà không hiểu vì sao công nghệ đó ra đời.
>   - **Đánh giá Trade-off theo ngữ cảnh (Contextual Trade-off Analysis):** Hiểu rõ khi nào nên dùng và khi nào KHÔNG nên dùng. Biết cách cân nhắc giữa Chi phí (Cost) vs Tốc độ (Performance) vs Tính nhất quán (Consistency) vs Độ phức tạp (Complexity).
>   - **Lựa chọn phương pháp phù hợp $\rightarrow$ System Design:** Ra quyết định kiến trúc thông qua bản ADR có dẫn chứng số liệu.
>
> **2. Nhận Định Sống Còn Về Phạm Vi Senior:**
> - **LÀM XONG PROJECT GIAO VẶT KHÔNG ĐẢM BẢO BAO QUÁT HẾT TOÀN BỘ ROADMAP VÌ ROADMAP HƯỚNG TỚI SENIOR.**
> - Dự án Giao Vặt dù đủ to và giải quyết nhiều bài toán backend khó (concurrency locking, redis queue, SSE, idempotency, webhook) nhưng bản chất nó vẫn chỉ là **một mô hình nghiệp vụ cụ thể** với tập hợp giả định kỹ thuật riêng.
> - **Senior Software Engineer không bao giờ dừng lại ở một dự án duy nhất dù dự án đó đủ to!**
> - Đẳng cấp Senior đòi hỏi:
>   - Năng lực **System Design tổng quát** bao quát nhiều ngành hàng khác nhau (E-commerce Flash Sale chịu tải hàng triệu QPS, Hệ thống Chat thời gian thực toàn cầu, Streaming/CDN phân tán, Hệ thống Sổ cái/FinTech đối soát tài chính phân tán...).
>   - Hiểu sâu bản chất **Hệ thống phân tán (Distributed Systems)**: Định lý CAP, PACELC, Distributed Consensus (Raft/Paxos), Eventual Consistency, Data Partitioning, Multi-region Replication.
>   - Năng lực **Vận hành sản xuất & SRE (Production Resilience)**: Chaos Engineering, Disaster Recovery (RTO/RPO), Capacity Planning bằng toán học, FinOps tối ưu chi phí hạ tầng cloud.
>   - Năng lực **Lãnh đạo kỹ thuật (Technical Leadership)**: Dẫn dắt RFC/ADR liên team, mentoring kỹ sư khác, giải quyết tranh luận kỹ thuật dựa trên dữ liệu.

## Lịch cố định mỗi tuần trong cả giai đoạn

### Thứ 2 — Requirement + estimation (2h)
- [ ] 30m: đọc ticket/JD/task; viết mục tiêu và acceptance criteria.
- [ ] 45m: estimate 3-point; ghi assumptions, dependencies, risks.
- [ ] 30m: đọc code liên quan và vẽ flow.
- [ ] 15m: ghi daily update bằng English.

### Thứ 3 — Implementation (2h)
- [ ] 30m: đọc tài liệu API/framework liên quan.
- [ ] 75m: code một vertical slice nhỏ.
- [ ] 15m: thêm unit test và commit.

### Thứ 4 — Database/API (2h)
- [ ] 30m: phân tích schema/query/transaction.
- [ ] 60m: implement migration, repository, API hoặc integration.
- [ ] 30m: chạy `EXPLAIN`, test edge case, ghi quyết định.

### Thứ 5 — Review/debug/quality (2h)
- [ ] 30m: review một PR của người khác.
- [ ] 45m: debug bug hoặc đọc stack trace/log.
- [ ] 30m: refactor/test/security check.
- [ ] 15m: ghi root cause hoặc review feedback.

### Thứ 6 — Java/DSA/English (2h)
- [ ] 45m: Java/Spring/SQL interview topic theo tuần.
- [ ] 45m: 1–2 bài DSA/SQL.
- [ ] 30m: nói/viết câu trả lời English.

### Thứ 7 — Feature/production lab (5h)
- [ ] 3h: hoàn thành feature hoặc lab theo kế hoạch quý.
- [ ] 1h: test, benchmark, deploy hoặc rollback drill.
- [ ] 1h: README/ADR/weekly retrospective.

### Chủ nhật
- [ ] Nghỉ; chỉ bù task chưa hoàn thành hoặc ôn 60 phút.

> Gate mỗi quý (mỗi khối 4 tuần): phải có output kiểm chứng được — feature shipped, số đo trước/sau, ADR, postmortem hoặc evidence tương đương. Trượt khối nào bù khối đó trước khi sang khối mới; không tích nợ học.

## Tuần 19–22 — Onboarding và delivery cơ bản

- [ ] Tuần 19: đọc architecture/codebase; chạy local; map module; tạo glossary domain.
- [ ] Tuần 20: nhận bug nhỏ; reproduce; fix; regression test; tạo PR.
- [ ] Tuần 21: nhận feature CRUD/API nhỏ; estimate; code; review; deploy.
- [ ] Tuần 22: viết design note và demo feature; xin feedback từ senior; làm một Spring Batch job báo cáo định kỳ + export Excel (Apache POI) + i18n nếu JD yêu cầu.

## Tuần 23–26 — Java/Spring chắc tay

- [ ] Tuần 23: Spring bean lifecycle, proxy, AOP; debug `@Transactional` self-invocation.
- [ ] Tuần 24: transaction propagation/isolation; tạo deadlock lab; đọc log.
- [ ] Tuần 25: JPA flush, dirty checking, batch operation, N+1; tối ưu query thật/lab.
- [ ] **Tuần 25 phụ:** Elasticsearch intro — indexing, mapping, query DSL cho search-heavy use case.
- [ ] Tuần 26: concurrency `ExecutorService`, `CompletableFuture`, timeout; virtual threads (JDK 21) PoC trên flow I/O-bound; test race condition.

## Tuần 27–30 — Testing và code quality

- [ ] Tuần 27: testing pyramid; lập test strategy cho một feature thật.
- [ ] Tuần 28: Testcontainers + integration test repository/service.
- [ ] Tuần 29: contract/API test; kiểm tra backward compatibility.
- [ ] Tuần 30: quality gate, static analysis, dependency vulnerability scan, OWASP ZAP baseline scan; sửa issue thật.

## Tuần 31–34 — SQL, performance, caching

- [ ] Tuần 31: query plan, composite index, selectivity; benchmark trước/sau.
- [ ] Tuần 32: connection pool, timeout, pagination; điều tra latency.
- [ ] Tuần 33: Redis cache-aside, TTL, invalidation; test stale data.
- [ ] Tuần 34: rate limit hoặc distributed lock; ghi ADR vì sao cần/không cần.

## Tuần 35–38 — Logging, monitoring, incident

- [ ] Tuần 35: structured logging, MDC, correlation ID; trace request.
- [ ] Tuần 36: Actuator/Micrometer → Prometheus/Grafana; dựng dashboard request/error/latency thật.
- [ ] **Tuần 36 phụ:** MongoDB intro — document model, aggregation pipeline, indexes.
- [ ] Tuần 37: OpenTelemetry tracing cơ bản; alert và runbook; mô phỏng dependency timeout.
- [ ] Tuần 38: viết blameless postmortem; hoàn tất follow-up action.

## Tuần 39–42 — CI/CD và cloud thực dụng

- [ ] Tuần 39: Jenkins pipeline công ty hoặc lab; build/test/artifact.
- [ ] Tuần 40: Docker image security, caching, registry; rollback image.
- [ ] Tuần 41: AWS core: IAM, VPC, RDS, S3, compute; vẽ deployment diagram.
- [ ] Tuần 42: deploy một service; kiểm tra health, logs, env, rollback.

## Tuần 43–46 — Microservices và messaging fundamentals

- [ ] Tuần 43: bounded context cho Giao Vặt (Order & Queue Service, Driver Matching & Delivery Service, Payment Service, Notification Service); vẽ service boundary.
- [ ] Tuần 44: REST inter-service, timeout, retry, circuit breaker, idempotency.
- [ ] Tuần 45: Kafka/RabbitMQ: producer, consumer, group, retry, DLQ, ordering.
- [ ] Tuần 46: implement event flow (OrderCreated, DriverAccepted, OrderDelivered, PaymentSettled); test duplicate delivery và failure.
- [ ] **Tuần 46 phụ:** gRPC intro cho inter-service communication (protobuf, streaming cơ bản).

## Tuần 47–50 — Distributed reliability

- [ ] Tuần 47: outbox concept, eventual consistency, schema evolution.
- [ ] Tuần 48: tracing, correlation ID, debugging multi-service.
- [ ] Tuần 49: saga concept; tích hợp sandbox VNPay/MoMo: webhook, idempotency key, reconciliation đơn giản; ADR rollback, không overbuild.
- [ ] **Tuần 49 phụ:** OAuth2/OIDC nâng cao — Authorization Server, token rotation, PKCE, mTLS.
- [ ] Tuần 50: load test một flow; ghi bottleneck và remediation.

## Tuần 51–54 — Ownership và technical communication

- [ ] Tuần 51: nhận ownership một module; viết module README/runbook.
- [ ] **Tuần 51 phụ:** Next.js/frontend senior — React hooks nâng cao, Server Components, data fetching.
- [ ] Tuần 52: dẫn refinement nhỏ; estimate và giải thích risk.
- [ ] **Tuần 52 phụ:** Next.js tiếp — SSR/SSG/ISR, performance optimization, testing.
- [ ] Tuần 53: review PR có checklist correctness/security/observability.
- [ ] Tuần 54: mentor hoặc pair với junior; viết tech sharing 10 phút.

## Tuần 55–59 — Mid interview Java/Spring/DB

- [ ] Tuần 55: Java deep: collections internals, JVM memory model, GC logs, chọn GC, pool sizing, memory visibility.
- [ ] Tuần 56: profiling lab: VisualVM/JFR/async-profiler, heap dump; tìm và fix một memory/CPU hotspot có số đo.
- [ ] Tuần 57: virtual threads + structured concurrency: migrate một flow I/O-bound; benchmark trước/sau.
- [ ] Tuần 58: Spring deep: proxy, transaction, security, testing, configuration.
- [ ] Tuần 59: SQL deep: locking, index, query plan, isolation, deadlock; mock technical round 1; sửa gap theo feedback.

## Tuần 60–63 — Mid System Design: Đa Dạng Hóa Kiến Trúc Ngoài Giao Vặt

- [ ] Tuần 60: **System Design 1 — URL Shortener & Global Rate Limiter:** 
  - Tính toán Capacity: Read/Write QPS, Storage trong 5 năm, Network Bandwidth.
  - Hashing (MD5/SHA256 truncated) vs Base62 với Auto-incrementing Sequence Generator (Twitter Snowflake).
  - Multi-tier Caching (Edge CDN $\rightarrow$ Redis $\rightarrow$ DB), Database Partitioning theo ID.
- [ ] Tuần 61: **System Design 2 — Notification Engine & Distributed Message Queuing:** 
  - Bức tranh Fan-out Architecture: Xử lý 1 thông báo gửi tới 10 triệu người dùng.
  - So sánh Message Brokers: Kafka (Log-based, high throughput, replayable) vs RabbitMQ (AMQP, flexible routing, dead-letter exchange).
  - Thiết kế Idempotent Consumer, Retry với Exponential Backoff + DLQ, Circuit Breaker với Resilience4j.
- [ ] Tuần 62: **System Design 3 — Ride-Hailing & Real-Time Driver Matching (Mở rộng quy mô lớn từ Giao Vặt):** 
  - Lưu trữ và truy vấn tọa độ địa lý Geospatial: Geohash, QuadTree, Google S2, Uber H3.
  - Driver location tracking: Cập nhật vị trí mỗi 4 giây qua WebSocket/gRPC streaming.
  - High-concurrency matching lock; Tính toán Capacity bằng số: QPS $\rightarrow$ Số container instance $\rightarrow$ DB Connection pool sizing $\rightarrow$ Chi phí cloud hàng tháng.
- [ ] Tuần 63: **System Design 4 — E-commerce Flash Sale & Tranh Chấp Tồn Kho Cực Đại (Khác biệt hoàn toàn với Giao Vặt):** 
  - Xử lý traffic spike 100.000+ QPS trong vài giây khi mở bán: Caching trang tĩnh tại CDN, chống bot traffic tại API Gateway.
  - Trừ kho nguyên tử bằng Redis Lua Script; So sánh Redisson Distributed Lock vs Database `PESSIMISTIC_WRITE`.
  - Hàng đợi đệm bất đồng bộ (Write-behind DB); Cơ chế suy giảm dịch vụ (Graceful Degradation) khi quá tải.
  - Trình bày 45 phút phản biện trade-offs; Mock System Design interview round.

## Tuần 64–68 — Chuẩn bị nhảy Mid

- [ ] Tuần 64: tổng hợp impact thật: feature, bug, latency, quality, ownership.
- [ ] Tuần 65: viết CV Mid và 5 STAR stories: incident, conflict, deadline, improvement, mentoring.
- [ ] Tuần 66: mock Java/Spring/SQL/system design/English.
- [ ] Tuần 67: đàm phán lương: dải thị trường Mid VN, cách trả expected salary, counter-offer, giữ việc 12–18 tháng trước khi nhảy; luyện 3 kịch bản offer.
- [ ] Tuần 68: apply có chọn lọc; cập nhật gap sau từng interview.

**Gate Mid:** có ít nhất 3 feature end-to-end, 3 bug/root-cause notes, 1 performance improvement có số đo, 1 CI/CD pipeline, 1 ADR/design doc, code review đều, giao tiếp English B2, hiểu microservices/cloud vận hành cơ bản. Đây là năng lực mục tiêu; offer 25–30 triệu còn tùy thị trường và hồ sơ.

---

# GIAI ĐOẠN 4 — 1–2 NĂM TIẾP
## Mid → Senior Software Engineer: Năng Lực Kiến Trúc Phân Tán Toàn Diện & Technical Leadership

> **TRIẾT LÝ TỐI THƯỢNG CỦA SENIOR ENGINEER:**
> 
> **Senior Software Engineer không bị giới hạn trong phạm vi của một dự án hay một công nghệ cụ thể.**
> Dự án Giao Vặt (dù rất lớn và bao quát nhiều bài toán khó) cũng chỉ là một bệ phóng thực nghiệm ban đầu. Để đạt và giữ vững danh hiệu Senior, kỹ sư phần mềm phải có:
> 1. **Tư Duy Lý Thuyết Nền Tảng Sâu Sắc (First-Principles Thinking & Deep Distributed Theory):** Nắm bản chất toán học và hệ thống của bài toán phân tán (CAP, PACELC, Consensus Raft/Paxos, Gossip, Vector Clocks, CRDT, Data Partitioning/Sharding, Multi-Region Active-Active Replication).
> 2. **Năng Lực System Design Đa Ngành Hàng (Cross-Domain Large-Scale Architecture):** Khả năng thiết kế độc lập từ con số không cho các hệ thống với đặc thù kinh doanh khác biệt (Flash Sale, Global Chat, Video Streaming/CDN, FinTech Distributed Ledger...).
> 3. **Production SRE & Khả Năng Chống Chịu Sự Cố (Production Resilience):** Chaos Engineering, Disaster Recovery (RTO/RPO), SLI/SLO/Error Budget, Capacity Planning bằng công thức toán học, FinOps tối ưu chi phí hạ tầng cloud.
> 4. **Technical Leadership & Architecture Governance:** Dẫn dắt RFC/ADR liên tổ chức, cố vấn (mentoring), review code chuẩn mực và ngồi bàn phỏng vấn tuyển dụng, hiệu chuẩn nhân tài.

## Lịch cố định mỗi tuần

### Thứ 2 — Technical direction (2h)
- [ ] Đọc roadmap/incident/metrics; chọn một risk kỹ thuật.
- [ ] Viết problem statement, baseline, expected outcome.

### Thứ 3 — Design/implementation (2h)
- [ ] Viết hoặc review ADR/RFC.
- [ ] Code/prototype phần rủi ro cao; thêm test.

### Thứ 4 — Reliability/performance (2h)
- [ ] Đo latency/error/cost/capacity.
- [ ] Chạy load test hoặc failure drill phù hợp.

### Thứ 5 — Team leverage (2h)
- [ ] Review PR khó; pair/debug; mentor.
- [ ] Cập nhật docs/runbook.

### Thứ 6 — Communication (2h)
- [ ] Viết status/risk bằng English.
- [ ] Luyện trình bày design/incident 10 phút.

### Thứ 7 — Deep work (5h)
- [ ] 3h: project/technical improvement.
- [ ] 1h: test/measurement.
- [ ] 1h: retrospective và evidence log.

## Quý 1 — Ownership hệ thống & Domain-Driven Design (DDD)

- [ ] Tuần 1–4: Nắm domain, dependency, SLO, cost, security; lập system map; vẽ kiến trúc target (Hexagonal / Clean / Ports & Adapters) cho module sở hữu.
- [ ] Tuần 5–8: Dẫn dắt một RFC; áp dụng Strategic & Tactical DDD (Bounded Contexts, Ubiquitous Language, Aggregate Roots, Value Objects, Domain Events, Anti-Corruption Layer - ACL) ở module phức tạp nhất; ship phần đầu tiên.
- [ ] Tuần 9–12: Đo lường outcome; hoàn thiện runbook; chia sẻ tech talk cho toàn bộ team kỹ thuật.

## Quý 2 — Reliability, SRE & Incident Leadership

- [ ] Tuần 13–16: Thiết lập SLI/SLO, Error Budget, Alert Quality, loại bỏ Alert Fatigue.
- [ ] Tuần 17–20: Dẫn dắt Incident Response, chủ trì Blameless Postmortem, theo dõi đóng các action items ngăn ngừa tái diễn.
- [ ] **Tuần 17–20 phụ (Chaos Engineering):** Tích hợp Chaos Mesh / Litmus, thực hiện các bài drill cố ý tiêm lỗi (Failure Injection): Network Latency/Partition, Pod Kill, Database CPU Spike.
- [ ] Tuần 21–24: Thực hiện diễn tập phục hồi sự cố thảm họa (Disaster Recovery Drill - DR): Backup/Restore PostgreSQL, tính toán và cam kết RTO (Recovery Time Objective) và RPO (Recovery Point Objective) bằng số liệu cụ thể.
- [ ] **Tuần 23–24 phụ (Advanced Multi-Region DR):** Kiến trúc Multi-Region Active-Passive vs Active-Active, Failover testing qua DNS/Global Load Balancer.

## Quý 3 — Scale, Distributed Systems & Cross-Domain Architectures

- [ ] Tuần 25–28: Capacity Planning bằng công thức số học (QPS $\rightarrow$ Instance count $\rightarrow$ Connection pool $\rightarrow$ Chi phí cloud), Data Partitioning, Consistent Hashing.
- [ ] Tuần 29–32: Distributed Transactions & Consistency: Idempotency, Transactional Outbox Pattern kết hợp Debezium CDC, Saga Pattern (Orchestration vs Choreography), Schema Evolution không downtime.
- [ ] **Tuần 30–32 phụ (Nghiên cứu kiến trúc thay thế):** Reactive Programming với Spring WebFlux, Event Sourcing & CQRS (Command Query Responsibility Segregation) PoC.
- [ ] **Chuyên đề System Design quy mô lớn ngoài Giao Vặt:**
  - *Case Study 1: Global Video Streaming & CDN (Netflix/YouTube):* Chunking HLS/DASH, Adaptive Bitrate, Multi-tier caching.
  - *Case Study 2: Distributed Financial Ledger (FinTech):* Double-entry bookkeeping, strict ACID, zero data loss, đối soát tự động (automated reconciliation).
- [ ] Tuần 33–36: Distributed Tracing với OpenTelemetry, Profiling JVM (async-profiler, JFR), Load testing phân tán với k6/Gatling, định vị và giải quyết nghẽn cổ chai.
- [ ] **Tuần 35–36 phụ:** GraalVM Native Image benchmark so sánh thời gian khởi động (Startup Time) và Memory Footprint với OpenJDK truyền thống.

## Quý 4 — Platform Engineering, Cloud & FinOps

- [ ] Tuần 37–40: Kubernetes (K8s) & Helm: Deployment, StatefulSet, ConfigMap/Secret, Ingress, HPA (Horizontal Pod Autoscaler), Custom Resource Definitions (CRD).
- [ ] Tuần 41–44: Infrastructure as Code (IaC) với Terraform: Quản lý hạ tầng đám mây dạng mã nguồn, Secret Management (HashiCorp Vault / AWS Secrets Manager), Deployment Strategies (Blue-Green, Canary).
- [ ] Tuần 45–48: Giảm thiểu Toil (công việc lặp lại vô nghĩa), chuẩn hóa CI/CD pipeline, Rollback an toàn; Rà soát hóa đơn đám mây (FinOps), tối ưu dung lượng và cắt giảm chi phí hạ tầng có số đo kiểm chứng.

## Quý 5 — Technical Leadership & Governance

- [ ] Tuần 49–52: Dẫn dắt Design Review liên team; thuyết phục các bên liên quan (Product Manager, Engineering Manager, Business) bằng giá trị kinh doanh (Cost / Risk / Time-to-Market), không chỉ bằng luận điểm kỹ thuật đơn thuần.
- [ ] Tuần 53–56: Cố vấn kỹ thuật (Mentoring) cho các kỹ sư Junior/Mid; xây dựng văn hóa chia sẻ kiến thức và feedback loop lành mạnh.
- [ ] Tuần 57–60: Xử lý các bất đồng kỹ thuật phức tạp trong tổ chức dựa trên dữ liệu và bằng chứng; tham gia hội đồng phỏng vấn tuyển dụng: chấm bài, đưa ra verdict, calibration cùng Engineering Leadership.

## Quý 6 — Senior Evidence & Impact

- [ ] Tuần 61–64: Hoàn thành một sáng kiến kỹ thuật (Technical Initiative) mang lại tác động lớn đo lường được (giảm p99 latency X%, tiết kiệm Y% chi phí, tăng độ tin cậy Z%).
- [ ] Tuần 65–68: Viết 2 bài Case Study chuyên sâu: (1) Kiến trúc giải quyết bài toán tải cao / tranh chấp dữ liệu, (2) Quá trình điều tra và khắc phục sự cố nghiêm trọng (Postmortem).
- [ ] Tuần 69–72: Mock Senior Interview toàn diện (Architecture, Incident Leadership, Behavioral) và hiệu chuẩn năng lực cùng Mentor.

## Quý 7–8 — Consolidation & Market Positioning

- [ ] Tuần 73–80: Duy trì vững chắc vai trò System Owner, tiếp tục dẫn dắt Design Review và phản ứng sự cố.
- [ ] Tuần 81–88: Hoàn thiện hồ sơ bằng chứng (Senior Evidence Portfolio); cập nhật CV và LinkedIn với các thành tựu đo lường được.
- [ ] Tuần 89–96: Đánh giá phạm vi tác động thực tế (Real Scope); chính thức ứng tuyển vị trí Senior Software Engineer khi đã có đầy đủ bằng chứng kiểm chứng, không chỉ dựa vào số năm kinh nghiệm đơn thuần.

**Evidence Senior cần có:**
- [ ] Dẫn một thiết kế từ requirement đến production.
- [ ] Có cải thiện đo được về latency, error rate, cost, reliability hoặc delivery.
- [ ] Xử lý incident và đóng follow-up.
- [ ] Mentor/review giúp team tiến bộ.
- [ ] Đã ngồi bàn phỏng vấn, chấm ứng viên và calibration.
- [ ] Có một cải thiện cost/cloud đo được.
- [ ] Viết được ADR/RFC/runbook rõ ràng bằng English.
- [ ] Giải thích được trade-off, failure mode, capacity, security, vận hành.

---

# Mapping evidence ↔ dải lương tham khảo (VN)

| Mốc | Evidence tối thiểu | Dải tham khảo |
|---|---|---|
| Fresher | CRUD + auth + test + CI trong 3 giờ; project clone/run/test được; giải thích OOP/collections/SQL/Spring | 12–15tr |
| Mid | ≥3 feature end-to-end; 1 performance improvement có số đo; 1 ADR/design doc; microservices/cloud vận hành cơ bản; English B2 | 25–30tr |
| Senior | Initiative có impact đo được (latency/error/cost/reliability); incident leadership; mentor/review; dẫn RFC đến production | 45–55tr |

> ponytail: dải chỉ tham khảo; JD, company size, English, đàm phán và thời điểm thị trường quyết định offer cuối.

---

# Weekly evidence checklist

- [ ] 5 ngày có ghi thời gian học/code.
- [ ] Ít nhất 1 commit có ý nghĩa.
- [ ] Ít nhất 1 test edge case.
- [ ] Ít nhất 1 bài DSA hoặc SQL có complexity/giải thích.
- [ ] Ít nhất 1 đoạn English nói hoặc viết về kỹ thuật.
- [ ] Cuối tuần: ghi Done, Gap, Next week; xóa topic không phục vụ gate kế tiếp.

---

# HỆ THỐNG TÀI LIỆU THAM KHẢO & TUTORIAL TRA CỨU CHUẨN

> Mục lục tra cứu chính thống, sách kinh điển và tutorial chất lượng cao nhất theo từng mảng kiến thức để đọc sâu và đối chiếu khi học.

## 1. Sách kinh điển gối đầu giường (Must-Read Books)

| Tên sách | Tác giả | Giá trị ứng dụng & Trọng tâm |
|---|---|---|
| **Effective Java (3rd Edition)** | Joshua Bloch | Quy chuẩn code Java chuẩn mực: Clean OOP, Immutability, Generics, Enums, Lambdas/Streams, Exceptions, Builder pattern. |
| **Designing Data-Intensive Applications (DDIA)** | Martin Kleppmann | "Kinh thánh" hệ thống phân tán: Data models, Storage engines, B-Trees vs LSM-Tree, Transactions, Replication, Partitioning, Consensus. |
| **High-Performance Java Persistence** | Vlad Mihalcea | Đi sâu vào bản chất Hibernate/JPA: JDBC batching, Caching 1st/2nd level, Connection pooling, Locking, Concurrency, N+1 fix. |
| **Java Concurrency in Practice** | Brian Goetz | Bản chất luồng trong Java: Thread safety, JMM (Java Memory Model), Happens-before, Locks, ThreadPool sizing, Race condition. |
| **Clean Code & Clean Architecture** | Robert C. Martin (Uncle Bob) | Nền tảng tư duy Clean Code: Tách method, đặt tên, SOLID principles, Hexagonal Architecture, phân tách ranh giới hệ thống. |

---

## 2. Kho Tutorials & Tài liệu tra cứu trực tiếp theo chuyên đề

### A. Java Core, JVM & Concurrency Internals
* **JVM Architecture & Memory Management (Heap, Stack, Metaspace):**
  * [Baeldung — JVM Memory Management](https://www.baeldung.com/java-memory-management-interview-questions) — Phân tích chi tiết Heap (Eden, Survivor, Old), Stack frames, Metaspace.
  * [Oracle — Java Garbage Collection Basics](https://www.oracle.com/webfolder/technetwork/tutorials/obe/java/gc01/index.html) — Cơ chế Mark & Sweep, Stop-The-World, Gen-based collection.
  * [JVM Anatomy Quarks (Aleksey Shipilëv)](https://shipilev.net/jvm/anatomy-quarks/) — Đi sâu vào bytecode, JIT compiler và memory barrier.
* **Java Concurrency & Java Memory Model (JMM):**
  * [Jenkov — Java Concurrency and Multithreading Tutorial](http://tutorials.jenkov.com/java-concurrency/index.html) — Hình vẽ trực quan, giải thích rõ `volatile`, `synchronized`, `ThreadLocal`, `ReentrantLock`.
  * [Baeldung — Java Memory Model (JMM)](https://www.baeldung.com/java-memory-model-happens-before) — Quy tắc Happens-Before, Instruction Reordering và Memory Visibility.
  * [Oracle — The Java Tutorials: Concurrency](https://docs.oracle.com/javase/tutorial/essential/concurrency/)
* **Java Virtual Threads (Project Loom - JDK 21):**
  * [Oracle — Virtual Threads Documentation](https://docs.oracle.com/en/java/javase/21/core/virtual-threads.html) — Hướng dẫn chính thức về Carrier Threads, Continuation và Non-blocking I/O.
  * [Baeldung — Java 21 Virtual Threads Guide](https://www.baeldung.com/java-virtual-threads)

### B. Spring Framework & Spring Boot Internals
* **Spring Official Reference Documentation:**
  * [Spring Framework Documentation (Core, IoC, AOP, Data)](https://docs.spring.io/spring-framework/reference/) — Tài liệu gốc của Spring Team.
  * [Spring Boot Official Reference](https://docs.spring.io/spring-boot/docs/current/reference/html/)
* **Spring Bean Lifecycle & BeanPostProcessor:**
  * [Baeldung — Spring Bean Lifecycle](https://www.baeldung.com/spring-bean-lifecycle) — Chi tiết các bước từ BeanDefinition đến `@PreDestroy`.
  * [DigitalOcean — Spring Bean Life Cycle](https://www.digitalocean.com/community/tutorials/spring-bean-lifecycle)
* **Spring AOP & Proxy Trap (Self-Invocation):**
  * [Baeldung — Intro to Spring AOP (CGLIB vs JDK Dynamic Proxy)](https://www.baeldung.com/spring-aop) — Giải thích cơ chế tạo proxy runtime.
  * [Vlad Mihalcea — Why @Transactional Doesn't Work in Self-Invocation](https://vladmihalcea.com/spring-transactional-explained/) — Bản chất vì sao proxy bị bypass khi gọi nội bộ class và 3 cách khắc phục.
  * [Baeldung — Spring @Transactional Propagation and Isolation](https://www.baeldung.com/spring-transactional-propagation-isolation)
* **Spring Security & OAuth2/JWT:**
  * [Spring Security Reference Manual](https://docs.spring.io/spring-security/reference/index.html) — Security filter chain, authentication manager, provider.
  * [Baeldung — Spring Security with JWT Guide](https://www.baeldung.com/spring-security-oauth-jwt)

### C. SQL, Database Internals & Hibernate/JPA
* **B-Tree Indexing & Query Tuning:**
  * [Use The Index, Luke! (Markus Winand)](https://use-the-index-luke.com/) — Giáo trình tra cứu kinh điển nhất về B-Tree Index, Clustered Index, Index Range Scan, Index Seek và tối ưu `WHERE`, `ORDER BY`.
* **Transaction Isolation Levels & MVCC:**
  * [PostgreSQL Official Docs — Concurrency Control & MVCC](https://www.postgresql.org/docs/current/mvcc.html) — Giải thích Snapshot Isolation, Dirty Read, Phantom Read và MVCC.
  * [MySQL InnoDB Internals — Transaction Model & Locking](https://dev.mysql.com/doc/refman/8.0/en/innodb-transaction-model.html) — Row-level locking, Next-Key Lock, Deadlock detection.
  * [Baeldung — A Beginner's Guide to Database Deadlocks](https://www.baeldung.com/cs/database-deadlocks) — Cơ chế Deadlock Graph và chiến lược Retry.
* **JPA/Hibernate High-Performance:**
  * [Vlad Mihalcea Tutorials & Blog](https://vladmihalcea.com/tutorials/) — Hướng dẫn xử lý N+1 query problem, fetch types, dirty checking, batch insert/update và distributed locking.

### D. Advanced API Design, Real-time & Web Integration
* **Idempotency Key Pattern & Payment Reliability:**
  * [Stripe API Documentation — Designing Idempotent APIs](https://stripe.com/docs/api/idempotent_requests) — Chuẩn thiết kế Idempotency Key thực tế cho hệ thống tài chính/thanh toán.
  * [Brandur — Implementing Stripe-like Idempotency Keys in Databases](https://brandur.org/idempotency-keys) — Bài phân tích kinh điển về cách lưu trữ và giải phóng Idempotency key trong Database/Redis.
* **Webhook Security & Best Practices:**
  * [Svix Webhooks Guide — Webhook Security & Signatures](https://www.svix.com/resources/guides/webhooks-security/) — Cách dùng HMAC-SHA256 ký và xác thực webhook, ngăn chặn Replay Attacks.
* **Real-time Web (WebSocket & SSE):**
  * [Baeldung — Server-Sent Events with Spring Boot](https://www.baeldung.com/spring-server-sent-events) — Triển khai `SseEmitter`, cấu hình timeout và reconnect.
  * [Spring Official Guide — Using WebSocket to Build an Interactive Web App](https://spring.io/guides/gs/messaging-stomp-websocket/) — STOMP protocol qua WebSocket.
* **RFC Standards:**
  * [RFC 7807 — Problem Details for HTTP APIs](https://datatracker.ietf.org/doc/html/rfc7807) — Chuẩn response lỗi thống nhất cho RESTful API.

### E. Microservices, Message Queues & System Design
* **Microservices Patterns (Chris Richardson):**
  * [Microservices.io Pattern Catalog](https://microservices.io/) — Tra cứu Saga Pattern (Orchestration vs Choreography), Transactional Outbox, CQRS, API Gateway.
* **Kafka & RabbitMQ:**
  * [Apache Kafka Official Documentation](https://kafka.apache.org/documentation/)
  * [Confluent — Kafka Fundamentals & Event Streaming Patterns](https://developer.confluent.io/learn/kafka-foundations/)
* **System Design & High-Level Architecture:**
  * [ByteByteGo (Alex Xu)](https://bytebytego.com/) — Sơ đồ và bài giảng trực quan về kiến trúc hệ thống quy mô lớn.
  * [System Design Primer (GitHub)](https://github.com/donnemartin/system-design-primer) — Tài nguyên mở toàn diện về thiết kế hệ thống.
