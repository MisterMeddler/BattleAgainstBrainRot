# Project BattleAgainstBrainrot: A Tile-Matching Logic Puzzle Web Application to Combat Digital Attention Fatigue

## Executive Summary

**BattleAgainstBrainrot** is a responsive, web-based daily puzzle application designed to actively combat the cognitive effects of digital overstimulation—commonly referred to as "brainrot." Rather than restricting access to devices, which is often met with resistance, BattleAgainstBrainrot goes with a gamified alternative: tile-matching logic puzzles presented in a calming, meditative interface. By substituting cheap dopamine loops with sustained, rewarding cognitive engagement, the app helps users rebuild their attention spans through consistent daily practice. Plus, who doesn't like a streaks leaderboard for encouragement? 

---

## 1. Problem Statement

### The Crisis of Digital Attention Fragmentation

In the modern digital landscape, the rise of short-form micro-content has altered how we spend our time. Platforms optimized for rapid-fire video consumption leverage hyper-stimulating algorithms designed to maximize immediate user engagement, creating what internet culture terms "brainrot"—a state of serotonin loop fatigue where continuous, low-effort neurological rewards erode an individual's capacity for sustained focus.

### Documented Consequences

**Cognitive Fragmentation:** Recent research [[1]](https://pmc.ncbi.nlm.nih.gov/articles/PMC11939997/) indicates that frequent switching between brief, high-stimulation media bursts significantly impacts cognitive performance and attention capacity. Users report diminished ability to engage with complex texts, nuanced arguments, or extended problem-solving tasks.

**Increased Mental Restlessness:** Consumers actively dealing with digital overstimulation report elevated baseline anxiety and a distinct inability to tolerate brief periods of boredom without reaching for a mobile device. This creates a feedback loop where discomfort with quiet moments drives further consumption.

**Inadequacy of Existing Solutions:** Current market solutions are primarily defensive. Screen time blockers and website restrictions rely heavily on user willpower and feel inherently punitive. They penalize negative behavior rather than cultivating positive habits, we cannot fight against a reward system with negative reinforcement.

### The Community Impacted

This problem disproportionately affects individuals who are socially or physically isolated. Digital overstimulation impacts students managing academic workloads, professionals in remote and hybrid work environments, and anyone who can no longer enjoy a long movie because it doesn't hold there attention.

### Why This Matters

The ability to maintain focus is a foundational cognitive skill tied to academic success, professional achievement, and mental well-being. Without active intervention, the trend toward fragmented attention threatens both individual potential and societal capacity for complex problem-solving. **Certainly, this isn't some silver bullet. It's just a little puzzle game meant to make people more fulfilled than doomscrolling. **

---

## 2. Proposed Solution

### What We Will Build

**BattleAgainstBrainrot** is a responsive web application offering daily tile-matching logic puzzles. Instead of aggressive restrictions or gameplay mechanics that encourage obsessive behavior, the app presents a **calming, meditative cognitive experience** that:

1. **Engages sustained attention** through structured logical problem-solving
2. **Replaces stimulation-seeking loops** with intrinsic reward (puzzle completion, streak progression)
3. **Encourages daily habit formation** via a persistent streak tracking system
4. **Creates healthy peer accountability** through a global leaderboard

### How It Addresses the Problem

| Problem | BattleAgainstBrainrot Response |
|---------|--------------------------------|
| **Hyper-stimulation & short attention spans** | Clean, distraction-free interface with ambient music; no flashing lights or aggressive timers |
| **Low-effort dopamine dependency** | Requires sustained problem-solving; rewards incremental progress and consistency over speed |
| **Lack of motivation to redirect habits** | Gamified streak system and community leaderboard provide intrinsic and social motivation without punitive messaging |
| **One-size-fits-all approach fails** | Responsive design + variable difficulty scaling allow users to select their own difficulty level |

### Why This Solution Is Feasible

Within a 10-week academic cycle, a focused MVP can deliver:
- **Puzzle validation engine** supporting both manually authored and procedurally generated puzzles
- **Secure user authentication** with minimal complexity (no payment processing, no complex social features)
- **A clean, responsive UI** achievable with standard web technologies (HTML/CSS/JavaScript)
- **Basic persistence layer** for user accounts and leaderboard data

The modular architecture ensures that core MVP features can ship independently, with stretch goals added incrementally without destabilizing the core product.

---

## 3. Core Features (MVP)

The minimum viable product consists of **four essential, interdependent systems**:

### Feature 1: Secure User Authentication & Profile Engine
**Why Essential:** Users must create persistent accounts to track streaks and populate the leaderboard. This is the foundation for all personalization and accountability mechanisms.

**Scope:**
- Registration & login endpoints with password hashing (bcrypt/Argon2)
- Session tokens (JWT or secure cookies) for authenticated state
- Basic user profile storage (username, created date, email optional)

**Testability:**
- A user can register, log in, and remain authenticated across page refreshes
- Invalid credentials are rejected with clear error messages
- Passwords are never stored in plaintext

---

### Feature 2: Interactive Tile-Based Puzzle Interface
**Why Essential:** The core gameplay experience must be intuitive, responsive, and visually calming. Without a smooth UI, users will abandon the app regardless of puzzle quality.

**Scope:**
- Responsive grid-based canvas rendering clickable tile components
- Visual state feedback (hover, active, solved, idle states)
- Touch and click event handling for desktop and mobile
- Reset button to restart the current puzzle
- Pause/menu navigation controls
- Ambient audio player with volume controls and mute toggle

**Testability:**
- Tiles respond correctly to clicks and touch events
- Visual feedback is immediate and clear
- Grid adapts responsively to desktop, tablet, and mobile screen sizes
- Pause and reset mechanics work without breaking game state
- Audio controls function consistently across browsers

---

### Feature 3: Puzzle Validation & Solution Verification System
**Why Essential:** The app must reliably validate whether a user has correctly solved a puzzle, regardless of whether the puzzle was manually authored or procedurally generated.

**Scope:**
- Core puzzle data structure representing grid, tile properties, and win conditions
- Win-state verification system checking user tile configurations against solutions in real time
- Support for both manually created puzzles (seed-based) and procedurally generated puzzles (if stretch goals are implemented)
- API endpoint exposing puzzle validation as a service the front-end can query

**Testability:**
- Win-state detection triggers correctly when puzzles are solved
- Invalid configurations are rejected appropriately
- Verification API returns reliable pass/fail decisions
- System supports scalability to different grid sizes and puzzle types

---

### Feature 4: Global Streak & Leaderboard System
**Why Essential:** Streak tracking transforms isolated puzzle sessions into a sustained habit. A public leaderboard provides healthy peer accountability without punitive messaging.

**Scope:**
- Streak calculus schema tracking current streak, best streak, and daily completion timestamps
- Daily completion validation logic (cron or timestamp check) to safely increment or reset streaks
- Leaderboard retrieval API aggregating top players by current/historical streak
- Leaderboard UI component displaying ranked players with their streak counts

**Testability:**
- A user's streak increments correctly for consecutive daily completions
- Missing a day or invalid completion window resets the streak appropriately
- Leaderboard correctly ranks and displays top players
- Leaderboard updates reflect newly submitted daily puzzles within a predictable window

---

## 4. Stretch Goals

If core MVP features ship ahead of schedule, the team will prioritize the following enhancements in order of complexity and value:

### Stretch Goal 1: Procedural Puzzle Generation Algorithm
Implement a deterministic back-end algorithm capable of generating randomized but mathematically guaranteed solvable tile-matching puzzles on demand. This eliminates repetitive gameplay and ensures infinite puzzle variety. Includes seeded generation for reproducibility.

### Stretch Goal 2: Tile Style & Art Customization
Allow users to swap default tiles for themed visual asset packs (e.g., seasonal themes, pixel art, minimalist designs). Builds community engagement and retention without changing core mechanics.

### Stretch Goal 3: Variable Difficulty Scaling
Introduce configurable grid sizes (4×4, 6×6, 8×8) and puzzle complexity profiles. Users self-select cognitive comfort levels, expanding appeal to both casual and hardcore players.

### Stretch Goal 4: Speed Trial Mode
A secondary, timed competitive mode for users seeking rapid problem-solving challenges. Leaderboard tracks fastest completion times separately from streak rankings.

### Stretch Goal 5: Endless Puzzle Mode
An unranked, infinite puzzle stream for meditative, continuous play without session interruptions. Perfect for users seeking flow state over achievement.

### Stretch Goal 6: Email Verification & Account Recovery
SMTP transactional email integration for account verification and password reset flows, improving account security and recovery options.

---

## 5. Deliverable Format

### User Access & Distribution
The final product will be a **fully hosted, production-ready web application** accessible via standard modern web browsers (Chrome, Firefox, Safari, Edge) **without requiring any local installations, compiling, or command-line setups**.

Users navigate to a single deployed URL and interact with the game immediately.

### Deployment Architecture (TBD)

The specific hosting configuration will be finalized by the team in Week 1 based on cost, infrastructure availability, and team preferences. Current options under consideration:

**Front-End Hosting (Static Assets):**
- GitHub Pages for zero-cost static asset hosting (HTML, CSS, JavaScript, leaderboard UI)
- Alternative: Vercel, Netlify, or equivalent static host

**Back-End Services:** 
- API server (authentication, puzzle validation, leaderboard queries) deployed to:
  - Lightweight cloud container (Vercel Serverless, Railway, Render, or equivalent)
  - University-provided hosting if available
  - Heroku (if budget allows)
- Persistent database for user accounts, streak data, and leaderboard rankings:
  - PostgreSQL (preferred for reliability)
  - SQLite (acceptable for MVP, migrate later if needed)

**Version Control:** All code, configuration, and documentation stored in GitHub with strict branch protection and peer code reviews.

---

## 6. Technology & Tools

### Rationale
The engineering stack prioritizes **high interoperability**, **rapid prototyping**, **minimal deployment overhead**, and **team skill alignment**.

| Component | Choice | Rationale |
|-----------|--------|-----------|
| **Front-End** | HTML5 / CSS3 / JavaScript (vanilla or lightweight framework) | Zero compilation overhead; runs anywhere; familiar to all team members |
| **Back-End** | Java or Go  | Strong ecosystem for REST APIs, authentication libraries, and database drivers; appropriate for academic timeline |
| **Database** | PostgreSQL (primary) or SQLite (MVP backup) | Mature, reliable, and available on most cloud platforms; strong data integrity guarantees |
| **Authentication** | JWT tokens + bcrypt/Argon2 | Industry-standard, implementable without external services |
| **Version Control** | GitHub | Native integration with project board, CI/CD, and team workflow |
| **Project Management** | GitHub Projects (Kanban) | Centralized issue tracking, sprint planning, and progress visualization |
| **Hosting** | TBD (GitHub Pages + cloud backend) | Flexible, scalable, and cost-effective for academic projects |

### Technology Flexibility
- **Front-End Framework:** If team votes to use React, Vue, etc, the architecture remains unchanged; only build tooling is added.
- **Back-End Language:** Go is lighter-weight; Java has larger ecosystem. Decision made in Week 1 after team assessment.
- **Database:** SQLite acceptable for MVP if cloud database setup proves too complex; migrate to PostgreSQL in stretch phase.

---

## 7. Timeline & Milestones

### 10-Week Agile Development Cycle

| Week | Phase / Objective | Major Milestone | Key Deliverables |
|------|------------------|-----------------|------------------|
| **1** | Team onboarding, architecture planning, repo setup | **Proposal Submitted** | GitHub repo initialized, README drafted, team roles assigned, tech stack finalized, hosting selected |
| **2** | Front-end layout mockups, auth schema design | **UI Mockup Drafted** | HTML boilerplate + CSS framework, database schema design document |
| **3** | Tile mechanics MVP, basic login endpoints | **Alpha Auth & Gameplay Working** | Tile click events functional, /register and /login endpoints tested, basic UI responsive |
| **4** | Puzzle validation system, leaderboard integration | **MVP Functionality Achieved** | Puzzle solver validates correctly, basic leaderboard retrieves and displays data |
| **5–10** | Stretch goals and stabilization (flexible allocation) | **Progressive Enhancement** | Features added based on remaining time; no MVP features sacrificed for stretch goals |

### Flexible Milestone Approach

**Key Principle:** MVP features are locked in by Week 4. If any MVP component falls behind schedule, the team prioritizes completion over stretch goals. Stretch features are implemented in order of priority only if time permits, with lower-priority features dropped first.

**Contingency Examples:**
- If puzzle validation takes 2 weeks instead of 1, Week 5 begins UI polish rather than procedural generation
- If authentication encounters security issues in Week 4, leaderboard optimization occurs instead of custom tiles
- Sprint planning each week reassesses remaining capacity and reprioritizes accordingly

### Definition of "Done" per Milestone
- All PRs peer-reviewed and merged to `main`
- Core features tested for basic functionality
- Feature branches deleted post-merge
- Updated documentation in repo README

---

## 8. Team Responsibilities & Agile Structure

### Agile Methodology Overview

The team operates under an **Agile framework**:

- **Team members **self-assign issues** from the GitHub Project board.
- **Bi-Weekly Sync Meetings:** Blockers identified, integration challenges resolved, and sprint progress reviewed.
- **Code Review Culture:** Every PR requires at least one peer approval.

### Distributed Responsibilities

Each team member holds a **technical ownership area** and contributes to **project management** through their designated role. This ensures both deep technical expertise and broad project visibility.

---

General roles to be adapted based on specific team preference

### 👤 Member 1: Authentication System & Meeting Manager

**Technical Ownership:**
- User account schema and database setup
- Registration & login endpoints with secure password handling
- Session token management

**Project Management Role:**
- Facilitates weekly planning and issue assignment
- Monitors timeline and flags delays early
- Maintains project board hygiene

---

### 👤 Member 2: User Interface & Product Owner

**Technical Ownership:**
- Front-end boilerplate and responsive layout
- Interactive tile grid component
- Audio player and control UI
- Cross-browser styling and polish

**Project Management Role:**
- Translates goals into clear GitHub issues
- Prioritizes backlog based on impact
- Triages scope and manages feature creep

---

### 👤 Member 3: Puzzle Validation System & QA Lead

**Technical Ownership:**
- Puzzle data structure and win-state logic
- Validation API endpoints
- Support for both manual and procedural puzzles (if implemented)

**Project Management Role:**
- Defines test cases and acceptance criteria
- Coordinates user experience testing
- Documents bugs and quality issues

---

### 👤 Member 4: Backend Data & Release Engineer

**Technical Ownership:**
- Database schema (users, streaks, leaderboard)
- Streak tracking and daily validation logic
- Leaderboard API and aggregation queries
- Deployment configuration and automation

**Project Management Role:**
- Leads code review process
- Manages CI/CD pipelines
- Owns final production deployment

---

### Team Collaboration Practices

**Bi-Weekly Planning (~30-60 minutes):**
- Review sprint progress and blockers
- Self-assign issues from backlog
- Estimate effort and set weekly goals

**Asynchronous Updates (Slack):**
- Quick status on blockers and progress

**Pull Request Workflow:**
1. Developer creates feature branch
2. Implements feature with basic verification
3. Opens PR with clear description
4. Peer review + Release Engineer sign-off
5. Merge to `main`; delete feature branch

**Documentation:**
- README updated with setup and architecture
- Each epic includes a summary of completed tasks
- Deployment runbook created by Week 9

---

## 9. Professionalism & Organization

### Document Structure & Presentation
This proposal is formatted as a **client-facing, professional technical document** suitable for stakeholder review, academic grading, and project kickoff meetings.

- **Clear headings and logical flow:** Each section builds understanding incrementally
- **Research-backed justification:** Problem statement anchored in scientific literature
- **Visual elements:** Tables for tech comparison and timeline milestones
- **Actionable detail:** Each section includes concrete, testable success criteria
- **Transparency:** Stretch goals, risk factors, and flexible contingencies are clearly stated

### TBD-Repository Organization
```
BattleAgainstBrainrot/
├── PROJECT_PROPOSAL.md          (this document)
├── README.md                      (setup & architecture)
├── .github/
│   ├── PULL_REQUEST_TEMPLATE.md  (PR guidelines)
│   ├── ISSUE_TEMPLATE/            (issue & epic templates)
│   └── workflows/                 (CI/CD automation)
├── docs/
│   ├── ARCHITECTURE.md
│   ├── DATABASE_SCHEMA.md
│   ├── API_SPEC.md
│   └── DEPLOYMENT.md
├── frontend/                       (web app code)
├── backend/                        (API server code)
└── .gitignore, LICENSE, etc.
```

### Code of Conduct & Team Norms
- **Respect peer expertise:** Each member owns their domain; support through code review
- **Communicate early:** Blockers surfaced immediately when discovered
- **Merge small, merge often:** PRs should be reviewable in <20 minutes
- **Celebrate wins:** Anytime we can show something off that's working, we should! Just post it in a team chat.

---

## 10. Risk Mitigation & Contingencies

### Adaptive Timeline Approach

**Core Principle:** MVP features are non-negotiable. If any MVP component falls behind, the team adapts by:

1. **Extending MVP timelines** (Week 4 becomes Week 5)
2. **Reducing stretch goals** in proportion to MVP delays
3. **Redistributing workload** among team members (In case of life events)

### Example Contingencies

| Scenario | Adjustment |
|----------|-----------|
| Authentication takes 3 weeks instead of 2 | Skip email verification stretch goal; prioritize core leaderboard |
| Puzzle validation is complex | Reduce initial grid size to 4×4; defer 6×6 and 8×8 sizes |
| Team member unavailable 2 weeks mid-project | Redistribute their tasks; defer lower-priority stretch goals |
| Database setup delayed by cloud provider issues | Use SQLite MVP; migrate to PostgreSQL post-launch |

---

## 11. Success Criteria & Acceptance

### MVP Acceptance Criteria (Target: Week 4)
- [ ] User can register and log in securely
- [ ] User remains authenticated across page refreshes
- [ ] Tile grid renders responsively on desktop and mobile
- [ ] Tiles respond to clicks with visual feedback
- [ ] Puzzle validation correctly identifies solved/unsolved states
- [ ] User's streak increments correctly for daily completions
- [ ] Leaderboard displays top 10 players with streaks

### Final Delivery Acceptance Criteria (Week 10)
- [ ] All MVP criteria met
- [ ] SOFT-At least 1–2 stretch goals implemented (based on timeline)
- [ ] Cross-browser testing passed (Chrome, Firefox, Safari, Edge)
- [ ] Basic performance validation (page load <3s, API response <300ms)
- [ ] Zero critical bugs in production
- [ ] Deployment documented and reproducible
- [ ] Team presentation delivered

---

## Conclusion

**BattleAgainstBrainrot** is a well-scoped, technically feasible, and socially meaningful solution to a genuine problem affecting millions of  workers and students. By combining proven game design principles (streaks, leaderboards) with meditative, low-stimulation mechanics, the app hopes to help users to reclaim their attention rather than punishing distraction.

Within 10 weeks, a focused team can deliver a production-ready web application that demonstrates the viability of the concept and provides a foundation for future expansion. The adaptive MVP-first approach ensures that core features ship on time while stretch goals remain safely optional.

**Let's get Puzzlin'!**

---

## References

[1] [Recent research on digital attention and cognitive fragmentation](https://pmc.ncbi.nlm.nih.gov/articles/PMC11939997/)

---

## Appendix: GitHub Project Board Setup

All development tasks are tracked in the **GitHub Projects Kanban board** organized by epic:

- **Epic 1:** User Interface (UI/UX) — 6 child issues
- **Epic 2:** Puzzle Validation System — 5 child issues
- **Epic 3:** User Authentication & Profile Engine — 6 child issues
- **Epic 4:** Global Streak & Leaderboard Backend — 4 child issues
- **Epic 5:** Project Infrastructure & Shared Deployment — 4 child issues

**Total: 25 actionable child issues across 5 epics**

Each issue includes acceptance criteria and an assigned owner. The board is updated continuously throughout the 10-week cycle; stakeholders can view progress at any time.

---

**Document Version:** 2.0  
**Last Updated:** 2026-10-03  
**Prepared By:** MisterMeddler (Wesley Reitz) using GitHub Copilot as well as Google Ai and Grammarly to populate issues and sub-issues, as well as formatting and citation creation.
