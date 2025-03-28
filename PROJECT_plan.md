# OpenStreetMap API documentation - project plan
<!--- Extract: analyze, synthesize, adjust (repeat). --->
## WORKFLOW
> VSC project (Markdown) -> integrate with GitHub desktop -> integrate with GitHub web -> public repository share with collaborators on GitHub Pages -> collaborators creates branches **Review** and **peerReview** -> cycle of push/pull/merge inside the project -> project publish on GitHub Pages with changes.

> Owner invite colaborators (via private mails) and merge branches (commits) to main. Proposal naming for branches: type (Review, peerReview) + initials (AR, KS, PK). Result:
- ReviewAR,
- peerReviewKS,
- peerReviewPK.

## SCHEDULE
> Also available on JIRA. Deadlines:
- [x]  March 13 - Organizational meeting (live).
- [x]  March 21 - Project plan.
- [ ]  April 13 - 20% draft.
- [ ]  April 21 - 100% draft (live checking).
- [ ]  May 10 - project fully reviewed (supervisor + peer reviewers).
- [ ]  May 17 - project published with changes.
- [ ]  May 24 - final exam, graduation.
> Bottlenecks identified (2), presentation preparedness time secured.

## PLAN
Navigation in Unified Modeling Language (UML):
> **[concept](#concept) -> [task](#tasks) <-> [reference](#reference) -> [result](#result)**

### Requirements
> Standards and good practices:
1. Doc is legal (complies with the UE/PL law).
2. Doc is transparent (reveal sources and human-machine interaction).[^1](#footnotes)
3. Doc is standardized (ISO/IEC CD 18019 / ISO standard 2001).
4. Doc is using Style Guide (optional).
5. Doc is *user friendly* (users: developers).
6. Doc is *machine friendly* (CDT-writing-forMT / UE guideline 2021).
7. Doc is using STE (ASD-STE100 / 2021).
8. Doc is open source (public repository).

> Info: Requirements checked with Hemingway App.[^2](#footnotes)

### Concept
^[Back to plan](#plan)^
> Migrate existing API. Reuse, reduce, improve, secure (RRIS).
1. Find item (open source API) to migration:
<!--
   1. User friendly text.
      - Machine friendly text.
-->
   - Find a list of open APIs:
      - [GitHub open API list](https://github.com/public-apis/public-apis)
   - Check categories of the list:
      - [GitHub open API list/Index](https://github.com/public-apis/public-apis?tab=readme-ov-file#index)
   - Select category from the list:
      - [GitHub open API list/Index/category](https://github.com/public-apis/public-apis?tab=readme-ov-file#geocoding)
   - Select item from the category:
      - GitHub open API list/Index/category/item = **64** (position on list).
       > Result: [item](#item).
2. Find model and anylze it.
    > Result: [eligible model](#model).
3. Check list of available frameworks for static pages that fit best.
   > Result: [framework](#framework).
4. Secure backup framework.
    > Result: [backup framework](#backup-framework).

#### Item
> Item data:

| API | Description | Auth | HTTPS | CORS |
--- | --- | --- | --- | ---
| [OpenStreetMap](https://wiki.openstreetmap.org/wiki/API_v0.6#Close:_POST_/api/0.6/notes/#id/close) | Navigation, geolocation and geographical data | OAuth | No | Unknown |
<!-- Distincion factor of the item in 'geocoding category': only with oAuth --->
> Item format:
- two columns.
> Item values:
- exist and works, but:
    - wiki format is deprecated,
    - usability can be increased.

^[back to concept](#concept)^
#### Model
> Model data:

| API | Description | Auth | HTTPS | CORS |
--- | --- | --- | --- | ---
| [Spotify](https://developer.spotify.com/documentation/web-api) | View Spotify music catalog, manage users' libraries, get recommendations and more | OAuth | Yes | Unknown |

> Model format:
- three columns.

> Model values:
- exist, works, is popular, becasue:
  - usability (UI, UX):
    - first column *TOC* is stable and scrollable,
    - second column *content* in condensed (wrapped) and structured,
    - third column *code* apears if needed and operate with *reverse navigation*.
      <!-- 'rev nav' = single page content navigation? --->
    -  Includes:
       - request body sample (Swagger/Postman),
            - request sample (cURL, HTTPie)
            - response sample (JSON).
<!--- Convergence factor between item and model: oAuth --->
^[back to concept](#concept)^
#### Framework
[mkdocs](https://www.mkdocs.org)
> Model data:
static webpage generator:
  - powered by Python,
  - configured with .yaml,
  - published on GitHub Pages (or others).
> Model format:
- three columns with *reverse usability*.

^[back to concept](#concept)^
#### Backup framework
[just-the-docs](https://just-the-docs.github.io/just-the-docs/)
> Model data:
static webpage generator:
  - powered by Jekyll,
  - configured with .yaml,
  - published on GitHub Pages.
> Model format:
- two columns, but exist improvement to three columns variant. Solutions:
  - three_column.html (custom layout),
  - config.yaml (modification),
  - custom.js (dynamic content in JS).

#### Scenario
[devScenario](PROJECT_devScenario.md) dedicated to get the results.

^[back to concept](#concept)^
### Tasks
^[Back to plan](#plan)^
- [x] March 13 - Organizational meeting (live):
  - [x] establish the rules,
  - [x] create plan,
  - [x] public plan,
  - [x] share plan with the team.
- [x] March 21 - Project plan:
  - [x] analyze review changes,
    - [ ] apply changes (add PROJECT_devScenario),
  - [ ] set up and test the environment,
    - [ ] built eligible template (fix bug if needed or change template),
    - [ ] put 15% of content to the template. 
- [ ] April 13 - 20% draft:
  - [ ] 100% content in new template,
- [ ] April 21 - 100% draft (live checking),
  - [ ] adjustments in meantime of review,
- [ ] May 10 - project fully reviewed (supervisor, peer reviewers).
  - [ ] fix bugs, merge changes.  
- [ ] May 17 - project published with changes.
  - [ ] create presentation.
- [ ] May 24 - final exam, graduation.
### Reference
^[Back to plan](#plan)^

[API knowledge source](https://idratherbewriting.com/learnapidoc/)

[OSM main page](https://wiki.openstreetmap.org/w/index.php?title=Pl:Strona_g%C5%82%C3%B3wna&uselang=pl)
### Result
^[Back to plan](#plan)^
> Migration completed if:
- Option 1 - minimal - two colums with increased usability:
  - [ ] wiki -> just-the-docs.
- Option 2 - optimal - three columns (third column *showcase only*):
  - [ ] wiki -> just-the-docs + third column.
- Option 3 -> maximal - three columns (third with reverese usability):
  - [ ] wiki -> mk-docs.
> Knowledge benefits:
1. Understand Application Programming Interface (API) mechanic.
2. Understand OpenStreetMap (OSM) software purpose and development.
> Additonal benefits:
- connection with SMEs (devs) established,
- open source admins (OSM) informed.
---
## Footnotes
[^1]:
> No LLM/AI involved in draft structure.

> LLM/AI used for one reasearch: how to upgrade [backup framework](#backup-framework) solution.

[^2]: 

[Hemingway editor web link](https://hemingwayapp.com/)

Result for points 1-8:
- Readability Grade 3 Good. Words:68
- 0 of 17 sentences are very hard to read.
- 0 of 17 sentences are hard to read. 1 weakener.
- 0 words with simpler alternatives.

^[Back to plan](#plan)^