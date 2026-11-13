## Backend & cloud engineer

I build services in Python and FastAPI, and I'm most interested in what happens to
them under load and when their dependencies fail.

### What I'm working on

Taking [url-shortener](https://github.com/tokky-1/url-shortener) from "runs on my laptop"
to "stands up from code" — Terraform for the whole AWS stack, deploys through GitHub
Actions, and a second round of load tests against the deployed version with autoscaling on.

### Selected work

**[url-shortener](https://github.com/tokky-1/url-shortener)** — FastAPI, Postgres and Redis,
deployed once to ECS Fargate. With Redis down it used to fall to 108 req/s at p99 8.2s. The
fix — a circuit breaker that re-arms *before* it probes, and turning off redis-py's default
ten retries — took it to 222–370 req/s at p99 0.3–0.5s. The README has the measurements, the
prediction I got wrong, and the three things that broke during the deploy.

**[msg-app](https://github.com/tokky-1/msg-app)** — A messenger for two people at a time.
FastAPI and React, REST for history and a WebSocket for live delivery. The login throttle
counts and records as one step under a Postgres advisory lock: counting first and recording
after left a ~100ms gap where 30 simultaneous guesses got 17 through against a cap of 3.

**[algo-visualizer](https://github.com/tokky-1/algo-visualizer)** — React. Each algorithm is
a generator yielding plain step objects, and a hook consumes them and owns playback, so the
algorithm never draws to the screen or manages a timer.

### Stack

Python · FastAPI · SQLAlchemy · Postgres · Redis · Docker · GitHub Actions · AWS (ECS Fargate, RDS, ECR, Secrets Manager) · pytest · k6
