<h1 align="center">Google Summer of Code 2025</h1>

<div align="center"><h2><i>Improve tests for all REST API endpoints — Eclipse SW360</i></h2></div>

<p align="center">
  <a href="#project-details">Project Details</a> |
  <a href="#milestones">Milestones</a> |
  <a href="#contributions">Contributions</a> |
  <a href="#deliverables">Deliverables</a> |
  <a href="#takeaways">Key Takeaways</a> |
  <a href="#acknowledgements">Acknowledgements</a>
</p>

<h2>Profile</h2>

- <b>Name</b>: Rohit Borra
- <b>Country</b>: India
- <b>Email</b>: brohit11544
- <b>Current role</b>: Software Developer (Backend)
- <b>GitHub</b>: [rohit11544](https://github.com/rohit11544)
- <b>LinkedIn</b>: [Rohit Borra](https://www.linkedin.com/in/rohit-borra-67758a1a2/)
- <b>Preferred communication</b>: email

<h2 id="project-details">📝 Project Details</h2>

<b>Title</b>: Improve tests for all REST API endpoints

<b>Overview</b>:
This work strengthens the SW360 REST layer by adding comprehensive integration tests across all resource controllers, covering CRUD flows, pagination, filtering, sorting, attachments, relationships, negative/error paths, and authorization-sensitive routes. The suite is built on Spring Boot’s TestRestTemplate and mocks for service boundaries where appropriate, and it produces JaCoCo coverage reports to guide future improvements. Repository: [eclipse-sw360/sw360](https://github.com/eclipse-sw360/sw360). Tests live under `rest/resource-server/src/test/java/.../integration`.

<b>Goals</b>:
- Add tests for all endpoints across controllers using the existing Java/Spring/Maven stack.
- Improve coverage by exercising multiple scenarios per endpoint (success, invalid, empty, and auth/error cases).
- Establish a baseline coverage report with JaCoCo; next step: surface coverage in GitHub Actions.

<h2 id="milestones">🏁 Milestones</h2>

Derived from the implemented test classes (SpecTest → Test), grouped logically.

- Core domain
  - Projects: end‑to‑end CRUD, search and filters, links, attachments, license clearing, SBOM import, reports
  - Components: listing, field selection, updates, merge/split, attachments, relationships
  - Releases: retrieval, search, attachments, usedBy, subscriptions, SPDX licenses, relationships, Fossology triggers
  - Users: tokens and profile APIs
- Supporting domain
  - Vendors: CRUD, search, releases, merge, exports
  - Packages: CRUD, complex search, relationships
  - Licenses/LicenseTypes/Obligations: CRUD, imports/exports, obligations links, whitelist
- Governance & workflows
  - Moderation Requests: list/byState/mySubmissions, validate, delete
  - Clearing Requests: lifecycle + comments
  - Change Logs: document change history
- Platform & infra
  - Schedule: schedule/unschedule/status for background jobs
  - Health: health readiness checks
  - Configurations: get/update, containers
  - Database Sanitation: duplicate search
  - Import/Export: templates, uploads, downloads
  - ECC: CRUD
  - Search: global search
  - Attachments: by SHA/download/upload

<h2 id="contributions">🚀 Contributions</h2>

- Added comprehensive integration tests for 21 areas of the REST API.
- Covered CRUD, pagination, filtering, sorting, relationships, attachments, and negative/error cases.
- Produced JaCoCo coverage; next step: publish coverage via GitHub Actions.

<b>Per‑controller endpoint coverage (examples; non‑exhaustive)</b>

- Components (`/api/components`): list, get, patch, delete, mycomponents, mySubscriptions, recentComponents, searchByExternalIds, attachments (POST/DELETE/download), merge/split, `{id}/releases`, `{id}/vulnerabilities`.
- Releases (`/api/releases`): list, get (single/batch), usedBy, attachments (POST/GET/DELETE), recentReleases, search, externalId, subscriptions, SPDX licenses, transitive releases, checkCyclicLink, vulnerability links, Fossology triggers/status.
- Projects (`/api/projects`): list, get, myprojects, link/unlink projects and packages, releases, attachments, license clearing and headers/count, vulnerability summary/list, license obligations, SBOM import (by type and file), reports.
- Vendors (`/api/vendors`): CRUD, releases, mergeVendors, exportVendorDetails.
- Vulnerabilities (`/api/vulnerabilities`): CRUD, trackingStatus, releaseVulnerabilityRelation, delete release links; negative CVE cases.
- Licenses/LicenseTypes/Obligations: license CRUD/imports/uploads/whitelist, licenseTypes list/get, obligations CRUD + batch get.
- Moderation Requests: list/byState/mySubmissions, validate, delete.
- Clearing Requests: lifecycle and comments.
- Configurations: get/update, container operations.
- Department: import scheduling, path configuration, logs and log content, members.
- Import/Export: component/release templates and links, users export, uploads, componentAttachment uploads.
- Schedule: schedule/unschedule/status endpoints for multiple services.
- ECC, Health, Search, DatabaseSanitation, Attachments: CRUD and utilities as present in tests.

<h2 id="deliverables">👨🏻‍🏫 Deliverables</h2>

| S.No | Endpoint Type                                 | Status  | PR                                               | Coverage |
| :---:| :-------------------------------------------- | :-----: | :----------------------------------------------- | :------: |
| 1    | ProjectSpecTest → ProjectTest                 | Merged  | [PR](https://github.com/eclipse-sw360/sw360/pull/3284) | 37%      |
| 2    | ComponentSpecTest → ComponentTest             | Merged  | [PR](https://github.com/eclipse-sw360/sw360/pull/3263) | 41%      |
| 3    | ReleaseSpecTest → ReleaseTest                 | Merged  | [PR](https://github.com/eclipse-sw360/sw360/pull/3281) | 15%      |
| 4    | UserSpecTest → UserTest                       | Merged  | [PR](https://github.com/eclipse-sw360/sw360/pull/3267) | 71%      |
| 5    | SearchSpecTest → SearchTest                   | Done    | NA                                               | 82%      |
| 6    | VendorSpecTest → VendorTest                   | Merged  | [PR](https://github.com/eclipse-sw360/sw360/pull/3307) | 90%      |
| 7    | VulnerabilitySpecTest → VulnerabilityTest     | Merged  | [PR](https://github.com/eclipse-sw360/sw360/pull/3309) | 70%      |
| 8    | ScheduleSpecTest → ScheduleTest               | Merged  | [PR](https://github.com/eclipse-sw360/sw360/pull/3310) | 85%      |
| 9    | PackageSpecTest → PackageTest                 | Merged  | [PR](https://github.com/eclipse-sw360/sw360/pull/3313) | 76%      |
| 10   | ImportExportSpecTest → ImportExportTest       | Merged  | [PR](https://github.com/eclipse-sw360/sw360/pull/3305), [PR](https://github.com/eclipse-sw360/sw360/pull/3306) | 94%      |
| 11   | LicenseSpecTest → LicenseTest                 | Merged  | [PR](https://github.com/eclipse-sw360/sw360/pull/3311) | 70%      |
| 12   | ModerationRequestSpecTest → ModerationRequestTest | Merged  | [PR](https://github.com/eclipse-sw360/sw360/pull/3348) | 87%      |
| 13   | HealthSpecTest → HealthTest                   | Merged  | [PR](https://github.com/eclipse-sw360/sw360/pull/3299) | —        |
| 14   | DatabaseSanitationSpecTest → DatabaseSanitation | Merged | [PR](https://github.com/eclipse-sw360/sw360/pull/3346) | 100%     |
| 15   | DepartmentSpecTest → DepartmentTest           | Merged  | [PR](https://github.com/eclipse-sw360/sw360/pull/3344) | 100%     |
| 16   | EccSpecTest → EccTest                         | Done    | NA                                               | 86%      |
| 17   | ConfigurationsSpecTest → ConfigurationsTest   | Merged  | [PR](https://github.com/eclipse-sw360/sw360/pull/3308) | 100%     |
| 18   | ClearingRequestSpecTest → ClearingRequestTest | Merged  | [PR](https://github.com/eclipse-sw360/sw360/pull/3347) | 82%      |
| 19   | ChangeLogSpecTest → ChangeLogTest             | Merged  | [PR](https://github.com/eclipse-sw360/sw360/pull/3343) | 100%     |
| 20   | AttachmentSpecTest → AttachmentTest           | Merged  | [PR](https://github.com/eclipse-sw360/sw360/pull/3298) | 72%      |
| 21   | ObligationSpecTest → ObligationTest           | Merged  | [PR](https://github.com/eclipse-sw360/sw360/pull/3314) | 80%      |

<b>Coverage reporting</b>: JaCoCo configured locally; next step is to publish coverage in CI (GitHub Actions) and surface deltas per package.

<h2 id="takeaways">📚 Key Takeaways</h2>

- Balanced full‑time work with consistent GSoC progress; improved time management.
- Practiced clean, maintainable Java test design and refactoring.
- Improved communication and collaboration with mentors/community.
- Deepened understanding of SW360 domain and REST testing patterns.
- Built reliable data seeding and mocking patterns across controllers.
- Strengthened debugging skills for flakiness and environment issues.

<h3>Challenges and how they were addressed</h3>

- Environment setup and realistic data preparation: standardized fixtures and helper utilities.
- Debugging failing tests across modules: isolated boundaries with mocks and added targeted assertions.
- Maximizing coverage with meaningful scenarios: expanded negative/auth cases and relationship paths.

<h2 id="acknowledgements">🎓 Acknowledgements</h2>

- Mentor: [Gaurav Mishra](https://github.com/GMishx)

<h2>Media</h2>

- Insert coverage screenshots for each package (21 placeholders):
  - [Insert] ProjectTest coverage
  - [Insert] ComponentTest coverage
  - [Insert] ReleaseTest coverage
  - [Insert] UserTest coverage
  - [Insert] SearchTest coverage
  - [Insert] VendorTest coverage
  - [Insert] VulnerabilityTest coverage
  - [Insert] ScheduleTest coverage
  - [Insert] PackageTest coverage
  - [Insert] ImportExportTest coverage
  - [Insert] LicenseTest coverage
  - [Insert] ModerationRequestTest coverage
  - [Insert] HealthTest coverage
  - [Insert] DatabaseSanitationTest coverage
  - [Insert] DepartmentTest coverage
  - [Insert] EccTest coverage
  - [Insert] ConfigurationsTest coverage
  - [Insert] ClearingRequestTest coverage
  - [Insert] ChangeLogTest coverage
  - [Insert] AttachmentTest coverage
  - [Insert] ObligationTest coverage

<h2>Future Work</h2>

- Publish coverage to GitHub Actions and add a coverage badge.
- Continue increasing coverage for Components, Projects, and Releases.

<h2>Links</h2>

- SW360 repository: [eclipse-sw360/sw360](https://github.com/eclipse-sw360/sw360)
