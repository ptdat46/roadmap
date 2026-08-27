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

**Dự án chính: StayHub** — Multi-tenant SaaS Platform cho Homestay
- **Scope:** Platform cung cấp hệ thống quản lý homestay cho nhiều tenant (homestay owner)
- **Multi-tenancy:** Mỗi tenant có **database riêng** (separate DB per tenant), cô lập hoàn toàn
- **Template system:** Cung cấp nhiều template homepage, mỗi tenant chọn và customize giao diện riêng
- **Core features:** Tenant onboarding, template selection, brand-level analytics, cross-tenant reporting
- **Architecture:** Monolith ban đầu với dynamic datasource routing, thiết kế sẵn cho microservices

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

### Thứ 6 — Debugging (2h)
- [ ] Dùng breakpoint, step over/into, evaluate expression, exception breakpoint.
- [ ] Sửa 3 bug cố ý: null, off-by-one, mutable state.
- [ ] Ghi root cause, fix, regression test.

### Thứ 7 — Java Core assessment (5h)
- [ ] 2h: làm bài test Java Core giới hạn thời gian.
- [ ] 1h: sửa bài sai.
- [ ] 1h: làm 3 bài DSA.
- [ ] 1h: chốt checklist và tag `java-core-ready`.

## Tuần 6 — Spring Core + Spring Boot

### Thứ 2 — IoC/DI (2h)
- [ ] Học IoC container, bean, constructor injection, component scan.
- [ ] Tạo Spring Boot app bằng Spring Initializr.
- [ ] Code hai implementation của `PricingService`; inject bằng `@Qualifier`.

### Thứ 3 — Configuration (2h)
- [ ] Học `@Configuration`, `@Bean`, profile, config properties, environment variable.
- [ ] Tạo `application-local.yml` và `application-test.yml`.
- [ ] Kiểm tra secret không nằm trong Git.

### Thứ 4 — Spring MVC (2h)
- [ ] Học `@RestController`, mapping, path variable, request param, request body.
- [ ] Viết `TenantController` GET/POST (quản lý tenant).
- [ ] Test request bằng curl/Postman.

### Thứ 5 — DTO + validation (2h)
- [ ] Học request DTO, response DTO, `@Valid`, constraints, enum.
- [ ] Thêm create/update tenant validation.
- [ ] Test 400 response cho payload sai.

### Thứ 6 — Service/repository layering (2h)
- [ ] Học Controller–Service–Repository; transaction ở service boundary.
- [ ] Refactor Tenant API thành 3 layer.
- [ ] Viết service unit test với fake repository.

### Thứ 7 — REST API lab (5h)
- [ ] 2h: hoàn thiện Tenant CRUD in-memory.
- [ ] 1h: global exception handler.
- [ ] 1h: OpenAPI dependency và endpoint docs.
- [ ] 1h: README API examples, commit.

## Tuần 7 — SQL + JPA/Hibernate

### Thứ 2 — Relational design (2h)
- [ ] Học table, PK/FK, normalization 1NF–3NF, constraint.
- [ ] Thiết kế ERD StayHub core: `Tenant`, `TenantAdmin`, `Template`, `TenantConfig`.
- [ ] Design separate DB per tenant: central DB quản lý tenants, mỗi tenant có DB riêng chứa Room/Booking.
- [ ] Viết migration V1 cho central DB bằng Flyway.

### Thứ 3 — SQL CRUD + JOIN (2h)
- [ ] Học INSERT/UPDATE/DELETE/SELECT, INNER/LEFT JOIN.
- [ ] Viết 10 query cho StayHub.
- [ ] Seed data; kiểm tra foreign key và duplicate.

### Thứ 4 — JPA entity/repository (2h)
- [ ] Học `@Entity`, ID generation, `JpaRepository`, query method.
- [ ] Mapping `Tenant` và `TenantAdmin`.
- [ ] Viết repository test với MySQL/PostgreSQL container nếu có thể.

