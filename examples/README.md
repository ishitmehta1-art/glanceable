# Examples

## verify-demo.html

The output of a verify-mode test. Open it in a browser.

The input, [`verify-demo-report.md`](verify-demo-report.md), is a short test report written in the style of a deep research report. It cites real GitHub sources for httpx, requests and aiohttp. Three claims in it are deliberately wrong, and one source is a made-up benchmark site that can't be reached.

An AI following `SKILL.md` checked every claim against its cited source on 2026-09-26:

| Report claim | Result |
|---|---|
| httpx reached 1.0 stable in 2025 | Not supported: the changelog's latest release is 0.28.1 (December 2024) |
| requests supports async natively since 2.30 | Not supported: the requests README doesn't mention it |
| aiohttp does not support WebSockets | Not supported: the aiohttp README says it supports client and server WebSockets |
| aiohttp is 3x faster than httpx | Couldn't check: the benchmark source can't be opened |
| httpx mirrors the requests API, has sync and async clients, and sets timeouts by default | Supported |

A script confirmed that every highlighted passage matches the source files word for word.
