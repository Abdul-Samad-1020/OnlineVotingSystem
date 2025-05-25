# Enhanced Voting Database System

## Overview

This SQL script creates a comprehensive, normalized voting system database (`voting_db_enhanced`) for teaching and demonstration purposes. It includes advanced concepts such as:

- **Primary Keys, Foreign Keys, Unique Constraints**
- **Normalization up to 3NF**
- **Full range of Relationships**: 1:1, 1:M, M:M
- **Comprehensive JOIN examples**: INNER, LEFT, RIGHT, FULL OUTER (simulated), SELF, CROSS
- **Views for analytics/reporting**
- **Stored Procedures & Triggers** for business logic and data integrity
- **Audit Trail** for system actions
- **Indexes for performance**
- **Sample Data** for all tables

---

## Table Structure Summary

| Table                       | Description                            | Key Concepts Demonstrated    |
|-----------------------------|----------------------------------------|-----------------------------|
| `parties`                   | Political parties registry             | PK, UNIQUE, 3NF             |
| `election_types`            | Types of elections                     | PK, UNIQUE, 3NF             |
| `addresses`                 | Voter address normalization            | PK, 1:M                     |
| `voters`                    | Registered voters                      | PK, FK, UNIQUE, 1:M         |
| `elections`                 | Elections (events)                     | PK, FK, CHECKS, 1:M         |
| `candidates`                | Candidates for elections               | PK, FK, UNIQUE, 1:M, M:M    |
| `votes`                     | Votes cast with audit trail            | PK, FK, UNIQUE, 1:M         |
| `election_voter_eligibility`| Eligibility for voters per election    | Composite PK, FK, M:M       |
| `voter_profiles`            | Extended voter information             | PK, UNIQUE, 1:1, JSON       |
| `system_audit_logs`         | System action log                      | PK, FK, JSON, Triggers      |

---

## Sample Data

- Parties, election types, addresses, voters, elections, candidates, votes, and eligibility are all pre-populated with realistic demo data for hands-on querying.

---

## Relationships

- **One-to-One:** `voters` ↔ `voter_profiles`
- **One-to-Many:** `addresses` → `voters`, `elections` → `candidates`
- **Many-to-Many:** `voters` ↔ `elections` (via `election_voter_eligibility`)
- **Self-referencing:** `system_audit_logs.user_id` → `voters.voter_id`

---

## Advanced Features

- **Views:** `election_results_summary`, `voter_participation_summary`
- **Stored Procedures:** 
  - `RegisterVoterForElection`: Validates and registers a voter for an election.
  - `CastVote`: Validates and records a vote, with business rules enforced.
- **Triggers:** 
  - `update_voter_last_login`: Automatically updates login time.
  - `prevent_late_voting`: Prevents voting after an election ends.
- **Window Functions:** For ranking and analytics in complex queries.
- **Business Rule Enforcement:** 
  - One vote per voter per election.
  - Only eligible voters can vote.
  - Candidates must be verified voters.
  - Date consistency for elections and registration.
- **Comprehensive JOINs:** Multiple examples of all JOIN types, including simulated FULL OUTER JOIN.

---

## Example Queries

- **Election results, voter participation, party stats, demographic analytics, data integrity validation, and more.**
- **Analytical queries** use window functions and CTEs for advanced statistics.

---

## Usage

1. **Run the script in a MySQL 8+ environment**.
2. **Explore the database**: Use provided queries for JOINs, analytics, and validation.
3. **Extend**: Add more elections, voters, or business logic as needed.

---

## Notes

- The schema is designed for teaching and demonstration; adapt for production use with appropriate security and scalability considerations.
- The audit trail and triggers provide a foundation for compliance and traceability.

---

## License

Open for educational and demonstration purposes.
