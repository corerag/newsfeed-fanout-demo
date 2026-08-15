# News Feed at Scale — Fan-out, Queues & Sharding

[![Validate HTML](https://github.com/corerag/newsfeed-fanout-demo/actions/workflows/validate-html.yml/badge.svg)](https://github.com/corerag/newsfeed-fanout-demo/actions/workflows/validate-html.yml)
[![License: MIT](https://img.shields.io/github/license/corerag/newsfeed-fanout-demo)](LICENSE)
[![Pages deployment](https://github.com/corerag/newsfeed-fanout-demo/actions/workflows/pages/pages-build-deployment/badge.svg)](https://corerag.github.io/newsfeed-fanout-demo/)
[![GitHub stars](https://img.shields.io/github/stars/corerag/newsfeed-fanout-demo?style=social)](https://github.com/corerag/newsfeed-fanout-demo/stargazers)
[![GitHub forks](https://img.shields.io/github/forks/corerag/newsfeed-fanout-demo?style=social)](https://github.com/corerag/newsfeed-fanout-demo/forks)
[![Open issues](https://img.shields.io/github/issues/corerag/newsfeed-fanout-demo)](https://github.com/corerag/newsfeed-fanout-demo/issues)
[![Last commit](https://img.shields.io/github/last-commit/corerag/newsfeed-fanout-demo)](https://github.com/corerag/newsfeed-fanout-demo/commits/master)

An interactive, single-file HTML demo of the news feed system from the
[System Design Primer](https://github.com/donnemartin/system-design-primer),
covering:

- **Fan-out-on-write** — a regular user's post is pushed to every follower's
  feed immediately.
- **Fan-out-on-read** — a high-follower account's post is written once and
  merged in at read time instead, since fanning out to millions of feeds on
  every post doesn't scale.
- **Message queue + backpressure** — the fan-out service enqueues jobs for
  workers to drain; the queue has a bounded capacity, and once it's full,
  new jobs are dropped and the fan-out service throttles until it recovers.
- **Sharding** — feed writes are partitioned across N shards by
  `follower_id % N`.
- **Rate limiting** — a per-account token bucket sits in front of both
  lanes and rejects excess posts outright, before any fan-out or queue work
  starts — a proactive quota, distinct from the queue's reactive
  backpressure.

Click any node in the architecture diagram for an explanation, adjust the
worker/shard/queue-capacity/rate-limit sliders, and use the action buttons
(including a traffic-burst button) to watch the system respond in real time.

## Running it

It's a single static HTML file with no build step and no dependencies.
Open `index.html` directly in a browser, or serve the directory with
anything static, e.g.:

```
npx serve .
```
