# Java & Next.js Fullstack Software Engineer — Roadmap học từng ngày

> **Mục tiêu:** 
> - **Fresher sau 4–5 tháng:** Đủ năng lực phỏng vấn và trúng tuyển cả hai vị trí: **Java Backend Developer** và **Fullstack Java + Next.js Developer** tại thị trường Việt Nam (Mức lương mục tiêu: 12–15+ triệu VNĐ).
> - **Junior thực chiến & Mid sau 12–14 tháng tiếp theo:** 25–30 triệu VNĐ.
> - **Senior Software Engineer sau 1–2 năm tích lũy scope thật:** 45–55+ triệu VNĐ.
>
> **Lịch chuẩn 15 giờ/tuần — Phát triển song song theo Lát Cắt Dọc Tính Năng (Vertical Slice Driven: 70% Java / 30% Next.js):**
> - **Nguyên tắc bất biến:** Triển khai tới chức năng nào thì làm chủ kiến thức Java Backend VÀ Next.js Frontend ở chính chức năng đó. Tuyệt đối không code mù hàng loạt API backend rồi cuối tuần mới làm frontend. Mỗi tính năng hoàn thiện trọn vẹn cả 2 phía song song:
>   - **Phần Backend (~70% thời lượng):** Code Controller, Service, Domain Logic, Database/Cache $\rightarrow$ Học sâu bản chất Java 17 LTS, Spring Boot 3.x, OOP, Type Safety, Concurrency, Database, Performance.
>   - **Phần Frontend (~30% thời lượng):** Xây dựng Component Next.js (App Router, TypeScript, Tailwind) tiêu thụ trực tiếp API vừa viết $\rightarrow$ Học State, Hooks, Form validation, Client Caching, UX.
>   - **Vòng lặp phản hồi tức thì (Immediate Feedback Loop):** Chạy và kiểm thử trực tiếp trên trình duyệt ngay trong ngày/chức năng đó, nhìn thấy dữ liệu và giao diện tương tác thật.
> - **Thứ 2 – Thứ 6 (2h/ngày):** Mỗi chặng 1–2 ngày hoàn thiện trọn vẹn 1 Lát cắt chức năng (Vertical Slice: Backend Java + Frontend Next.js + Test trên browser).
> - **Thứ 7 (5h):** Tích hợp sâu, tối ưu hóa hiệu năng, xử lý các kịch bản biên (Edge cases, Race conditions, Errors), viết bài test tự động và hoàn thiện tài liệu.
> - **Chủ nhật:** Nghỉ hoặc bù tối đa 2 giờ.
>
> **Chiến Lược Luyện DSA Cho Các Vòng Phỏng Vấn Live Coding (Live Coding Track — 2–3 bài LeetCode/tuần):**
> - **Bối cảnh thị trường:** Nhiều công ty Product, FinTech, Unicorn tại Việt Nam (Shopee, VNG/Zalo, NAB, MoMo, Axon, Line Technology, Grab...) và các công ty Global Outsourcing (FPT Software Global, KMS...) đều có vòng Online Assessment (HackerRank/Codility/LeetCode) và vòng phỏng vấn Live Coding 1-on-1 trước khi vào vòng chuyên sâu Framework/System.
> - **Phương pháp "Pattern-Based DSA" (Blind 75 / NeetCode 150):** Tuyệt đối không cày bừa hàng trăm bài ngẫu nhiên. Lộ trình chọn lọc chính xác **40 bài cốt lõi nhất** thuộc 14 mẫu thuật toán kinh điển, phân bổ nhịp nhàng 2 bài/tuần bám sát cấu trúc dữ liệu Java học trong tuần.
> - **Quy Trình 4 Bước Chuẩn Mực Khi Live Coding (The 4-Step Live Coding Framework):**
>   1. **Clarify (3–5m):** Đặt câu hỏi làm rõ đề, xác định input/output, hỏi về giới hạn dữ liệu ($N \le 10^5$ hay $10^9$) và các trường hợp biên (null, rỗng, số âm, mảng trùng lặp).
>   2. **Approach & Big-O (5–7m):** Nghĩ thành tiếng (Think Out Loud). Nêu giải pháp thô (Brute-force) trước $\rightarrow$ đề xuất giải pháp tối ưu ($O(N)$ dùng Hash Map / Two Pointers thay vì $O(N^2)$). Phân tích Time & Space Complexity trước khi code; thống nhất với Interviewer rồi mới bắt đầu gõ phím.
>   3. **Clean Idiomatic Java (15m):** Viết code sạch bằng Java 17 chuẩn mực (dùng đúng Collections `HashMap`, `ArrayList`, `Deque`, `PriorityQueue`; biến đặt tên rõ nghĩa, không viết tắt, bẻ nhỏ hàm nếu cần).
>   4. **Dry Run & Verification (3–5m):** Tự mình chạy tay (dry run) từng dòng với một ví dụ cụ thể và edge cases; chủ động bắt bug trước khi người phỏng vấn lên tiếng.
>
> **Quy tắc:** học xong phải code; feature phải có test; mỗi tuần có commit; mỗi tính năng đều có giao diện tương tác chạy trên browser; mỗi tuần luyện 2 bài DSA live code.

---

# GIAI ĐOẠN 1 — TUẦN 1–8
## Java 17 LTS + Spring Boot Foundation & Next.js Frontend (70% Backend / 30% Frontend)

**Mục tiêu cuối giai đoạn:** 
- **Backend (70%):** Tự tay dựng và làm chủ một Backend Spring Boot 3.x chuẩn sản xuất chạy trên **Java 17 LTS**; hiểu sâu kiến trúc phân tầng 3 layers; tự viết RESTful API kết nối Database quan hệ (PostgreSQL/MySQL); nắm vững cú pháp, câu điều kiện, vòng lặp, OOP, Java Collections, Domain Exceptions, Stream API và Concurrency Locking cơ bản trực tiếp trên codebase Giao Vặt; có test tự động MockMvc và Testcontainers.
- **Frontend (30%):** Dựng được giao diện Web Giao Vặt hoàn chỉnh bằng **Next.js (App Router, TypeScript, Tailwind CSS)**: Form đặt đơn có validation Zod, Bảng tin đơn hàng (`/feed`) hiển thị danh sách đơn từ DB, nút "Nhận đơn" (Claim) tương tác trực tiếp với API Backend.
- **Tích hợp Fullstack:** Khắc phục triệt để lỗi CORS, xử lý định dạng lỗi chuẩn RFC 7807 `ProblemDetail` hiển thị lên UI, hoàn thành luồng End-to-End v0 chạy mượt mà trên trình duyệt.

> **NGUYÊN TẮC HỌC CỐT LÕI CỦA GIAI ĐOẠN 1 (PRACTICE-FIRST FULLSTACK VIA GIAO VẶT):**
> - **Môi trường kỹ thuật chuẩn:** Sử dụng **Java 17 LTS** + **Spring Boot 3.x** cho Backend; **Next.js 14+ (App Router, TypeScript)** cho Frontend.
> - **Tuyệt đối không học qua ví dụ console rời rạc nhỏ lẻ:** Bỏ qua các bài toán máy tính cầm tay, quản lý sinh viên mảng console, quản lý thư viện console. Chúng gây phân mảnh và không phản ánh cách tư duy của kỹ sư phần mềm thực chiến.
> - **Phát triển tính năng song song BE và FE (Vertical Slice Driven):**
>   1. Không code mù hàng loạt API backend rồi bỏ ngỏ giao diện. Mỗi tuần chia thành các chức năng cụ thể của Giao Vặt.
>   2. Với mỗi chức năng: code API Backend (nắm kiến thức Java phần đó) $\rightarrow$ code ngay Component Frontend Next.js tương ứng (nắm kiến thức Next.js phần đó) $\rightarrow$ bật trình duyệt lên kiểm thử ngay lập tức.
>   3. Nhờ làm song song, người học làm chủ tự nhiên cả logic cú pháp Java (kiểu dữ liệu, toán tử, `if/else`, switch-case, vòng lặp, OOP, Collections, Custom Exceptions, Stream API) lẫn kiến trúc Frontend hiện đại (React state, hooks, Zod schema, component composition).

**Dự án chính: Giao Vặt Platform** — On-Demand Crowdsourced Delivery Platform (Nền tảng tiện chuyến & giao việc vi mô)
- **Scope nghiệp vụ:** Hệ thống kết nối Người tạo đơn (Creator) và Người tiện chuyến / Tài xế (Runner). Khách đăng nhu cầu giao hàng/đi nhờ xe $\rightarrow$ Đơn hàng hiển thị trên Bảng tin công khai (`Order Feed`) $\rightarrow$ Runner duyệt bảng tin và nhận đơn (`claimOrder`).
- **Core Mechanism:** Bảng tin đơn hàng tập trung (`OPEN` orders), cơ chế khóa chống tranh chấp khi nhiều Runner cùng bấm nhận 1 đơn trong cùng tích tắc (Concurrency Locking với `@Version`), thông báo real-time cập nhật trạng thái đơn (Server-Sent Events / SSE).
- **Core features:** Creator đăng đơn (điểm đón, điểm trả, khoảng cách, cước phí), Bảng tin đơn mở công khai, Runner duyệt feed & nhận đơn (`OPEN` $\rightarrow$ `ACCEPTED`), cập nhật hành trình (`PICKED_UP` $\rightarrow$ `IN_TRANSIT` $\rightarrow$ `COMPLETED` / `CANCELLED`), tính giá linh hoạt (Strategy Pattern), phân quyền Creator vs Runner bằng JWT.
- **Architecture:** Monolith Spring Boot 3 chuẩn 3 layers (Controller–Service–Repository Seam) + Next.js App Router Frontend, In-Memory Cache/Queue (Redis ở Giai đoạn 2), PostgreSQL/MySQL tập trung.

### Danh mục 9 Module Chức năng Bắt buộc của App Giao Vặt (Khai thác 100% Roadmap)
1. **Module 1 — Authentication & RBAC (Tuần 9, 15):** Đăng ký/đăng nhập Creator & Runner; Spring Security 6 + JWT Stateless; Refresh Token Rotation; phân quyền `@PreAuthorize("hasRole('...')")`; cấu hình MDC Logging `traceId`; ẩn số điện thoại khách trên public feed; giao diện Next.js phân quyền theo Role.
2. **Module 2 — Đăng đơn & Định giá thông minh (Tuần 3, 6, 15, 17):** Jakarta Validation `@Valid` & Zod validation ở Frontend; GoF Strategy Pattern cho tính giá cước (`StandardPricingStrategy`, `SurgePricingStrategy` giờ cao điểm, `BadWeatherPricingStrategy` thời tiết xấu); Idempotency Key Pattern chống bấm đúp tạo đơn trùng; chuẩn hóa lỗi theo RFC 7807 `ProblemDetail`.
3. **Module 3 — Redis In-Memory Priority Queue & Feed (Tuần 10):** Redis Sorted Set (ZSET) lưu `orders:open` theo score thời gian/giá cước; Cache-Aside pattern cho chi tiết đơn `order:{id}`; Sliding Window Rate Limiting bằng Redis; Next.js hiển thị đếm ngược khi bị rate limit.
4. **Module 4 — Runner Claim Order & Concurrency Control (Tuần 7, 8, 17, 24–26):** Giải quyết triệt để race condition khi nhiều Runner cùng bấm nhận 1 đơn bằng JPA Optimistic Locking (`@Version`); đối chứng so sánh với Pessimistic Locking hoặc Redisson Distributed Lock; Next.js Optimistic UI & Rollback khi gặp lỗi 409 Conflict.
5. **Module 5 — Real-time Feed & Notifications (Tuần 17):** Server-Sent Events (`SseEmitter`) quản lý luồng real-time một chiều nhẹ; Event-Driven Architecture (`ApplicationEventPublisher`); Thread Pool bất đồng bộ Java 17 LTS; Next.js lắng nghe qua native `EventSource` tự động nhảy đơn mới không cần F5.
6. **Module 6 — Quản lý vòng đời đơn & State Machine (Tuần 2, 4, 6, 8, 12):** Quản lý chu trình trạng thái: `DRAFT` $\rightarrow$ `OPEN` $\rightarrow$ `ACCEPTED` $\rightarrow$ `PICKED_UP` $\rightarrow$ `IN_TRANSIT` $\rightarrow$ `COMPLETED` / `CANCELLED`; Custom Exceptions (`InvalidOrderStateException`, `OrderNotFoundException`); Global Exception Handler `@RestControllerAdvice`; Unit & Integration tests với MockMvc.
7. **Module 7 — Thanh toán Sandbox & Webhook (Tuần 17, 49):** Tích hợp cổng thanh toán giả lập (VNPay/Stripe Sandbox); Webhook Receiver xác thực chữ ký số HMAC-SHA256; Idempotent Webhook Processing (chống duplicate webhook callback khi cổng gửi lại).
8. **Module 8 — Báo cáo định kỳ & Spring Batch (Tuần 4, 22):** `@Scheduled` hoặc Spring Batch tự động tổng kết doanh thu Runner lúc 00:00 hàng ngày; xuất file báo cáo Excel bằng Apache POI; Java Stream API (`groupingBy`, `summarizingDouble`); hiển thị biểu đồ trên giao diện Next.js.
9. **Module 9 — Database Tuning, Testing & DevOps (Tuần 5, 7, 11, 12, 36):** Flyway Database Migrations (`V1`, `V2`); B-Tree Composite Index `(status, created_at)` kèm benchmark `EXPLAIN ANALYZE`; Testcontainers (PostgreSQL + Redis thật); Multi-thread stress test với JUnit 5 + `CountDownLatch`; Dockerfile multi-stage cho cả Backend và Frontend; Docker Compose full stack; GitHub Actions CI pipeline.

---

## Tuần 1 — Khởi tạo Base Giao Vặt: Backend Spring Boot (Java 17 LTS) & Frontend Next.js Song Song

### Thứ 2 — Khởi Tạo Nền Tảng Song Song: Backend Spring Boot & Frontend Next.js (2h)
- [ ] **Backend (70%):**
  - Cài đặt JDK 17 (Java 17 LTS), IntelliJ IDEA, Git, Maven (hoặc Gradle wrapper); kiểm tra `java -version`, `mvn -version`, `git --version`.
  - Khởi tạo dự án Spring Boot 3.x (Java 17) cho Giao Vặt qua Spring Initializr (dependencies: `spring-boot-starter-web`, `lombok`, `spring-boot-starter-test`).
  - Khám phá cấu trúc thư mục của 1 Backend Spring Boot chuẩn: `src/main/java`, `src/main/resources`, `pom.xml` (quản lý dependency, plugin compiler target 17).
  - Tìm hiểu điểm khởi chạy ứng dụng: `@SpringBootApplication`, phương thức `main`, Spring ApplicationContext khởi động ra sao.
- [ ] **Frontend (30%):**
  - Cài đặt Node.js LTS; khởi tạo dự án Next.js 14+ trong thư mục `frontend/` bằng lệnh `npx create-next-app@latest` (TypeScript, Tailwind CSS, App Router, ESLint).
  - Khám phá cấu trúc thư mục App Router: `app/layout.tsx`, `app/page.tsx`, `components/`, `lib/`. Hiểu khái niệm cốt lõi: **Server Components (RSC - mặc định)** vs **Client Components (`'use client'`)**.
- [ ] Khởi chạy cả 2 server local (Backend cổng 8080, Frontend cổng 3000); commit initial codebase.

### Thứ 3 — Chức năng 1: Hoàn Thiện Lát Cắt Ping Health Check Cả Hai Phía (2h)
- [ ] **Backend (70%):**
  - Tạo Controller đầu tiên: `PingController` với endpoint `GET /api/v1/ping` trả về JSON trạng thái `{"status": "UP", "message": "Giao Vat Platform v1 - Ready"}`.
  - Tìm hiểu cơ chế HTTP Request/Response, annotation `@RestController`, `@GetMapping`.
  - Học cú pháp Java nền tảng: Biến, kiểu dữ liệu primitive vs reference, `String`, hằng số (`final`), quy ước đặt tên (CamelCase, Clean Code).
  - Cấu hình **CORS** bằng `@CrossOrigin(origins = "http://localhost:3000")` hoặc `WebMvcConfigurer` cho phép frontend gọi sang.
- [ ] **Frontend (30%):**
  - Xây dựng Component `PingStatus` (`'use client'`): Dùng `fetch()` gọi API `http://localhost:8080/api/v1/ping` để hiển thị trạng thái kết nối lên trang chủ Next.js.
  - Quản lý trạng thái bằng `useState` và `useEffect`: Hiển thị badge xanh *"Đã kết nối máy chủ"* hoặc đỏ *"Mất kết nối máy chủ"*.
- [ ] **Chạy thử trên trình duyệt:** Mở `http://localhost:3000`, thấy ngay giao diện Next.js hiển thị badge xanh kết nối thành công tới Spring Boot!

