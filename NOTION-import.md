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
## Java Core + Backend foundation

**Mục tiêu cuối giai đoạn:** tự viết Java sạch; hiểu OOP/DSA; dùng Git/Maven; viết REST API Spring Boot kết nối MySQL/PostgreSQL; có test cơ bản.

**Dự án chính: Giao Vặt** — On-Demand Delivery & Order Queue Platform (Clone Grab đơn giản mô hình Crowdsourcing)
- **Scope:** Hệ thống kết nối Khách hàng (Customer) và Tài xế (Driver). Thay vì hệ thống tự động gán tài xế, Khách hàng đăng yêu cầu giao hàng $\rightarrow$ Đơn chuyển vào hàng đợi công khai (`Order Queue`) $\rightarrow$ Các tài xế duyệt queue và tự do pick cuốc mong muốn.
- **Core Mechanism:** Hàng đợi đơn hàng tập trung (`PENDING` orders), cơ chế khóa chống tranh chấp khi nhiều tài xế cùng bấm pick 1 cuốc (Concurrency Locking), thông báo real-time cập nhật queue và trạng thái đơn (Server-Sent Events / WebSocket).
- **Core features:** Customer đăng đơn (điểm đón, điểm trả, cước phí), hàng đợi cuốc xe công khai, Driver duyệt queue & pick cuốc (`PENDING` $\rightarrow$ `ACCEPTED`), cập nhật hành trình (`IN_TRANSIT` $\rightarrow$ `COMPLETED` / `CANCELLED`), tính giá linh hoạt (Strategy Pattern), phân quyền Customer vs Driver bằng JWT.
- **Architecture:** Monolith Spring Boot chuẩn 3 layers (Controller–Service–Repository), Redis In-Memory Queue/Cache, PostgreSQL/MySQL tập trung, thiết kế module hóa sẵn sàng mở rộng sang Microservices phân tán.

### Danh mục 9 Module Chức năng Bắt buộc của App Giao Vặt (Khai thác 100% Roadmap)
1. **Module 1 — Authentication & RBAC (Tuần 9, 15):** Đăng ký/đăng nhập Customer & Driver; Spring Security 6 + JWT Stateless; Refresh Token Rotation lưu Redis; phân quyền `@PreAuthorize("hasRole('...')")`; cấu hình MDC Logging `traceId`; ẩn số điện thoại khách trên public queue (chỉ hiển thị sau khi tài xế pick cuốc).
2. **Module 2 — Đăng đơn & Định giá thông minh (Tuần 6, 15, 17):** DTO Validation `@Valid`; GoF Strategy Pattern cho tính giá cước (`StandardPricingStrategy`, `SurgePricingStrategy` giờ cao điểm, `BadWeatherPricingStrategy` thời tiết xấu); Idempotency Key Pattern (Header `Idempotency-Key` lưu Redis chống bấm đúp tạo đơn trùng); chuẩn hóa lỗi theo RFC 7807 `ProblemDetail`.
3. **Module 3 — Redis In-Memory Priority Queue (Tuần 10):** Redis Sorted Set (ZSET) lưu `orders:pending` theo score thời gian/giá cước; Cache-Aside pattern cho chi tiết đơn `order:{id}`; Sliding Window Rate Limiting bằng Redis để chống bot/spam refresh queue.
4. **Module 4 — Driver Pick Order & Concurrency Control (Tuần 7, 17, 24–26):** Giải quyết triệt để race condition khi nhiều tài xế cùng bấm pick 1 đơn bằng JPA Optimistic Locking (`@Version`); đối chứng so sánh với Pessimistic Locking (`PESSIMISTIC_WRITE`) hoặc Redisson Distributed Lock; cấu hình Spring `@Retryable` tự động retry với exponential backoff khi gặp deadlock.
5. **Module 5 — Real-time Queue & Notifications (Tuần 17):** Server-Sent Events (`SseEmitter`) quản lý luồng real-time; Event-Driven Architecture (`ApplicationEventPublisher`); sử dụng Virtual Threads (JDK 21) cho tác vụ push notification bất đồng bộ (broadcast thêm đơn mới vào queue, gỡ đơn đã nhận, báo khách có tài xế nhận).
6. **Module 6 — Quản lý vòng đời đơn & State Machine (Tuần 4, 6, 8, 12):** Quản lý chu trình trạng thái: `PENDING` $\rightarrow$ `ACCEPTED` $\rightarrow$ `IN_TRANSIT` $\rightarrow$ `COMPLETED` / `CANCELLED`; Custom Exceptions (`InvalidOrderStateException`, `OrderNotFoundException`); Global Exception Handler `@RestControllerAdvice`; Unit & Integration tests với MockMvc.
7. **Module 7 — Thanh toán Sandbox & Webhook (Tuần 17, 49):** Tích hợp cổng thanh toán giả lập (VNPay/Stripe Sandbox); Webhook Receiver xác thực chữ ký số HMAC-SHA256; Idempotent Webhook Processing (chống duplicate webhook callback khi cổng gửi lại).
8. **Module 8 — Báo cáo định kỳ & Spring Batch (Tuần 4, 22):** `@Scheduled` hoặc Spring Batch tự động tổng kết doanh thu tài xế lúc 00:00 hàng ngày; xuất file báo cáo Excel bằng Apache POI; tính toán thống kê bằng Java Stream API (`groupingBy`, `summarizingDouble`).
9. **Module 9 — Database Tuning, Testing & DevOps (Tuần 5, 7, 11, 12, 36):** Flyway Database Migrations (`V1`, `V2`); B-Tree Composite Index `(status, created_at)` kèm benchmark `EXPLAIN ANALYZE`; Testcontainers (PostgreSQL + Redis thật); Multi-thread stress test với JUnit 5 + `CountDownLatch`; Dockerfile multi-stage; Docker Compose full stack; GitHub Actions CI pipeline; Spring Actuator & Prometheus metrics.

## Tuần 1 — Setup, syntax, control flow

### Thứ 2 — Môi trường + chương trình đầu tiên (2h)
- [ ] Cài JDK 21, IntelliJ IDEA, Git, Maven; kiểm tra `java --version`, `mvn --version`, `git --version`.
- [ ] Học cấu trúc class, `main`, biến, primitive/reference type, `String`.
- [ ] Tạo repository `java-roadmap`; commit chương trình Hello World.

### Thứ 3 — Kiểu dữ liệu + toán tử (2h)
- [ ] Học numeric types, boolean, casting, overflow, operator precedence.
- [ ] Code máy tính đơn giản: cộng, trừ, nhân, chia, modulo; validate chia cho 0.
- [ ] Viết 5 assert kiểm tra boundary cases; commit.

