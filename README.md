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

**[php-src](https://github.com/php/php-src)** — performance of the PHP interpreter: string functions, `json_encode()`, `htmlspecialchars()`, CSV, the compiler, and threaded (ZTS) builds. I benchmark changes on Intel and AMD with several compilers, compare output with master, and report regressions alongside gains. I also review and measure other contributors' performance PRs.

**[php-src-bench](https://github.com/ArtUkrainskiy/php-src-bench)** — the A/B benchmark tool behind that work. Public reports include the comparison, full tables, output verification and commands to reproduce.

**[web-request-cost](https://github.com/ArtUkrainskiy/web-request-cost)** — CPU and memory per request of 12 web stacks (PHP-FPM, FrankenPHP, RoadRunner, Swoole, Go, Node.js, .NET, Java and others) on PostgreSQL and MySQL, with every raw record.

#### Pull requests

| PR | Change | Measured |
|---|---|---|
| [![#25115](https://img.shields.io/github/pulls/detail/state/php/php-src/25115?label=%2325115&style=for-the-badge)](https://github.com/php/php-src/pull/25115) | `strpos()` and related functions: compact Sunday table for 9–31-byte needles | Primary medians on 108 application fixtures: 4.5–27.2% less time on AMD; Intel results vary, with reproduced slowdowns of 2.9–4.1%. A synthetic 64-byte-needle control takes ~31% more time on AMD/GCC 15 ([report](https://github.com/ArtUkrainskiy/php-src-bench/tree/main/reports/compact-sunday)) |
| [![#24774](https://img.shields.io/github/pulls/detail/state/php/php-src/24774?label=%2324774&style=for-the-badge)](https://github.com/php/php-src/pull/24774) | `base64_decode()`: decode four characters at a time in the character loop | 24–44 B tokens/keys: 41–50% fewer instructions; line-wrapped 64 KB: 68–76% fewer instructions, depending on format and strict mode. Clean 64 KB is nearly unchanged ([report](https://github.com/ArtUkrainskiy/php-src-bench/tree/main/reports/base64-decode-quads)) |
| [![#24448](https://img.shields.io/github/pulls/detail/state/php/php-src/24448?label=%2324448&style=for-the-badge)](https://github.com/php/php-src/pull/24448) | mysqlnd: relaxed atomics instead of a mutex for statistics in ZTS builds (issue [#24447](https://github.com/php/php-src/issues/24447)) | FrankenPHP + MySQL, 16 threads: 10–47% less CPU per request, depending on the cores the threads run on; statistics cost 12–91% before, 0.6–1.4% after ([report](https://github.com/ArtUkrainskiy/php-src-bench/tree/main/reports/mysqlnd-zts-stats)) |
| [![#24283](https://img.shields.io/github/pulls/detail/state/php/php-src/24283?label=%2324283&style=for-the-badge)](https://github.com/php/php-src/pull/24283) | `json_encode()`: decode valid UTF-8 inline | non-ASCII text 9–32% fewer cycles, 6 compiler/CPU configs; with GCC 13/14 on Intel some ASCII inputs up to 20% more ([report](https://github.com/ArtUkrainskiy/php-src-bench/tree/main/reports/json-encode-utf8-inline)) |
| [![#24207](https://img.shields.io/github/pulls/detail/state/php/php-src/24207?label=%2324207&style=for-the-badge)](https://github.com/php/php-src/pull/24207) | `php_mblen()` without `mbrlen()` for ASCII | `fgetcsv()` 4,210 → 500 ns per row ([report](https://github.com/ArtUkrainskiy/php-src-bench/tree/main/reports/fgetcsv-mblen)) |
| [![#24198](https://img.shields.io/github/pulls/detail/state/php/php-src/24198?label=%2324198&style=for-the-badge)](https://github.com/php/php-src/pull/24198) | `#[\Deprecated]` without constructing the attribute (issue [#24191](https://github.com/php/php-src/issues/24191)) | 5,016 → 2,778 instructions per deprecated call ([report](https://github.com/ArtUkrainskiy/php-src-bench/tree/main/reports/deprecation-cost)) |
| [![#24180](https://img.shields.io/github/pulls/detail/state/php/php-src/24180?label=%2324180&style=for-the-badge)](https://github.com/php/php-src/pull/24180) | `[$a, $b] = [$b, $a]` without building the array | 922 → 523 instructions per swap ([report](https://github.com/ArtUkrainskiy/php-src-bench/tree/main/reports/list-assign-from-array-literal)) |
| [![#24145](https://img.shields.io/github/pulls/detail/state/php/php-src/24145?label=%2324145&style=for-the-badge)](https://github.com/php/php-src/pull/24145) | ASCII fast path in `htmlspecialchars()` | 41–89% fewer cycles where something has to be encoded (English text, HTML, Markdown, JavaScript) ([report](https://github.com/ArtUkrainskiy/php-src-bench/tree/main/reports/htmlspecialchars-ascii-fast-path)) |
| [![#24142](https://img.shields.io/github/pulls/detail/state/php/php-src/24142?label=%2324142&style=for-the-badge)](https://github.com/php/php-src/pull/24142) | `html_entity_decode()`: stop at the first non-name byte | a string of `&` 3.5× faster; `&param=` URLs in text up to 7% slower |

<details>
<summary>Reviewed and measured</summary>

Selected reviews with reproduced bugs, concrete fixes or performance measurements. Results describe the revisions reviewed; linked comments and reports give the details.

| PR | Change | Result |
|---|---|---|
| [![#24666](https://img.shields.io/github/pulls/detail/state/php/php-src/24666?label=%2324666&style=for-the-badge)](https://github.com/php/php-src/pull/24666) | SIMD scanning in `json_encode()` / `json_decode()` | Localized posts: non-Latin decoding 22–52% more cycles, English decoding 28–37% fewer; measured a variant to reduce the regression ([report](https://github.com/ArtUkrainskiy/php-src-bench/tree/main/reports/pr-24666-json-scan)) |
| [![#24604](https://img.shields.io/github/pulls/detail/state/php/php-src/24604?label=%2324604&style=for-the-badge)](https://github.com/php/php-src/pull/24604) | Integer allocation formulas in uuencode/uudecode | No clear speedup: decode instructions flat, GCC 13 encode about 4% higher; round-trip and malformed-input fuzzing matched master ([review](https://github.com/php/php-src/pull/24604#issuecomment-6432040886)) |
| [![#24602](https://img.shields.io/github/pulls/detail/state/php/php-src/24602?label=%2324602&style=for-the-badge)](https://github.com/php/php-src/pull/24602) | Cleanup after misbehaving stream filters | Reproduced a 48-byte stream-bucket leak with a `PSFS_PASS_ON` filter ([review](https://github.com/php/php-src/pull/24602#issuecomment-6436591222)) |
| [![#24590](https://img.shields.io/github/pulls/detail/state/php/php-src/24590?label=%2324590&style=for-the-badge)](https://github.com/php/php-src/pull/24590) | Integer-overflow and allocator hardening | Checked shift-overflow detection against a 128-bit oracle; found missed positive shifts and behavior changes needing regression tests ([review](https://github.com/php/php-src/pull/24590#issuecomment-6363425873)) |
| [![#24465](https://img.shields.io/github/pulls/detail/state/php/php-src/24465?label=%2324465&style=for-the-badge)](https://github.com/php/php-src/pull/24465) | Persistent PDO statement cleanup | Reproduced a server-side prepared-statement leak with libpq < 17 after an aborted transaction; supplied a cleanup fix and reproducer ([review](https://github.com/php/php-src/pull/24465#discussion_r4334117189)) |
| [![#24433](https://img.shields.io/github/pulls/detail/state/php/php-src/24433?label=%2324433&style=for-the-badge)](https://github.com/php/php-src/pull/24433) | Validation before `unserialize()` callbacks | ASan reproduced a heap-use-after-free introduced by the proposed change; base and master were unaffected ([review](https://github.com/php/php-src/pull/24433#issuecomment-6339854230)) |
| [![#24404](https://img.shields.io/github/pulls/detail/state/php/php-src/24404?label=%2324404&style=for-the-badge)](https://github.com/php/php-src/pull/24404) | `array_merge()` with an empty argument | Found that the proposed fix still retained a stale next index for temporary arrays; supplied reproducers and a one-line correction ([review](https://github.com/php/php-src/pull/24404#issuecomment-6339674375)) |
| [![#24385](https://img.shields.io/github/pulls/detail/state/php/php-src/24385?label=%2324385&style=for-the-badge)](https://github.com/php/php-src/pull/24385) | Inline parsing of PostgreSQL integer columns | 10–26% fewer PHP cycles per execute/fetchAll of 10,000 integer rows; text columns near flat ([report](https://github.com/ArtUkrainskiy/php-src-bench/tree/main/reports/pr-24385-pdo-pgsql-int)) |
| [![#24272](https://img.shields.io/github/pulls/detail/state/php/php-src/24272?label=%2324272&style=for-the-badge)](https://github.com/php/php-src/pull/24272) | OPcache shared-memory locks under ZTS | Deterministically reproduced one thread releasing another thread's lock; confirmed that process-wide fcntl locks make it architecture-independent ([review](https://github.com/php/php-src/pull/24272#issuecomment-6439137107)) |
| [![#24261](https://img.shields.io/github/pulls/detail/state/php/php-src/24261?label=%2324261&style=for-the-badge)](https://github.com/php/php-src/pull/24261) | JIT exception checks on function leave | Measured 3 fewer instructions per scalar function call, but no cycle improvement on the microbenchmark or bench.php ([review](https://github.com/php/php-src/pull/24261#issuecomment-6412288666)) |
| [![#24199](https://img.shields.io/github/pulls/detail/state/php/php-src/24199?label=%2324199&style=for-the-badge)](https://github.com/php/php-src/pull/24199) | RFC: CSV extension | Found a generator use-after-free and quadratic file rescanning; retested those fixes, then found overlapping-token round-trip failures ([report](https://github.com/ArtUkrainskiy/php-src-bench/tree/main/reports/csv-pr-24199)) |
| [![#24188](https://img.shields.io/github/pulls/detail/state/php/php-src/24188?label=%2324188&style=for-the-badge)](https://github.com/php/php-src/pull/24188) | `hash_pbkdf2()` with precomputed HMAC states | 43–53% fewer cycles at 1,000 iterations (35% for whirlpool), 0–5% more at 1 iteration; the hash contexts that hold the key should be wiped before freeing |
| [![#24157](https://img.shields.io/github/pulls/detail/state/php/php-src/24157?label=%2324157&style=for-the-badge)](https://github.com/php/php-src/pull/24157) | `array_push()` of several values in bulk | 9–38% fewer cycles for three or more values; three mutations passed the tests, two short tests suggested that catch them |
| [![#24080](https://img.shields.io/github/pulls/detail/state/php/php-src/24080?label=%2324080&style=for-the-badge)](https://github.com/php/php-src/pull/24080) | `mb_substr()` on valid UTF-8 | 10–98% fewer cycles in nine languages, depending on bytes per character and position; the first version returned different results for UTF-8-Mobile encodings, fixed in the PR with the suggested change |
| [![#23961](https://img.shields.io/github/pulls/detail/state/php/php-src/23961?label=%2323961&style=for-the-badge)](https://github.com/php/php-src/pull/23961) | charset lookup of the HTML functions, UTF-8 first | short UTF-8 strings 18–27% fewer cycles on top of #23957; with clang 18 `"MacRoman"` +35% cycles ([report](https://github.com/ArtUkrainskiy/php-src-bench/tree/main/reports/pr-23961-html-charset)) |
| [![#23957](https://img.shields.io/github/pulls/detail/state/php/php-src/23957?label=%2323957&style=for-the-badge)](https://github.com/php/php-src/pull/23957) | Clean-input fast path in `htmlspecialchars()` | Symfony Demo: 0.93% fewer instructions/request, 1.06% combined with #24145; output checked on 20,000 random inputs ([report](https://github.com/ArtUkrainskiy/php-src-bench/tree/main/reports/htmlspecialchars-vs-23957)) |
| [![#23789](https://img.shields.io/github/pulls/detail/state/php/php-src/23789?label=%2323789&style=for-the-badge)](https://github.com/php/php-src/pull/23789) | SSE2/NEON `bin2hex()`/`hex2bin()` | `hex2bin()` returned wrong bytes on big-endian AArch64, two-line fix; short inputs 1–4% more cycles ([report](https://github.com/ArtUkrainskiy/php-src-bench/tree/main/reports/pr-23789-bin2hex-hex2bin)) |
| [![#23682](https://img.shields.io/github/pulls/detail/state/php/php-src/23682?label=%2323682&style=for-the-badge)](https://github.com/php/php-src/pull/23682) | Byte lookup table in `json_encode()` | 4 KiB ASCII: 25–33% fewer instructions; Cyrillic with GCC: 19–21% more cycles ([review](https://github.com/php/php-src/pull/23682#issuecomment-6135485527)) |
| [![#23675](https://img.shields.io/github/pulls/detail/state/php/php-src/23675?label=%2323675&style=for-the-badge)](https://github.com/php/php-src/pull/23675) | SSE2/NEON path in `json_encode()` | mostly-ASCII strings of 256 bytes and more 1.3–5× faster; Cyrillic and CJK text 4–19% slower with GCC |
| [![#23585](https://img.shields.io/github/pulls/detail/state/php/php-src/23585?label=%2323585&style=for-the-badge)](https://github.com/php/php-src/pull/23585) | Packed-array `sort()` / `rsort()` / `usort()` | Large integer sort/rsort: 40–50% fewer cycles and 64–79% fewer instructions; fuzzed against master and checked under ASan/UBSan ([report](https://github.com/ArtUkrainskiy/php-src-bench/tree/main/reports/pr-23585-packed-sort)) |
| [![#23517](https://img.shields.io/github/pulls/detail/state/php/php-src/23517?label=%2323517&style=for-the-badge)](https://github.com/php/php-src/pull/23517) | `array_shift()` with one `memmove()` | draining a queue of 1,000 ints 82–84% fewer cycles |
| [![#23189](https://img.shields.io/github/pulls/detail/state/php/php-src/23189?label=%2323189&style=for-the-badge)](https://github.com/php/php-src/pull/23189) | `var_export()` without temporary strings | 15–68% fewer cycles on small and medium values; on 32-bit builds the escaped length overflowed and `var_export()` crashed; long strings got slower; a one-pass variant was faster than master in every case measured ([report](https://github.com/ArtUkrainskiy/php-src-bench/tree/main/reports/pr-23189-var-export)) |
| [![#23110](https://img.shields.io/github/pulls/detail/state/php/php-src/23110?label=%2323110&style=for-the-badge)](https://github.com/php/php-src/pull/23110) | `unserialize()` back-reference lookup | 14–31% fewer cycles on payloads with many references |
| [![#22648](https://img.shields.io/github/pulls/detail/state/php/php-src/22648?label=%2322648&style=for-the-badge)](https://github.com/php/php-src/pull/22648) | `array_diff()` with a bitset for ints | ints 71–88% fewer cycles; arrays of strings pay +1–7% for the check |

</details>
