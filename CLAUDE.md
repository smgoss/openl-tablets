# Project Guide: OpenL Tablets (VividCloud Modernization Pilot)

## Business Domain & System Role
- **Domain:** Insurance Business Rules Management System (BRMS) & Decision Rating Engine.
- **Core Capabilities:** Excel/Table-based rule modeling, rule compilation to Java bytecode, decision tables, rating algorithms, claims/underwriting policy execution, REST web services.
- **Upstream:** EIS Group (`https://eisgroup.com`) / OpenL Tablets.
- **License:** LGPL-3.0.

## Build & Test Instructions
- **Java Target:** Java 21 LTS (`<release>21</release>`).
- **Build Core:** `mvn clean compile -DskipTests`
- **Run Unit Tests (Fast):** `mvn test -DskipTestsForQuick=true`
- **Run Single Module Test:** `mvn test -pl DEV/org.openl.rules -Dtest=SomeTest`
- **Run Specific Test:** `mvn test -Dtest=*Rating*Test`

## Module Layout
- `DEV/`: Core rules engine, compiler, syntax trees, type systems, and bytecode generators (`org.openl.core`, `org.openl.rules`).
- `STUDIO/`: Web-based rules editor and repository management (Java backend + TypeScript frontend).
- `WSFrontend/`: Rule deployment, REST/OpenAPI endpoint generation, and runtime execution.
- `DEMO/`: Reference tutorials, rating templates, and sample rule models.
- `Util/`: OpenAPI parser, Excel builder, OpenTelemetry, and Maven plugin.

## Engineering Standards & Agent Guardrails
- **Minimal, Cohesive Diffs:** Do not refactor unrelated modules or formatting. Confine edits to the exact files required for the task.
- **No Test Cheating:** Never comment out assertions, remove `@Test`, or introduce stub implementations (`return null; // TODO`).
- **Protected Paths:** Never edit root CI workflows, license headers, `.env` files, or git configuration.