### Thứ 4 — Điều kiện (2h)
- [ ] Học `if/else`, nested condition, `switch`, ternary; tránh điều kiện lồng quá sâu.
- [ ] Code phân loại điểm, năm nhuận, loại tam giác.
- [ ] Viết test tay cho input hợp lệ, biên, không hợp lệ.

### Thứ 5 — Vòng lặp (2h)
- [ ] Học `for`, enhanced `for`, `while`, `do-while`, `break`, `continue`.
- [ ] Code menu console và bài tổng chữ số, số nguyên tố, Fibonacci.
- [ ] Ghi Big-O cho từng bài; commit.

### Thứ 6 — Method + clean code (2h)
- [ ] Học parameter, return, scope, overload; một method chỉ nên có một trách nhiệm.
- [ ] Tách bài tuần thành method nhỏ; đặt tên rõ; bỏ duplicate code.
- [ ] Tự review diff; ghi 3 điểm đã sửa.

### Thứ 7 — Mini project 1 (5h)
- [ ] 1h: thiết kế menu Student Management.
- [ ] 2h: code add/list/find/delete student bằng array.
- [ ] 1h: validation ID, name, score; custom error message.
- [ ] 1h: README, commit, quay video chạy demo.

**Chủ nhật:** nghỉ; tùy chọn xem lại 10 câu hỏi tự kiểm tra.

## Tuần 2 — OOP căn bản

### Thứ 2 — Class, object, constructor (2h)
- [ ] Học class, field, method, constructor, `this`.
- [ ] Refactor Student thành class; tạo `StudentService`.
- [ ] Test tạo object và default validation.

### Thứ 3 — Encapsulation + immutability (2h)
- [ ] Học private field, getter/setter có validation; immutable object.
- [ ] Tạo `Money` hoặc `Address` immutable; không expose mutable collection.
- [ ] Review lỗi setter cho phép state sai.

### Thứ 4 — Composition (2h)
- [ ] Học composition vs inheritance; dependency giữa object.
- [ ] Tạo `Course`, `Enrollment`, `Student`; quản lý đăng ký học.
- [ ] Viết test enrollment duplicate.

### Thứ 5 — Inheritance + override (2h)
- [ ] Học `extends`, override, `super`, `final`; nhận diện inheritance không phù hợp.
- [ ] Code `User`, `Admin`, `Customer`; thay thế phần duplicate bằng composition nếu cần.
- [ ] Ghi một ví dụ “is-a” và một ví dụ “has-a”.

### Thứ 6 — Interface + polymorphism (2h)
- [ ] Học interface, abstract class, polymorphism, dependency on abstraction.
- [ ] Tạo `NotificationSender` với Email/SMS fake implementation.
- [ ] Test cùng một service chạy với hai implementation.

### Thứ 7 — Mini project 2 (5h)
- [ ] 1h: thiết kế Library gồm `Book`, `Member`, `Loan`.
- [ ] 2h: code borrow/return/search; dùng composition.
- [ ] 1h: validation và exception.
- [ ] 1h: UML, README, refactor, commit.

## Tuần 3 — Collections + Big-O

### Thứ 2 — List (2h)
- [ ] Học `ArrayList`, `LinkedList`, index, iteration, mutation.
- [ ] Refactor Library từ array sang `List`.
- [ ] So sánh chi phí truy cập và insert; ghi Big-O.

### Thứ 3 — Set (2h)
- [ ] Học `HashSet`, `LinkedHashSet`, `TreeSet`, `equals/hashCode` contract.
- [ ] Chặn member/book duplicate; test object equality.
- [ ] Ghi khi cần uniqueness, ordering, sorting.

### Thứ 4 — Map (2h)
- [ ] Học `HashMap`, `LinkedHashMap`, `TreeMap`, `getOrDefault`, `computeIfAbsent`.
- [ ] Code word frequency và index book theo ID.
- [ ] Giải thích bucket, hash collision, load factor ở mức phỏng vấn Fresher.

### Thứ 5 — Queue, Deque, PriorityQueue (2h)
- [ ] Học FIFO, LIFO, priority ordering.
- [ ] Code booking queue và task priority queue.
- [ ] Test empty queue, duplicate priority, overflow policy.

### Thứ 6 — Generics (2h)
- [ ] Học generic class/method, bounded wildcard, PECS, type erasure.
- [ ] Viết `Repository<T, ID>` in-memory tối thiểu.
- [ ] Xóa raw type; bật compiler warning và sửa.

### Thứ 7 — DSA lab (5h)
- [ ] 1h: học Big-O, array/hashmap pattern.
- [ ] 2h: làm Two Sum, Valid Anagram, Group Anagrams.
- [ ] 1h: làm Contains Duplicate, Top K Frequent Elements.
- [ ] 1h: ghi approach, complexity, lỗi sai, commit.

## Tuần 4 — Exceptions, Stream, functional Java

### Thứ 2 — Exception (2h)
- [ ] Học checked/unchecked, `throw`, `throws`, try/catch/finally.
- [ ] Tạo `BookNotFoundException`, `InvalidLoanException`.
- [ ] Test exception type và message; không catch `Exception` vô tội vạ.

### Thứ 3 — File I/O (2h)
- [ ] Học `Path`, `Files`, UTF-8, try-with-resources.
- [ ] Export/import Library CSV.
- [ ] Xử lý file thiếu, dòng lỗi, duplicate ID; test bằng temporary directory.

### Thứ 4 — Lambda + functional interface (2h)
- [ ] Học Predicate, Function, Consumer, Supplier, method reference.
- [ ] Viết filter student/book bằng predicate.
- [ ] So sánh lambda với anonymous class; tránh lambda khó đọc.

### Thứ 5 — Stream API (2h)
- [ ] Học `filter`, `map`, `sorted`, `distinct`, `reduce`, `collect`, `groupingBy`.
- [ ] Tạo report: sách theo category, student theo score range.
- [ ] Test empty stream và null input; không dùng `parallelStream` tùy tiện.

### Thứ 6 — Optional, record, switch expression (2h)
- [ ] Học `Optional` cho return value, record cho DTO/value object, switch expression.
- [ ] Refactor query result và report.
- [ ] Ghi rõ: không dùng record cho JPA entity mutable.

### Thứ 7 — Chốt Java Core (5h)
- [ ] 2h: hoàn thiện Library v1 và test.
- [ ] 1h: làm 5 bài DSA Easy array/string/hashmap.
- [ ] 1h: mock interview Java Core 20 câu.
- [ ] 1h: dọn repo, README, tag `java-core-v1`.

## Tuần 5 — Git, Maven, testing workflow

