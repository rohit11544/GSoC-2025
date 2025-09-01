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
- <b>Preferred communication</b>: Email

<h2 id="project-details">📝 Project Details</h2>

<b>Title</b>: Improve tests for all REST API endpoints

<b>Overview</b>:
This work strengthens the SW360 REST layer by adding comprehensive integration tests across all resource controllers, covering CRUD flows, pagination, filtering, sorting, attachments, relationships, negative/error paths, and authorization-sensitive routes. The suite is built on Spring Boot’s TestRestTemplate and mocks for service boundaries where appropriate, and it produces JaCoCo coverage reports to guide future improvements. Repository: [eclipse-sw360/sw360](https://github.com/eclipse-sw360/sw360). Tests live under `rest/resource-server/src/test/java/.../integration`.

<b>Goals</b>:
- Add tests for all endpoints across controllers using the existing Java/Spring/Maven stack.
- Improve coverage by exercising multiple scenarios per endpoint (success, invalid, empty, and auth/error cases).
- Establish a baseline coverage report with JaCoCo; next step: surface coverage in GitHub Actions.

<h2 id="milestones">🏁 Milestones</h2>

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

- Mentor: [Gaurav Mishra](https://github.com/GMishx) , [Rudra Chopra](https://github.com/rudra-superrr)

<h2>Media</h2>

- Coverage report for each package : 
  - ProjectTest coverage : <img width="1200" height="483" alt="image" src="https://github.com/user-attachments/assets/2b7e3b67-e56d-4771-85e6-5c6c3a8ff365" />
  
  - ComponentTest coverage : <img width="1116" height="287" alt="image" src="https://github.com/user-attachments/assets/1ebc8068-75e3-4159-8bff-a955840a37a6" />
  
  - ReleaseTest coverage : <img width="1166" height="382" alt="image" src="https://github.com/user-attachments/assets/6239e31f-32aa-4f03-a0c0-d31718cda30e" />

  - UserTest coverage : <img width="1062" height="283" alt="image" src="https://github.com/user-attachments/assets/913df021-ac1d-4a03-8e02-dd85aedcf419" />

  - SearchTest coverage : <img width="1062" height="283" alt="image" src="https://github.com/user-attachments/assets/6d0bcc8e-eb36-41ef-ab54-e04eaee3d4b7" />

  - VendorTest coverage : <img width="1062" height="283" alt="image" src="https://github.com/user-attachments/assets/3b31ce04-ad0d-4040-8d53-e7245ca94b10" />

  - VulnerabilityTest coverage : <img width="1218" height="356" alt="image" src="https://github.com/user-attachments/assets/e58e738f-3fc9-4561-a67e-b624f3f6bc61" />

  - ScheduleTest coverage : <img width="1079" height="249" alt="image" src="https://github.com/user-attachments/assets/da4a0973-4d88-4eaa-9128-ea49849a4c18" />

  - PackageTest coverage : <img width="1079" height="249" alt="image" src="https://github.com/user-attachments/assets/19552381-ca52-4037-a52d-f5fe3d3ed0e5" />

  - ImportExportTest coverage : <img width="1079" height="249" alt="image" src="https://github.com/user-attachments/assets/456dc369-8855-418a-86b7-f2148f3419b1" />

  - LicenseTest coverage : <img width="1079" height="249" alt="image" src="https://github.com/user-attachments/assets/f2dbc62a-48cc-4520-90d8-ff2010aaff3d" />

  - ModerationRequestTest coverage : <img width="1168" height="335" alt="image" src="https://github.com/user-attachments/assets/1e500bd3-2dad-440d-89b5-4b88bea4a474" />

  - DatabaseSanitationTest coverage : <img width="1156" height="243" alt="image" src="https://github.com/user-attachments/assets/d1855035-8b6c-4074-8b70-92e613bc3f37" />

  - DepartmentTest coverage : <img width="1156" height="243" alt="image" src="https://github.com/user-attachments/assets/6fcde8f2-31e5-42ce-b097-a26b5e9768a0" />

  - EccTest coverage : <img width="1018" height="229" alt="image" src="https://github.com/user-attachments/assets/8418e528-45da-4cd4-9c2b-cea881c92836" />

  - ConfigurationsTest coverage : <img width="1140" height="261" alt="image" src="https://github.com/user-attachments/assets/78f558ae-27cc-440f-b588-f9187e9129eb" />

  - ClearingRequestTest coverage : <img width="1140" height="261" alt="image" src="https://github.com/user-attachments/assets/c4fd24eb-0a63-4604-a5ec-4ec40c42ba73" />

  - ChangeLogTest coverage : <img width="1200" height="262" alt="image" src="https://github.com/user-attachments/assets/a8b15913-74fc-4934-9208-6e46d5b8e4fa" />

  - AttachmentTest coverage : <img width="1122" height="304" alt="image" src="https://github.com/user-attachments/assets/929dfb88-d254-4489-bd3e-98bbbfb973b1" />

  - ObligationTest coverage : <img width="1130" height="255" alt="image" src="https://github.com/user-attachments/assets/7bb5b0df-21e2-4a22-8302-1cec83848e41" />


<h2>Future Work</h2>

- Publish coverage to GitHub Actions and add a coverage badge.
- Continue increasing coverage for Components, Projects, and Releases.

<h2>Links</h2>

- SW360 repository: [eclipse-sw360/sw360](https://github.com/eclipse-sw360/sw360)
