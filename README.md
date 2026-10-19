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

**[php-src](https://github.com/php/php-src)** — performance of the PHP interpreter: string functions, `json_encode()`, `htmlspecialchars()`, CSV, the compiler, and threaded (ZTS) builds. Every change comes with measurements on Intel and AMD with several compilers, a byte-for-byte comparison with master, and the cases where it gets slower. I also review other contributors' performance PRs with the same measurements.

**[php-src-bench](https://github.com/ArtUkrainskiy/php-src-bench)** — the A/B benchmark tool behind that work, with a public report for every change: what was compared, full tables, how the output was verified, commands to reproduce.

**[web-request-cost](https://github.com/ArtUkrainskiy/web-request-cost)** — CPU and memory per request of 12 web stacks (PHP-FPM, FrankenPHP, RoadRunner, Swoole, Go, Node.js, .NET, Java and others) on PostgreSQL and MySQL, with every raw record.

#### Pull requests

| PR | Change | Measured |
|---|---|---|
| [![#24448](https://img.shields.io/github/pulls/detail/state/php/php-src/24448?label=%2324448&style=for-the-badge)](https://github.com/php/php-src/pull/24448) | mysqlnd: relaxed atomics instead of a mutex for statistics in ZTS builds | FrankenPHP + MySQL, 16 threads: 10–47% less CPU per request, depending on the cores the threads run on; statistics cost 12–91% before, 0.6–1.4% after ([report](https://github.com/ArtUkrainskiy/php-src-bench/tree/main/reports/mysqlnd-zts-stats)) |
| [![#24283](https://img.shields.io/github/pulls/detail/state/php/php-src/24283?label=%2324283&style=for-the-badge)](https://github.com/php/php-src/pull/24283) | `json_encode()`: decode valid UTF-8 inline | non-ASCII text 9–32% fewer cycles, 6 compiler/CPU configs; with GCC 13/14 on Intel some ASCII inputs up to 20% more ([report](https://github.com/ArtUkrainskiy/php-src-bench/tree/main/reports/json-encode-utf8-inline)) |
| [![#24207](https://img.shields.io/github/pulls/detail/state/php/php-src/24207?label=%2324207&style=for-the-badge)](https://github.com/php/php-src/pull/24207) | `php_mblen()` without `mbrlen()` for ASCII | `fgetcsv()` 4,210 → 500 ns per row ([report](https://github.com/ArtUkrainskiy/php-src-bench/tree/main/reports/fgetcsv-mblen)) |
| [![#24198](https://img.shields.io/github/pulls/detail/state/php/php-src/24198?label=%2324198&style=for-the-badge)](https://github.com/php/php-src/pull/24198) | `#[\Deprecated]` without constructing the attribute | 5,016 → 2,778 instructions per deprecated call ([report](https://github.com/ArtUkrainskiy/php-src-bench/tree/main/reports/deprecation-cost)) |
| [![#24180](https://img.shields.io/github/pulls/detail/state/php/php-src/24180?label=%2324180&style=for-the-badge)](https://github.com/php/php-src/pull/24180) | `[$a, $b] = [$b, $a]` without building the array | 922 → 523 instructions per swap ([report](https://github.com/ArtUkrainskiy/php-src-bench/tree/main/reports/list-assign-from-array-literal)) |
| [![#24145](https://img.shields.io/github/pulls/detail/state/php/php-src/24145?label=%2324145&style=for-the-badge)](https://github.com/php/php-src/pull/24145) | ASCII fast path in `htmlspecialchars()` | 41–89% fewer cycles where something has to be encoded (English text, HTML, Markdown, JavaScript) ([report](https://github.com/ArtUkrainskiy/php-src-bench/tree/main/reports/htmlspecialchars-ascii-fast-path)) |
| [![#24142](https://img.shields.io/github/pulls/detail/state/php/php-src/24142?label=%2324142&style=for-the-badge)](https://github.com/php/php-src/pull/24142) | `html_entity_decode()`: stop at the first non-name byte | a string of `&` 3.5× faster; `&param=` URLs in text up to 7% slower |

Numbers for #24198 and #24180 are instructions on an Intel i7-13700H, #24448 is on an AMD Ryzen 9 5950X; the reports have the full tables, machines and compilers.

#### Issues

| Issue | Found | Measured |
|---|---|---|
| [![#24447](https://img.shields.io/github/issues/detail/state/php/php-src/24447?label=%2324447&style=for-the-badge)](https://github.com/php/php-src/issues/24447) | mysqlnd takes a process-wide mutex on every statistics update in ZTS builds (FrankenPHP, threaded Apache) | FrankenPHP + MySQL: +7–32% CPU per request depending on the load, up to +91% depending on where the threads run; fix in #24448 ([write-up](https://artukrainskiy.github.io/posts/mysqlnd-zts-statistics/)) |
| [![#24191](https://img.shields.io/github/issues/detail/state/php/php-src/24191?label=%2324191&style=for-the-badge)](https://github.com/php/php-src/issues/24191) | a call to a `#[\Deprecated]` function constructs the attribute even when `E_DEPRECATED` is filtered | about 5,000 instructions per call; fix in #24198 |
| [![#24183](https://img.shields.io/github/issues/detail/state/php/php-src/24183?label=%2324183&style=for-the-badge)](https://github.com/php/php-src/issues/24183) | the benchmark CI builds Symfony Demo without ext-intl | 18% of the measured request is a polyfill |

#### Reviewed and measured

Performance PRs by other contributors, measured on current master with GCC 13.3, GCC 14.2, clang 18.1 and clang 20.1 (Intel i7-13700H, the flags of the official Docker image), with the output compared to master. What the measurements showed:

| PR | Change | Result |
|---|---|---|
| [![#24080](https://img.shields.io/github/pulls/detail/state/php/php-src/24080?label=%2324080&style=for-the-badge)](https://github.com/php/php-src/pull/24080) | `mb_substr()` on valid UTF-8 | 10–98% fewer cycles in nine languages, depending on bytes per character and position; the first version returned different results for UTF-8-Mobile encodings, fixed in the PR with the suggested change |
| [![#23189](https://img.shields.io/github/pulls/detail/state/php/php-src/23189?label=%2323189&style=for-the-badge)](https://github.com/php/php-src/pull/23189) | `var_export()` without temporary strings | 15–68% fewer cycles on small and medium values; on 32-bit builds the escaped length overflowed and `var_export()` crashed; long strings got slower; a one-pass variant was faster than master in every case measured ([report](https://github.com/ArtUkrainskiy/php-src-bench/tree/main/reports/pr-23189-var-export)) |
| [![#23789](https://img.shields.io/github/pulls/detail/state/php/php-src/23789?label=%2323789&style=for-the-badge)](https://github.com/php/php-src/pull/23789) | SSE2/NEON `bin2hex()`/`hex2bin()` | `hex2bin()` returned wrong bytes on big-endian AArch64, two-line fix; short inputs 1–4% more cycles ([report](https://github.com/ArtUkrainskiy/php-src-bench/tree/main/reports/pr-23789-bin2hex-hex2bin)) |
| [![#24188](https://img.shields.io/github/pulls/detail/state/php/php-src/24188?label=%2324188&style=for-the-badge)](https://github.com/php/php-src/pull/24188) | `hash_pbkdf2()` with precomputed HMAC states | 43–53% fewer cycles at 1,000 iterations (35% for whirlpool), 0–5% more at 1 iteration; the hash contexts that hold the key should be wiped before freeing |
| [![#23961](https://img.shields.io/github/pulls/detail/state/php/php-src/23961?label=%2323961&style=for-the-badge)](https://github.com/php/php-src/pull/23961) | charset lookup of the HTML functions, UTF-8 first | short UTF-8 strings 18–27% fewer cycles on top of #23957; with clang 18 `"MacRoman"` +35% cycles ([report](https://github.com/ArtUkrainskiy/php-src-bench/tree/main/reports/pr-23961-html-charset)) |
| [![#24157](https://img.shields.io/github/pulls/detail/state/php/php-src/24157?label=%2324157&style=for-the-badge)](https://github.com/php/php-src/pull/24157) | `array_push()` of several values in bulk | 9–38% fewer cycles for three or more values; three mutations passed the tests, two short tests suggested that catch them |
| [![#23517](https://img.shields.io/github/pulls/detail/state/php/php-src/23517?label=%2323517&style=for-the-badge)](https://github.com/php/php-src/pull/23517) | `array_shift()` with one `memmove()` | draining a queue of 1,000 ints 82–84% fewer cycles |
| [![#22648](https://img.shields.io/github/pulls/detail/state/php/php-src/22648?label=%2322648&style=for-the-badge)](https://github.com/php/php-src/pull/22648) | `array_diff()` with a bitset for ints | ints 71–88% fewer cycles; arrays of strings pay +1–7% for the check |
| [![#23110](https://img.shields.io/github/pulls/detail/state/php/php-src/23110?label=%2323110&style=for-the-badge)](https://github.com/php/php-src/pull/23110) | `unserialize()` back-reference lookup | 14–31% fewer cycles on payloads with many references |
| [![#23675](https://img.shields.io/github/pulls/detail/state/php/php-src/23675?label=%2323675&style=for-the-badge)](https://github.com/php/php-src/pull/23675) | SSE2/NEON path in `json_encode()` | mostly-ASCII strings of 256 bytes and more 1.3–5× faster; Cyrillic and CJK text 4–19% slower with GCC |

#### Writing

- [One mutex for every row: mysqlnd statistics in thread-based PHP](https://artukrainskiy.github.io/posts/mysqlnd-zts-statistics/)
- [12 web stacks on vendor defaults, PostgreSQL and MySQL: what a request costs and what the drivers change](https://artukrainskiy.github.io/posts/web-request-cost-stage-1/)
- [json_encode() in php-src, autumn 2026: where the time goes and what is on the table](https://artukrainskiy.github.io/posts/json-encode-utf8-autumn-2026/)
- [php-src's benchmark CI, read as a history](https://github.com/ArtUkrainskiy/php-src-bench/tree/main/reports/php-benchmark-history) — 7,024 master commits of callgrind results, plotted.
