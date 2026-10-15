# Dependency Exit Capsule: svix

**Verdict:** Migrated, gaps remain · **Confidence:** high · **Run:** `20261015-101601-svix-7e9e`

| Repository     | Dependency     | From     | To     | Branch     |
| -------------- | -------------- | -------- | ------ | ---------- |
| ayushsshukla/WorkSphere | svix | 2.0.0 | svix@2.8.0 | `themis/svix-20261015` |

> Provenance: **OBSERVED** read from the repo or a registry · **EXECUTED** ran in the sandbox, log attached ·
> **AI-RECOMMENDED** model reasoning over observed data · **UNVERIFIED** not backed by a check

## Maintenance problem
- **OBSERVED** · Planner · `svix` ranks with risk score 25.3 and is deprecated
  <sub><https://registry.npmjs.org/svix></sub>

## Dependency and repository details
- **OBSERVED** · Scout · Language: typescript
  <sub>`tsconfig.json`</sub>
- **OBSERVED** · Scout · Package manager: npm
  <sub>`package-lock.json`</sub>
- **OBSERVED** · Scout · Node version: 20
  <sub>`.nvmrc`</sub>
- **OBSERVED** · Scout · Test command: `npm test` (jest)
  <sub>`package.json`</sub>
- **OBSERVED** · Scout · Linters: eslint
  <sub>`eslint.config.mjs`</sub>
- **OBSERVED** · Scout · 94 direct dependencies (35 dev); tree read from package-lock.json
  <sub>`package-lock.json`</sub>

## Risk indicators
- **EXECUTED** · Scout · npm-audit reported 98 vulnerability record(s)
  <sub>`npm audit --json --package-lock-only` → exit 1, log `logs/002-npm-audit.log`</sub>
- **EXECUTED** · Scout · osv-scanner reported 102 vulnerability record(s)
  <sub>`osv-scanner scan source --format json --lockfile package-lock.json` → exit 1, log `logs/003-osv-scanner.log`</sub>
- **EXECUTED** · Scout · trivy reported 81 vulnerability record(s)
  <sub>`trivy fs --scanners vuln --format json --quiet --skip-dirs node_modules .` → exit 0, log `logs/004-trivy-fs.log`</sub>
- **OBSERVED** · Scout · `prisma` (score 70): 16 known vulnerabilit(y/ies); installed 7.10.0, latest 8.0.0-rc.23; latest release 0 days ago; 138 transitive packages
  <sub><https://registry.npmjs.org/prisma></sub>
- **OBSERVED** · Scout · `partykit` (score 69.6): 49 known vulnerabilit(y/ies); installed 0.0.115, latest 0.0.115; latest release 511 days ago; 96 transitive packages
  <sub><https://registry.npmjs.org/partykit></sub>
- **OBSERVED** · Scout · `@solana/web3.js` (score 60.7): 8 known vulnerabilit(y/ies); installed 1.99.0, latest 1.99.0; latest release 36 days ago; 57 transitive packages
  <sub><https://registry.npmjs.org/@solana%2Fweb3.js></sub>
- **OBSERVED** · Scout · `ts-jest` (score 60): 18 known vulnerabilit(y/ies); installed 29.4.12, latest 29.4.15; latest release 0 days ago; 362 transitive packages
  <sub><https://registry.npmjs.org/ts-jest></sub>
- **OBSERVED** · Scout · `@prisma/client` (score 60): 16 known vulnerabilit(y/ies); installed 7.10.0, latest 7.10.0; latest release 50 days ago; 140 transitive packages
  <sub><https://registry.npmjs.org/@prisma%2Fclient></sub>
- **OBSERVED** · Scout · `eslint-config-next` (score 60): 15 known vulnerabilit(y/ies); installed 16.3.5, latest 16.4.1; latest release 0 days ago; 346 transitive packages
  <sub><https://registry.npmjs.org/eslint-config-next></sub>
- **OBSERVED** · Scout · `jest` (score 60): 15 known vulnerabilit(y/ies); installed 30.5.2, latest 30.5.2; latest release 26 days ago; 349 transitive packages
  <sub><https://registry.npmjs.org/jest></sub>
- **OBSERVED** · Scout · `snarkjs` (score 58.4): 12 known vulnerabilit(y/ies); installed 0.7.6, latest 0.7.6; latest release 275 days ago; 34 transitive packages
  <sub><https://registry.npmjs.org/snarkjs></sub>

## Usage locations
- **EXECUTED** · Planner · Opengrep found 2 usage site(s) of `svix`
  <sub>`opengrep scan --config /home/runner/work/H26_UntrainedModels_THEMIS/H26_UntrainedModels_THEMIS/target/.themis/runs/20...` → exit 0, log `logs/1001-opengrep-usage.log`</sub>
- **OBSERVED** · Planner · src/lib/notifications/channels/webhookChannel.ts:2 `import` (themis-svix-import)
  <sub>`src/lib/notifications/channels/webhookChannel.ts:2`</sub>