### Thứ 5 — Relationships (2h)
- [ ] Học `@ManyToOne`, `@OneToMany`, owning side, cascade, fetch.
- [ ] Mapping `Tenant`–`Template`–`TenantConfig`.
- [ ] Test persist, find, delete; tránh cascade nguy hiểm.

### Thứ 6 — Transactions + N+1 (2h)
- [ ] Học `@Transactional`, lazy loading, N+1, JOIN FETCH, EntityGraph.
- [ ] Tạo N+1 bằng SQL logging; sửa và ghi số query trước/sau.
- [ ] Test rollback khi tạo tenant fail.

### Thứ 7 — Chuyển Tenant API sang DB (5h)
- [ ] 2h: repository + service + DTO + MapStruct hoặc mapping thủ công.
- [ ] 1h: pagination/sorting/filter.
- [ ] 1h: integration tests.
- [ ] 1h: ERD, migration, README, commit.

## Tuần 8 — Project v0 + gate

### Thứ 2 — Tenant onboarding + DB provisioning (2h)
- [ ] Code create/register new homestay tenant.
- [ ] Auto-provision database riêng cho tenant mới (dynamic datasource).
- [ ] Assign tenant admin, setup tenant config (currency, timezone, template).
- [ ] Test tenant isolation: admin A không xem được data của admin B.

### Thứ 3 — Error handling + API quality (2h)
- [ ] Chuẩn hóa error code, status, timestamp, path, validation errors.
- [ ] Thêm sorting/filtering/pagination cho listing.
- [ ] Cập nhật OpenAPI.

### Thứ 4 — Integration test (2h)
- [ ] Viết test controller bằng MockMvc.
- [ ] Viết test database transaction và migration.
- [ ] Chạy toàn bộ `mvn test`; sửa flaky test.

### Thứ 5 — Refactor + performance (2h)
- [ ] Review SOLID, naming, package, duplicate logic.
- [ ] Chạy `EXPLAIN` query tenant; thêm index hợp lý.
- [ ] Ghi benchmark trước/sau.

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

**Mục tiêu:** StayHub v1 là multi-tenant platform với brand management, tenant onboarding, revenue aggregation, có auth, test, Docker, CI, deploy, tài liệu. Sau tuần 18 bắt đầu apply, không chờ học Senior.

## Tuần 9 — Spring Security + password/JWT

### Thứ 2 — Security fundamentals (2h)
- [ ] Học authentication, authorization, filter chain, principal, authority.
- [ ] Thêm Spring Security; phân biệt Platform Admin vs Tenant Admin roles.
- [ ] Implement tenant context từ JWT token (tenant_id → datasource routing).
- [ ] Test endpoint public/private; tenant isolation ở datasource level.

### Thứ 3 — Password (2h)
- [ ] Học password hashing, BCrypt, credential flow.
- [ ] Tạo User/Role schema và migration.
- [ ] Test register: duplicate email, password yếu, password không lưu plain text.

### Thứ 4 — Login JWT (2h)
- [ ] Học JWT header/payload/signature, expiry, access token.
- [ ] Code login trả access token.
- [ ] Test token hợp lệ, sai signature, hết hạn.

### Thứ 5 — Authorization (2h)
- [ ] Học RBAC và method security.
- [ ] Brand Admin: quản lý toàn bộ homestays; Tenant Admin: chỉ quản lý homestay của mình.
- [ ] Test tenant isolation: Tenant Admin A không xem được data của Tenant Admin B.

### Thứ 6 — Refresh/logout (2h)
- [ ] Học refresh token rotation và revoke cơ bản.
- [ ] Code refresh/logout; secret từ environment.
- [ ] Ghi threat model ngắn.

### Thứ 7 — Auth integration (5h)
- [ ] 2h: hoàn thiện auth flow.
- [ ] 1h: integration tests.
- [ ] 1h: CORS/SameSite/CSRF decision cho API.
- [ ] 1h: README security.

## Tuần 10 — Dynamic datasource + Template system