### Thứ 2 — Git workflow (2h)
- [ ] Học branch, merge, rebase, conflict, stash, revert, cherry-pick.
- [ ] Tạo feature branch cho Library; cố ý tạo conflict rồi resolve.
- [ ] Viết commit message theo dạng imperative.

### Thứ 3 — Maven (2h)
- [ ] Học `pom.xml`, dependency scope, lifecycle, plugin, project layout.
- [ ] Tạo Maven project; thêm JUnit 5 và Mockito.
- [ ] Chạy `mvn clean test`, `mvn package`; hiểu target artifact.

### Thứ 4 — Unit test (2h)
- [ ] Học arrange-act-assert, test naming, parameterized test.
- [ ] Test `LibraryService`: borrow, return, duplicate, not-found.
- [ ] Bổ sung boundary cases; không test implementation detail.

### Thứ 5 — Mockito (2h)
- [ ] Học mock/stub/verify, interaction test, fake vs mock.
- [ ] Mock repository trong service test.
- [ ] Viết một test không dùng Mockito để so sánh trade-off.

### Thứ 6 — Debugging & JVM Memory + Concurrency Fundamentals (2h)
- [ ] Dùng breakpoint, step over/into, evaluate expression, exception breakpoint; sửa 3 bug: null, off-by-one, mutable state.
- [ ] Học JVM Memory Layout: Heap (Young Gen: Eden, Survivor; Old Gen), Stack Frame, Metaspace, Program Counter; cơ chế Garbage Collection căn bản (Mark & Sweep, Stop-The-World).
- [ ] Học Java Memory Model (JMM): Visibility, Reordering, Happens-Before; Concurrency primitives: `volatile` vs `synchronized`, `AtomicInteger`/CAS (Compare-And-Swap), `ReentrantLock` & Condition.
- [ ] Viết test chứng minh `volatile` giải quyết visibility và `AtomicInteger` giải quyết lost update trong multi-thread; ghi root cause và test regression.

### Thứ 7 — Java Core assessment (5h)
- [ ] 2h: làm bài test Java Core giới hạn thời gian.
- [ ] 1h: sửa bài sai.
- [ ] 1h: làm 3 bài DSA.
- [ ] 1h: chốt checklist và tag `java-core-ready`.

## Tuần 6 — Spring Core + Spring Boot

### Thứ 2 — IoC/DI + Spring Bean Lifecycle (2h)
- [ ] Học IoC container, ApplicationContext vs BeanFactory, bean scopes (Singleton, Prototype).
- [ ] Học chi tiết **Spring Bean Lifecycle**: BeanDefinition -> Instantiation -> Populate properties -> Aware interfaces -> `BeanPostProcessor` (before) -> `@PostConstruct` / `InitializingBean` -> `BeanPostProcessor` (after) -> In use -> `@PreDestroy` / `DisposableBean`.
- [ ] Tạo Spring Boot app bằng Spring Initializr; code hai implementation của `PricingService`; inject bằng `@Qualifier`.

### Thứ 3 — Configuration (2h)
- [ ] Học `@Configuration`, `@Bean`, profile, config properties, environment variable.
- [ ] Tạo `application-local.yml` và `application-test.yml`.
- [ ] Kiểm tra secret không nằm trong Git.

### Thứ 4 — Spring MVC (2h)
- [ ] Học `@RestController`, mapping, path variable, request param, request body.
- [ ] Viết `DeliveryOrderController` GET/POST (khách đăng đơn hàng, xem danh sách queue đơn chờ).
- [ ] Test request bằng curl/Postman.

### Thứ 5 — DTO + validation (2h)
- [ ] Học request DTO, response DTO, `@Valid`, constraints, enum (`OrderStatus`: PENDING, ACCEPTED, IN_TRANSIT, COMPLETED, CANCELLED).
- [ ] Thêm validation cho CreateOrderRequest (`pickupAddress`, `dropoffAddress`, `price`, `itemNote`, `phoneNumber`).
- [ ] Test 400 response cho payload thiếu trường hoặc giá cước <= 0.

### Thứ 6 — Layering & Spring Proxy Internals (2h)
- [ ] Học Controller–Service–Repository; transaction ở service boundary.
- [ ] Học cơ chế **Spring AOP & Proxy**: JDK Dynamic Proxy (dựa trên interface) vs CGLIB Proxy (kế thừa class con tạo bytecode runtime).
- [ ] Phân tích và reproduce bẫy kinh điển: **`@Transactional` / `@Async` Self-Invocation trap** (gọi method transactional cùng class dẫn đến bypass proxy, không mở transaction); thực hành 3 cách khắc phục (tách bean, self-injection bằng `@Lazy`, dùng `TransactionTemplate`).
- [ ] Refactor Order API thành 3 layer; viết service unit test với fake repository.

### Thứ 7 — REST API lab (5h)
- [ ] 2h: hoàn thiện Order & Queue CRUD in-memory.
- [ ] 1h: global exception handler (xử lý `OrderNotFoundException`, `InvalidOrderStateException`).
- [ ] 1h: OpenAPI dependency và endpoint docs.
- [ ] 1h: README API examples, commit.

## Tuần 7 — SQL + JPA/Hibernate

### Thứ 2 — Relational design (2h)
- [ ] Học table, PK/FK, normalization 1NF–3NF, constraint.
- [ ] Thiết kế ERD Giao Vặt core: `User` (id, email, password, fullName, phone, role), `DeliveryOrder` (id, customer_id, driver_id, pickupAddress, dropoffAddress, price, status, version, createdAt), `OrderReview`.
- [ ] Thiết kế database tập trung: index trên `status` và `created_at` để tối ưu truy vấn danh sách queue đơn chờ.
- [ ] Viết migration V1 cho database bằng Flyway.

### Thứ 3 — SQL CRUD, JOIN + B-Tree Index (2h)
- [ ] Học INSERT/UPDATE/DELETE/SELECT, INNER/LEFT/RIGHT JOIN.
- [ ] Học cấu trúc **B-Tree Index**: Cấu trúc cây cân bằng $O(\log N)$, leaf nodes linked list cho range query, Clustered Index (Primary Key) vs Secondary Index; phân biệt Index Seek vs Index Scan vs Full Table Scan.
- [ ] Viết 10 query cho Giao Vặt: lọc đơn `PENDING` theo thời gian mới nhất, lịch sử đơn của khách hàng, tổng thu nhập của tài xế; seed data; kiểm tra foreign key và duplicate.

### Thứ 4 — JPA entity/repository (2h)
- [ ] Học `@Entity`, ID generation, `JpaRepository`, query method.
- [ ] Mapping `User` và `DeliveryOrder`.
- [ ] Viết repository test với MySQL/PostgreSQL container nếu có thể (Testcontainers).

