<h1 align="center">Hi, I'm Ritesh Sinha 👋</h1>

<h3 align="center">Full-Stack Developer | 5+ Years of Experience</h3>

Full-Stack Developer with 5+ years of experience building high-performance web and mobile products with React, TypeScript, Next.js, and React Native on Node.js and PostgreSQL backends.

## 💻 Languages & Technologies

<p align="center">
  <img src="https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black" alt="JavaScript" />
  <img src="https://img.shields.io/badge/TypeScript-3178C6?style=for-the-badge&logo=typescript&logoColor=white" alt="TypeScript" />
  <img src="https://img.shields.io/badge/React-61DAFB?style=for-the-badge&logo=react&logoColor=black" alt="React" />
  <img src="https://img.shields.io/badge/Next.js-000000?style=for-the-badge&logo=nextdotjs&logoColor=white" alt="Next.js" />
  <img src="https://img.shields.io/badge/Node.js-339933?style=for-the-badge&logo=nodedotjs&logoColor=white" alt="Node.js" />
  <img src="https://img.shields.io/badge/PostgreSQL-4169E1?style=for-the-badge&logo=postgresql&logoColor=white" alt="PostgreSQL" />
</p>

| Area | Technologies |
| --- | --- |
| **Languages** | JavaScript (ES6+), TypeScript, SQL, HTML5, CSS3 |
| **Web & Mobile** | React, Next.js, React Native, Expo, Redux, Context API, Tailwind CSS, shadcn/ui |
| **Geospatial & Visualization** | Deck.gl, MapLibre, amCharts, GeoJSON, GeoParquet, GeoArrow, PMTiles |
| **Backend & APIs** | Node.js, Express, REST APIs, JWT, Auth0, Prisma, Sequelize |
| **Databases & Messaging** | PostgreSQL, MySQL, Redis, RabbitMQ |
| **Testing & Performance** | Jest, React Testing Library, Playwright, k6, Web Workers, streaming file processing |
| **Infrastructure & Monitoring** | Docker, Docker Compose, Nginx, AWS, GCS integrations, CI/CD, Prometheus, Grafana, Pino |

## 🚀 Featured Projects

### ✈️ Flight Booking Microservices

**React · Node.js · Express · MySQL · Sequelize · Redis · RabbitMQ · Prometheus · Grafana**

[Repository](https://github.com/inductionotg/FlightBooking-10x) · [Architecture](https://github.com/inductionotg/FlightBooking-10x/blob/main/docs/architecture.md) · [Project Guide & Demo](https://github.com/inductionotg/FlightBooking-10x#project-demo)

A flight booking application with a React customer/admin interface and five backend services covering authentication, flight search, booking, notifications, and API gateway routing.

- Built flight search, booking, cancellation, durable booking history, and admin catalog workflows with JWT authentication and role-based authorization.
- Implemented **transactional seat reservations, idempotency keys, and durable recovery**. A last-seat concurrency test changed from **20 confirmations for one seat to 1 confirmation and 19 rejections**, with zero inventory drift.
- Added **Redis caching**, five-second TTLs, request coalescing, booking/cancellation invalidation, and bounded database fallback.
- Created a composite route/price index, reducing **rows examined per search from 10,304 to 100** and mean SQL execution from **11.51 ms to 1.02 ms** in recorded local benchmarks.
- Built booking notifications with a **transactional outbox**, durable RabbitMQ queues, duplicate handling, delayed retries, dead-lettering, and SMTP delivery.
- Instrumented services with structured logs, trace propagation, **Prometheus metrics and Grafana dashboards**; used k6, outage tests, and CPU profiling to investigate performance bottlenecks.

### 🛒 OrderFlow — E-Commerce Saga

**React · Tailwind CSS · Node.js · Express · PostgreSQL · Prisma · RabbitMQ · Redis · Docker**

[Repository](https://github.com/inductionotg/ecom) · [Architecture & Saga Flows](https://github.com/inductionotg/ecom/blob/main/docs/ARCHITECTURE.md) · [Docker Setup](https://github.com/inductionotg/ecom/blob/main/docs/DOCKER.md)

An event-driven checkout application that demonstrates coordination across independent Order, Inventory, and Payment services.

- Designed a **choreography-based Saga** for stock reservation, simulated payment, and order confirmation, with inventory compensation when payment fails.
- Stored orders, line items, and the initial **outbox event in one Prisma transaction**, then published pending events through a background relay.
- Implemented conditional SQL updates and **all-or-nothing stock reservations** to handle insufficient inventory without partial holds.
- Added processed-event deduplication, a **dead-letter queue**, correlation IDs, and structured Pino logs for diagnosing asynchronous workflows.
- Built **Redis cache-aside product reads** with five-minute expiry, stock-change invalidation, and PostgreSQL fallback; packaged services with Docker Compose.
- Developed a **React storefront and operations dashboard** with a persistent cart, order-status polling, payment details, revenue metrics, service health, and dead-letter inspection.

### 🛡️ GatewayX — Distributed API Gateway & Rate Limiter

**Node.js · Express · Redis · Lua · PostgreSQL · Prisma · Nginx · Docker**

[Repository](https://github.com/inductionotg/GatewayX) · [Project Guide](https://github.com/inductionotg/GatewayX/blob/main/docs/GUIDE.md)

A custom API gateway that routes, balances, limits, aggregates, and recovers requests across User, Product, and Review services.

- Configured **two gateway instances behind Nginx** and round-robin routing across two product replicas.
- Implemented an **atomic Redis Lua token bucket** with a shared server clock and all-or-nothing admission across user, IP, and authentication buckets.
- Returned **429 with Retry-After** for exhausted budgets and 503 when Redis was unavailable; used verified sessions and trusted proxy configuration for rate-limit identity.
- Built per-instance **circuit breakers** with closed/open/half-open states, bounded timeouts, a single recovery probe, and protection against stale in-flight results.
- Used **Promise.all** for parallel product/review aggregation, returning partial responses during review outages and skipping product replicas with open circuits.
- Implemented **Redis-backed sessions**, login session rotation, logout invalidation, HttpOnly cookies, and scrypt password hashing; demonstrated session continuity and recovery during container outages.