### Thứ 2 — Dynamic datasource routing (2h)
- [ ] Implement AbstractRoutingDataSource để route đến DB của tenant dựa trên JWT.
- [ ] Test: request với tenant_A token → query DB tenant_A, không leak sang tenant_B.
- [ ] Handle edge case: tenant DB chưa tồn tại, connection pool per tenant.

### Thứ 3 — Template system (2h)
- [ ] Design template entity: `Template` (id, name, css, html layout, config schema).
- [ ] Code API: list templates, assign template cho tenant, customize template config.
- [ ] Test: tenant A thay đổi template không ảnh hưởng tenant B.

### Thứ 4 — Redis basics (2h)
- [ ] Học key/value, TTL, cache-aside, invalidation.
- [ ] Chạy Redis bằng Docker Compose.
- [ ] Cache tenant config/template.

### Thứ 5 — Cache correctness (2h)
- [ ] Invalidate cache sau create/update/delete tenant.
- [ ] Test stale data và cache miss.
- [ ] Ghi khi không nên cache.

### Thứ 6 — Rate limit + security (2h)
- [ ] Học rate-limit concept; dùng giải pháp đơn giản phù hợp project.
- [ ] Giới hạn login hoặc tenant onboarding API.
- [ ] Không lưu token/password trong log.

### Thứ 7 — Reliability lab (5h)
- [ ] 2h: hoàn thiện tenant provisioning.
- [ ] 1h: cache test.
- [ ] 1h: load 20 request và ghi latency đơn giản.
- [ ] 1h: root-cause note.

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
- [ ] Lập test matrix cho Tenant/Auth/Template.
- [ ] Bỏ test trùng hoặc test implementation detail.

### Thứ 3 — Testcontainers/MockMvc (2h)
- [ ] Chạy MySQL/PostgreSQL thật trong Testcontainers.
- [ ] Viết repository + controller integration tests.
- [ ] Sửa test isolation.

### Thứ 4 — Logging/observability (2h)
- [ ] Structured logging, log level, correlation ID.
- [ ] Thêm request ID và exception log không lộ secret.
- [ ] Dùng Actuator health/info/metrics cơ bản.

### Thứ 5 — Performance (2h)
- [ ] Đo query booking bằng `EXPLAIN`.
- [ ] Kiểm tra N+1, pagination, index, connection pool.
- [ ] Ghi before/after; không claim tối ưu nếu không đo.

### Thứ 6 — Bug hunt (2h)
- [ ] Tạo hoặc nhận 5 bug: validation, auth, tenant isolation, template config, stale cache.
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
- [ ] Viết 1 epic StayHub và 8 user stories.
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
- [ ] Viết ADR chọn monolith, MySQL/PostgreSQL, JWT.
- [ ] Viết runbook start/test/rollback.

### Thứ 6 — AI coding assistant (2h)
- [ ] Chọn Copilot, Cursor hoặc Codeium; dùng cho một endpoint và test.
- [ ] Lưu prompt, generated diff, review comments, test output.
- [ ] Cố ý kiểm tra hallucinated API, security flaw, missing edge case.

### Thứ 7 — Review workflow (5h)
- [ ] 2h: tạo PR cho feature template customization hoặc tenant billing.
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
- [ ] Map sang bài toán thật: gợi ý room cùng khu vực.

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
- [ ] Refactor `PricingService`/`NotificationSender` trong StayHub sang Strategy.
- [ ] Ghi khi nào KHÔNG cần pattern; tránh over-engineering.

### Thứ 3 — Observer + Template Method + Adapter (2h)
- [ ] Học Observer (Spring events), Template Method, Adapter, Decorator.
- [ ] Code domain event `TenantCreated` dùng `ApplicationEventPublisher`.
- [ ] Test listener chạy sau commit; ghi trade-off sync/async.

### Thứ 4 — HTTP/networking (2h)
- [ ] Học DNS, TCP/TLS handshake, HTTP/1.1 vs 2, keep-alive, CORS, cookie vs token.
- [ ] Dùng `curl -v` trace một request StayHub; đọc certificate chain.
- [ ] Vẽ đường đi request: client → load balancer → app → DB.

