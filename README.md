### Artem Ukrainskiy

Software engineer and team lead with 15 years of experience. I have worked in product and outsourcing teams, as a developer, tech lead and team lead, on systems where load, latency and cost matter.

[Blog](https://artukrainskiy.github.io/) · [Habr](https://habr.com/ru/users/Ukrainskiy) · art.ukrainskiy@gmail.com

#### What I do

- **High-load backends**: microservice design, splitting monoliths, search, caching, traffic routing and failover.
- **Data and observability**: metrics pipelines, tracing, alerting, analytics on ClickHouse, decisions made from data rather than guesses.
- **Performance**: profiling down to CPU instructions and memory, from application code to native extensions and the language runtime.
- **Leading teams**: architecture, planning, code review, hiring, mentoring, development standards.

![PHP](https://img.shields.io/badge/PHP-777BB4?logo=php&logoColor=white)
![Go](https://img.shields.io/badge/Go-00ADD8?logo=go&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?logo=python&logoColor=white)
![C++](https://img.shields.io/badge/C++-00599C?logo=cplusplus&logoColor=white)
![C](https://img.shields.io/badge/C-A8B9CC?logo=c&logoColor=black)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?logo=typescript&logoColor=white)
![ClickHouse](https://img.shields.io/badge/ClickHouse-FFCC01?logo=clickhouse&logoColor=black)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?logo=postgresql&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-4479A1?logo=mysql&logoColor=white)
![MongoDB](https://img.shields.io/badge/MongoDB-47A248?logo=mongodb&logoColor=white)
![Elasticsearch](https://img.shields.io/badge/Elasticsearch-005571?logo=elasticsearch&logoColor=white)
![Kafka](https://img.shields.io/badge/Kafka-231F20?logo=apachekafka&logoColor=white)
![RabbitMQ](https://img.shields.io/badge/RabbitMQ-FF6600?logo=rabbitmq&logoColor=white)
![Laravel](https://img.shields.io/badge/Laravel-FF2D20?logo=laravel&logoColor=white)

#### Open source

**[php-src](https://github.com/php/php-src)** — performance of the PHP interpreter: string functions, `json_encode()`, `htmlspecialchars()`, CSV, the compiler. Every change comes with measurements on Intel and AMD with several compilers, a byte-for-byte comparison with master, and the cases where it gets slower. I also review other contributors' performance PRs with the same measurements.

**[php-src-bench](https://github.com/ArtUkrainskiy/php-src-bench)** — the A/B benchmark tool behind that work, with a public report for every change: what was compared, full tables, how the output was verified, commands to reproduce.

| PR | Change | Measured |
|---|---|---|
| [![#24283](https://img.shields.io/github/pulls/detail/state/php/php-src/24283?label=%2324283&style=for-the-badge)](https://github.com/php/php-src/pull/24283) | `json_encode()`: decode valid UTF-8 inline | non-ASCII text 0.68–0.91 of master's cycles, 6 compiler/CPU configs; with GCC 13/14 on Intel some ASCII inputs up to 1.20 ([report](https://github.com/ArtUkrainskiy/php-src-bench/tree/main/reports/json-encode-utf8-inline)) |
| [![#24207](https://img.shields.io/github/pulls/detail/state/php/php-src/24207?label=%2324207&style=for-the-badge)](https://github.com/php/php-src/pull/24207) | `php_mblen()` without `mbrlen()` for ASCII | `fgetcsv()` 4,210 → 500 ns per row ([report](https://github.com/ArtUkrainskiy/php-src-bench/tree/main/reports/fgetcsv-mblen)) |
| [![#24198](https://img.shields.io/github/pulls/detail/state/php/php-src/24198?label=%2324198&style=for-the-badge)](https://github.com/php/php-src/pull/24198) | `#[\Deprecated]` without constructing the attribute | 5,016 → 2,778 instructions per deprecated call ([report](https://github.com/ArtUkrainskiy/php-src-bench/tree/main/reports/deprecation-cost)) |
| [![#24180](https://img.shields.io/github/pulls/detail/state/php/php-src/24180?label=%2324180&style=for-the-badge)](https://github.com/php/php-src/pull/24180) | `[$a, $b] = [$b, $a]` without building the array | 922 → 523 instructions per swap ([report](https://github.com/ArtUkrainskiy/php-src-bench/tree/main/reports/list-assign-from-array-literal)) |
| [![#24145](https://img.shields.io/github/pulls/detail/state/php/php-src/24145?label=%2324145&style=for-the-badge)](https://github.com/php/php-src/pull/24145) | ASCII fast path in `htmlspecialchars()` | English text 1.7× faster (64 KB), Russian 1.2–1.5× ([report](https://github.com/ArtUkrainskiy/php-src-bench/tree/main/reports/htmlspecialchars-ascii-fast-path)) |
| [![#24142](https://img.shields.io/github/pulls/detail/state/php/php-src/24142?label=%2324142&style=for-the-badge)](https://github.com/php/php-src/pull/24142) | `html_entity_decode()`: stop at the first non-name byte | a string of `&` 3.5× faster; `&param=` URLs in text up to 1.07× slower |

Numbers for #24198 and #24180 are instructions on an Intel i7-13700H; the reports have the full tables, machines and compilers.

#### Writing

- [json_encode() in php-src, autumn 2026: where the time goes and what is on the table](https://artukrainskiy.github.io/posts/json-encode-utf8-autumn-2026/)
- [php-src's benchmark CI, read as a history](https://github.com/ArtUkrainskiy/php-src-bench/tree/main/reports/php-benchmark-history) — 7,024 master commits of callgrind results, plotted.