- **OBSERVED** · Planner · src/lib/notifications/channels/webhookChannel.ts:40 `Webhook` (themis-svix-usage-new)
  <sub>`src/lib/notifications/channels/webhookChannel.ts:40`</sub>

## AI analysis and recommendations
- **AI-RECOMMENDED** · Scout · `prisma`: The Prisma dependency has a high overall risk score of 70, driven by multiple high‑severity vulnerabilities in transitive packages such as deepmerge-ts and fast‑uri, all of which have available fixes in earlier versions of those packages. The presence of these unresolved issues in the current dependency tree makes Prisma a priority for migration.
  <sub>openai/gpt-oss-20b; inputs: ranked-dependencies.json</sub>
- **AI-RECOMMENDED** · Planner · Upgrade `svix` with `svix@2.8.0` (confidence: high). The repository imports svix and constructs a Webhook with a secret. The latest 2.8.0 release is compatible with the existing constructor signature. No API changes affect the usage sites. No fix rules are required. The deprecation message refers to the verify function signature, which is not used in the current code. Therefore the migration is straightforward.
  <sub>openai/gpt-oss-20b; inputs: dependency.json, usage-map.json, toolchain.json</sub>

## Proposed changes
- **AI-RECOMMENDED** · Planner · dependency: upgrade svix to 2.8.0 (package.json, package-lock.json)
  <sub>openai/gpt-oss-20b; inputs: dependency.json, usage-map.json, toolchain.json</sub>
- **AI-RECOMMENDED** · Planner · tests: characterization tests for svix call sites (src/lib/notifications/channels/webhookChannel.ts)
  <sub>openai/gpt-oss-20b; inputs: dependency.json, usage-map.json, toolchain.json</sub>
- **EXECUTED** · Migrator · Created branch `themis/svix-20261015` from 69d7ada in a separate worktree
  <sub>`git worktree add -B themis/svix-20261015 /home/runner/work/H26_UntrainedModels_THEMIS/H26_UntrainedModels_THEMIS/work...` → exit 0, log `logs/1001-git-worktree-add.log`</sub>
- **EXECUTED** · Migrator · Added `svix@2.8.0` to the manifest and lockfile
  <sub>`npm install --package-lock-only --ignore-scripts --no-audit --no-fund svix@2.8.0` → exit 0, log `logs/1002-pm-add.log`</sub>

## Suggested tests
- **AI-RECOMMENDED** · Planner · src/lib/notifications/channels/webhookChannel.ts:40
  <sub>openai/gpt-oss-20b; inputs: dependency.json, usage-map.json, toolchain.json</sub>
- **AI-RECOMMENDED** · Migrator · Generated 1 characterization test file(s): src/__tests__/themis-svix.characterization.test.ts. 
  <sub>openai/gpt-oss-20b; inputs: call-sites.json, suggested-tests.md, toolchain.json, existing-test-files.txt, test-shapes.md</sub>

## Executed results
- **EXECUTED** · Verifier · Baseline install (main @ 69d7ada) exited 1
  <sub>`docker build --file /home/runner/work/H26_UntrainedModels_THEMIS/H26_UntrainedModels_THEMIS/docker/sandbox.Dockerfile...` → exit 1, log `logs/3002-docker-build-baseline.log`</sub>
- **EXECUTED** · Verifier · Candidate install (themis/svix-20261015 @ 1157b8d) exited 1
  <sub>`docker build --file /home/runner/work/H26_UntrainedModels_THEMIS/H26_UntrainedModels_THEMIS/docker/sandbox.Dockerfile...` → exit 1, log `logs/6002-docker-build-candidate.log`</sub>
- **EXECUTED** · Verifier · Security rescan: baseline 161, candidate 161 finding(s); 0 resolved, 0 new
  <sub>`security rescan (npm audit / OSV-Scanner / Trivy or pip-audit)` → exit 1, log `logs/6003-npm-audit.log`</sub>
- **UNVERIFIED** · Verifier · Call-site coverage: 0 of 1 affected call sites exercised by passing characterization tests
  <sub>no tests ran on the candidate</sub>

## Compatibility and maintenance gaps
- **UNVERIFIED** · Migrator · Characterization tests could not be validated because the baseline install failed
  <sub>see logs/1006-docker-build-baseline.log</sub>
- **UNVERIFIED** · Verifier · Black-box probes were not run (no start command and port detected, or no Docker sandbox).
  <sub>probes skipped</sub>
- **UNVERIFIED** · Verifier · Call site not covered by a passing test: src/lib/notifications/channels/webhookChannel.ts:40 Webhook
  <sub>no characterization test names this site</sub>

## Unresolved concerns and limitations
- **UNVERIFIED** · Verifier · Tests were not run on both sides because an install failed.
  <sub>baseline or candidate install failed</sub>