### Thứ 5 — Relationships (2h)
- [ ] Học `@ManyToOne`, `@OneToMany`, owning side, cascade, fetch.
- [ ] Mapping `DeliveryOrder` với `User` (Customer) và `User` (Driver); mapping `OrderReview`.
- [ ] Test persist, find, delete; tránh cascade nguy hiểm (không xóa user khi xóa order).

### Thứ 6 — Transactions, Isolation Levels, MVCC & Deadlock (2h)
- [ ] Học `@Transactional`, lazy loading, N+1, JOIN FETCH, EntityGraph; tạo N+1 bằng SQL logging và tối ưu.
- [ ] Học **Transaction Isolation Levels**: READ UNCOMMITTED, READ COMMITTED, REPEATABLE READ, SERIALIZABLE; phân tích 4 hiện tượng dị thường: **Dirty Read**, **Non-repeatable Read**, **Phantom Read**, **Lost Update**.
- [ ] Học cơ chế **MVCC** (Multi-Version Concurrency Control) trong PostgreSQL & MySQL InnoDB (Undo Log, Read View để đọc non-blocking snapshot).
- [ ] Phân tích nguyên nhân **Deadlock**: 2 transaction tranh chấp khóa chéo nhau; cách xem MySQL Deadlock Log (`SHOW ENGINE INNODB STATUS`); giải pháp chuẩn hóa thứ tự lock và cơ chế retry.
- [ ] Test rollback khi tạo đơn hoặc tài xế nhận cuốc fail.

### Thứ 7 — Chuyển Order & Queue API sang DB (5h)
- [ ] 2h: repository + service + DTO + MapStruct hoặc mapping thủ công.
- [ ] 1h: pagination/sorting/filter cho danh sách queue đơn hàng chờ.
- [ ] 1h: integration tests.
- [ ] 1h: ERD, migration, README, commit.

## Tuần 8 — Project v0 + gate

### Thứ 2 — Order Lifecycle & Driver Pick Order flow (2h)
- [ ] Code API khách tạo đơn giao hàng (`POST /api/orders`) $\rightarrow$ lưu trạng thái `PENDING`.
- [ ] Code API tài xế xem danh sách đơn chờ (`GET /api/orders/queue`).
- [ ] Code API tài xế nhận cuốc (`PUT /api/orders/{id}/accept`) $\rightarrow$ gán `driver_id`, cập nhật trạng thái `ACCEPTED`.
- [ ] Test validation trạng thái: chặn tài xế nhận đơn đã được nhận hoặc đơn đã bị hủy; chặn khách tự nhận đơn của mình.

### Thứ 3 — Error handling + API quality (2h)
- [ ] Chuẩn hóa error code, status, timestamp, path, validation errors.
- [ ] Thêm sorting/filtering/pagination cho order listing và queue.
- [ ] Cập nhật OpenAPI.

### Thứ 4 — Integration test (2h)
- [ ] Viết test controller bằng MockMvc cho luồng tạo đơn và nhận đơn.
- [ ] Viết test database transaction và migration.
- [ ] Chạy toàn bộ `mvn test`; sửa flaky test.

### Thứ 5 — Refactor + performance (2h)
- [ ] Review SOLID, naming, package, duplicate logic.
- [ ] Chạy `EXPLAIN` query queue đơn hàng; thêm composite index `(status, created_at)`.
- [ ] Ghi benchmark trước/sau khi đánh index.

### Thứ 6 — Interview gate (2h)
- [ ] Trả lời 15 câu Java, 15 câu Spring, 10 câu SQL.
- [ ] Làm 2 bài DSA Easy trong 45 phút.
- [ ] Ghi lỗ hổng; tạo backlog sửa.

### Thứ 7 — Demo gate (5h)
- [ ] 2h: làm lại một CRUD entity từ số 0, không xem code cũ.
- [ ] 1h: chạy demo và quay video.
- [ ] 1h: hoàn thiện README/ERD/API.
- [ ] 1h: tag `foundation-ready`.

---

# GIAI ĐOẠN 2 — TUẦN 9–18
## Đủ điều kiện apply Java Fresher — mục tiêu 12–15 triệu

**Mục tiêu:** Giao Vặt v1 là on-demand delivery platform với Order Queue tập trung, cơ chế Driver pick cuốc, phân quyền Customer vs Driver, Redis Caching, rate limiting, Docker, CI/CD, deploy và tài liệu chuẩn. Sau tuần 18 bắt đầu apply, không chờ học Senior.

## Tuần 9 — Spring Security + password/JWT

### Thứ 2 — Security fundamentals (2h)
- [ ] Học authentication, authorization, filter chain, principal, authority.
- [ ] Thêm Spring Security; phân biệt các Role: `ROLE_CUSTOMER`, `ROLE_DRIVER`, `ROLE_ADMIN`.
- [ ] Implement user context từ JWT token (lấy `user_id`, `role` từ SecurityContextHolder).
- [ ] Test endpoint public (đăng ký, đăng nhập) vs private (đăng đơn, nhận đơn, xem queue).

### Thứ 3 — Password (2h)
- [ ] Học password hashing, BCrypt, credential flow.
- [ ] Tạo User/Role schema và migration.
- [ ] Test register: duplicate email/phone, password yếu, password không lưu plain text.

### Thứ 4 — Login JWT (2h)
- [ ] Học JWT header/payload/signature, expiry, access token.
- [ ] Code login trả access token kèm role (`CUSTOMER` hoặc `DRIVER`).
- [ ] Test token hợp lệ, sai signature, hết hạn.

### Thứ 5 — Authorization & RBAC (2h)
- [ ] Học RBAC và method security (`@PreAuthorize`).
- [ ] Khách hàng (`ROLE_CUSTOMER`): chỉ xem và hủy đơn của chính mình; không thể gọi API nhận cuốc.
- [ ] Tài xế (`ROLE_DRIVER`): duyệt danh sách queue các đơn `PENDING`; nhận cuốc và cập nhật đơn mình đã nhận.
- [ ] Bảo mật dữ liệu: Ẩn số điện thoại khách hàng trên public queue; chỉ tài xế đã pick cuốc thành công mới xem được số điện thoại khách.

### Thứ 6 — Refresh/logout (2h)
- [ ] Học refresh token rotation và revoke cơ bản.
- [ ] Code refresh/logout; secret từ environment.
- [ ] Ghi threat model ngắn.

### Thứ 7 — Auth integration (5h)
- [ ] 2h: hoàn thiện auth flow.
- [ ] 1h: integration tests.
- [ ] 1h: CORS/SameSite/CSRF decision cho API.
- [ ] 1h: README security.

## Tuần 10 — Redis In-Memory Order Queue & Caching