### Thứ 5 — Linux shell + server log (2h)
- [ ] Học `grep`, `tail -f`, `journalctl`, `systemctl`, `ps/top`, `lsof` port.
- [ ] Tìm lỗi trong log server bằng grep + context; kill process chiếm port.
- [ ] Ghi 5 câu lệnh hay dùng vào runbook.

### Thứ 6 — OWASP self-audit (2h)
- [ ] Học OWASP Top 10; lập checklist từng mục với StayHub.
- [ ] Tự tìm: injection, broken auth, IDOR, misconfig, XSS; sửa ít nhất 2 finding.
- [ ] Ghi finding + fix vào README security.

### Thứ 7 — Interview drill (5h)
- [ ] 2h: mock 20 câu design patterns + HTTP/networking.
- [ ] 1h: giải thích 3 pattern bằng code StayHub không nhìn slide.
- [ ] 1h: SQL JOIN/aggregate 10 câu.
- [ ] 1h: index/transaction/deadlock 5 câu + `EXPLAIN` một query StayHub.

## Tuần 16 — Project polish + English

### Thứ 2 — API polish (2h)
- [ ] Chuẩn hóa naming, status code, pagination response.
- [ ] Cập nhật OpenAPI examples.
- [ ] Test backward compatibility trong phạm vi project.

### Thứ 3 — README/architecture (2h)
- [ ] Vẽ architecture diagram request flow.
- [ ] Viết ERD và trade-offs.
- [ ] Viết “Known limitations”.

### Thứ 4 — English introduction (2h)
- [ ] Viết self-introduction 90 giây.
- [ ] Ghi âm 3 lần; sửa pronunciation/grammar.
- [ ] Học từ vựng: requirement, estimate, trade-off, incident, root cause.

### Thứ 5 — English project demo (2h)
- [ ] Trình bày StayHub 5 phút bằng English.
- [ ] Giải thích một bug và cách fix 3 phút.
- [ ] Tự trả lời "why separate DB per tenant?", "how implement dynamic datasource?".

### Thứ 6 — CV (2h)
- [ ] Viết CV English một trang; mô tả output, không bịa kinh nghiệm.
- [ ] Đưa keyword đúng: Java, Spring Boot, REST, Maven, Git, SQL, Docker, CI/CD, testing.
- [ ] Soát ATS và lỗi tiếng Anh.

### Thứ 7 — Portfolio release (5h)
- [ ] 2h: fix blocker và deploy.
- [ ] 1h: quay demo.
- [ ] 1h: tag release `stayhub-v1`.
- [ ] 1h: kiểm tra clone → run → test theo README.

## Tuần 18 — Fresher gate + bắt đầu apply

### Thứ 2 — Java mock (2h)
- [ ] Mock 30 câu Java Core/OOP/Collections/exception.
- [ ] Sửa 5 lỗ hổng lớn nhất.

### Thứ 3 — Spring mock (2h)
- [ ] Mock DI/MVC/JPA/transaction/Security/testing.
- [ ] Vẽ request flow không nhìn tài liệu.

### Thứ 4 — Project mock (2h)
- [ ] Kể StayHub theo format problem → design → implementation → trade-off → result.
- [ ] Trả lời follow-up về concurrency, DB, security.

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

> Giai đoạn này ưu tiên kinh nghiệm công ty thật. Mỗi tuần giữ lịch học nhẹ nhưng gắn với task thật. Nếu chưa có job, dùng StayHub như môi trường mô phỏng (multi-tenant SaaS platform) và ghi rõ là personal project.

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

- [ ] Tuần 43: bounded context cho StayHub (Tenant Service, Template Service, Billing Service, Analytics Service); vẽ service boundary.
- [ ] Tuần 44: REST inter-service, timeout, retry, circuit breaker, idempotency.
- [ ] Tuần 45: Kafka/RabbitMQ: producer, consumer, group, retry, DLQ, ordering.
- [ ] Tuần 46: implement event flow (TenantProvisioned, TemplateChanged, BillingEvent); test duplicate delivery và failure.
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