### Thứ 4 — Chức năng 2: Khung API Đơn Hàng & Đồng Bộ Interface Type (2h)
- [ ] **Backend (70%):**
  - Tạo `OrderController` với 2 endpoint cơ bản: `POST /api/v1/orders` (tạo đơn hàng) và `GET /api/v1/orders` (lấy danh sách đơn hàng).
  - Khái niệm DTO (Data Transfer Object): Tạo `CreateOrderRequest` và `OrderResponse`.
  - Học Java 17 `record`: Viết DTO bằng Java `record` (immutable data carrier gọn gàng) vs class truyền thống.
  - Học cách nhận dữ liệu trong Spring Boot: `@PostMapping`, `@RequestBody`, `@RequestParam`.
- [ ] **Frontend (30%):**
  - Tạo file `types/order.ts`: Định nghĩa TypeScript interface `CreateOrderInput` và `Order` khớp 1:1 với các trường trong Java DTO record của Backend.
  - Xây dựng hàm gọi API `fetchOrders()` trong thư mục `lib/api.ts`.
- [ ] **Chạy thử:** Kiểm tra tính khớp kiểu (Type-safe contract) giữa TypeScript Interface và Java Record DTO; commit.

### Thứ 5 — Chức năng 3: IoC/DI Tầng Service & Mock Data Hiển Thị Trình Duyệt (2h)
- [ ] **Backend (70%):**
  - Học nguyên lý Inversion of Control (IoC) và Dependency Injection (DI) trong Spring Boot.
  - Phân tách trách nhiệm: Controller chỉ nhận HTTP và trả response; Logic nghiệp vụ thuộc về Service.
  - Tạo `OrderService` (đánh dấu `@Service`), inject vào `OrderController` qua Constructor Injection (Spring Best Practice, tránh dùng `@Autowired` trên field).
  - Viết method trong `OrderService`: tạo 2 đơn hàng mock và trả về `List<OrderResponse>`.
- [ ] **Frontend (30%):**
  - Tạo trang danh sách đơn thô (`app/orders/page.tsx`) trên Next.js gọi `GET /api/v1/orders`.
  - Render danh sách đơn hàng mock ra màn hình với layout Tailwind đơn giản.
- [ ] **Chạy thử trên trình duyệt:** Tải trang `http://localhost:3000/orders`, thấy ngay danh sách 2 đơn hàng mock từ Spring Boot Service hiển thị lên giao diện web!

### Thứ 6 — Chuẩn Hóa API Contract & OpenAPI / Swagger (2h)
- [ ] **Backend (70%):**
  - Tích hợp SpringDoc OpenAPI / Swagger (`/swagger-ui.html`) để tự động sinh tài liệu API trực quan.
  - Thêm chú thích `@Operation`, `@ApiResponse` mô tả rõ ràng các tham số request và response.
  - Chuẩn hóa cấu hình CORS toàn cục cho toàn bộ các endpoint `/api/v1/**`.
- [ ] **Frontend (30%):**
  - Xây dựng API Client tập trung (`lib/api.ts`) với cấu hình baseURL đọc từ biến môi trường `.env.local` (`NEXT_PUBLIC_API_URL=http://localhost:8080`).
  - Viết helper hàm xử lý response và parse JSON an toàn; commit.

### Thứ 7 — Fullstack Base Lab & Luyện Live Coding DSA Mở Đầu (5h)
- [ ] 2h: Khởi chạy song song cả 2 dịch vụ; kiểm thử trọn vẹn luồng gọi API từ Next.js sang Spring Boot trên trình duyệt (F12 Network tab kiểm tra status 200, headers, CORS).
- [ ] 1h: Kiểm tra tài liệu Swagger UI tại `http://localhost:8080/swagger-ui.html` và viết README giới thiệu kiến trúc Fullstack Monorepo.
- [ ] 1h: Commit toàn bộ mã nguồn và tag release Git: `fullstack-base-v0`.
- [ ] 1h: **Luyện Live Coding DSA (Arrays & Hashing — Khởi động):**
  - Thực hành khung 4 bước (Clarify $\rightarrow$ Big-O $\rightarrow$ Code Java 17 $\rightarrow$ Dry Run):
  - Bài 1: **Two Sum** (LeetCode 1, Easy) — Dùng `HashMap` 1 lần duyệt tối ưu từ $O(N^2)$ xuống $O(N)$ Time / $O(N)$ Space.
  - Bài 2: **Valid Anagram** (LeetCode 242, Easy) — Dùng mảng tần suất `int[26]` tối ưu $O(N)$ Time / $O(1)$ Space.
  - Lưu mã nguồn giải pháp vào thư mục `dsa/week-01/`; commit.

**Chủ nhật:** Nghỉ; tự kiểm tra lại kiến trúc Spring Boot 3 layers và luồng tương tác Next.js.

---

## Tuần 2 — Chức Năng Tạo Đơn Hàng & Máy Trạng Thái Đơn Hàng

### Thứ 2 — Chức Năng Tạo Đơn (Backend: Model, Kiểu Dữ Liệu & Tính Cước Sàn) (2h)
- [ ] **Backend (70%):**
  - Tạo class thực thể nghiệp vụ trung tâm: `Order` (chứa: `id`, `creatorId`, `runnerId`, `pickupAddress`, `dropoffAddress`, `distanceInKm`, `offeredPrice`, `minPrice`, `status`, `category`, `createdAt`).
  - Học các kiểu dữ liệu số thực và tiền tệ trong Java: `BigDecimal` vs `long` (lý do không dùng `double`/`float` cho tiền tệ vì sai số dấu phẩy động).
  - Học Java Enum: Tạo `OrderCategory` (`RIDE`, `FOOD`, `PARCEL`) và `OrderStatus` (`OPEN`, `ACCEPTED`, `PICKED_UP`, `IN_TRANSIT`, `COMPLETED`, `CANCELLED`).
  - Viết method tính cước sàn tối thiểu `calculateMinPrice(distanceInKm, category)` bằng `switch expression` (Java 17): `RIDE` (10k/km), `FOOD` (12k/km), `PARCEL` (8k/km).
  - Thêm Jakarta Validation `@Valid` trên DTO: `@NotBlank` địa chỉ, `@Positive` khoảng cách, `@Min` cước phí.
- [ ] **Frontend (30%):**
  - Định nghĩa Zod schema validation trên Next.js (`lib/validations/order.ts`) với các quy tắc ràng buộc tương đồng backend: địa chỉ không rỗng, khoảng cách $> 0$, cước phí $\ge$ cước sàn tối thiểu; commit.

### Thứ 3 — Chức Năng Tạo Đơn (Frontend: Form Nhập Liệu & Submit Đơn Hàng) (2h)
- [ ] **Frontend (70%):**
  - Xây dựng trang Form Tạo Đơn Hàng (`app/orders/create/page.tsx`) bằng **React Hook Form** kết hợp **Zod Schema**: Ô nhập điểm đón, điểm trả, khoảng cách, dropdown danh mục, ô nhập cước đề xuất.
  - Xử lý validate ngay khi gõ phím; tự động tính và hiển thị mức cước sàn gợi ý theo khoảng cách và danh mục người dùng vừa chọn.
  - Viết hàm submit form gọi `POST /api/v1/orders` sang Backend.
- [ ] **Backend (30%):**
  - Viết logic lưu đơn hàng in-memory trong `OrderService` và trả về `OrderResponse` kèm mã đơn vừa sinh.
- [ ] **Chạy thử trên trình duyệt:** Điền form trên Next.js $\rightarrow$ Bấm "Tạo đơn hàng" $\rightarrow$ Backend nhận và xử lý $\rightarrow$ Web hiển thị Toast thông báo xanh: *"Tạo đơn hàng #1 thành công!"*.

### Thứ 4 — Chức Năng Máy Trạng Thái Đơn Hàng (State Machine & Guard Clauses) (2h)
- [ ] **Backend (70%):**
  - Học quản lý chu trình trạng thái đơn hàng (State Transitions):
    - Đơn chỉ có thể nhận (`ACCEPTED`) khi đang ở trạng thái `OPEN`.
    - Đơn chỉ có thể chuyển sang `PICKED_UP` khi đang ở trạng thái `ACCEPTED`.
    - Khách chỉ được hủy (`CANCELLED`) khi đơn chưa có Runner nhận (`OPEN`).
  - Viết hàm kiểm tra và chuyển trạng thái `canTransitionTo(currentStatus, targetStatus)`.
  - Áp dụng kỹ thuật "Early Return / Guard Clauses", tránh nested `if/else` sâu; commit.
- [ ] **Frontend (30%):**
  - Tạo component `StatusBadge` hiển thị trạng thái đơn hàng dạng badge màu sắc trực quan (Xanh lá `OPEN`, Vàng `ACCEPTED`, Xanh dương `IN_TRANSIT`, Xám `COMPLETED`, Đỏ `CANCELLED`).
  - Đưa `StatusBadge` vào hiển thị cạnh tiêu đề đơn hàng; commit.

### Thứ 5 — Chức Năng Danh Sách Đơn Bảng Tin & Collections In-Memory (2h)
- [ ] **Backend (70%):**
  - Học các loại vòng lặp trong Java: `for` truyền thống, enhanced `for-each`, `while`, `break`, `continue`.
  - Lưu trữ danh sách đơn hàng in-memory bằng Java Collections (`List<Order>`, `ArrayList`).
  - Viết hàm tìm kiếm và lọc đơn hàng theo từ khóa địa chỉ hoặc cước phí tối thiểu bằng vòng lặp. Dùng `while` mô phỏng sinh ID tự tăng an toàn.
  - Phân tích độ phức tạp thời gian Big-O: $O(N)$; commit.
- [ ] **Frontend (30%):**
  - Nâng cấp trang danh sách đơn hàng trên Next.js: Hiển thị các đơn vừa tạo dạng danh sách thẻ, có hiển thị `StatusBadge` và cước phí định dạng VNĐ.
- [ ] **Chạy thử trên trình duyệt:** Vào form tạo đơn 1, tạo đơn 2 $\rightarrow$ Mở trang danh sách thấy cả 2 đơn hàng tự động xuất hiện với badge `OPEN`!

### Thứ 6 — Chức Năng Báo Lỗi Nghiệp Vụ Cước Sàn (Validation Error Handling) (2h)
- [ ] **Backend (70%):**
  - Kiểm tra điều kiện nghiệp vụ: Nếu `offeredPrice < minPrice` gợi ý $\rightarrow$ Trả về mã lỗi HTTP `400 Bad Request` kèm thông báo: *"Cước phí đề xuất không được nhỏ hơn cước sàn tối thiểu: ... VNĐ"*.
  - Bắt lỗi vi phạm Jakarta Validation `@Valid` và trả về danh sách lỗi các trường; commit.
- [ ] **Frontend (30%):**
  - Bắt mã lỗi 400 từ Backend trong hàm gọi API của Next.js.
  - Hiển thị thông báo lỗi màu đỏ trực tiếp dưới ô nhập cước phí: *"Giá đề xuất quá thấp so với cước sàn gợi ý"*; commit.

### Thứ 7 — Fullstack Order Slice Lab & Luyện Live Coding DSA (5h)
- [ ] 2h: Thử nghiệm thực tế trên trình duyệt: Cố ý nhập giá thấp hơn cước sàn $\rightarrow$ Kiểm tra giao diện chặn lỗi đúng $\rightarrow$ Nhập giá hợp lệ $\rightarrow$ Tạo đơn thành công; kiểm tra badge đổi màu.
- [ ] 1h: Viết unit test cho logic tính giá cước và state machine.
- [ ] 1h: Dọn dẹp mã nguồn và commit code.
- [ ] 1h: **Luyện Live Coding DSA (Two Pointers — Hai Con Trỏ):**
  - Bài 3: **Valid Palindrome** (LeetCode 125, Easy) — Kỹ thuật 2 con trỏ chạy từ 2 đầu bỏ qua ký tự đặc biệt $O(N)$ Time / $O(1)$ Space.
  - Bài 4: **Two Sum II - Input Array Is Sorted** (LeetCode 167, Medium) — Hai con trỏ co hẹp trên mảng tăng dần $O(N)$ Time / $O(1)$ Space (giải thích vì sao tối ưu hơn HashMap).
  - Tự luyện giải thích Big-O bằng tiếng Anh/Việt; commit code vào `dsa/week-02/`.

---

## Tuần 3 — Chức Năng Định Giá Đa Thuật Toán (Strategy Pattern) & Bảng Tin Đơn Hàng (Order Feed)

### Thứ 2 — Chức Năng Định Giá Thông Minh (Backend: GoF Strategy Pattern) (2h)
- [ ] **Backend (70%):**
  - Học nguyên lý OOP: Interface, Abstract Class, Polymorphism (Tính đa hình), Composition over Inheritance.
  - Áp dụng **Strategy Pattern** cho bài toán tính cước phí Giao Vặt (Module 2):
    - Tạo interface `PricingStrategy` với method `calculatePrice(distanceInKm)`.
    - Triển khai `StandardPricingStrategy` (giá cước ngày thường).
    - Triển khai `SurgePricingStrategy` (nhân hệ số giờ cao điểm 1.5x).
    - Triển khai `BadWeatherPricingStrategy` (nhân hệ số trời mưa 1.3x).
  - Dùng Spring `@Component` và `@Qualifier` hoặc Factory để chọn strategy linh hoạt theo điều kiện; commit.
- [ ] **Frontend (30%):**
  - Thêm các ô checkbox tùy chọn trên Form Tạo Đơn của Next.js: "Giờ cao điểm (1.5x)", "Thời tiết mưa gió (1.3x)"; commit.

### Thứ 3 — Chức Năng Định Giá Thông Minh (Frontend: Dynamic Calculation & UI) (2h)
- [ ] **Frontend (70%):**
  - Xử lý tính cước động trên Next.js: Khi người dùng tích chọn "Giờ cao điểm" hoặc "Thời tiết xấu", giao diện tự động tính toán lại mức cước ước tính theo thời gian thực ($0$ms delay) trước khi submit.
  - Gửi kèm cờ `pricingOption` (`STANDARD`, `SURGE`, `BAD_WEATHER`) trong payload request tạo đơn.
- [ ] **Backend (30%):**
  - Controller nhận tùy chọn định giá, áp dụng đúng `PricingStrategy` tương ứng để tính toán cước sàn và lưu thông tin vào đơn hàng.
- [ ] **Chạy thử trên trình duyệt:** Tích chọn checkbox "Trời mưa" $\rightarrow$ cước sàn gợi ý tự nhảy tăng 30% trên giao diện $\rightarrow$ Bấm tạo đơn $\rightarrow$ Backend áp dụng đúng `BadWeatherPricingStrategy`!

### Thứ 4 — Chức Năng Bảng Tin Ưu Tiên (Backend: Java Collections Deep Dive) (2h)
- [ ] **Backend (70%):**
  - Học Java Collections Framework: Hierarchy của `Collection`, `List`, `Set`, `Map`.
  - `ArrayList` vs `LinkedList`: Hiệu năng truy xuất ngẫu nhiên $O(1)$ vs chèn/xóa $O(N)$ trong bảng tin đơn hàng.
  - `HashMap` vs `ConcurrentHashMap`:
    - Lưu trữ danh sách đơn hàng in-memory dạng Key-Value (`Map<Long, Order>`).
    - Tìm kiếm đơn theo ID với độ phức tạp $O(1)$.
    - Hiểu sâu cơ chế bên trong của `HashMap`: Hash function, Buckets, Hash Collision (Chaining bằng LinkedList / Red-Black Tree khi bucket $\ge 8$), Load Factor (0.75), Rehashing.
    - Hợp đồng bất biến: `equals()` và `hashCode()` contract.
  - Áp dụng `PriorityQueue` sắp xếp thứ tự ưu tiên bảng tin theo cước phí đề xuất ($O(\log N)$); commit.
- [ ] **Frontend (30%):**
  - Thiết kế Component `OrderCard` tái sử dụng: Hiển thị điểm đón, điểm trả, khoảng cách km, badge loại đơn hàng (Chở người / Đồ ăn / Bưu kiện), mức cước nổi bật và thời gian tạo; commit.

### Thứ 5 — Chức Năng Bảng Tin Ưu Tiên (Frontend: Order Feed UI & Sorting) (2h)
- [ ] **Frontend (70%):**
  - Dựng trang Bảng Tin Đơn Hàng công khai (`app/feed/page.tsx`) dành cho Runner.
  - Gọi API `GET /api/v1/orders/feed`, render danh sách thẻ `OrderCard` dạng lưới (grid layout) với Tailwind CSS.
  - Hiển thị thông báo trạng thái "Đang tải dữ liệu..." (Loading skeleton) và "Chưa có đơn hàng nào" (Empty state).
- [ ] **Backend (30%):**
  - API `GET /api/v1/orders/feed` lấy các đơn hàng từ `PriorityQueue` in-memory và trả về danh sách đã sắp xếp.