### Thứ 2 — Redis Data Structures & Order Queue (2h)
- [ ] Học String, Set, Sorted Set (ZSet), Hash, TTL trong Redis.
- [ ] Thiết kế Order Queue trên Redis: khi khách đăng đơn, lưu chi tiết vào Hash `order:{id}` và đẩy `order_id` vào Set/ZSet `orders:pending` (sắp xếp theo timestamp tạo đơn).
- [ ] Code API tài xế lấy danh sách đơn chờ trực tiếp từ Redis để giảm tải tối đa cho Database chính.

### Thứ 3 — Order State Synchronization & Cache-Aside (2h)
- [ ] Xử lý đồng bộ: khi tài xế pick cuốc thành công (`PENDING` $\rightarrow$ `ACCEPTED`), xóa `order_id` khỏi Redis Set `orders:pending`.
- [ ] Cập nhật cache chi tiết đơn `order:{id}` và lưu đồng thời xuống Database.
- [ ] Xử lý Cache-Aside pattern và fallback query DB khi Redis gặp sự cố.

### Thứ 4 — Redis setup & Docker Compose (2h)
- [ ] Chạy Redis bằng Docker Compose.
- [ ] Cấu hình Spring Data Redis, `RedisTemplate` và serializer JSON an toàn.
- [ ] Viết test kết nối và test thao tác trên Redis Queue.

### Thứ 5 — Cache Correctness & Invalidation (2h)
- [ ] Invalidate cache sau khi đơn bị khách hủy hoặc tài xế hoàn thành đơn.
- [ ] Test stale data và cache miss; xử lý Cache Penetration bằng cách lưu null object ngắn hạn.
- [ ] Ghi rõ nguyên tắc: dữ liệu tiền bạc/trạng thái thanh toán luôn đọc từ DB gốc.

### Thứ 6 — Rate Limiting & Anti-Spam (2h)
- [ ] Học thuật toán Token Bucket và Sliding Window Rate Limiting.
- [ ] Triển khai Rate Limiting với Redis: Giới hạn khách tạo tối đa 5 đơn/phút; giới hạn tài xế spam pick đơn tối đa 10 lần/phút để chống bot script.
- [ ] Không lưu token/password và số điện thoại thô trong server log.

### Thứ 7 — Reliability & Concurrency Lab (5h)
- [ ] 2h: hoàn thiện luồng Redis Queue + DB fallback.
- [ ] 1h: test đồng bộ trạng thái khi có nhiều request tạo đơn và pick đơn đồng thời.
- [ ] 1h: đo latency API lấy danh sách queue từ Redis so với query PostgreSQL trực tiếp.
- [ ] 1h: root-cause note và commit.

## Tuần 11 — Docker + CI/CD

### Thứ 2 — Docker backend (2h)
- [ ] Học image/container/layer/volume/network.
- [ ] Viết Dockerfile multi-stage cho Spring Boot.
- [ ] Build và chạy image.

### Thứ 3 — Compose (2h)
- [ ] Viết Compose cho app + MySQL/PostgreSQL + Redis.
- [ ] Healthcheck và environment variables.
- [ ] Kiểm tra one-command startup.

### Thứ 4 — GitHub Actions (2h)
- [ ] Học workflow, job, step, cache dependency.
- [ ] Pipeline checkout → setup JDK → `mvn test` → package.
- [ ] Tạo badge CI.

### Thứ 5 — Jenkins (2h)
- [ ] Chạy Jenkins local/container.
- [ ] Tạo Pipeline: checkout → Maven test → archive artifact.
- [ ] Ghi khác biệt Jenkins vs GitHub Actions.

### Thứ 6 — Deployment (2h)
- [ ] Học deploy env, logs, healthcheck, rollback cơ bản.
- [ ] Deploy backend lên Render/Railway/Fly.io hoặc máy chủ phù hợp.
- [ ] Không commit secret; tạo `.env.example`.

### Thứ 7 — CI/CD finish (5h)
- [ ] 2h: build image trong CI.
- [ ] 1h: integration test trong CI nếu runner hỗ trợ.
- [ ] 1h: deploy demo.
- [ ] 1h: README runbook và rollback.

## Tuần 12 — Testing, debugging, performance

### Thứ 2 — Testing pyramid (2h)
- [ ] Phân biệt unit, slice, integration, e2e.
- [ ] Lập test matrix cho Customer/Driver/Order Queue/Pick Order.
- [ ] Bỏ test trùng hoặc test implementation detail.

### Thứ 3 — Testcontainers/MockMvc (2h)
- [ ] Chạy MySQL/PostgreSQL thật trong Testcontainers.
- [ ] Viết repository + controller integration tests cho luồng Order & Queue.
- [ ] Sửa test isolation.

### Thứ 4 — Logging/observability (2h)
- [ ] Structured logging, log level, correlation ID.
- [ ] Thêm request ID và exception log không lộ secret, không lộ số điện thoại khách.
- [ ] Dùng Actuator health/info/metrics cơ bản.

### Thứ 5 — Performance (2h)
- [ ] Đo query danh sách queue đơn hàng bằng `EXPLAIN`.
- [ ] Kiểm tra N+1 khi query Order kèm User (Customer/Driver), pagination, composite index `(status, created_at)`.
- [ ] Ghi before/after; không claim tối ưu nếu không đo.

### Thứ 6 — Bug hunt (2h)
- [ ] Tạo hoặc nhận 5 bug: validation thiếu trường, sai quyền role, race condition khi 2 tài xế cùng pick đơn, stale cache queue trên Redis, lộ SĐT khách trước khi pick.
- [ ] Debug từng bug; thêm regression test.
- [ ] Viết root cause ngắn bằng English.

### Thứ 7 — Quality gate (5h)
- [ ] 2h: chạy test full.
- [ ] 1h: review code như reviewer lạ.
- [ ] 1h: fix top 5 risk.
- [ ] 1h: cập nhật quality checklist.

## Tuần 13 — Agile, Jira, Confluence, AI workflow

### Thứ 2 — Agile/Scrum (2h)
- [ ] Học backlog, epic, story, acceptance criteria, sprint, DoD.
- [ ] Viết 1 epic Giao Vặt và 8 user stories (Khách đăng đơn, Hiển thị Queue, Tài xế pick cuốc, Cập nhật lộ trình, Hủy đơn, Đánh giá).
- [ ] Chia story theo vertical slice.

### Thứ 3 — Jira mock (2h)
- [ ] Tạo board cá nhân; tạo issue, label, priority, estimate.
- [ ] Lập sprint 1 tuần; kéo task theo trạng thái.
- [ ] Viết daily update: done/next/blocker.

