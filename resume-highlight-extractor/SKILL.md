---
name: "resume-highlight-extractor"
description: "Analyzes Java backend project code to extract technical highlights and generates resume-ready bullet points using the STAR method. Invoke when user asks for resume help, project summaries, or code highlights for Java projects."
---

# Java Backend Project Highlight Extractor

This skill helps Java backend engineers extract technical highlights from their codebase and format them for a resume.

## Workflow

1.  **Context Gathering**:
    -   Ask the user which project or directory to analyze (if not current).
    -   Ask the user for their target role level (Junior, Senior, Lead/Architect).
    -   Ask for specific tech stack focus (e.g., "Focus on Spring Cloud and High Concurrency").

2.  **Codebase Analysis (Java Focused)**:
    -   Scan the codebase for "High Value" indicators:
        -   **Concurrency & Async**: `CompletableFuture`, `ExecutorService`, custom ThreadPools, `@Async`, `ReentrantLock`, CAS operations, `ThreadLocal` usage.
        -   **Performance & Tuning**: Custom JVM flags, HikariCP/Druid config, Caffeine/Guava local cache, Redis caching strategies (annotations or `RedisTemplate`), Database indexing/sharding logic.
        -   **Spring Ecosystem**: Custom AOP aspects (annotations), Event listeners (`@EventListener`), Bean lifecycle hooks (`InitializingBean`, `@PostConstruct`), Spring Cloud components (Feign, Gateway, Sentinel/Resilience4j).
        -   **Complex Business Logic**: State machines, Rule engines (Drools/EasyRules), Design Patterns (Strategy, Factory, Chain of Responsibility, Template Method).
        -   **Architecture & Reliability**: Distributed locks (Redisson/Zookeeper), Idempotency mechanisms, Distributed transactions (Seata/Saga), Message Queue consumers (RocketMQ/Kafka/RabbitMQ).
        -   **DevOps & Tools**: Dockerfiles (multi-stage builds), K8s configs, CI/CD pipelines, Prometheus/Grafana integration.

3.  **Highlight Generation (STAR Method)**:
    -   For each identified highlight, draft a bullet point using the STAR method:
        -   **Situation**: What was the problem? (e.g., "Order processing system faced thread exhaustion during peak traffic...")
        -   **Task**: What needed to be done? (e.g., "Optimize the asynchronous task execution model...")
        -   **Action**: What did you do? (Technical details! e.g., "Refactored to use `CompletableFuture` with a custom `ThreadPoolExecutor` and implemented non-blocking I/O...")
        -   **Result**: What was the outcome? (Quantify! e.g., "Reduced p99 latency by 200ms and increased throughput by 3x under high load.")

4.  **Output Format**:
    -   Present the findings in a clear, Markdown-formatted list.
    -   Group by category (e.g., "High Concurrency & Performance", "Distributed Architecture", "Core Business Logic").
    -   Provide a "Resume Ready" section with polished bullet points.
    -   Refer to `references/java_backend_keywords.md` for enhancing vocabulary.

## Tips for Best Results

-   **Quantify**: Estimate numbers (QPS, TPS, Latency, Heap Size).
-   **Java Terminology**: Use precise terms like *GC Tuning*, *Double-Checked Locking*, *Aspect-Oriented Programming*, *Bean Lifecycle*.
-   **Action Verbs**: *Architected, Engineered, Tuned, Decoupled, Orchestrated*.