- [ ] **Chạy thử trên trình duyệt:** Tạo 3 đơn hàng với mức cước 50k, 150k, 80k $\rightarrow$ Mở trang `/feed`, thấy đơn 150k tự động nhảy lên đầu tiên!

### Thứ 6 — Chức Năng Lọc Đơn Theo Danh Mục (Category Filtering) (2h)
- [ ] **Backend (70%):**
  - Thêm query param `category` vào API feed: `GET /api/v1/orders/feed?category=FOOD`.
  - Lọc danh sách đơn hàng in-memory theo `OrderCategory` bằng Collections.
- [ ] **Frontend (30%):**
  - Thêm thanh Tab lọc danh mục trên trang `/feed`: [Tất cả] | [Chở người] | [Đồ ăn] | [Bưu kiện].
  - Bấm chọn tab nào thì gọi API lọc theo danh mục đó.
- [ ] **Chạy thử trên trình duyệt:** Bấm tab "Đồ ăn" trên web $\rightarrow$ danh sách thẻ đơn hàng lọc tức thì, chỉ hiện đơn hàng đồ ăn!

### Thứ 7 — Fullstack Feed Integration Lab & Luyện Live Coding DSA (5h)
- [ ] 2h: Kiểm thử toàn diện luồng: Tạo nhiều đơn với các danh mục và mức giá khác nhau $\rightarrow$ Kiểm tra Bảng tin sắp xếp và lọc chính xác 100%.
- [ ] 1h: Viết bài test JUnit cho Strategy Pattern và bài test component `OrderCard` ở Frontend.
- [ ] 1h: Commit và tổng kết tuần.
- [ ] 1h: **Luyện Live Coding DSA (Hashing & Frequency Mapping):**
  - Bài 5: **Contains Duplicate** (LeetCode 217, Easy) — Dùng `HashSet` kiểm tra phần tử trùng lặp trong $O(N)$ Time / $O(N)$ Space.
  - Bài 6: **Group Anagrams** (LeetCode 49, Medium) — Gom nhóm chuỗi đảo chữ bằng chuỗi đã sắp xếp hoặc mảng tần suất làm Key trong `HashMap` $O(N \cdot K \log K)$ Time / $O(N \cdot K)$ Space.
  - Tự luyện giải thích cách thiết kế Key trong HashMap cho Interviewer; commit code vào `dsa/week-03/`.

---

## Tuần 4 — Chức Năng Xử Lý Ngoại Lệ Chuẩn RFC 7807 & Báo Cáo Doanh Thu (Stream API)

### Thứ 2 — Chức Năng Xử Lý Ngoại Lệ Tập Trung Chuẩn RFC 7807 (Backend) (2h)
- [ ] **Backend (70%):**
  - Học cơ chế ngoại lệ Java: Checked vs Unchecked (`RuntimeException`). Tại sao Spring Boot hiện đại ưu tiên Unchecked Domain Exceptions?
  - Tạo bộ Custom Domain Exceptions cho Giao Vặt:
    - `OrderNotFoundException` (khi không tìm thấy ID đơn hàng).
    - `InvalidOrderStateException` (khi chuyển trạng thái sai quy tắc).
    - `PriceBelowMinimumException` (khi khách trả giá thấp hơn giá sàn).
  - Xây dựng Global Exception Handler tập trung bằng `@RestControllerAdvice` và `@ExceptionHandler`.
  - Chuẩn hóa payload lỗi theo chuẩn quốc tế **RFC 7807 ProblemDetail** (Spring 6 / Spring Boot 3 hỗ trợ native: `status`, `title`, `detail`, `instance`, `timestamp`); tuyệt đối không để lộ stack trace thô; commit.
- [ ] **Frontend (30%):**
  - Khai báo TypeScript interface `ProblemDetail` khớp với RFC 7807 của Backend: `type`, `title`, `status`, `detail`, `timestamp`; commit.

### Thứ 3 — Chức Năng Xử Lý Ngoại Lệ Tập Trung Chuẩn RFC 7807 (Frontend Toast & Error Handling) (2h)
- [ ] **Frontend (70%):**
  - Xây dựng module xử lý lỗi tập trung phía Frontend (`lib/error-handler.ts`).
  - Tự động bắt payload `ProblemDetail` từ Backend và render thông báo Toast cảnh báo màu đỏ thân thiện (hiển thị `title` và `detail` cụ thể).
  - Xử lý các mã lỗi phổ biến: 400 (Dữ liệu sai), 404 (Không tìm thấy), 409 (Xung đột trạng thái).
- [ ] **Backend (30%):**
  - Viết test kiểm tra các endpoint ném ngoại lệ và trả về đúng status code RFC 7807.
- [ ] **Chạy thử trên trình duyệt:** Cố tình truy cập chi tiết đơn hàng ID 9999 không tồn tại $\rightarrow$ Web hiển thị Toast thông báo đỏ đẹp mắt: *"Không tìm thấy đơn hàng: Đơn hàng #9999 không tồn tại trong hệ thống"* thay vì bị sập trắng màn hình!

### Thứ 4 — Chức Năng Thống Kê Báo Cáo Doanh Thu (Backend: Java Stream API) (2h)
- [ ] **Backend (70%):**
  - Học lập trình hàm Java: Lambda expressions `() -> {}`, Functional Interfaces (`Predicate`, `Function`, `Consumer`), Method References (`Order::getId`).
  - Học Java Stream API: `filter()`, `map()`, `sorted()`, `distinct()`, `toList()`.
  - Thống kê doanh thu Runner bằng `Collectors`:
    - `groupingBy(Order::getCategory)`: Nhóm đơn hàng theo danh mục.
    - `summarizingDouble(Order::getOfferedPrice)`: Tính tổng doanh thu, cước phí trung bình, đơn giá cao nhất/thấp nhất.
  - Xây dựng API `GET /api/v1/reports/summary` trả về báo cáo tổng hợp.
  - Sử dụng `Optional<T>` xử lý dữ liệu tránh triệt để `NullPointerException`; commit.
- [ ] **Frontend (30%):**
  - Dựng khung trang Báo cáo thống kê (`app/reports/page.tsx`) trên Next.js với các thẻ KPI cards: Tổng đơn hàng, Tổng doanh thu, Giá cước trung bình; commit.

### Thứ 5 — Chức Năng Thống Kê Báo Cáo Doanh Thu (Frontend: Reporting UI & Charts) (2h)
- [ ] **Frontend (70%):**
  - Kết nối trang `/reports` gọi API `GET /api/v1/reports/summary` từ Spring Boot.
  - Hiển thị các số liệu thống kê lên các thẻ KPI cards.
  - Dùng Recharts (hoặc Chart.js) trực quan hóa biểu đồ doanh thu theo từng danh mục đơn hàng (`RIDE`, `FOOD`, `PARCEL`).
- [ ] **Backend (30%):**
  - Kiểm tra độ chính xác của các phép tính toán thống kê Stream API; commit.
- [ ] **Chạy thử trên trình duyệt:** Tạo thêm 2 đơn hàng mới $\rightarrow$ Mở trang `/reports`, thấy các số liệu tổng doanh thu và biểu đồ tự động cập nhật số liệu mới chính xác 100%!

### Thứ 6 — Chức Năng Xuất Báo Cáo CSV (CSV Export) (2h)
- [ ] **Backend (70%):**
  - Xây dựng endpoint `GET /api/v1/reports/export-csv` xuất danh sách đơn hàng ra định dạng CSV.
  - Sử dụng cú pháp `try-with-resources` để tự động đóng luồng `PrintWriter` / `BufferedWriter`, chống rò rỉ tài nguyên (resource leak).
  - Cấu hình header response `Content-Disposition: attachment; filename="orders-report.csv"`.
- [ ] **Frontend (30%):**
  - Thêm nút bấm "Tải báo cáo CSV" trên trang `/reports` của Next.js, kích hoạt tải file CSV trực tiếp về máy tính người dùng; commit.

### Thứ 7 — Fullstack Reporting Lab & Luyện Live Coding DSA (5h)
- [ ] 2h: Thử nghiệm gửi dữ liệu sai từ Form Next.js $\rightarrow$ Kiểm tra Backend trả mã lỗi RFC 7807 $\rightarrow$ Frontend hiển thị thông báo lỗi rõ ràng.
- [ ] 1h: Kiểm tra trang báo cáo `/reports`, bấm nút "Tải báo cáo CSV" $\rightarrow$ File CSV tải về máy $\rightarrow$ Kiểm tra khớp dữ liệu.
- [ ] 1h: Viết test cho Stream API report service ở Backend; commit.
- [ ] 1h: **Luyện Live Coding DSA (Strings & Greedy Two Pointers):**
  - Bài 7: **Longest Common Prefix** (LeetCode 14, Easy) — Duyệt chuỗi theo chiều dọc (Vertical Scanning) $O(N \cdot M)$ Time / $O(1)$ Space.
  - Bài 8: **Valid Palindrome II** (LeetCode 680, Easy) — Bỏ qua tối đa 1 ký tự bằng đệ quy con trỏ tham lam $O(N)$ Time / $O(1)$ Space.
  - Thực hành tự dry run test case trước mặt Interviewer; commit code vào `dsa/week-04/`.

---

## Tuần 5 — Chiến Lược Kiểm Thử Tự Động (TDD) Cả Hai Phía & Monorepo Quality

### Thứ 2 — Kiểm Thử Đơn Vị Backend (JUnit 5 & Mockito) (2h)
- [ ] **Backend (70%):**
  - Nguyên lý kiểm thử: Mô hình Arrange-Act-Assert (AAA), First-Class Tests, Red-Green-Refactor.
  - JUnit 5 Annotations: `@Test`, `@BeforeEach`, `@DisplayName`, `@ParameterizedTest`.
  - Mocking với Mockito: `@Mock`, `@InjectMocks`, `when().thenReturn()`, `verify()`.
  - Viết bộ unit test độc lập cho `OrderService`: Test logic tính cước, kiểm tra điều kiện tạo đơn, kiểm tra ném ngoại lệ khi dữ liệu sai.
- [ ] **Frontend (30%):**
  - Cài đặt Vitest và React Testing Library trong thư mục `frontend/`.
  - Cấu hình file `vitest.config.ts` và thiết lập môi trường test `jsdom`; commit.

### Thứ 3 — Kiểm Thử Đơn Vị Giao Diện (Frontend: Vitest & React Testing Library) (2h)
- [ ] **Frontend (70%):**
  - Viết unit test cho component `OrderCard`: Kiểm tra render đúng địa chỉ đón/trả, khoảng cách km, badge danh mục và định dạng tiền tệ VNĐ.
  - Viết unit test cho logic validation của Form Tạo Đơn: Kiểm tra form chặn submit và hiển thị thông báo lỗi màu đỏ khi để trống địa chỉ hoặc nhập giá tiền âm.
- [ ] **Backend (30%):**
  - Chạy `mvn test` hoặc `.\gradlew.bat test` đảm bảo toàn bộ unit test backend pass 100%.
- [ ] **Kết quả:** Chạy `npm test` ở frontend và `gradlew test` ở backend: Cả 2 phía đều pass xanh 100%!

### Thứ 4 — Kiểm Thử Tích Hợp API (Backend: MockMvc) (2h)
- [ ] **Backend (70%):**
  - Học kiểm thử tầng Web với `@WebMvcTest` và `MockMvc`.
  - Viết test mô phỏng gửi request HTTP tới `OrderController`:
    - Gửi payload hợp lệ $\rightarrow$ Kiểm tra mã trạng thái `200 OK` hoặc `201 Created` và cấu trúc JSON trả về.
    - Gửi thiếu trường bắt buộc $\rightarrow$ Kiểm tra mã trạng thái `400 Bad Request`.
    - Gọi đơn không tồn tại $\rightarrow$ Kiểm tra mã trạng thái `404 Not Found` khớp chuẩn RFC 7807 `ProblemDetail`.
- [ ] **Frontend (30%):**
  - Cài đặt Mock Service Worker (MSW) để giả lập API endpoints phía frontend; commit.

### Thứ 5 — Kiểm Thử Tích Hợp Giao Diện (Frontend: MSW & Form Submit Flow) (2h)
- [ ] **Frontend (70%):**
  - Dùng MSW giả lập phản hồi API `POST /api/v1/orders`.
  - Viết integration test cho toàn bộ luồng người dùng trên giao diện: Điền thông tin vào form $\rightarrow$ bấm nút Tạo đơn $\rightarrow$ kiểm tra nút chuyển sang trạng thái Loading $\rightarrow$ kiểm tra hiển thị thông báo Toast thành công.
- [ ] **Backend (30%):**
  - Rà soát coverage các bài test MockMvc; commit.

### Thứ 6 — JVM Memory Layout, Concurrency Cơ Bản & TypeScript Type Safety (2h)
- [ ] **Backend (70%):**
  - Học kiến trúc bộ nhớ JVM: Heap (Young, Old), Stack Frame, Metaspace, GC căn bản (Mark & Sweep).
  - Nền tảng Concurrency trên Java 17: JMM (Visibility, Reordering, Happens-Before), `volatile` vs `synchronized`, `AtomicInteger`, CAS.
  - Tạo bài lab đa luồng nhỏ: 10 threads cùng cộng dồn biến đếm đơn hàng để chứng minh Lost Update nếu không đồng bộ hóa; commit.
- [ ] **Frontend (30%):**
  - Kiểm tra type safety toàn diện: Chạy `npm run typecheck`, loại bỏ toàn bộ kiểu `any` trong code TypeScript frontend; commit.

### Thứ 7 — Fullstack Quality Gate & Luyện Live Coding DSA (5h)
- [ ] 2h: Thiết lập kịch bản chạy test tự động: `npm test` ở frontend pass 100% và `mvn test` / `.\gradlew.bat test` ở backend pass 100%.
- [ ] 1h: Tạo script 1 lệnh kiểm tra toàn diện chất lượng (format, typecheck, unit/integration test); Tag release Git: `fullstack-core-passed`.
- [ ] 1h: Mock interview tự vấn đáp 15 câu Java Core/Testing và 5 câu React/Next.js Testing.
- [ ] 1h: **Luyện Live Coding DSA (Stack & JVM Memory Internals):**
  - Bài 9: **Valid Parentheses** (LeetCode 20, Easy) — Ứng dụng Stack LIFO so khớp dấu ngoặc $O(N)$ Time / $O(N)$ Space (`ArrayDeque<Character>`).
  - Bài 10: **Min Stack** (LeetCode 155, Medium) — Thiết kế ngăn xếp có `getMin()` trong $O(1)$ Time dùng 2 Stack hoặc Linked Node bọc giá trị nhỏ nhất; commit vào `dsa/week-05/`.

---

## Tuần 6 — Tách Khớp Nối Kiến Trúc (Seam), Vòng Đời Đơn Hàng & Next.js Client

### Thứ 2 — Tách Khớp Nối Kiến Trúc Module Sâu (Backend Seam & IoC Internals) (2h)
- [ ] **Backend (70%):**
  - Học sâu cơ chế Spring IoC: `ApplicationContext` vs `BeanFactory`.
  - Bean Scopes: Singleton (mặc định), Prototype, Request, Session.
  - Chi tiết vòng đời của một Spring Bean (**Spring Bean Lifecycle**): `BeanDefinition` $\rightarrow$ Instantiation $\rightarrow$ Populate Properties $\rightarrow$ Aware Interfaces $\rightarrow$ `BeanPostProcessor` $\rightarrow$ `@PostConstruct` $\rightarrow$ In use $\rightarrow$ `@PreDestroy`.
  - Thiết kế Module Sâu (Deep Module): Tạo Seam rõ ràng giữa Controller và Service, ẩn hoàn toàn logic xử lý bên trong.
- [ ] **Frontend (30%):**
  - Tách bạch cấu trúc Component: Phân tách **Container Components** (chứa logic gọi API, quản lý state) vs **Presentational Components** (thuần hiển thị UI, nhận props); commit.

### Thứ 3 — Spring AOP, Proxy Internals & Self-Invocation Trap (2h)
- [ ] **Backend (70%):**
  - Học nguyên lý Aspect-Oriented Programming (AOP): Pointcut, Advice, JoinPoint, Aspect.
  - Cơ chế Spring Proxy: JDK Dynamic Proxy (dựa trên Interface) vs CGLIB Proxy (bytecode runtime).
  - Tái hiện và giải thích bẫy kinh điển: **`@Transactional` / `@Async` Self-Invocation Trap**:
    - Khi một method trong class tự gọi trực tiếp một method khác có `@Transactional` cùng class, proxy bị bypass hoàn toàn $\rightarrow$ Transaction không bao giờ được mở!
    - Thực hành 3 cách khắc phục chuẩn: (1) Tách sang Bean/Service khác, (2) Tự inject chính mình bằng `@Lazy`, (3) Dùng `TransactionTemplate`.