### Thứ 4 — Planning/retro (2h)
- [ ] Estimate 3 task bằng 3-point/story points; ghi assumptions.
- [ ] Tự mô phỏng sprint planning.
- [ ] Viết retrospective: keep/stop/start, một action item.

### Thứ 5 — Confluence/design docs (2h)
- [ ] Viết design doc: context, requirements, API, ERD, alternatives, risks.
- [ ] Viết ADR chọn kiến trúc queue đơn hàng, MySQL/PostgreSQL, Redis cache, JWT.
- [ ] Viết runbook start/test/rollback.

### Thứ 6 — AI coding assistant (2h)
- [ ] Chọn Copilot, Cursor hoặc Codeium; dùng cho một endpoint và test.
- [ ] Lưu prompt, generated diff, review comments, test output.
- [ ] Cố ý kiểm tra hallucinated API, security flaw, missing edge case.

### Thứ 7 — Review workflow (5h)
- [ ] 2h: tạo PR cho feature tính cước linh hoạt hoặc hủy đơn hàng.
- [ ] 1h: review diff bằng checklist correctness/security/test.
- [ ] 1h: dùng AI tạo test rồi tự sửa test sai.
- [ ] 1h: ghi AI workflow vào README.

## Tuần 14 — DSA nâng cao: recursion, tree, graph, DP

### Thứ 2 — Recursion + binary search (2h)
- [ ] Học recursion, base case, call stack; binary search và biến thể.
- [ ] Làm 3 bài: Binary Search, Search in Rotated Sorted Array, Koko Eating Bananas.
- [ ] Ghi template binary search tránh off-by-one; test boundary.

### Thứ 3 — Tree (2h)
- [ ] Học BST, DFS/BFS, inorder/preorder/postorder, height.
- [ ] Làm 3 bài: Invert Binary Tree, Max Depth, Validate BST, Level Order Traversal.
- [ ] Code cả đệ quy và iterative bằng stack/queue.

### Thứ 4 — Heap + Trie (2h)
- [ ] Học `PriorityQueue` làm heap, top-k pattern; Trie cho prefix search.
- [ ] Làm 2 bài: K Closest Points, Top K Frequent (bản heap); tự implement Trie.
- [ ] So sánh heap vs sort cho top-k; ghi complexity.

### Thứ 5 — Graph cơ bản (2h)
- [ ] Học adjacency list/matrix, BFS/DFS, connected component, topo sort.
- [ ] Làm 2 bài: Number of Islands, Course Schedule.
- [ ] Map sang bài toán thật: tìm cuốc xe gần tọa độ hiện tại của tài xế nhất (Nearest Driver / Shortest Route).

### Thứ 6 — DP nhập môn (2h)
- [ ] Học memoization vs tabulation; Climbing Stairs, House Robber, Coin Change.
- [ ] Viết state transition bằng lời trước khi code; không học mẹo.
- [ ] Ghi bảng dp cho từng bài.

### Thứ 7 — Timed DSA set (5h)
- [ ] 2h: 3 bài Mixed Easy/Medium có timer (array/hashmap/two pointers).
- [ ] 1h: 1 bài Medium tree/graph vừa code vừa giải thích.
- [ ] 1h: review lỗi và pattern chưa thuộc.
- [ ] 1h: cập nhật DSA notes; commit.

## Tuần 15 — Design patterns, HTTP/networking, Linux, security audit

### Thứ 2 — Strategy + Factory + Builder (2h)
- [ ] Học GoF: Strategy, Factory Method, Builder, Singleton (và vì sao hạn chế dùng).
- [ ] Refactor `PricingService` (áp dụng Strategy Pattern: `StandardPricingStrategy`, `SurgePricingStrategy` cho giờ cao điểm) và `NotificationSender` trong Giao Vặt.
- [ ] Ghi khi nào KHÔNG cần pattern; tránh over-engineering.

### Thứ 3 — Observer + Template Method + Adapter (2h)
- [ ] Học Observer (Spring events), Template Method, Adapter, Decorator.
- [ ] Code domain event `OrderCreatedEvent`, `OrderAcceptedEvent` dùng `ApplicationEventPublisher`.
- [ ] Test listener chạy sau commit; ghi trade-off sync/async.

### Thứ 4 — HTTP/networking (2h)
- [ ] Học DNS, TCP/TLS handshake, HTTP/1.1 vs 2, keep-alive, CORS, cookie vs token.
- [ ] Dùng `curl -v` trace một request Giao Vặt; đọc certificate chain.
- [ ] Vẽ đường đi request: client → load balancer → app → DB.

### Thứ 5 — Linux shell + server log (2h)
- [ ] Học `grep`, `tail -f`, `journalctl`, `systemctl`, `ps/top`, `lsof` port.
- [ ] Tìm lỗi trong log server bằng grep + context; kill process chiếm port.
- [ ] Ghi 5 câu lệnh hay dùng vào runbook.

### Thứ 6 — OWASP self-audit (2h)
- [ ] Học OWASP Top 10; lập checklist từng mục với Giao Vặt.
- [ ] Tự tìm: injection, broken auth, BOLA/IDOR (tài xế A sửa đơn của tài xế B), misconfig, thiếu rate limit; sửa ít nhất 2 finding.
- [ ] Ghi finding + fix vào README security.

### Thứ 7 — Interview drill (5h)
- [ ] 2h: mock 20 câu design patterns + HTTP/networking.
- [ ] 1h: giải thích 3 pattern bằng code Giao Vặt không nhìn slide.
- [ ] 1h: SQL JOIN/aggregate 10 câu.
- [ ] 1h: index/transaction/deadlock 5 câu + `EXPLAIN` query queue Giao Vặt.

## Tuần 16 — Project polish + English

### Thứ 2 — API polish (2h)
- [ ] Chuẩn hóa naming, status code, pagination response cho queue đơn.
- [ ] Cập nhật OpenAPI examples.
- [ ] Test backward compatibility trong phạm vi project.

### Thứ 3 — README/architecture (2h)
- [ ] Vẽ architecture diagram request flow: Khách tạo đơn $\rightarrow$ Queue Redis $\rightarrow$ Tài xế pick $\rightarrow$ SSE notification.
- [ ] Viết ERD và trade-offs (vì sao dùng Optimistic Lock cho Pick Order).
- [ ] Viết “Known limitations”.

### Thứ 4 — English introduction (2h)
- [ ] Viết self-introduction 90 giây.
- [ ] Ghi âm 3 lần; sửa pronunciation/grammar.
- [ ] Học từ vựng: requirement, estimate, trade-off, incident, root cause.

### Thứ 5 — English project demo (2h)
- [ ] Trình bày Giao Vặt 5 phút bằng English.
- [ ] Giải thích một bug và cách fix 3 phút (ví dụ: race condition khi 2 tài xế cùng pick 1 đơn).
- [ ] Tự trả lời: "how do you prevent double-picking orders?", "how is the in-memory queue designed with Redis?".

