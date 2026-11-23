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

#### Writing

- [One mutex for every row: mysqlnd statistics in thread-based PHP](https://artukrainskiy.github.io/posts/mysqlnd-zts-statistics/)
- [12 web stacks on vendor defaults, PostgreSQL and MySQL: what a request costs and what the drivers change](https://artukrainskiy.github.io/posts/web-request-cost-stage-1/)
- [json_encode() in php-src, autumn 2026: where the time goes and what is on the table](https://artukrainskiy.github.io/posts/json-encode-utf8-autumn-2026/)
- [php-src's benchmark CI, read as a history](https://github.com/ArtUkrainskiy/php-src-bench/tree/main/reports/php-benchmark-history) — 7,024 master commits of callgrind results, plotted.

#### Open source

**[php-src](https://github.com/php/php-src)** — performance and correctness of the PHP interpreter. I measure changes on several CPUs and compilers, check the output against master, and report regressions next to gains. I also review other contributors' PRs.

**[php-src-bench](https://github.com/ArtUkrainskiy/php-src-bench)** — the A/B benchmark tool behind that work. Public reports include the comparison, full tables, output verification and commands to reproduce.

**[web-request-cost](https://github.com/ArtUkrainskiy/web-request-cost)** — CPU and memory per request of 12 web stacks (PHP-FPM, FrankenPHP, RoadRunner, Swoole, Go, Node.js, .NET, Java and others) on PostgreSQL and MySQL, with every raw record.

#### RFC

- [Prepared Literal String Matching and Replacement](https://wiki.php.net/rfc/prepared_literal_string_matching) · [discussion](https://news-web.php.net/php.internals/133028)

#### Pull requests

| PR | Change | Measured |
|---|---|---|
| [![#25516](https://img.shields.io/github/pulls/detail/state/php/php-src/25516?label=%2325516&style=for-the-badge)](https://github.com/php/php-src/pull/25516) | `PDO::FETCH_OBJ` as a properties table | 12–20% fewer cycles per fetch ([report](https://github.com/ArtUkrainskiy/php-src-bench/tree/main/reports/pdo-fetch-obj)) |
| [![#25437](https://img.shields.io/github/pulls/detail/state/php/php-src/25437?label=%2325437&style=for-the-badge)](https://github.com/php/php-src/pull/25437) | Reusable compiled XML Schema (`Dom\XMLSchema`) | 20 KB invoice validated in 0.31 ms instead of 51 ms |
| [![#25122](https://img.shields.io/github/pulls/detail/state/php/php-src/25122?label=%2325122&style=for-the-badge)](https://github.com/php/php-src/pull/25122) | `Str\Matcher` / `Str\Replacer` (RFC) | 42–44% less time than `preg_match()` with 128 keys ([report](https://github.com/ArtUkrainskiy/php-src-bench/tree/main/reports/multi-pattern-search)) |
| [![#25115](https://img.shields.io/github/pulls/detail/state/php/php-src/25115?label=%2325115&style=for-the-badge)](https://github.com/php/php-src/pull/25115) | Compact Sunday table in `strpos()` | 4.5–27% less time on AMD, up to 4% more on Intel ([report](https://github.com/ArtUkrainskiy/php-src-bench/tree/main/reports/compact-sunday)) |
| [![#24774](https://img.shields.io/github/pulls/detail/state/php/php-src/24774?label=%2324774&style=for-the-badge)](https://github.com/php/php-src/pull/24774) | `base64_decode()` four characters at a time | 41–76% fewer instructions on short and line-wrapped input ([report](https://github.com/ArtUkrainskiy/php-src-bench/tree/main/reports/base64-decode-quads)) |
| [![#24448](https://img.shields.io/github/pulls/detail/state/php/php-src/24448?label=%2324448&style=for-the-badge)](https://github.com/php/php-src/pull/24448) | mysqlnd statistics without a mutex in ZTS builds | FrankenPHP + MySQL: 10–47% less CPU per request ([report](https://github.com/ArtUkrainskiy/php-src-bench/tree/main/reports/mysqlnd-zts-stats)) |
| [![#24283](https://img.shields.io/github/pulls/detail/state/php/php-src/24283?label=%2324283&style=for-the-badge)](https://github.com/php/php-src/pull/24283) | Inline UTF-8 decoding in `json_encode()` | non-ASCII text 9–32% fewer cycles; some ASCII up to 20% more with GCC 13/14 ([report](https://github.com/ArtUkrainskiy/php-src-bench/tree/main/reports/json-encode-utf8-inline)) |
| [![#24207](https://img.shields.io/github/pulls/detail/state/php/php-src/24207?label=%2324207&style=for-the-badge)](https://github.com/php/php-src/pull/24207) | `php_mblen()` without `mbrlen()` for ASCII | `fgetcsv()` 8× faster per row ([report](https://github.com/ArtUkrainskiy/php-src-bench/tree/main/reports/fgetcsv-mblen)) |
| [![#24198](https://img.shields.io/github/pulls/detail/state/php/php-src/24198?label=%2324198&style=for-the-badge)](https://github.com/php/php-src/pull/24198) | `#[\Deprecated]` without constructing the attribute | 44% fewer instructions per deprecated call ([report](https://github.com/ArtUkrainskiy/php-src-bench/tree/main/reports/deprecation-cost)) |
| [![#24180](https://img.shields.io/github/pulls/detail/state/php/php-src/24180?label=%2324180&style=for-the-badge)](https://github.com/php/php-src/pull/24180) | `[$a, $b] = [$b, $a]` without building the array | 43% fewer instructions per swap ([report](https://github.com/ArtUkrainskiy/php-src-bench/tree/main/reports/list-assign-from-array-literal)) |
| [![#24145](https://img.shields.io/github/pulls/detail/state/php/php-src/24145?label=%2324145&style=for-the-badge)](https://github.com/php/php-src/pull/24145) | ASCII fast path in `htmlspecialchars()` | 41–89% fewer cycles ([report](https://github.com/ArtUkrainskiy/php-src-bench/tree/main/reports/htmlspecialchars-ascii-fast-path)) |
| [![#24142](https://img.shields.io/github/pulls/detail/state/php/php-src/24142?label=%2324142&style=for-the-badge)](https://github.com/php/php-src/pull/24142) | `html_entity_decode()` stops at the first non-name byte | up to 3.5× faster; `&param=` URLs up to 7% slower |

#### Bug fixes

| PR | Bug |
|---|---|
| [![#25529](https://img.shields.io/badge/%2325529-merged-blueviolet?style=for-the-badge)](https://github.com/php/php-src/pull/25529) | Phar signing reads a freed OpenSSL key ([commit](https://github.com/php/php-src/commit/9af71942c6610852dd6350cf19e278628c8b5b60)) |
| [![#25524](https://img.shields.io/github/pulls/detail/state/php/php-src/25524?label=%2325524&style=for-the-badge)](https://github.com/php/php-src/pull/25524) | `openssl_csr_new()`: `string_mask` carries over to later calls |
| [![#25523](https://img.shields.io/github/pulls/detail/state/php/php-src/25523?label=%2325523&style=for-the-badge)](https://github.com/php/php-src/pull/25523) | `openssl_error_string()` returns errors from a previous request |
| [![#25539](https://img.shields.io/github/pulls/detail/state/php/php-src/25539?label=%2325539&style=for-the-badge)](https://github.com/php/php-src/pull/25539) | master didn't build with GCC 15 |
| [![#25532](https://img.shields.io/github/pulls/detail/state/php/php-src/25532?label=%2325532&style=for-the-badge)](https://github.com/php/php-src/pull/25532) | `posix_get_last_error()` and `socket_last_error()` returned errors from a previous request |

#### Other projects

| PR | Change | Measured |
|---|---|---|
| [![#345](https://img.shields.io/github/pulls/detail/state/open-telemetry/opentelemetry-php-instrumentation/345?label=%23345&style=for-the-badge)](https://github.com/open-telemetry/opentelemetry-php-instrumentation/pull/345) | Skip the unused `WithSpan` lookup | up to 4.6% fewer cycles per request |
| [![#346](https://img.shields.io/github/pulls/detail/state/open-telemetry/opentelemetry-php-instrumentation/346?label=%23346&style=for-the-badge)](https://github.com/open-telemetry/opentelemetry-php-instrumentation/pull/346) | Return early for methods without hooks | up to 1.4% fewer cycles per request |

<details>
<summary>Reviewed and measured</summary>

Selected reviews with measurements or reproduced bugs. Results are for the revision reviewed.

| PR | Change | Result |
|---|---|---|
| [![#25545](https://img.shields.io/github/pulls/detail/state/php/php-src/25545?label=%2325545&style=for-the-badge)](https://github.com/php/php-src/pull/25545) | Closure cache leak with heap run-time caches | found a second leak, under opcache only ([review](https://github.com/php/php-src/pull/25545#issuecomment-7048930543)) |
| [![#25243](https://img.shields.io/github/pulls/detail/state/php/php-src/25243?label=%2325243&style=for-the-badge)](https://github.com/php/php-src/pull/25243) | GC threshold with large live graphs | 85% less time with 1M live objects; suggested fix merged ([report](https://github.com/ArtUkrainskiy/php-src-bench/tree/main/reports/pr-25243-gc-threshold)) |
| [![#24666](https://img.shields.io/github/pulls/detail/state/php/php-src/24666?label=%2324666&style=for-the-badge)](https://github.com/php/php-src/pull/24666) | SIMD scanning in JSON | non-Latin decoding 22–52% more cycles; measured a fix ([report](https://github.com/ArtUkrainskiy/php-src-bench/tree/main/reports/pr-24666-json-scan)) |
| [![#24604](https://img.shields.io/github/pulls/detail/state/php/php-src/24604?label=%2324604&style=for-the-badge)](https://github.com/php/php-src/pull/24604) | Integer formulas in uuencode | no measurable speedup ([review](https://github.com/php/php-src/pull/24604#issuecomment-6432040886)) |
| [![#24602](https://img.shields.io/github/pulls/detail/state/php/php-src/24602?label=%2324602&style=for-the-badge)](https://github.com/php/php-src/pull/24602) | Stream filter cleanup | reproduced a bucket leak ([review](https://github.com/php/php-src/pull/24602#issuecomment-6436591222)) |
| [![#24590](https://img.shields.io/github/pulls/detail/state/php/php-src/24590?label=%2324590&style=for-the-badge)](https://github.com/php/php-src/pull/24590) | Integer-overflow hardening | found missed shift overflows ([review](https://github.com/php/php-src/pull/24590#issuecomment-6363425873)) |
| [![#24465](https://img.shields.io/github/pulls/detail/state/php/php-src/24465?label=%2324465&style=for-the-badge)](https://github.com/php/php-src/pull/24465) | Persistent PDO statement cleanup | reproduced a statement leak, supplied a fix ([review](https://github.com/php/php-src/pull/24465#discussion_r4334117189)) |
| [![#24433](https://img.shields.io/github/pulls/detail/state/php/php-src/24433?label=%2324433&style=for-the-badge)](https://github.com/php/php-src/pull/24433) | Validation before `unserialize()` callbacks | ASan found a use-after-free in the change ([review](https://github.com/php/php-src/pull/24433#issuecomment-6339854230)) |
| [![#24404](https://img.shields.io/github/pulls/detail/state/php/php-src/24404?label=%2324404&style=for-the-badge)](https://github.com/php/php-src/pull/24404) | `array_merge()` with an empty array | fix incomplete, supplied a one-line correction ([review](https://github.com/php/php-src/pull/24404#issuecomment-6339674375)) |
| [![#24385](https://img.shields.io/github/pulls/detail/state/php/php-src/24385?label=%2324385&style=for-the-badge)](https://github.com/php/php-src/pull/24385) | PostgreSQL integer columns | 10–26% fewer cycles per fetch ([report](https://github.com/ArtUkrainskiy/php-src-bench/tree/main/reports/pr-24385-pdo-pgsql-int)) |
| [![#24272](https://img.shields.io/github/pulls/detail/state/php/php-src/24272?label=%2324272&style=for-the-badge)](https://github.com/php/php-src/pull/24272) | OPcache locks under ZTS | reproduced one thread releasing another's lock ([review](https://github.com/php/php-src/pull/24272#issuecomment-6439137107)) |
| [![#24261](https://img.shields.io/github/pulls/detail/state/php/php-src/24261?label=%2324261&style=for-the-badge)](https://github.com/php/php-src/pull/24261) | JIT exception check on return | 3 fewer instructions per call, no cycle gain ([review](https://github.com/php/php-src/pull/24261#issuecomment-6412288666)) |
| [![#24199](https://img.shields.io/github/pulls/detail/state/php/php-src/24199?label=%2324199&style=for-the-badge)](https://github.com/php/php-src/pull/24199) | CSV extension (RFC) | found a use-after-free, quadratic rescans and round-trip failures ([report](https://github.com/ArtUkrainskiy/php-src-bench/tree/main/reports/csv-pr-24199)) |
| [![#24188](https://img.shields.io/github/pulls/detail/state/php/php-src/24188?label=%2324188&style=for-the-badge)](https://github.com/php/php-src/pull/24188) | `hash_pbkdf2()` with precomputed HMAC | 43–53% fewer cycles at 1,000 iterations |
| [![#24157](https://img.shields.io/github/pulls/detail/state/php/php-src/24157?label=%2324157&style=for-the-badge)](https://github.com/php/php-src/pull/24157) | Bulk `array_push()` | 9–38% fewer cycles for three or more values |
| [![#24080](https://img.shields.io/github/pulls/detail/state/php/php-src/24080?label=%2324080&style=for-the-badge)](https://github.com/php/php-src/pull/24080) | `mb_substr()` on valid UTF-8 | 10–98% fewer cycles; found a UTF-8-Mobile bug |
| [![#23961](https://img.shields.io/github/pulls/detail/state/php/php-src/23961?label=%2323961&style=for-the-badge)](https://github.com/php/php-src/pull/23961) | HTML charset lookup, UTF-8 first | 18–27% fewer cycles on short UTF-8 strings ([report](https://github.com/ArtUkrainskiy/php-src-bench/tree/main/reports/pr-23961-html-charset)) |
| [![#23957](https://img.shields.io/github/pulls/detail/state/php/php-src/23957?label=%2323957&style=for-the-badge)](https://github.com/php/php-src/pull/23957) | Clean-input path in `htmlspecialchars()` | 0.93% fewer instructions per Symfony Demo request ([report](https://github.com/ArtUkrainskiy/php-src-bench/tree/main/reports/htmlspecialchars-vs-23957)) |
| [![#23789](https://img.shields.io/github/pulls/detail/state/php/php-src/23789?label=%2323789&style=for-the-badge)](https://github.com/php/php-src/pull/23789) | SIMD `bin2hex()` / `hex2bin()` | found wrong output on big-endian AArch64 ([report](https://github.com/ArtUkrainskiy/php-src-bench/tree/main/reports/pr-23789-bin2hex-hex2bin)) |
| [![#23682](https://img.shields.io/github/pulls/detail/state/php/php-src/23682?label=%2323682&style=for-the-badge)](https://github.com/php/php-src/pull/23682) | Lookup table in `json_encode()` | ASCII 25–33% fewer instructions, Cyrillic up to 21% more cycles ([review](https://github.com/php/php-src/pull/23682#issuecomment-6135485527)) |
| [![#23675](https://img.shields.io/github/pulls/detail/state/php/php-src/23675?label=%2323675&style=for-the-badge)](https://github.com/php/php-src/pull/23675) | SIMD `json_encode()` | ASCII 1.3–5× faster, Cyrillic and CJK 4–19% slower |
| [![#23585](https://img.shields.io/github/pulls/detail/state/php/php-src/23585?label=%2323585&style=for-the-badge)](https://github.com/php/php-src/pull/23585) | Packed-array sorting | 40–50% fewer cycles on large integer arrays ([report](https://github.com/ArtUkrainskiy/php-src-bench/tree/main/reports/pr-23585-packed-sort)) |
| [![#23517](https://img.shields.io/github/pulls/detail/state/php/php-src/23517?label=%2323517&style=for-the-badge)](https://github.com/php/php-src/pull/23517) | `array_shift()` with one `memmove()` | 82–84% fewer cycles draining a queue |
| [![#23189](https://img.shields.io/github/pulls/detail/state/php/php-src/23189?label=%2323189&style=for-the-badge)](https://github.com/php/php-src/pull/23189) | `var_export()` without temporary strings | found a 32-bit crash; measured a faster variant ([report](https://github.com/ArtUkrainskiy/php-src-bench/tree/main/reports/pr-23189-var-export)) |
| [![#23110](https://img.shields.io/github/pulls/detail/state/php/php-src/23110?label=%2323110&style=for-the-badge)](https://github.com/php/php-src/pull/23110) | `unserialize()` back-references | 14–31% fewer cycles |
| [![#22648](https://img.shields.io/github/pulls/detail/state/php/php-src/22648?label=%2322648&style=for-the-badge)](https://github.com/php/php-src/pull/22648) | `array_diff()` with an int bitset | 71–88% fewer cycles on ints |
| [![#19709](https://img.shields.io/github/pulls/detail/state/php/php-src/19709?label=%2319709&style=for-the-badge)](https://github.com/php/php-src/pull/19709) | Generational GC (proof of concept) | reproduced a use-after-free ([review](https://github.com/php/php-src/pull/19709#issuecomment-6845015586)) |
| [![#18556](https://img.shields.io/github/pulls/detail/state/php/php-src/18556?label=%2318556&style=for-the-badge)](https://github.com/php/php-src/pull/18556) | Shared closure run-time cache under opcache | 260 → 4 fresh caches per Laravel request ([report](https://github.com/ArtUkrainskiy/php-src-bench/tree/main/reports/pr-18556-closure-rtc)) |

</details>