- [ ] **Frontend (30%):**
  - Áp dụng Custom Hook `useOrders()` để đóng gói logic gọi API, giúp các UI component không bị dính chặt vào thư viện fetch/axios; commit.

### Thứ 4 — Chức Năng Cập Nhật Tiến Độ Vòng Đời Đơn Hàng (Backend API) (2h)
- [ ] **Backend (70%):**
  - Xây dựng API `PATCH /api/v1/orders/{id}/status`: Cho phép cập nhật trạng thái đơn hàng (`OPEN` $\rightarrow$ `ACCEPTED` $\rightarrow$ `PICKED_UP` $\rightarrow$ `IN_TRANSIT` $\rightarrow$ `COMPLETED` / `CANCELLED`).
  - Kiểm tra tính hợp lệ của việc chuyển trạng thái qua máy trạng thái `canTransitionTo()`.
  - Ném `InvalidOrderStateException` (trả về 409 Conflict) nếu tài xế cố tình nhảy cóc trạng thái (ví dụ từ `OPEN` nhảy thẳng lên `COMPLETED`).
- [ ] **Frontend (30%):**
  - Thêm TypeScript function `updateOrderStatus(orderId, newStatus)` trong `lib/api.ts`; commit.

### Thứ 5 — Chức Năng Cập Nhật Tiến Độ Vòng Đời Đơn Hàng (Frontend Controls UI) (2h)
- [ ] **Frontend (70%):**
  - Thêm các nút bấm hành động cập nhật tiến độ trên từng thẻ đơn hàng của Runner:
    - Khi đơn đang `ACCEPTED`: Hiển thị nút "Đã lấy hàng" (chuyển sang `PICKED_UP`).
    - Khi đơn đang `PICKED_UP`: Hiển thị nút "Bắt đầu giao" (chuyển sang `IN_TRANSIT`).
    - Khi đơn đang `IN_TRANSIT`: Hiển thị nút "Hoàn thành" (chuyển sang `COMPLETED`).
  - Xử lý loading và cập nhật badge màu sắc ngay lập tức sau khi bấm.
- [ ] **Backend (30%):**
  - Test endpoint PATCH với các trạng thái hợp lệ và không hợp lệ.
- [ ] **Chạy thử trên trình duyệt:** Runner bấm nút "Đã lấy hàng" $\rightarrow$ Badge trên web lập tức chuyển sang màu cam `PICKED_UP`, nút bấm đổi thành "Bắt đầu giao" mượt mà!

### Thứ 6 — Request Tracing & Correlation Header (Fullstack Observability) (2h)
- [ ] **Backend (70%):**
  - Tạo `RequestLoggingFilter` kế thừa `OncePerRequestFilter`: Đọc header `X-Trace-Id` từ client (hoặc tự sinh UUID nếu chưa có), ghi nhận thời gian xử lý và in log ra console.
  - Sử dụng DTO Validation nâng cao Jakarta Bean Validation: `@NotNull`, `@NotBlank`, `@Positive`, `@Min`, `@Size`.
- [ ] **Frontend (30%):**
  - Cấu hình Axios / Fetch Request Interceptor: Tự động sinh mã UUID và đính kèm vào header `X-Trace-Id` trong mọi request gửi đi.
  - Cấu hình Response Interceptor log thời gian phản hồi của request lên console trình duyệt; commit.

### Thứ 7 — Fullstack Seam Hardening Lab & Luyện Live Coding DSA (5h)
- [ ] 2h: Cấu hình chuẩn `CorsConfigurationSource` trong Spring Boot cho phép `http://localhost:3000` kèm credentials.
- [ ] 1h: Kiểm tra luồng gọi API kèm mã `X-Trace-Id` xuyên suốt Frontend và Backend; viết test MockMvc.
- [ ] 1h: Commit mã nguồn và dọn dẹp các warnings.
- [ ] 1h: **Luyện Live Coding DSA (Linked List & Fast/Slow Pointers):**
  - Bài 11: **Linked List Cycle** (LeetCode 141, Easy) — Thuật toán rùa và thỏ (Floyd’s Tortoise and Hare) phát hiện chu trình $O(N)$ Time / $O(1)$ Space.
  - Bài 12: **Middle of the Linked List** (LeetCode 876, Easy) — Con trỏ nhanh gấp đôi con trỏ chậm tìm trung điểm trong 1 pass $O(N)$ Time / $O(1)$ Space; commit vào `dsa/week-06/`.

---

## Tuần 7 — Chuyển Đổi Sang Database Thật (PostgreSQL + Flyway + JPA) & Phân Trang

### Thứ 2 — Database Relational & Migration Flyway (Backend) (2h)
- [ ] **Backend (70%):**
  - Học thiết kế cơ sở dữ liệu quan hệ: Bảng, Primary Key (PK), Foreign Key (FK), Constraints.
  - Thiết kế schema cho Giao Vặt:
    - Bảng `users`: `id`, `email`, `password_hash`, `full_name`, `phone_number`, `role` (`ROLE_CREATOR`, `ROLE_RUNNER`).
    - Bảng `orders`: `id`, `creator_id`, `runner_id`, `pickup_address`, `dropoff_address`, `distance_km`, `min_price`, `offered_price`, `status`, `version`, `created_at`, `updated_at`.
  - Tạo file migration Flyway: `src/main/resources/db/migration/V1__init_schema.sql`.
  - Khởi chạy PostgreSQL qua Docker Compose local (`docker compose up -d postgres`).
  - Cấu hình Spring Data JPA, `application.yml` kết nối Postgres thật, HikariCP connection pool; commit.
- [ ] **Frontend (30%):**
  - Giữ nguyên giao diện Next.js, đảm bảo contract API không đổi (tính tương thích ngược).

### Thứ 3 — Chuyển Đổi Sang Database Thật: Kiểm Tra Tính Tương Thích Giao Diện (Frontend) (2h)
- [ ] **Frontend (70%):**
  - Mở form tạo đơn trên Next.js $\rightarrow$ Submit tạo 3 đơn hàng mới.
  - Tắt server Spring Boot và khởi động lại $\rightarrow$ Tải lại trang danh sách trên Next.js $\rightarrow$ Toàn bộ 3 đơn hàng vẫn còn nguyên vẹn 100% nhờ đã lưu bền vững xuống PostgreSQL thật (thay thế hoàn toàn bộ nhớ in-memory tạm thời)!
- [ ] **Backend (30%):**
  - Kiểm tra bảng `orders` trong PostgreSQL qua tool GUI (DBeaver / DataGrip) để xác nhận dữ liệu đã lưu đúng kiểu `BIGDECIMAL`, `VARCHAR`, `TIMESTAMP`.
- [ ] **Kết quả:** Hệ thống chính thức chạy trên Database quan hệ thật mà không làm gãy giao diện!

### Thứ 4 — Chức Năng Phân Trang Bảng Tin (Backend: Pageable & Index) (2h)
- [ ] **Backend (70%):**
  - Học cấu trúc **B-Tree Index**: Cấu trúc cây cân bằng $O(\log N)$, leaf nodes linked list cho range query; phân biệt Index Scan vs Full Table Scan.
  - Tạo composite index trên `(status, created_at)` để tối ưu câu truy vấn lấy danh sách đơn chờ nhận trên bảng tin.
  - Sử dụng Spring Data JPA `Pageable` và `PageRequest`:
    - Repository method: `findByStatusOrderByCreatedAtDesc(OrderStatus status, Pageable pageable)`.
    - API `GET /api/v1/orders/feed?page=0&size=10`.
  - Trả về DTO phân trang chứa: `content`, `pageNumber`, `pageSize`, `totalElements`, `totalPages`.
- [ ] **Frontend (30%):**
  - Khai báo TypeScript interface `PaginatedResponse<T>` khớp với cấu trúc `Page` của Spring Boot; commit.

### Thứ 5 — Chức Năng Phân Trang Bảng Tin (Frontend: Pagination Controls UI) (2h)
- [ ] **Frontend (70%):**
  - Xây dựng thanh điều khiển phân trang ở cuối trang Bảng Tin (`app/feed/page.tsx`):
    - Nút "Trang trước" (disabled khi ở trang đầu).
    - Danh sách số trang `[1] [2] [3] ...`.
    - Nút "Trang sau" (disabled khi ở trang cuối).
    - Hiển thị thông tin *"Hiển thị 10 trên tổng số 45 đơn hàng"*.
  - Bấm chuyển trang $\rightarrow$ Gọi API tải dữ liệu trang tương ứng mượt mà.
- [ ] **Backend (30%):**
  - Kiểm tra câu query `COUNT(*)` và query dữ liệu phân trang trong log SQL.
- [ ] **Chạy thử trên trình duyệt:** Tạo 15 đơn hàng $\rightarrow$ Bấm sang "Trang 2" trên web $\rightarrow$ Bảng tin hiển thị chính xác 5 đơn hàng của trang tiếp theo!

### Thứ 6 — Quan Hệ JPA, Xử Lý N+1 Query & Auditing (2h)
- [ ] **Backend (70%):**
  - Mapping quan hệ `@ManyToOne` giữa `Order` và `User` (Creator/Runner), luôn đặt `FetchType.LAZY`.
  - Tái hiện lỗi **N+1 Query Problem**: Khi load danh sách 10 đơn hàng kèm thông tin Creator $\rightarrow$ Hibernate bắn 1 câu query lấy đơn + 10 câu query lấy Creator!
  - Giải quyết triệt để N+1 bằng `JOIN FETCH` trong JPQL: `SELECT o FROM Order o JOIN FETCH o.creator WHERE o.status = :status`.
  - Cấu hình JPA Auditing: `@CreatedDate`, `@LastModifiedDate`, `AuditingEntityListener`.
- [ ] **Frontend (30%):**
  - Hiển thị thời gian tạo đơn định dạng thân thiện trên `OrderCard` (ví dụ: *"5 phút trước"*, *"14:30 09/10/2026"*); commit.

### Thứ 7 — Fullstack Database Integration Lab & Luyện Live Coding DSA (5h)
- [ ] 2h: Seed 25 đơn hàng mẫu trong PostgreSQL; kiểm tra thao tác chuyển trang và lọc dữ liệu trên web; kiểm tra log SQL sạch lỗi N+1 (`JOIN FETCH`).
- [ ] 1h: Viết integration test với `@DataJpaTest` hoặc Testcontainers PostgreSQL; commit.
- [ ] 1h: Tổng kết tuần và rà soát schema database.
- [ ] 1h: **Luyện Live Coding DSA (Binary Search & Database Indexing):**
  - Bài 13: **Binary Search** (LeetCode 704, Easy) — Chặt nhị phân kinh điển chống tràn số nguyên `mid = left + (right - left) / 2` trong $O(\log N)$ Time / $O(1)$ Space.
  - Bài 14: **Search a 2D Matrix** (LeetCode 74, Medium) — Ánh xạ ma trận $M \times N$ thành mảng 1D ảo và chặt nhị phân trong $O(\log(M \cdot N))$ Time; commit vào `dsa/week-07/`.

---

## Tuần 8 — Chức Năng Runner Nhận Đơn (Claim Order) & Khóa Concurrency (@Version)

### Thứ 2 — Chức Năng Runner Nhận Đơn (Backend: Claim Order API) (2h)
- [ ] **Backend (70%):**
  - Xây dựng API `POST /api/v1/orders/{id}/claim`: Cho phép Runner nhận một đơn hàng đang `OPEN`.
  - Logic nghiệp vụ:
    - Kiểm tra đơn hàng có tồn tại không (nếu không $\rightarrow$ ném `OrderNotFoundException` 404).
    - Kiểm tra trạng thái đơn hàng có phải `OPEN` không (nếu đã bị nhận rồi $\rightarrow$ ném `InvalidOrderStateException` 409).
    - Gán `runner_id` của tài xế và chuyển trạng thái đơn hàng sang `ACCEPTED`.
    - Lưu xuống Database.
- [ ] **Frontend (30%):**
  - Viết hàm API `claimOrder(orderId)` trong `lib/api.ts`; commit.

### Thứ 3 — Chức Năng Runner Nhận Đơn (Frontend: Claim Button & Interaction) (2h)
- [ ] **Frontend (70%):**
  - Thêm nút **"Nhận đơn" (Claim Order)** màu xanh lá nổi bật trên từng thẻ `OrderCard` của trang Bảng Tin.
  - Khi Runner bấm nút "Nhận đơn":
    - Nút hiển thị spinner loading và bị disabled để chống bấm đúp.
    - Gọi API `POST /api/v1/orders/{id}/claim`.
    - Khi thành công: Bắn Toast chúc mừng *"Bạn đã nhận đơn #... thành công!"*, thẻ đơn hàng tự động biến mất khỏi bảng tin `OPEN`.
  - Thêm tab "Đơn tôi đã nhận" trên menu: Hiển thị danh sách các đơn mà Runner hiện tại đã nhận.
- [ ] **Backend (30%):**
  - Test luồng nhận đơn thành công qua Postman/curl.
- [ ] **Chạy thử trên trình duyệt:** Runner lướt Bảng tin $\rightarrow$ Bấm "Nhận đơn" $\rightarrow$ Đơn biến mất khỏi bảng tin và xuất hiện trong mục "Đơn tôi đã nhận"!

### Thứ 4 — Chống Race Condition Concurrency (Backend: JPA Optimistic Locking) (2h)
- [ ] **Backend (70%):**
  - Phân tích bài toán thực tế: Hai tài xế A và B cùng nhìn thấy 1 đơn hàng giá cao và cùng bấm "Nhận đơn" trong cùng 1 tích tắc. Nếu không khóa $\rightarrow$ Cả 2 cùng nhận thành công $\rightarrow$ Thảm họa dữ liệu!
  - Triển khai **Optimistic Locking** trên Entity `Order`: Thêm trường `@Version private Long version;`.
  - Khi có tranh chấp ghi: Hibernate tự động kiểm tra version; transaction thứ hai sẽ bị từ chối và ném ra ngoại lệ `OptimisticLockingFailureException`.
  - Cấu hình Global Exception Handler bắt `OptimisticLockingFailureException` $\rightarrow$ Trả về mã lỗi HTTP `409 Conflict` kèm thông điệp: *"Rất tiếc! Đơn hàng này vừa được một tài xế khác nhận trước bạn vài phần nghìn giây."*.
- [ ] **Frontend (30%):**
  - Xử lý bắt mã lỗi 409 trong hàm gọi nhận đơn của Next.js; commit.

### Thứ 5 — Chống Race Condition Concurrency (Frontend: Optimistic UI & Rollback) (2h)
- [ ] **Frontend (70%):**
  - Áp dụng kỹ thuật **Optimistic UI (Cập nhật giao diện lạc quan)**:
    - Khi Runner bấm "Nhận đơn", giao diện lập tức đổi trạng thái sang "Đang xử lý" ($0$ms delay).
  - Xử lý **Rollback UI**:
    - Nếu Backend trả về HTTP `409 Conflict` (bị tranh chấp đơn) $\rightarrow$ Giao diện lập tức phục hồi lại trạng thái cũ, loại bỏ đơn khỏi danh sách và hiển thị Toast cảnh báo màu cam: *"Đơn hàng vừa được tài xế khác nhận! Vui lòng chọn đơn khác."*.
- [ ] **Backend (30%):**
  - Viết bài test đa luồng JUnit 5 kết hợp `CountDownLatch` và `ExecutorService`: 2 threads cùng gọi claim 1 đơn hàng $\rightarrow$ Chứng minh đúng 1 thread thành công và 1 thread nhận lỗi 409 Conflict.
- [ ] **Chạy thử trên trình duyệt:** Mở 2 tab trình duyệt cạnh nhau $\rightarrow$ Cùng bấm "Nhận đơn" trên 1 đơn hàng trong cùng 1 tích tắc $\rightarrow$ Tab 1 nhận thành công, Tab 2 nhận ngay cảnh báo 409 và UI rollback chuẩn xác 100%!

### Thứ 6 — Dọn Dẹp Mã Nguồn, Linter & Chuẩn Hóa Codebase (2h)
- [ ] Format code toàn bộ dự án: Backend theo chuẩn Google Java Style, Frontend theo ESLint & Prettier.
- [ ] Tối ưu hóa câu truy vấn bảng tin: Kiểm tra `EXPLAIN ANALYZE` trên PostgreSQL đảm bảo câu query tận dụng index `(status, created_at)`.
- [ ] Loại bỏ toàn bộ `console.log` thừa và code rác; commit.