### Thứ 6 — CV (2h)
- [ ] Viết CV English một trang; mô tả output, không bịa kinh nghiệm.
- [ ] Đưa keyword đúng: Java, Spring Boot, REST, Maven, Git, SQL, Docker, CI/CD, Redis, Concurrency Locking, SSE.
- [ ] Soát ATS và lỗi tiếng Anh.

### Thứ 7 — Portfolio release (5h)
- [ ] 2h: fix blocker và deploy.
- [ ] 1h: quay demo.
- [ ] 1h: tag release `giaovat-v1`.
- [ ] 1h: kiểm tra clone → run → test theo README.

## Tuần 17 — Production API Patterns, Real-time & Webhooks

### Thứ 2 — Advanced RESTful & Idempotency Key Pattern (2h)
- [ ] Học chuẩn RESTful nâng cao: chuẩn hóa lỗi HTTP theo RFC 7807 (Problem Details for HTTP APIs), API Versioning qua Header/URL.
- [ ] Học nguyên lý **Idempotent API**: Sự khác biệt giữa GET/PUT/DELETE (vốn idempotent) vs POST (không idempotent).
- [ ] Implement **Idempotency Key Pattern** cho Order Creation API (`POST /api/orders`) và Payment API: nhận header `Idempotency-Key`, dùng Redis lưu trạng thái key (PENDING / COMPLETED) kèm TTL để chống khách bấm đúp hoặc mạng retry tạo nhiều đơn trùng lặp.
- [ ] Test race condition: gửi đồng thời 2 request cùng Idempotency-Key -> chỉ 1 request xử lý tạo đơn, request sau nhận kết quả cache hoặc 409 Conflict.

### Thứ 3 — Webhook Architecture & Security (2h)
- [ ] Học mô hình Webhook: Webhook Publisher vs Webhook Consumer; cơ chế retry với exponential backoff và dead-letter queue (DLQ).
- [ ] Xây dựng Webhook Receiver nhận callback thanh toán (giả lập VNPay/Stripe): xác thực tính toàn vẹn payload bằng chữ ký số HMAC-SHA256 bí mật.
- [ ] Thiết kế Webhook Idempotency: xử lý trường hợp bên thứ 3 gửi lại cùng 1 webhook nhiều lần hoặc gửi out-of-order (sự kiện sau đến trước).
- [ ] Test giả lập: gửi webhook giả mạo chữ ký (phải trả 401/403) và webhook hợp lệ (update trạng thái đơn hàng).

### Thứ 4 — Real-time Web: WebSocket & Server-Sent Events (SSE) (2h)
- [ ] So sánh các cơ chế giao tiếp Client-Server: Short Polling, Long Polling, Server-Sent Events (SSE) và WebSocket (STOMP).
- [ ] Xây dựng tính năng real-time queue & booking alert bằng **Server-Sent Events (`SseEmitter`)** trong Spring Boot:
  - Khi khách tạo đơn mới: Push event `NEW_ORDER_AVAILABLE` tới app của toàn bộ tài xế đang mở queue.
  - Khi 1 tài xế pick cuốc thành công: Push event `ORDER_REMOVED` tới các tài xế khác để ẩn đơn khỏi màn hình, đồng thời push event `DRIVER_ACCEPTED` cho khách hàng.
- [ ] Xử lý quản lý vòng đời SSE connection: timeout, reconnect từ client, heartbeat ping định kỳ, dọn dẹp bộ nhớ khi client disconnect.

### Thứ 5 — Concurrency Control & Database Locking (2h)
- [ ] Phân tích bài toán **Double-Picking / Race Condition** khi 10 tài xế cùng bấm pick 1 đơn hời trong cùng 1 tích tắc.
- [ ] So sánh **Optimistic Locking** (`@Version` trong JPA) vs **Pessimistic Locking** (`PESSIMISTIC_WRITE` / `SELECT ... FOR UPDATE` trong SQL).
- [ ] Code cả 2 giải pháp trên entity `DeliveryOrder`; viết test đa luồng với `CountDownLatch` / `ExecutorService` (10 thread cùng gọi `acceptOrder(orderId)` $\rightarrow$ chỉ duy nhất 1 tài xế nhận thành công, 9 tài xế còn lại nhận lỗi `409 Conflict` hoặc `OptimisticLockException`).

### Thứ 6 — Deadlock Simulation & Resolution Drill (2h)
- [ ] Tạo bài lab Deadlock: viết 2 transaction chạy song song cập nhật chéo tài nguyên (Transaction 1: lock A rồi lock B; Transaction 2: lock B rồi lock A).
- [ ] Quan sát database treo và bắt exception; xem deadlock graph trong log engine database (`SHOW ENGINE INNODB STATUS`).
- [ ] Cấu hình Spring `@Retryable` với exponential backoff để tự động retry khi gặp transient deadlock; chuẩn hóa thứ tự lock tài nguyên để triệt tiêu deadlock.

### Thứ 7 — End-to-End Payment & Notification Lab (5h)
- [ ] 2h: Ghép nối luồng hoàn chỉnh: Khách tạo đơn (kèm Idempotency Key) $\rightarrow$ Đẩy vào Redis Queue $\rightarrow$ Tài xế pick (Optimistic Lock) $\rightarrow$ Update DB $\rightarrow$ Push thông báo SSE cho khách và gỡ đơn khỏi queue của các tài xế khác.
- [ ] 1h: Viết integration tests toàn luồng với Testcontainers và MockMvc.
- [ ] 1h: Viết tài liệu ADR (Architectural Decision Record) về giải pháp Idempotency và Locking đã chọn.
- [ ] 1h: Commit, push code và review checklist tuần.

## Tuần 18 — Fresher gate + bắt đầu apply

### Thứ 2 — Java mock (2h)
- [ ] Mock 30 câu Java Core/OOP/Collections/exception.
- [ ] Sửa 5 lỗ hổng lớn nhất.

### Thứ 3 — Spring mock (2h)
- [ ] Mock DI/MVC/JPA/transaction/Security/testing.
- [ ] Vẽ request flow không nhìn tài liệu.

### Thứ 4 — Project mock (2h)
- [ ] Kể Giao Vặt theo format problem $\rightarrow$ design $\rightarrow$ implementation $\rightarrow$ trade-off $\rightarrow$ result.
- [ ] Trả lời follow-up về race condition khi nhiều tài xế pick cuốc, kiến trúc hàng đợi Redis, xử lý SSE real-time.

### Thứ 5 — English mock (2h)
- [ ] Mock introduction, project, teamwork, failure, learning plan.
- [ ] Ghi âm và chấm: clarity, structure, technical vocabulary.