### Thứ 7 — Demo Gate 1: Monolith v0 & Thử Thách Live Coding Milestone (5h)
- [ ] 2h: Chạy trọn vẹn kịch bản người dùng thực tế trên trình duyệt từ A-Z (Creator tạo đơn $\rightarrow$ Runner lướt feed nhận đơn $\rightarrow$ Optimistic Locking bảo vệ an toàn $\rightarrow$ Cập nhật tiến độ).
- [ ] 1h: Quay video demo 3 phút toàn bộ luồng chạy trên trình duyệt; Hoàn thiện README khởi chạy.
- [ ] 1h: Tag release Git chính thức: `fullstack-foundation-ready`.
- [ ] 1h: **Thử Thách Live Coding Milestone v0 (Bấm giờ 35 phút):**
  - Bài 15: **3Sum** (LeetCode 15, Medium) — Bài toán phỏng vấn kinh điển kết hợp Sorting + Two Pointers + Bỏ qua phần tử trùng lặp $O(N^2)$ Time / $O(1)$ extra Space.
  - Tự quay video hoặc nói to giải thích 4 bước Live Coding (Clarify $\rightarrow$ Big-O $\rightarrow$ Code $\rightarrow$ Dry Run); commit vào `dsa/week-08/`.

---

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

## Tuần 9 — Authentication, RBAC & Fullstack Security Architecture

### Thứ 2 — Chức Năng 1: Đăng Ký, Đăng Nhập & Password Hashing (Backend) (2h)
- [ ] **Backend (70%):**
  - Học lý thuyết kiến trúc xác thực: Stateful Session vs Stateless Token (JWT).
  - An toàn mật khẩu: Rainbow table attacks, cơ chế Salt, Key Stretching, BCrypt vs Argon2.
  - Cấu hình Spring Security 6 với `BCryptPasswordEncoder` (cost factor 10 hoặc 12).
  - Tạo schema bảng `users` và migration Flyway `V2__security_users.sql` (`id`, `email`, `phone`, `password_hash`, `role`, `created_at`).
  - Viết API đăng ký (`POST /api/v1/auth/register`) và đăng nhập (`POST /api/v1/auth/login`): Chặn duplicate email/phone, hash mật khẩu 100% trước khi lưu DB.
- [ ] **Frontend (30%):**
  - Định nghĩa Zod schema validation cho Form Đăng ký và Đăng nhập (`email`, `phone`, `password` tối thiểu 8 ký tự kèm chữ hoa/số); commit.

### Thứ 3 — Chức Năng 1: Đăng Ký, Đăng Nhập & Password Hashing (Frontend Form & Submit) (2h)
- [ ] **Frontend (70%):**
  - Xây dựng trang Đăng ký (`app/register/page.tsx`) và Đăng nhập (`app/login/page.tsx`) bằng React Hook Form + Zod.
  - Gọi API `POST /api/v1/auth/register` $\rightarrow$ Nhận phản hồi thành công $\rightarrow$ Chuyển hướng sang trang đăng nhập.
  - Gọi API `POST /api/v1/auth/login` $\rightarrow$ Nhận Access Token từ Spring Boot $\rightarrow$ Lưu token an toàn.
- [ ] **Backend (30%):**
  - Viết test đăng ký và đăng nhập với MockMvc.
- [ ] **Chạy thử trên trình duyệt:** Đăng ký tài khoản mới trên web $\rightarrow$ Kiểm tra PostgreSQL thấy mật khẩu đã mã hóa BCrypt $\rightarrow$ Đăng nhập thành công và nhận JWT!

### Thứ 4 — Chức Năng 2: JWT Stateless Token & Phân Quyền RBAC (Backend) (2h)
- [ ] **Backend (70%):**
  - Cấu trúc JWT: Header (HS256), Payload (`sub`, `roles`, `exp`), Signature.
  - Xây dựng `JwtTokenProvider`: Sinh Access Token (hạn 30 phút) chứa `userId` và `role`.
  - Xây dựng `JwtAuthenticationFilter` kế thừa `OncePerRequestFilter`: Đọc Bearer token từ header, xác thực chữ ký và nạp Principal vào `SecurityContextHolder`.
  - Phân quyền nghiêm ngặt bằng `@PreAuthorize("hasRole('...')")`:
    - `ROLE_CREATOR`: Chỉ tạo và hủy đơn của chính mình; không thể gọi API nhận đơn (`claimOrder`).
    - `ROLE_RUNNER`: Duyệt danh sách đơn `OPEN`; nhận đơn và cập nhật tiến độ đơn mình đã nhận.
  - Bảo mật dữ liệu nhạy cảm: Ẩn số điện thoại Creator trên public feed; chỉ Runner nhận đơn thành công mới xem được SĐT; commit.
- [ ] **Frontend (30%):**
  - Khai báo TypeScript interface cho User profile và token payload; commit.

### Thứ 5 — Chức Năng 2: JWT Stateless & Route Protection Theo Role (Frontend) (2h)
- [ ] **Frontend (70%):**
  - Xây dựng `AuthContext` và hook `useAuth()`: Quản lý trạng thái đăng nhập, hàm `login()`, `logout()`, giải mã role từ JWT.
  - Xây dựng Next.js `middleware.ts` bảo vệ Route:
    - Chưa đăng nhập $\rightarrow$ Chặn vào `/orders/new` hoặc `/my-orders` $\rightarrow$ Redirect về `/login`.
    - Kiểm tra Role: Tài khoản `ROLE_CREATOR` không thể vào trang `/runner/feed`; chỉ `ROLE_RUNNER` mới được vào.
  - Trên Bảng tin: Ẩn số điện thoại khách hàng (hiển thị `0987***`); chỉ sau khi Runner nhận đơn thành công mới hiển thị đầy đủ số điện thoại.
- [ ] **Backend (30%):**
  - Viết test kiểm tra các API trả về 403 Forbidden khi user không đúng Role.
- [ ] **Chạy thử trên trình duyệt:** Đăng nhập tài khoản Creator $\rightarrow$ Thử vào trang `/runner/feed` bị chặn redirect; Đăng nhập Runner $\rightarrow$ Thấy feed nhưng SĐT bị che dấu sao; Bấm nhận đơn thành công $\rightarrow$ SĐT hiện đầy đủ!

### Thứ 6 — Chức Năng 3: Refresh Token Rotation trong Redis (Fullstack) (2h)
- [ ] **Backend (70%):**
  - Cơ chế **Refresh Token Rotation**: Mỗi lần refresh, cấp Refresh Token mới và hủy token cũ.
  - Lưu Refresh Token trong Redis với TTL 7 ngày; phát hiện Replay Attack (nếu token cũ bị dùng lại $\rightarrow$ revoke toàn bộ phiên user).
  - API `POST /api/v1/auth/refresh` và `POST /api/v1/auth/logout`.
- [ ] **Frontend (30%):**
  - Cấu hình Axios / Fetch Response Interceptor: Tự động gọi API `/refresh` trong suốt (silent refresh) khi nhận mã lỗi 401 Unauthorized $\rightarrow$ Lưu token mới và tự động thử lại request ban đầu mà người dùng không bị văng đăng nhập; commit.

### Thứ 7 — Fullstack Auth Integration Lab & Luyện Live Coding DSA (5h)
- [ ] 2h: Ghép nối toàn bộ luồng Auth: Đăng ký $\rightarrow$ Đăng nhập $\rightarrow$ Điều hướng theo Role $\rightarrow$ Đăng xuất.
- [ ] 1h: Kiểm tra cơ chế Silent Refresh token ngầm trong suốt; cấu hình CORS chặt chẽ.
- [ ] 1h: Viết Integration Test cho các endpoint bảo mật; commit.
- [ ] 1h: **Luyện Live Coding DSA (Sliding Window — Cửa Sổ Trượt):**
  - Bài 17: **Best Time to Buy and Sell Stock** (LeetCode 121, Easy) — Cửa sổ trượt đơn giản duy trì giá đáy trong $O(N)$ Time / $O(1)$ Space.
  - Bài 18: **Longest Substring Without Repeating Characters** (LeetCode 3, Medium) — Cửa sổ trượt linh hoạt kết hợp `HashMap`/mảng vị trí $O(N)$ Time / $O(\min(N, M))$ Space; commit vào `dsa/week-09/`.

---

## Tuần 10 — Caching Architecture, Redis Feed & Anti-Spam Rate Limiting

### Thứ 2 — Chức Năng 1: Bảng Tin Đơn Mở Bằng Redis Sorted Set (Backend) (2h)
- [ ] **Backend (70%):**
  - Học lý thuyết Caching: Cache-Aside vs Write-Through; Ba thảm họa Caching (Cache Penetration, Cache Breakdown, Cache Avalanche) và giải pháp.
  - Học sâu các cấu trúc dữ liệu Redis: String, Hash, Sorted Set (ZSET).
  - Thiết kế Bảng Tin Đơn Hàng trên Redis:
    - **Sorted Set (ZSET)** key `orders:open`: Score là timestamp tạo đơn hoặc cước phí, Member là `orderId` $\rightarrow$ Hỗ trợ phân trang và sắp xếp siêu tốc $O(\log N + M)$.
    - **Hash** key `order:{id}`: Lưu snapshot chi tiết đơn hàng dạng JSON/Fields để đọc siêu tốc không cần chạm Database.
  - Xử lý đồng bộ hai chiều (Redis $\leftrightarrow$ Database): Tạo đơn đẩy Redis $\rightarrow$ Nhận đơn gỡ khỏi Redis; Cơ chế Fallback an toàn query DB nếu Redis tạm thời mất kết nối.
- [ ] **Frontend (30%):**
  - Giữ nguyên giao diện Next.js Bảng tin, chuẩn bị API client đón nhận tốc độ phản hồi cao từ Redis; commit.

### Thứ 3 — Chức Năng 1: Bảng Tin Đơn Mở Bằng Redis Sorted Set (Frontend Benchmark) (2h)
- [ ] **Frontend (70%):**
  - Kết nối trang `/feed` của Next.js gọi API Bảng tin đọc dữ liệu từ Redis.
  - Tích hợp TanStack Query (React Query) hoặc SWR: Quản lý cache client (`stale-while-revalidate`), tự động refetch khi window focus.
  - Đo thời gian phản hồi: Mở DevTools Network tab đo đạc tốc độ tải Bảng tin ($<15$ms khi trúng Redis cache so với $40-60$ms khi query DB trực tiếp).
- [ ] **Backend (30%):**
  - Thực hành bài test tắt container Redis: Kiểm tra Spring Boot tự động fallback query từ PostgreSQL mà không làm gián đoạn API.
- [ ] **Chạy thử trên trình duyệt:** Tải trang Bảng tin thấy danh sách đơn hiện lên tức thì; Tắt Redis $\rightarrow$ Tải lại trang web vẫn hiển thị dữ liệu từ DB fallback mà không bị lỗi giao diện!

### Thứ 4 — Chức Năng 2: Chống Spam Bằng Sliding Window Rate Limiting (Backend) (2h)
- [ ] **Backend (70%):**
  - Lý thuyết các thuật toán Rate Limiting: Fixed Window, Sliding Window Log, Token Bucket, Leaky Bucket.
  - Triển khai **Sliding Window Rate Limiter** bằng Redis ZSET:
    - Giới hạn Creator: Tối đa 5 request tạo đơn/phút (chống spam đơn ảo).
    - Giới hạn Runner: Tối đa 30 request refresh bảng tin/phút và tối đa 10 request claim đơn/phút (chống auto-clicker bot).
  - Khi vượt ngưỡng: Trả về mã lỗi HTTP `429 Too Many Requests` kèm header `Retry-After: <seconds>`; commit.
- [ ] **Frontend (30%):**
  - Khai báo logic bắt mã lỗi 429 và đọc header `Retry-After` trong API client; commit.

### Thứ 5 — Chức Năng 2: Chống Spam Bằng Sliding Window Rate Limiting (Frontend Toast) (2h)
- [ ] **Frontend (70%):**
  - Xử lý trải nghiệm người dùng khi bị Rate Limiting:
    - Bắt lỗi HTTP `429 Too Many Requests` từ Backend.
    - Đọc header `Retry-After` và hiển thị Toast đếm ngược thời gian: *"Bạn thao tác quá nhanh, vui lòng chờ {seconds}s trước khi tải lại!"*.
    - Tự động disable nút "Làm mới bảng tin" và hiển thị đồng hồ đếm ngược trên nút (ví dụ: *"Chờ 8s..."*) để ngăn người dùng tiếp tục spam click.
- [ ] **Backend (30%):**
  - Viết test mô phỏng gửi 6 request liên tiếp trong 10 giây để kiểm tra kích hoạt 429.
- [ ] **Chạy thử trên trình duyệt:** Bấm spam nút làm mới bảng tin 35 lần liên tục $\rightarrow$ Giao diện lập tức hiện Toast cảnh báo 429, nút bấm bị khóa và đếm ngược từng giây chính xác!

### Thứ 6 — Reliability, Latency Measurement & Cache Consistency (2h)
- [ ] Kiểm tra tính nhất quán (Cache Consistency): Creator hủy đơn $\rightarrow$ Đảm bảo key trong Redis ZSET và Hash `order:{id}` bị xóa sạch ngay lập tức.
- [ ] Cấu hình Lettuce Connection Pool tối ưu: `max-active`, `max-idle`, `min-idle`.
- [ ] Ghi lại tài liệu ADR lựa chọn Redis Sorted Set cho Bảng Tin; commit.

### Thứ 7 — Fullstack Feed Performance Lab & Luyện Live Coding DSA (5h)
- [ ] 2h: Viết test đa luồng mô phỏng đồng thời 50 request vừa tạo đơn vừa nhận đơn, kiểm tra tính toàn vẹn dữ liệu giữa Redis và PostgreSQL.
- [ ] 1h: Đo đạc và lập biểu đồ latency so sánh giữa Redis Feed và Database Query.
- [ ] 1h: Tự review code theo checklist Caching & Rate Limiting; commit.
- [ ] 1h: **Luyện Live Coding DSA (Heap / Priority Queue & Top-K):**
  - Bài 19: **Kth Largest Element in an Array** (LeetCode 215, Medium) — Min-Heap kích thước $K$ trong $O(N \log K)$ Time hoặc Quickselect $O(N)$ trung bình.
  - Bài 20: **Top K Frequent Elements** (LeetCode 347, Medium) — `HashMap` đếm tần suất + Min-Heap hoặc Bucket Sort trong $O(N)$ Time; commit vào `dsa/week-10/`.

---

## Tuần 11 — Containerization, CI/CD Pipeline & Fullstack Deployment

### Thứ 2 — Đóng Gói Container Spring Boot (Backend Multi-stage Dockerfile) (2h)
- [ ] **Backend (70%):**
  - Học lý thuyết Virtualization vs Containerization, 12-Factor App cho Cloud-Native.
  - Viết Dockerfile Multi-stage tối ưu cho Spring Boot (Java 17 LTS):
    - Stage 1: Build source bằng Maven wrapper (`eclipse-temurin:17-jdk-alpine`).
    - Stage 2: Runtime với JRE siêu nhẹ (`eclipse-temurin:17-jre-alpine`, $<200$MB), tạo user non-root để đảm bảo an ninh.
  - Build image và chạy container backend local; commit.
- [ ] **Frontend (30%):**
  - Tìm hiểu cơ chế build production của Next.js: `next build` và cấu hình `output: 'standalone'`; commit.

### Thứ 3 — Đóng Gói Container Next.js (Frontend Standalone Dockerfile) (2h)
- [ ] **Frontend (70%):**
  - Bật cấu hình `output: 'standalone'` trong `next.config.js` để Next.js chỉ copy các file `node_modules` thực sự cần thiết.
  - Viết Dockerfile Multi-stage cho Next.js:
    - Stage 1 (`deps`): Cài đặt dependencies với cache npm/pnpm.
    - Stage 2 (`builder`): Build mã nguồn (`next build`).
    - Stage 3 (`runner`): Chạy server Node.js với image Alpine tối giản, giảm dung lượng image từ ~1GB xuống dưới 150MB.
  - Quản lý biến môi trường: `NEXT_PUBLIC_API_URL` (build-time) vs Biến môi trường Server (runtime).
- [ ] **Backend (30%):**
  - Kiểm tra healthcheck Actuator `/actuator/health` trong container backend.
- [ ] **Chạy thử:** Build cả 2 Docker image độc lập và kiểm tra kích thước tối ưu (cả 2 đều $<200$MB)!

### Thứ 4 — Docker Compose Fullstack Chạy 1 Lệnh Duy Nhất (2h)
- [ ] Viết file `docker-compose.yml` Fullstack duy nhất định nghĩa toàn bộ stack:
  - Dịch vụ `frontend` (Next.js port 3000).
  - Dịch vụ `backend` (Spring Boot port 8080, `depends_on` postgres & redis có `condition: service_healthy`).
  - Dịch vụ `postgres` (port 5432, persistent volume).
  - Dịch vụ `redis` (port 6379).
- [ ] Cấu hình network bridge và biến môi trường nội bộ giữa các container.
- [ ] Chạy lệnh duy nhất: `docker compose up -d` $\rightarrow$ Mở trình duyệt xem ứng dụng Fullstack chạy trơn tru từ A-Z; commit.