### Thứ 6 — Application setup (2h)
- [ ] Tạo tracker: company, JD, date, stage, gap, follow-up.
- [ ] Chọn 10 JD Fresher/Junior; map keyword với project.
- [ ] Không ứng tuyển nếu phải bịa kinh nghiệm.
- [ ] Đàm phán cơ bản: tra dải lương Fresher VN, cách trả "expected salary", không khai số thấp hơn dải mình muốn.

### Thứ 7 — Final gate (5h)
- [ ] 2h: full mock Java + Spring + SQL.
- [ ] 1h: full demo.
- [ ] 1h: gửi 3 application chất lượng.
- [ ] 1h: retrospective và lập kế hoạch tháng 5–17.

**Gate Fresher:** clone/run/test được; code CRUD + auth trong 3 giờ; giải thích OOP/collections/SQL/Spring; có project và CI; nói project English cơ bản; hiểu Agile/Jira/Confluence/AI workflow. Đạt gate thì apply, không chờ hoàn hảo.

> Trượt gate: apply intern/Fresher dải thấp hơn (8–12tr) hoặc thực tập có lương; không đứng ngoài thị trường. Đặt lại gate sau 4 tuần bù đúng phần trượt.

---

# GIAI ĐOẠN 3 — THÁNG 5–17
## Junior thực chiến → đủ điều kiện apply Mid Java Software Engineer, mục tiêu 25–30 triệu

> Giai đoạn này ưu tiên kinh nghiệm công ty thật. Mỗi tuần giữ lịch học nhẹ nhưng gắn với task thật. Nếu chưa có job, dùng Giao Vặt như môi trường mô phỏng (on-demand delivery platform) và ghi rõ là personal project.

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

## Tuần 60–63 — Mid system design

- [ ] Tuần 60: design URL shortener; capacity, API, DB, cache.
- [ ] Tuần 61: design notification system; queue, retry, idempotency.
- [ ] Tuần 62: design booking system; availability, locking, consistency; tính capacity bằng số: QPS → số instance → connection pool → chi phí.
- [ ] Tuần 63: trình bày 45 phút; phản biện trade-off; mock system design round.

## Tuần 64–68 — Chuẩn bị nhảy Mid

- [ ] Tuần 64: tổng hợp impact thật: feature, bug, latency, quality, ownership.
- [ ] Tuần 65: viết CV Mid và 5 STAR stories: incident, conflict, deadline, improvement, mentoring.
- [ ] Tuần 66: mock Java/Spring/SQL/system design/English.
- [ ] Tuần 67: đàm phán lương: dải thị trường Mid VN, cách trả expected salary, counter-offer, giữ việc 12–18 tháng trước khi nhảy; luyện 3 kịch bản offer.
- [ ] Tuần 68: apply có chọn lọc; cập nhật gap sau từng interview.

**Gate Mid:** có ít nhất 3 feature end-to-end, 3 bug/root-cause notes, 1 performance improvement có số đo, 1 CI/CD pipeline, 1 ADR/design doc, code review đều, giao tiếp English B2, hiểu microservices/cloud vận hành cơ bản. Đây là năng lực mục tiêu; offer 25–30 triệu còn tùy thị trường và hồ sơ.

---

# GIAI ĐOẠN 4 — 1–2 NĂM TIẾP
## Mid → Senior Software Engineer

> Không học theo danh sách keyword. Mỗi quý chọn một bài toán production có impact, dẫn từ design đến outcome.

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

## Quý 1 — Ownership hệ thống

- [ ] Tuần 1–4: nắm domain, dependency, SLO, cost, security; lập system map; vẽ kiến trúc target (hexagonal/clean) cho module sở hữu.
- [ ] Tuần 5–8: dẫn một RFC; áp dụng tactical DDD (aggregate, value object, domain event, anti-corruption layer) ở module phức tạp nhất; ship phần đầu tiên.
- [ ] Tuần 9–12: đo outcome; hoàn thiện runbook; chia sẻ cho team.

## Quý 2 — Reliability và incident leadership

- [ ] Tuần 13–16: SLI/SLO, error budget, alert quality.
- [ ] Tuần 17–20: incident response, postmortem, follow-up ownership.
- [ ] **Tuần 17–20 phụ:** Chaos engineering — Chaos Mesh/Litmus, failure injection drills.
- [ ] Tuần 21–24: backup/restore hoặc DR drill theo hệ thống thật.
- [ ] **Tuần 23–24 phụ:** Advanced DR — multi-region, RTO/RPO calculation, failover testing.

## Quý 3 — Scale và distributed systems

- [ ] Tuần 25–28: capacity planning bằng số (QPS → instance → pool → cost), partitioning, cache, queue.
- [ ] Tuần 29–32: idempotency, outbox/saga, schema evolution.
- [ ] **Tuần 30–32 phụ:** WebFlux reactive programming, CQRS/Event Sourcing PoC.
- [ ] Tuần 33–36: tracing, profiling, load test, bottleneck remediation.
- [ ] **Tuần 35–36 phụ:** GraalVM native image benchmark so sánh với JVM truyền thống.

## Quý 4 — Platform/cloud và delivery

- [ ] Tuần 37–40: Kubernetes/Helm hoặc platform thực tế của công ty.
- [ ] Tuần 41–44: Terraform/IaC, secrets, deployment strategy.
- [ ] Tuần 45–48: giảm toil, chuẩn hóa pipeline, rollback, operational docs; rà hóa đơn cloud, cắt cost có số đo (FinOps nhẹ).

## Quý 5 — Technical leadership

- [ ] Tuần 49–52: dẫn design review liên team; thuyết phục stakeholder bằng business value (cost/risk/time), không chỉ trade-off kỹ thuật.
- [ ] Tuần 53–56: mentor một kỹ sư; tạo feedback loop.
- [ ] Tuần 57–60: xử lý conflict kỹ thuật bằng dữ liệu; ngồi bàn phỏng vấn: chấm bài, đưa verdict, calibration với manager.

## Quý 6 — Senior evidence

- [ ] Tuần 61–64: hoàn thành một initiative có impact đo được.
- [ ] Tuần 65–68: viết case study architecture/incident/performance.
- [ ] Tuần 69–72: mock Senior interview và calibration với manager/mentor.

## Quý 7–8 — Consolidation

- [ ] Tuần 73–80: duy trì ownership, mentor, design review, incident response.
- [ ] Tuần 81–88: chốt portfolio evidence; cập nhật CV/LinkedIn.
- [ ] Tuần 89–96: đánh giá scope thực tế; apply Senior khi đã có evidence, không chỉ đủ số năm.

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