### Thứ 5 — Reverse Proxy & Dập Tắt Hoàn Toàn Vấn Đề CORS (2h)
- [ ] Cấu hình Reverse Proxy Nginx (hoặc Next.js Rewrites trong `next.config.js`):
  - Ánh xạ đường dẫn `/api/*` từ trình duyệt thẳng tới container backend `http://backend:8080`.
  - Gom toàn bộ hệ thống dưới 1 origin duy nhất $\rightarrow$ Loại bỏ hoàn toàn các rắc rối về CORS trên môi trường production.
- [ ] Kiểm tra gọi API qua reverse proxy thành công 100%; commit.

### Thứ 6 — CI/CD Pipeline với GitHub Actions Cho Cả Hai Phía (2h)
- [ ] Cấu hình workflow GitHub Actions (`.github/workflows/ci.yml`):
  - Trigger: Mọi PR và Push vào nhánh `main`.
  - Job 1 — Backend: Setup JDK 17 $\rightarrow$ Cache Maven $\rightarrow$ Run Tests (`mvn test`).
  - Job 2 — Frontend: Setup Node.js $\rightarrow$ Cache npm $\rightarrow$ Run Typecheck & Tests (`npm run typecheck && npm test`).
  - Job 3 — Build Docker Images khi 2 job trên pass xanh 100%.
- [ ] Đẩy code lên GitHub và kiểm tra pipeline CI chạy thành công; commit.

### Thứ 7 — Fullstack Docker Compose & Luyện Live Coding DSA (5h)
- [ ] 2h: Tự động hóa build và push Docker images lên GHCR/Docker Hub; deploy thử nghiệm lên Cloud (Render/Railway).
- [ ] 1h: Viết Runbook hướng dẫn chi tiết cách khởi động, kiểm tra log, backup và rollback hệ thống.
- [ ] 1h: Tag release Git: `giaovat-fullstack-docker-ready`; commit.
- [ ] 1h: **Luyện Live Coding DSA (Intervals — Xử Lý Khoảng Thời Gian/Lộ Trình):**
  - Bài 21: **Merge Intervals** (LeetCode 56, Medium) — Sắp xếp theo điểm bắt đầu và gộp các khoảng giao nhau trong $O(N \log N)$ Time / $O(N)$ Space.
  - Bài 22: **Insert Interval** (LeetCode 57, Medium) — Chèn khoảng mới và xử lý overlap trong 1 lần duyệt $O(N)$ Time / $O(N)$ Space; commit vào `dsa/week-11/`.

---

## Tuần 12 — Testing Strategy, Observability & Fullstack E2E Quality

### Thứ 2 — E2E Testing với Playwright (Frontend Kịch Bản Người Dùng Thật) (2h)
- [ ] **Frontend (70%):**
  - Học lý thuyết Testing Pyramid: Unit Test vs Integration Test vs End-to-End (E2E) Test.
  - Cài đặt và cấu hình **Playwright** trong thư mục `frontend/`.
  - Viết kịch bản kiểm thử E2E người dùng thực tế:
    - Kịch bản 1: Creator đăng nhập $\rightarrow$ điền form tạo đơn hàng $\rightarrow$ thấy thông báo Toast thành công $\rightarrow$ chuyển hướng về danh sách đơn.
    - Kịch bản 2: Runner truy cập `/feed` $\rightarrow$ thấy đơn hàng vừa tạo xuất hiện trên bảng tin.
- [ ] **Backend (30%):**
  - Chạy backend local sẵn sàng đón nhận request từ Playwright test; commit.

### Thứ 3 — Testcontainers Thực Chiến với PostgreSQL & Redis Thật (Backend) (2h)
- [ ] **Backend (70%):**
  - Tại sao H2 Database là "bẫy giả lập" nguy hiểm (khác biệt về SQL dialect, locking behavior, JSON support so với PostgreSQL thật)?
  - Cấu hình Testcontainers trong Spring Boot 3 (`@Testcontainers`, `@Container` PostgreSQL + Redis).
  - Viết bộ integration test kiểm tra trọn vẹn luồng tạo đơn $\rightarrow$ lưu DB $\rightarrow$ đẩy Redis feed $\rightarrow$ claim đơn.
  - Đảm bảo tính độc lập tuyệt đối giữa các bài test (Test Isolation & Clean Database); commit.
- [ ] **Frontend (30%):**
  - Chạy Playwright test headless: Kiểm tra toàn bộ bài test E2E pass xanh 100%.

### Thứ 4 — Ba Trụ Cột Observability & MDC Tracing (Backend) (2h)
- [ ] **Backend (70%):**
  - Học lý thuyết Observability: Metrics (Prometheus/Actuator), Logs (JSON structured format), Traces (đường đi request).
  - Cấu hình MDC (Mapped Diagnostic Context) Filter: Đọc header `X-Trace-Id` từ client (hoặc tự sinh UUID nếu client chưa có), đính kèm `traceId` và `userId` vào mọi log entry của request.
  - Expose các endpoint giám sát Actuator an toàn: `/actuator/health`, `/actuator/metrics`.
- [ ] **Frontend (30%):**
  - Khai báo logic gắn `X-Trace-Id` tự động vào request interceptor; commit.

### Thứ 5 — Tracing Request Xuyên Suốt Từ Trình Duyệt Vào Log Server (Frontend) (2h)
- [ ] **Frontend (70%):**
  - Cấu hình client Next.js tự động gửi header `X-Trace-Id: <uuid>` trong mọi request API.
  - Khi có lỗi phát sinh: Hiển thị mã `Trace ID: {uuid}` ngay trên màn hình lỗi của trình duyệt để người dùng có thể chụp ảnh báo cáo hỗ trợ.
- [ ] **Backend (30%):**
  - Tối ưu hóa câu truy vấn: Đánh Composite Index `(status, created_at)` hoặc Partial Index `WHERE status = 'OPEN'`.
- [ ] **Chạy thử:** Gửi 1 request từ giao diện Next.js $\rightarrow$ Mở terminal Spring Boot thấy đúng mã `X-Trace-Id` xuất hiện trong log!

### Thứ 6 — End-to-End Traceability Drill & Săn Lỗi Thực Tế (2h)
- [ ] Thực hành bài tập "Săn lỗi xuyên suốt (End-to-End Traceability Drill)":
  - Cố ý tạo một request lỗi từ form Next.js $\rightarrow$ Lấy mã `traceId` hiển thị trên màn hình lỗi trình duyệt.
  - Dùng lệnh Linux grep đúng mã `traceId` đó trong log Spring Boot: `grep "traceId=..." app.log` $\rightarrow$ Xác định chính xác exception stack trace và root cause trong dưới 30 giây!
- [ ] Tối ưu hóa hiệu năng giao diện với Google Lighthouse: Đảm bảo điểm số Performance $\ge 90$; commit.

### Thứ 7 — Fullstack Quality Gate & Luyện Live Coding DSA (5h)
- [ ] 2h: Chạy toàn bộ test suite: Backend Testcontainers (pass 100%) + Frontend Playwright E2E & Vitest (pass 100%).
- [ ] 1h: Sửa 4 bẫy lỗi kinh điển: N+1 Query Hibernate, lộ SĐT trên feed, race condition claim đơn, stale cache Redis.
- [ ] 1h: Chạy stress test 100 concurrent requests tới endpoint bảng tin; commit code.
- [ ] 1h: **Luyện Live Coding DSA (Binary Tree Traversal — Duyệt Cây Nhị Phân):**
  - Bài 23: **Maximum Depth of Binary Tree** (LeetCode 104, Easy) — Duyệt DFS đệ quy và BFS hàng đợi $O(N)$ Time / $O(H)$ Space.
  - Bài 24: **Same Tree** (LeetCode 100, Easy) — So sánh cấu trúc và giá trị 2 cây đồng thời $O(N)$ Time / $O(H)$ Space; commit vào `dsa/week-12/`.

---

## Tuần 13 — Agile, Engineering Processes, Vertical Slices & AI Workflows

### Thứ 2 — Agile / Scrum & Thiết Kế Vertical Slice Story (2h)
- [ ] Học quy trình Agile/Scrum: Product Backlog, Sprint Planning, Daily Standup, Sprint Review, Retrospective.
- [ ] Khái niệm **Vertical Slice Architecture (Lát cắt dọc)**: Mỗi story phải đi xuyên suốt toàn bộ các tầng (UI Next.js $\rightarrow$ API Controller $\rightarrow$ Service Domain $\rightarrow$ Database/Cache) để mang lại giá trị kiểm thử được cho người dùng, thay vì chia task nằm ngang (chỉ làm UI hoặc chỉ làm DB).
- [ ] Thiết kế 1 User Story hoàn chỉnh chuẩn Vertical Slice: **Tính năng "Hủy đơn hàng của Creator"** (khách chỉ được hủy khi đơn đang `OPEN`); commit.

### Thứ 3 — Triển Khai Vertical Slice Feature: Hủy Đơn Hàng Cả Hai Phía (2h)
- [ ] **Backend (70%):**
  - Xây dựng API `PATCH /api/v1/orders/{id}/cancel`: Kiểm tra quyền sở hữu (`ROLE_CREATOR`), kiểm tra trạng thái phải là `OPEN`, chuyển trạng thái `CANCELLED` trong Database và gỡ đơn khỏi Redis feed.
- [ ] **Frontend (30%):**
  - Thêm nút "Hủy đơn" trên danh sách đơn của Creator $\rightarrow$ Bấm nút mở Modal xác nhận lý do hủy $\rightarrow$ Bấm xác nhận gọi API `PATCH /cancel` $\rightarrow$ Thẻ đơn hàng đổi trạng thái và ẩn khỏi bảng tin công khai.
- [ ] **Chạy thử trên trình duyệt:** Creator tạo đơn $\rightarrow$ Runner thấy đơn trên feed $\rightarrow$ Creator bấm "Hủy đơn" trên web $\rightarrow$ Đơn lập tức biến mất khỏi feed của Runner!

### Thứ 4 — Mô Phỏng Jira Board, Estimation & Sprint Retrospective (2h)
- [ ] Tạo board Kanban/Scrum cá nhân (GitHub Projects hoặc Jira Free).
- [ ] Học kỹ thuật ước lượng công việc: Planning Poker, Story Points, 3-Point Estimation (Optimistic, Most Likely, Pessimistic).
- [ ] Thực hành quy trình làm việc theo task: Kéo card `In Progress` $\rightarrow$ tạo branch `feature/ticket-id` $\rightarrow$ code & test $\rightarrow$ mở Pull Request $\rightarrow$ review $\rightarrow$ merge vào `main`.
- [ ] Viết tài liệu Sprint Retrospective: Keep, Stop, Start; commit.

### Thứ 5 — Kỹ Thuật Viết Design Doc & Architectural Decision Records (ADR) (2h)
- [ ] Học tầm quan trọng của việc viết tài liệu kỹ thuật trong doanh nghiệp: *"Code là cái hệ thống làm, Design Doc là vì sao hệ thống làm như vậy"*.
- [ ] Cấu trúc chuẩn của một bản **ADR (Architectural Decision Record)**: Title, Status, Context, Decision, Consequences (Pros & Cons).
- [ ] Viết 2 bản ADR chính thức cho Giao Vặt lưu tại thư mục `docs/adr/`:
  - `ADR-001`: Lựa chọn cơ chế Concurrency Locking cho luồng Runner Claim Order (Optimistic Locking `@Version` vs Pessimistic Lock).
  - `ADR-002`: Lựa chọn Redis Sorted Set cho Bảng Tin Đơn Hàng thời gian thực.
- [ ] Commit tài liệu.

### Thứ 6 — AI-Assisted Workflows Khớp Kiểu TypeScript và Java DTO (2h)
- [ ] Thiết kế kiến trúc component Next.js theo nguyên tắc Single Responsibility: Tách biệt Container Component vs Presentational Component.
- [ ] Thực hành tích hợp AI coding assistants (GitHub Copilot, Cursor, Antigravity) vào quy trình Fullstack:
  - Prompt tạo component giao diện kèm Zod schema khớp với DTO Java Backend.
  - Soát lỗi hallucination: Đảm bảo AI không sinh ra các trường dữ liệu lệch pha giữa TypeScript Interface và Java Record DTO; commit.

### Thứ 7 — Fullstack Vertical Slice PR & Luyện Live Coding DSA (5h)
- [ ] 2h: Mở Pull Request hoàn chỉnh trên GitHub cho tính năng "Hủy đơn hàng" bao gồm cả mã nguồn Frontend và Backend kèm ảnh chụp minh họa.
- [ ] 1h: Tự review Pull Request dựa trên checklist nghiêm ngặt 2 trục: Standards và Spec; tinh chỉnh code và merge PR.
- [ ] 1h: Cập nhật changelog dự án và chuẩn bị kế hoạch sprint tiếp theo.
- [ ] 1h: **Luyện Live Coding DSA (Binary Search Tree — Cây Tìm Kiếm Nhị Phân):**
  - Bài 25: **Invert Binary Tree** (LeetCode 226, Easy) — Đảo ngược cây nhị phân kinh điển $O(N)$ Time / $O(H)$ Space.
  - Bài 26: **Validate Binary Search Tree** (LeetCode 98, Medium) — Kiểm tra tính hợp lệ BST bằng range bounds `[min, max]` $O(N)$ Time / $O(H)$ Space; commit vào `dsa/week-13/`.

---

## Tuần 14 — Cấu Trúc Dữ Liệu, Giải Thuật & Bản Đồ Không Gian Tiện Tuyến (Geospatial)

### Thứ 2 — Thuật Toán Tìm Kiếm & Binary Search Biến Thể Trong Định Vị Partition/Log (2h)
- [ ] **Backend (70%):**
  - Học bản chất đệ quy (Call Stack, Base Case, Stack Overflow) vs Vòng lặp khử đệ quy.
  - Binary Search ($O(\log N)$) và các biến thể tìm biên (Find First/Last Occurrence).
  - Ứng dụng trong System Design: Tìm kiếm log timestamp, định vị partition key trong hệ thống phân tán.
  - Luyện 3 bài LeetCode: Binary Search, Search in Rotated Sorted Array, Koko Eating Bananas.
- [ ] **Frontend (30%):**
  - Xây dựng thanh tìm kiếm đơn hàng trên Next.js tích hợp Debounce input (tránh gửi request dồn dập sau mỗi phím gõ).
  - Highlight từ khóa tìm kiếm trực tiếp trên danh sách thẻ đơn hàng (`OrderCard`).
- [ ] **Chạy thử trên trình duyệt:** Gõ từ khóa tìm đơn trên web $\rightarrow$ request gửi mượt mà với debounce 300ms và bôi vàng từ khóa tìm thấy.

### Thứ 3 — Cấu Trúc Cây (Tree/BST) & Tối Ưu Hóa B-Tree Index (2h)
- [ ] **Backend (70%):**
  - Tree fundamentals: Depth, Height, DFS (Pre/In/Postorder), BFS (Level-order).
  - Binary Search Tree (BST) và cân bằng cây (AVL, Red-Black Tree).
  - Ứng dụng trong System Design: Vì sao Database dùng B-Tree / B+Tree cho index trên đĩa thay vì BST (tối ưu hóa I/O Block đĩa).
  - Luyện 3 bài: Invert Binary Tree, Validate BST, Binary Tree Level Order Traversal.
- [ ] **Frontend (30%):**
  - Xây dựng component hiển thị cây phân cấp danh mục đơn hàng (`OrderCategory`: Hàng tiêu dùng $\rightarrow$ Thực phẩm / Đồ gia dụng; Tài liệu $\rightarrow$ Hỏa tốc / Tiết kiệm) dạng Accordion/Tree-select.
- [ ] **Chạy thử trên trình duyệt:** Click mở/đóng các nhánh danh mục trên giao diện để lọc đơn hàng theo cây phân cấp.

### Thứ 4 — Heap, Priority Queue & Top-K Đơn Hàng Cần Giao Gấp (2h)
- [ ] **Backend (70%):**
  - Cấu trúc Binary Heap: Min-Heap, Max-Heap ($O(1)$ peek, $O(\log N)$ push/pop).
  - Xây dựng thuật toán lọc Top-K đơn hàng gấp nhất (hạn chót gần nhất hoặc tiền công cao nhất) trong bộ nhớ.
  - Luyện 2 bài: K Closest Points to Origin, Top K Frequent Elements.
- [ ] **Frontend (30%):**
  - Thiết kế Widget "Top Đơn Hàng Gấp Cần Giao" ghim nổi bật ở đầu bảng tin Next.js.
  - Tích hợp Badge đồng hồ đếm ngược thời gian giao hàng (Urgency Countdown) chuyển màu từ xanh $\rightarrow$ vàng $\rightarrow$ đỏ.
- [ ] **Chạy thử trên trình duyệt:** Bảng tin hiển thị widget Top đơn gấp với đồng hồ đếm ngược nhảy từng giây sống động.

### Thứ 5 — Định Vị Không Gian (Geospatial) & Quét Đơn Gần Nhất (Nearest Driver) (2h)
- [ ] **Backend (70%):**
  - Biểu diễn đồ thị & thuật toán Dijkstra tìm đường ngắn nhất; Luyện bài: Number of Islands.
  - Xây dựng API `GET /api/v1/orders/nearby?lat=...&lng=...&radius=5` áp dụng công thức khoảng cách **Haversine** (hoặc PostGIS) lọc các đơn hàng trong bán kính 5km quanh tọa độ Runner.
- [ ] **Frontend (30%):**
  - Tích hợp bản đồ tương tác (Leaflet / OpenStreetMap) vào Next.js.
  - Lấy tọa độ GPS trình duyệt (`navigator.geolocation`) $\rightarrow$ Vẽ Marker vị trí của Runner kèm vòng tròn bán kính quét 5km $\rightarrow$ Vẽ các Marker đơn hàng xung quanh.
- [ ] **Chạy thử trên trình duyệt:** Bật định vị trên trình duyệt $\rightarrow$ Bản đồ hiển thị vị trí hiện tại và các điểm lấy hàng xung quanh Runner kèm khoảng cách ước tính (vd: 1.2 km).

### Thứ 6 — Ghép Lộ Trình Tiện Tuyến (Route Matching & Polyline Visualization) (2h)
- [ ] **Backend (70%):**
  - Thuật toán ghép lộ trình tiện đường (Multi-order Batching / Topological Sort): Runner lấy đơn 1 $\rightarrow$ lấy đơn 2 $\rightarrow$ trả đơn 1 $\rightarrow$ trả đơn 2 nếu đường đi trùng tuyến $\ge 70\%$. Luyện bài: Course Schedule.
  - API `POST /api/v1/orders/batch-route`: Tính toán thứ tự giao hàng tối ưu giảm thiểu tổng quãng đường di chuyển.
- [ ] **Frontend (30%):**
  - Vẽ đường dẫn lộ trình (Polyline) nối liền các điểm giao/nhận trên bản đồ Next.js.
  - Thẻ tóm tắt lộ trình tiện chuyến: Tổng quãng đường (km), Thời gian ước tính (phút), Tiền công kép nhận được (VNĐ).
- [ ] **Chạy thử trên trình duyệt:** Runner chọn ghép 2 đơn tiện chuyến $\rightarrow$ Bản đồ tự động vẽ tuyến đường tối ưu nhiều điểm dừng trực quan!

### Thứ 7 — Timed Algorithm Assessment & Geospatial Integration Lab (5h) [Fullstack Integration]
- [ ] 2h: Giải 3 bài LeetCode Easy/Medium có bấm giờ (mỗi bài tối đa 35 phút).
- [ ] 1h: Tự giải thích thuật toán bằng tiếng Anh theo cấu trúc: Idea $\rightarrow$ Complexity $\rightarrow$ Edge Cases $\rightarrow$ Code.
- [ ] 1h: Kiểm thử tích hợp toàn diện luồng bản đồ: Giả lập di chuyển vị trí Runner trên Chrome DevTools Sensors $\rightarrow$ Bản đồ tự động gọi API cập nhật danh sách đơn hàng gần nhất theo thời gian thực.
- [ ] 1h: Commit bài giải thuật toán và mã nguồn bản đồ tiện chuyến.

---

## Tuần 15 — Software Design Patterns, Network Protocols & Fullstack Security Audit

### Thứ 2 — GoF Design Patterns & Giao Diện Chọn Chính Sách Vận Chuyển (2h)
- [ ] **Backend (70%):**
  - GoF Patterns: Strategy, Factory Method, Builder, Adapter/Decorator. Tránh Over-engineering.
  - Mở rộng Strategy Pattern cho các gói dịch vụ vận chuyển: Giao Hỏa Tốc (`ExpressPricingStrategy`), Giao Tiết Kiệm (`SaverPricingStrategy`), Giao Tiện Chuyến (`CarpoolPricingStrategy`).
- [ ] **Frontend (30%):**
  - Component chọn gói dịch vụ vận chuyển dạng Radio Card có icon minh họa trên form tạo đơn.
  - Khi người dùng click chuyển gói $\rightarrow$ Tính toán lại cước ước tính tức thì hiển thị trên giao diện.
- [ ] **Chạy thử trên trình duyệt:** Chọn đổi giữa Giao Hỏa Tốc và Tiện Chuyến $\rightarrow$ Cước phí trên giao diện thay đổi tức thì đúng theo Strategy backend.

### Thứ 3 — Event-Driven Architecture & Hệ Thống Chuông Thông Báo Trực Quan (2h)
- [ ] **Backend (70%):**
  - Mô hình Event-Driven trong Spring Boot: `ApplicationEventPublisher`, `@EventListener` và `@TransactionalEventListener(phase = AFTER_COMMIT)`.
  - Phát sinh sự kiện: `OrderCreatedEvent`, `OrderClaimedEvent`, `OrderCompletedEvent`.
  - Phân biệt xử lý sự kiện đồng bộ (Synchronous) vs bất đồng bộ (`@Async`). Viết test đảm bảo transaction DB commit thành công mới bắn event.
- [ ] **Frontend (30%):**
  - Component Chuông thông báo (Notification Bell) trên thanh Navbar của Next.js.
  - Hiển thị badge số lượng thông báo chưa đọc; click mở danh sách thông báo sự kiện đơn hàng vừa diễn ra.
- [ ] **Chạy thử trên trình duyệt:** Tạo đơn hoặc nhận đơn $\rightarrow$ Chuông thông báo trên web nhảy số và hiển thị bản tin sự kiện mới.

### Thứ 4 — Networking Protocols (HTTP/1.1, HTTP/2, HTTP/3) & Web Inspector DevTools (2h)
- [ ] **Backend (70%):**
  - TCP/IP stack 4 tầng, TLS handshake, so sánh HTTP/1.1 (Keep-Alive, HoL Blocking) vs HTTP/2 (Binary Framing, Multiplexing qua 1 connection, HPACK) vs HTTP/3 (QUIC trên nền UDP).
  - Lệnh Linux điều tra server: `grep`, `awk`, `tail -f`, `netstat`, `curl -v` trace chi tiết một request tới Giao Vặt API.
- [ ] **Frontend (30%):**
  - Dùng Chrome DevTools Network Tab: So sánh Waterfall, kiểm tra HTTP/2 Multiplexing (nhiều request đi qua 1 connection ID duy nhất), phân tích TTFB (Time to First Byte), kích thước payload nén Gzip/Brotli.
- [ ] **Chạy thử trên trình duyệt:** Inspect tab Network trên trình duyệt khi tải trang bảng tin $\rightarrow$ Kiểm tra giao thức `h2`, headers và thời gian phản hồi.

### Thứ 5 — Kiểm Toán An Toàn Backend & Chống Lỗ Hổng BOLA/IDOR (2h)
- [ ] **Backend (70%):**
  - OWASP Top 10 API Security: BOLA / IDOR (Broken Object Level Authorization), Broken Authentication, SQL Injection.
  - Xây dựng cơ chế kiểm tra quyền sở hữu chặt chẽ: Creator A tuyệt đối không được xem/sửa đơn của Creator B; Runner chỉ được cập nhật đơn mà chính mình đã nhận.
  - Viết bài test JUnit chứng minh hệ thống chặn đứng tấn công IDOR với HTTP `403 Forbidden`.
- [ ] **Frontend (30%):**
  - Phân quyền giao diện người dùng: Tự động ẩn các nút hành động ("Hủy đơn", "Hoàn thành") nếu tài khoản đang đăng nhập không phải chủ sở hữu hoặc người nhận đơn.
  - Trang báo lỗi 403 thân thiện khi người dùng cố tình nhập URL trang đơn hàng của người khác.
- [ ] **Chạy thử trên trình duyệt:** Đăng nhập 2 tài khoản khác nhau trên 2 profile trình duyệt $\rightarrow$ Thử vào link đơn của người khác $\rightarrow$ Giao diện chặn lại và hiển thị cảnh báo từ chối truy cập.

### Thứ 6 — Client-Side Security: Chống XSS, Cấu Hình CSP & Bảo Vệ Token (2h)
- [ ] **Frontend (70%):**
  - Phòng chống Cross-Site Scripting (XSS): Cơ chế JSX auto-escaping; loại bỏ nguy cơ từ `dangerouslySetInnerHTML` và URL `javascript:`.
  - Chuyển đổi cơ chế lưu trữ JWT: Tuyệt đối không lưu token nhạy cảm trong `localStorage` $\rightarrow$ Sử dụng Cookie `HttpOnly, Secure, SameSite=Strict` để JavaScript trình duyệt không thể đọc trộm.
  - Cấu hình Content Security Policy (CSP) và Security Headers trong `next.config.js` (`X-Frame-Options: DENY`, `X-Content-Type-Options: nosniff`).
- [ ] **Backend (30%):**
  - Cấu hình Spring Security hỗ trợ đọc JWT từ HttpOnly Cookie bên cạnh header `Authorization: Bearer`.
  - Cấu hình CORS chặt chẽ: Chỉ chấp nhận đúng domain Frontend chỉ định, cấm dùng `*` khi bật `allowCredentials(true)`.
- [ ] **Chạy thử trên trình duyệt:** Thử gõ script `<script>alert('hack')</script>` vào ô mô tả đơn hàng $\rightarrow$ Web render văn bản thuần an toàn; mở tab Application kiểm tra cookie JWT có cờ HttpOnly.

### Thứ 7 — Fullstack Security Penetration Drill & Luyện Live Coding DSA (5h)
- [ ] 2h: Vấn đáp 20 câu hỏi về Design Patterns, Networking HTTP và Fullstack Security (client & server).
- [ ] 1h: Vẽ sơ đồ Strategy Pattern và Event-Driven Architecture; Penetration drill giả lập IDOR và XSS.
- [ ] 1h: Tổng kết checklist an ninh và cập nhật tài liệu.
- [ ] 1h: **Luyện Live Coding DSA (Graph & Backtracking):**
  - Bài 35: **Clone Graph** (LeetCode 133, Medium) — BFS/DFS kết hợp `HashMap` sao chép đồ thị vô hướng trong $O(V + E)$ Time.
  - Bài 36: **Subsets** (LeetCode 78, Medium) — Backtracking sinh toàn bộ tập hợp con trong $O(2^N \cdot N)$ Time; commit vào `dsa/week-15/`.

---

## Tuần 16 — System Architecture Documentation, English Communication & Portfolio

### Thứ 2 — Chuẩn Hóa Toàn Diện RESTful API & OpenAPI Contracts (2h)
- [ ] **Backend (70%):**
  - Rà soát toàn bộ API Contracts: Chuẩn hóa URI danh từ số nhiều (`/api/v1/orders`), quy chuẩn phân trang (`page`, `size`, `sort`).
  - Cập nhật toàn bộ OpenAPI / Swagger examples cho request và response; chuẩn hóa mã lỗi RFC 7807 `ProblemDetail`.
- [ ] **Frontend (30%):**
  - Tự động sinh kiểu dữ liệu TypeScript (hoặc đồng bộ Zod schemas) từ OpenAPI JSON spec của backend, đảm bảo tính nhất quán 100% giữa hai phía.
- [ ] **Chạy thử trên trình duyệt:** Mở Swagger UI (`/swagger-ui.html`) kiểm tra toàn bộ endpoint hoạt động trơn tru; kiểm tra Frontend typecheck pass không có cảnh báo kiểu.

### Thứ 3 — Vẽ Kiến Trúc Hệ Thống Chuẩn C4 Model Fullstack (2h)
- [ ] Học mô hình tài liệu kiến trúc **C4 Model**: Context, Container, Component, Code.
- [ ] Vẽ sơ đồ kiến trúc hệ thống Giao Vặt Fullstack:
  - Sơ đồ Container: Browser Client (Next.js App) $\rightarrow$ Reverse Proxy / Nginx $\rightarrow$ Backend Monolith (Spring Boot 3) $\rightarrow$ Data Stores (PostgreSQL 16 & Redis 7).
  - Sơ đồ Request Flow chi tiết: Khách tạo đơn trên UI Next.js $\rightarrow$ Ghi DB & Redis Feed ZSET $\rightarrow$ Runner Claim (Optimistic Locking) $\rightarrow$ SSE Broadcast cập nhật trực tiếp màn hình client.
- [ ] Viết phần "Architecture Overview" vào README dự án; commit.

### Thứ 4 — Technical English: Introduction & Storytelling (2h)
- [ ] Soạn thảo bản giới thiệu bản thân bằng tiếng Anh (Self-Introduction) trong 90 giây định vị rõ: Kỹ sư Fullstack thiên về Backend (Java Spring Boot 70% + Next.js 30%).
- [ ] Luyện tập ghi âm 3 lần; chỉnh sửa phát âm và ngữ pháp.
- [ ] Nắm vững vốn từ vựng kỹ thuật chuẩn: *concurrency, race condition, data consistency, trade-off, optimistic locking, latency, horizontal scaling, bottleneck, root cause, reactive UI, optimistic UI rollback*.
- [ ] Lưu bản script giới thiệu vào repo; commit.

### Thứ 5 — Technical English: Demo Dự Án Giao Vặt Fullstack (2h)
- [ ] Chuẩn bị bài thuyết trình 5 phút bằng tiếng Anh về dự án Giao Vặt theo cấu trúc STAR:
  - Problem & Context $\rightarrow$ Architecture Design $\rightarrow$ Technical Challenges (Concurrency Locking, Realtime Feed SSE, Rate Limiting & Optimistic UI) $\rightarrow$ Trade-offs $\rightarrow$ Results & Metrics.
  - Tự trả lời 2 câu hỏi kỹ thuật hóc búa bằng tiếng Anh:
    1. *"How do you prevent race conditions when two runners claim the same order simultaneously on the web interface?"*
    2. *"Why did you choose Server-Sent Events (SSE) over WebSocket for real-time order feeds in Next.js?"*
- [ ] Ghi âm và đánh giá độ lưu loát; commit.

### Thứ 6 — Next.js UI/UX Polish & Mobile-First Responsive Design (2h) [Next.js 30%]
- [ ] Tinh chỉnh giao diện toàn bộ app Giao Vặt chuẩn Mobile-first bằng Tailwind CSS (phù hợp với Runner thao tác bằng điện thoại di động ngoài đường).
- [ ] Cải thiện trải nghiệm người dùng (UX):
  - Thêm hiệu ứng Skeleton Loading trong khi chờ dữ liệu bảng tin tải về.
  - Thiết kế Empty States thân thiện khi chưa có đơn hàng nào quanh khu vực.
  - Hỗ trợ chế độ Dark Mode / Light Mode mượt mà.
- [ ] Tối ưu hóa SEO Metadata và OpenGraph tags cho trang chia sẻ link đơn hàng; commit.

### Thứ 7 — Release Fullstack Portfolio Sản Phẩm Giao Vặt v1 & Luyện Live Coding DSA (5h)
- [ ] 2h: Soạn thảo CV 1 trang tiếng Anh chuẩn ATS; quay video demo ngắn (3–5 phút) thể hiện toàn bộ luồng người dùng thật trên trình duyệt.
- [ ] 1h: Tạo Git Tag release chính thức: `v1.0.0-fullstack-giaovat`; kiểm tra clean clone Docker Compose.
- [ ] 1h: **Luyện Live Coding DSA (1D Dynamic Programming — Quy Hoạch Động 1D):**
  - Bài 37: **Climbing Stairs** (LeetCode 70, Easy) — Bản chất dãy Fibonacci, tối ưu từ Memoization sang $O(N)$ Time / $O(1)$ Space.
  - Bài 38: **House Robber** (LeetCode 198, Medium) — Quy hoạch động lựa chọn $dp[i] = \max(dp[i-1], dp[i-2] + nums[i])$ trong $O(N)$ Time / $O(1)$ Space; commit vào `dsa/week-16/`.
- [ ] 1h: Tổng kết portfolio và sẵn sàng tuần nước rút.

---

## Tuần 17 — Production API Patterns, Real-time & High-Concurrency Locking

### Thứ 2 — Lát Cắt Dọc 1: Chống Bấm Đúp Tạo Đơn (Idempotency Key Pattern) [Fullstack] (2h)
- [ ] **Backend (70%):**
  - Học nguyên lý Idempotent API (GET, PUT vs POST, PATCH).
  - Thiết kế Idempotency Key Pattern cho `POST /api/v1/orders`:
    - Interceptor kiểm tra Header `Idempotency-Key` (UUID).
    - Redis lệnh `SET order:idempotency:{key} "PROCESSING" NX EX 120`.
    - Nếu key đã tồn tại: Chặn ngay lập tức và trả về `409 Conflict` (kèm thông điệp đang xử lý) hoặc kết quả đã cache.
    - Xử lý xong cập nhật value thành `"COMPLETED"` kèm Order ID.
  - Viết test JUnit giả lập gửi đồng thời 2 request cùng Idempotency Key; commit.
- [ ] **Frontend (30%):**
  - Form tạo đơn Next.js: Tự động sinh UUID `Idempotency-Key` gắn vào request header khi bấm submit.
  - Disable nút "Đăng Đơn" và hiển thị trạng thái loading quay tròn để ngăn người dùng bấm spam liên tục.
- [ ] **Chạy thử trên trình duyệt:** Bấm đúp nút tạo đơn cực nhanh hoặc gửi lại request từ tab Network $\rightarrow$ Trình duyệt hiển thị thông báo hợp lý, DB chỉ ghi nhận 1 đơn hàng duy nhất!

### Thứ 3 — Lát Cắt Dọc 2: Tích Hợp Webhook & Cổng Thanh Toán Sandbox [Fullstack] (2h)
- [ ] **Backend (70%):**
  - Học mô hình Webhook: Polling vs Callback, nguy cơ Replay Attack & Spoofing.
  - Xây dựng Webhook Receiver endpoint `POST /api/v1/payments/webhook`:
    - Xác thực chữ ký số bằng thuật toán **HMAC-SHA256** dựa trên Shared Secret Key.
    - Kiểm tra tính hợp lệ của timestamp chống Replay Attack quá thời hạn.
    - Idempotent Webhook Processing: Cổng thanh toán gọi lại nhiều lần thì trạng thái đơn vẫn chỉ cập nhật đúng 1 lần duy nhất.
- [ ] **Frontend (30%):**
  - Trang thanh toán Sandbox: Nút "Giả lập Thanh Toán Thành Công / Thất Bại" cho đơn hàng.
  - Giao diện chi tiết đơn hàng: Tự động chuyển huy hiệu trạng thái sang "Đã thanh toán (PAID)" mà không cần F5 trang.
- [ ] **Chạy thử trên trình duyệt:** Bấm nút giả lập thanh toán $\rightarrow$ Webhook xử lý $\rightarrow$ Thẻ đơn hàng trên trình duyệt chuyển trạng thái xanh sang `PAID` ngay lập tức!

### Thứ 4 — Lát Cắt Dọc 3: Bảng Tin Thời Gian Thực Với Server-Sent Events (SSE) [Fullstack] (2h)
- [ ] **Backend (70%):**
  - So sánh giao tiếp thời gian thực: Short Polling vs Long Polling vs WebSocket vs Server-Sent Events (SSE). Vì sao SSE tối ưu cho Bảng Tin Giao Vặt (nhẹ, HTTP chuẩn, native reconnect trình duyệt).
  - Triển khai Spring Boot `SseEmitter`:
    - API `GET /api/v1/orders/feed/stream`: Runner đăng ký nhận stream bảng tin thời gian thực.
    - Khi Creator tạo đơn: Push event `NEW_ORDER_AVAILABLE` tới toàn bộ Runner đang kết nối.
    - Khi có Runner nhận đơn: Push event `ORDER_CLAIMED` để các Runner khác tự động xóa đơn khỏi màn hình.
    - Quản lý Heartbeat ping định kỳ 15 giây.
- [ ] **Frontend (30%):**
  - Xây dựng custom hook `useOrderFeedStream()` trong Next.js sử dụng native browser `EventSource`:
    - Lắng nghe event `NEW_ORDER_AVAILABLE` $\rightarrow$ Tự động chèn đơn mới vào đầu bảng tin kèm hiệu ứng viền vàng nhấp nháy mà không cần tải lại trang.
    - Lắng nghe event `ORDER_CLAIMED` $\rightarrow$ Tự động làm mờ và loại bỏ đơn khỏi bảng tin với hiệu ứng mượt mà.
- [ ] **Chạy thử trên trình duyệt:** Mở 2 tab trình duyệt cạnh nhau (1 Creator, 1 Runner) $\rightarrow$ Tab Creator bấm Tạo đơn $\rightarrow$ Tab Runner thấy đơn hàng mới nhảy lên bảng tin ngay lập tức qua SSE ($<50$ms)!

### Thứ 5 — Lát Cắt Dọc 4: Concurrency Locking & Optimistic UI Rollback [Fullstack] (2h)
- [ ] **Backend (70%):**
  - Phân tích bài toán Double-Picking / Race Condition khi nhiều Runner cùng tranh 1 đơn.
  - So sánh Pessimistic Lock (`SELECT ... FOR UPDATE`) vs Optimistic Lock (`@Version` trong JPA).
  - Triển khai `@Version private Long version;` trên entity `Order`.
  - Bắt `OptimisticLockingFailureException` chuyển thành HTTP `409 Conflict` trả về cho client.
- [ ] **Frontend (30%):**
  - Triển khai **Optimistic UI (Cập nhật giao diện lạc quan)** cho nút "Nhận đơn":
    - Khi Runner bấm "Nhận đơn" $\rightarrow$ Giao diện lập tức chuyển trạng thái sang "Đang nhận việc" và vô hiệu hóa nút ($0$ms delay cảm ứng).
    - Xử lý **Rollback UI**: Nếu backend trả về HTTP `409 Conflict` (do tài xế khác nhanh tay nhận trước), giao diện lập tức phục hồi lại trạng thái cũ và bắn Toast cảnh báo đỏ: *"Rất tiếc! Đơn hàng này vừa được tài xế khác nhận trước bạn. Vui lòng chọn đơn khác!"*.
- [ ] **Chạy thử trên trình duyệt:** Mở 2 tab Runner A và Runner B cạnh nhau trên cùng 1 đơn hàng $\rightarrow$ Cùng bấm "Nhận đơn" trong một tích tắc $\rightarrow$ Runner A nhận việc thành công, Runner B thấy Toast 409 và nút phục hồi trở lại!

### Thứ 6 — Nâng Cao: Deadlock Drill, Resilient Connection & UI Status Badge (2h)
- [ ] **Backend (70%):**
  - Viết test concurrency stress bằng JUnit 5 `CountDownLatch` (10 thread cùng claim 1 đơn): Chứng minh duy nhất 1 thread thành công, 9 thread còn lại nhận 409 Conflict.
  - Dọn dẹp tài nguyên và ngăn chặn rò rỉ bộ nhớ của `SseEmitter` khi client ngắt kết nối (`onCompletion`, `onTimeout`, `onError`).
  - Cấu hình `@Retryable` với exponential backoff cho các tác vụ cần thử lại.
- [ ] **Frontend (30%):**
  - Cơ chế tự động kết nối lại (Auto-reconnect with Backoff) khi kết nối SSE bị gián đoạn.
  - Hiển thị huy hiệu trạng thái kết nối SSE (Connection Badge): Xanh lá "Trực tuyến", Vàng "Đang kết nối lại...", Đỏ "Mất kết nối".
- [ ] **Chạy thử trên trình duyệt:** Thử tắt mạng tạm thời trên browser $\rightarrow$ Huy hiệu chuyển sang màu vàng $\rightarrow$ Bật lại mạng $\rightarrow$ Kết nối tự động phục hồi và tiếp tục nhận đơn mới.

### Thứ 7 — Fullstack High-Concurrency & Luyện Live Coding DSA (5h) [Fullstack Integration]
- [ ] 2h: Ghép nối trọn vẹn kịch bản Real-time & Concurrency trên 3 màn hình trình duyệt (1 Creator + 2 Runner): Creator tạo đơn $\rightarrow$ SSE đẩy 2 Runner $\rightarrow$ Tranh chấp đơn có Optimistic UI Rollback $\rightarrow$ Webhook thanh toán cập nhật realtime.
- [ ] 1h: Giả lập mạng chậm (Network Throttling 3G) kiểm tra tính bền bỉ của Idempotency Key và cơ chế chống bấm đúp; hoàn thiện 2 bản ADR.
- [ ] 1h: **Luyện Live Coding DSA (Monotonic Stack & Queue Simulation):**
  - Bài 39: **Daily Temperatures** (LeetCode 739, Medium) — Monotonic Decreasing Stack tìm phần tử lớn hơn tiếp theo trong $O(N)$ Time / $O(N)$ Space.
  - Bài 40: **Implement Stack using Queues** (LeetCode 225, Easy) — Mô phỏng ngăn xếp bằng 1 hàng đợi `Queue` $O(N)$ push / $O(1)$ pop; commit vào `dsa/week-17/`.
- [ ] 1h: Commit mã nguồn và ghi video màn hình làm bằng chứng thực nghiệm đưa vào portfolio phỏng vấn.

---

## Tuần 18 — Fresher Gate & Sẵn Sàng Ứng Tuyển Thực Tế (Fullstack Java + Next.js)

### Thứ 2 — Mock Technical Interview: Java Core & Next.js/React Fundamentals (2h)
- [ ] Vấn đáp chuyên sâu Java Core (70%): OOP principles, Immutability, Collections Framework internals, JVM Memory (Heap, Stack, Metaspace), Garbage Collection, Java Memory Model, Concurrency primitives.
- [ ] Vấn đáp React & Next.js Core (30%): Virtual DOM, Client Components vs Server Components, React Hooks (`useState`, `useEffect`, `useCallback`, `useMemo`), cơ chế Data Fetching và Caching trên trình duyệt.
- [ ] Luyện nhanh 1 câu hỏi giải thuật nhẩm miệng (Mental LeetCode): Trình bày ý tưởng giải Two Sum hoặc Valid Anagram trong 3 phút không gõ phím; commit ghi chú.

### Thứ 3 — Mock Technical Interview: Spring Boot, Database & Fullstack Architecture (2h)
- [ ] Vấn đáp Spring Boot & Database: IoC/DI, Bean Lifecycle, Proxy mechanism & self-invocation trap, `@Transactional` isolation & propagation, N+1 query fix, B-Tree index structure, MVCC snapshot, JPA `@Version` locking.
- [ ] Vấn đáp luồng dữ liệu Fullstack từ đầu tới cuối: User tương tác UI Next.js $\rightarrow$ HTTP Request kèm `Idempotency-Key` $\rightarrow$ Spring Filter xác thực JWT $\rightarrow$ Controller $\rightarrow$ Service $\rightarrow$ DB Transaction & Redis Feed $\rightarrow$ SSE Emitter $\rightarrow$ EventSource cập nhật DOM; commit.

### Thứ 4 — Mock System & Project Presentation Fullstack (2h)
- [ ] Trình bày dự án Giao Vặt theo cấu trúc chuẩn: Bối cảnh $\rightarrow$ Vấn đề $\rightarrow$ Giải pháp kiến trúc Fullstack $\rightarrow$ Thách thức kỹ thuật (Concurrency Race Condition, Real-time Feed SSE, Rate Limiting, Optimistic UI) $\rightarrow$ Trade-offs $\rightarrow$ Kết quả đạt được.
- [ ] Trả lời phản biện các câu hỏi hóc búa của nhà tuyển dụng xoay quanh Optimistic Locking, SSE connection leak, Idempotency pattern, và bảo mật JWT.

### Thứ 5 — Mock Interview bằng Tiếng Anh (English Technical Round) (2h)
- [ ] Mô phỏng vòng phỏng vấn kỹ thuật bằng tiếng Anh: Self-introduction, Project walk-through, Behavioral questions (STAR method), Career aspiration.
- [ ] Ghi âm lại và chấm điểm dựa trên: Độ rõ ràng (Clarity), Cấu trúc câu trả lời (Structure), Từ vựng kỹ thuật chính xác (Technical Vocabulary).

### Thứ 6 — Thiết Lập Hệ Thống Ứng Tuyển & Chiến Lược Săn Việc (2h)
- [ ] Tạo bảng Job Application Tracker: Công ty, Vị trí, Link JD, Ngày nộp, Trạng thái, Điểm còn thiếu, Kế hoạch follow-up.
- [ ] Lựa chọn 15 Job Descriptions (JD) phù hợp trên thị trường Việt Nam (ITviec, TopCV, LinkedIn):
  - Nhóm 1: Vị trí **Java Fresher / Junior Backend Developer** (chiếm 60–70% mục tiêu).
  - Nhóm 2: Vị trí **Fullstack Fresher / Junior (Java + Next.js/React)** (chiếm 30–40% mục tiêu, lợi thế cạnh tranh tuyệt đối nhờ có sản phẩm hoàn chỉnh).
- [ ] Tùy biến CV: Nhấn mạnh thế mạnh Java Backend sâu bản chất (70%), đồng thời chứng minh năng lực tự chủ xây dựng giao diện Next.js hiện đại (30%) $\rightarrow$ Điểm cộng cực lớn giúp vượt trội 90% ứng viên Fresher khác chỉ biết code lý thuyết đồ chơi.
- [ ] Học kỹ năng đàm phán lương ban đầu: Tìm hiểu dải lương Fresher tại thị trường Việt Nam (12–15+ triệu), cách trả lời câu hỏi "Mức lương mong muốn của bạn là bao nhiêu?".

### Thứ 7 — Final Gate Assessment: Đạt Chuẩn Apply Fresher Fullstack & Vòng Thi Live Coding (5h)
- [ ] 2h: Thử thách Live Coding Fullstack: Tự tay dựng một tính năng Fullstack từ A-Z (Giao diện Next.js Form + Table kết nối Spring Boot API + DB PostgreSQL có validation, auth và exception handling) trong vòng 120 phút không xem tài liệu cũ.
- [ ] 1h: **Vòng Thi Phỏng Vấn Live Coding DSA (Live Coding Mock Interview Round — 45 phút):**
  - Bốc thăm ngẫu nhiên 1 bài LeetCode Medium trong bộ 40 bài cốt lõi (ví dụ: *3Sum*, *Longest Substring Without Repeating Characters*, *Top K Frequent Elements*, hoặc *Course Schedule*).
  - Bấm giờ 35 phút, giải trực tiếp trước camera hoặc người phỏng vấn mô phỏng theo chuẩn 4 bước: 5m Clarify & Edge cases $\rightarrow$ 5m Nêu ý tưởng Brute-force & Big-O $\rightarrow$ 15m Gõ code Java 17 sạch $\rightarrow$ 5m Dry run test case.
  - Phân tích Time Complexity và Space Complexity tự tin, chuẩn xác.
- [ ] 1h: Chạy toàn bộ test suite (Backend JUnit + Frontend Vitest/Playwright pass 100%) và demo sản phẩm toàn diện.
- [ ] 0.5h: Gửi 5 bộ hồ sơ ứng tuyển chất lượng đầu tiên tới các công ty đã chọn lọc.
- [ ] 0.5h: Đánh giá Retrospective toàn bộ Giai đoạn 1 & 2, lập kế hoạch bước vào Giai đoạn 3 (Junior $\rightarrow$ Mid).

**Tiêu chuẩn hoàn thành Gate Fresher (DoD Fresher Fullstack):**
- Có repository Git chuẩn mực; clone về máy mới chạy được ngay toàn bộ stack bằng `docker compose up`.
- Nắm vững kiến trúc Backend 3 layers, code thành thạo CRUD + Auth + Concurrency trong 2–3 giờ.
- Xây dựng được giao diện Next.js tương tác mượt mà, kết nối real-time SSE và xử lý Optimistic UI chuyên nghiệp.
- **Vượt qua bài thi Live Coding DSA:** Giải quyết được bài LeetCode Easy/Medium trong 30–35 phút theo chuẩn 4 bước Live Coding, giải thích mạch lạc Big-O và edge cases.
- Giải thích rành rọt bản chất OOP, Collections, Concurrency primitives, SQL Index, Spring Proxy, JPA Locking, và React Lifecycle.
- Trình bày được dự án và trả lời phỏng vấn kỹ thuật bằng tiếng Anh tự tin.
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

### Thứ 6 — Java/DSA Live Coding/English (2h)
- [ ] 45m: Java/Spring/SQL interview topic theo tuần (đào sâu internals, GC tuning, connection pool, transaction isolation).
- [ ] 45m: **Luyện Live Coding DSA phỏng vấn công ty Top tại VN (Shopee, VNG, NAB, Axon, Line, Grab):** 1–2 bài LeetCode Medium/Hard theo các chủ đề chuyên sâu:
  - Graph nâng cao (BFS/DFS, Topological Sort, Dijkstra, Word Ladder).
  - Dynamic Programming (Coin Change, Longest Increasing Subsequence, Word Break).
  - Trie / Prefix Tree (Implement Trie, Word Search II).
  - System-Adjacent DSA: LRU Cache (LeetCode 146), LFU Cache, Monotonic Deque (Sliding Window Maximum).
  - Tiếp tục duy trì khung 4 bước Live Coding và giải thích Big-O bằng tiếng Anh.
- [ ] 30m: Luyện nói và viết câu trả lời phỏng vấn kỹ thuật bằng tiếng Anh (English STAR method).

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
