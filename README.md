# Awesome vCon [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

A curated list of the vCon (Virtualized Conversation) standard—specs, SDKs, tools, datasets, tutorials, community, and production adopters.

> vCon is a JSON-based, signed/encrypted container for complete conversations—participants, media, analysis, and attachments—with extensions for consent and lifecycle.

---

## Contents

- [Overview](#overview)
- [Specifications](#specifications)
- [SDKs & Libraries](#sdks--libraries)
- [Servers & Platforms](#servers--platforms)
- [Developer Tools](#developer-tools)
- [Data & Samples](#data--samples)
- [Use Cases & Case Studies](#use-cases--case-studies)
- [Related Standards & Tech](#related-standards--tech)
- [Documentation & Tutorials](#documentation--tutorials)
- [Community & Events](#community--events)
- [Name Collisions & Caveats](#name-collisions--caveats)
- [Contributing](#contributing)
- [License](#license)

---

## Overview

- **IETF vCon Working Group** — charter, drafts, agendas.  
  https://datatracker.ietf.org/group/vcon/documents/

- **“vCon: an Open Standard for Conversation Data”** — whitepaper/slide deck that seeded the effort.  
  https://www.slideshare.net/slideshow/vcon-an-open-standard-for-conversation-datapdf/252048502

- **Official docs hub (GitBook)** — approachable intro, FAQ, examples.  
  https://docs.vcons.org/

---

## Specifications

- **Core container (Internet-Draft)** — JSON schema, signing (JWS), encryption (JWE), media inline or by URL.  
  Datatracker: https://datatracker.ietf.org/doc/draft-ietf-vcon-vcon-container/  
  HTML: https://ietf-wg-vcon.github.io/draft-ietf-vcon-vcon-container/draft-ietf-vcon-vcon-container.html

- **Overview** — purpose, analogies (vCard/PDF), scope.  
  https://datatracker.ietf.org/doc/draft-ietf-vcon-vcon-overview/

- **Privacy Primer** — consent, minimization, redaction guidance mapped to fields.  
  https://datatracker.ietf.org/doc/draft-ietf-vcon-privacy-primer/

- **Contact Center Extension** — roles, CC-specific metadata in `party`.  
  https://datatracker.ietf.org/doc/draft-ietf-vcon-cc-extension/

- **Consent Attachment** — standardized consent record inside a vCon.  
  https://datatracker.ietf.org/doc/draft-howe-vcon-consent/

- **Lifecycle + SCITT** — provenance/audit log of create/process/redact/delete.  
  https://datatracker.ietf.org/doc/draft-howe-vcon-lifecycle/

- **MIMI Messages mapping** — representing chat threads as vCons.  
  https://rohanmahy.github.io/vcon-mimi-messages/draft-mahy-vcon-messages.html

- **Contact-center use cases & requirements (informational)**  
  https://www.ietf.org/archive/id/draft-rosenberg-vcon-cc-usecases-01.html

---

## SDKs & Libraries

### Python (reference path)

- **py-vcon** — core Python API + CLI; signing/encryption; filter plugin architecture; server package included.  
  https://github.com/py-vcon/py-vcon

- **py-vcon-server** — FastAPI service for ingestion, pipelines, workers.  
  https://github.com/py-vcon/py-vcon/blob/main/py_vcon_server/README.md

- **vcon-lib** — core Python models & validation.  
  https://github.com/vcon-dev/vcon-lib

- **Pydantic models (community)** — experimental models for strict validation.  
  https://github.com/vcon-dev

### JavaScript/TypeScript

- **vcon-js** — create/parse vCons in Node/browser (alpha).  
  https://github.com/vcon-dev/vcon-js

---

## Servers & Platforms

- **Open-source Conserver** — reference vCon store/processor; REST ingest, plugins, workers; Dockerized.  
  Docs: https://www.conserver.io/vcon-library  
  py-vcon-server: https://github.com/py-vcon/py-vcon/blob/main/py_vcon_server/README.md

- **vConGPT** — managed, enterprise-grade Conserver with SCITT audit, E2E encryption, SLAs.  
  http://vcongpt.com/

- **Strolid Conserver Platform** — commercial platform built by vCon originators.  
  https://strolid.ai/vcon-conservers/

---

## Developer Tools

- **CLI & Validator** — ship with `py-vcon` (`vcon` commands) for create/merge/validate.  
  https://github.com/py-vcon/py-vcon

- **vcon-admin** — Streamlit admin for stores; import/export (Redis, S3, Mongo, JSONL), logs, inspector, Milvus vector search, OpenAI workbench.  
  https://github.com/vcon-dev/vcon-admin

- **vcon_faker** — generator for realistic fake vCons and audio; S3 upload helpers.  
  https://github.com/vcon-dev/vcon_faker

- **vCon Right-to-Know** — GDPR/CCPA SAR demo: search by identity to access/delete.  
  https://github.com/vcon-dev/vcon-right-to-know

- **vCon App Template** — full-stack starter for building vCon apps.  
  https://github.com/vcon-dev/vcon-app-template

- **Interoperability repos** — test vectors & cross-impl checks.  
  https://github.com/vcon-dev

- **Visual Pipeline Editor** — no-code graph to chain processors (speech-to-text → sentiment → …) in Conserver.  
  https://www.conserver.io/vcon-library

---

## Data & Samples

- **Fake vCons** — sample JSON corpora for testing and demos.  
  https://github.com/vcon-dev

- **App demo: vCon Diary** — Streamlit app pulling calls, transcribing/summarizing, storing as vCons (CarrierX + OpenAI + Mongo).  
  https://github.com/vcon-dev/vcon-app-template

---

## Use Cases & Case Studies

- **Contact Center interop** — single, vendor-neutral container replaces ad-hoc exports.  
  https://www.ietf.org/archive/id/draft-rosenberg-vcon-cc-usecases-01.html

- **AI conversation intelligence** — analysis-ready JSON enables fleet-scale summarization, topic/sentiment mining.  
  Clarity Voice x Strolid x Creo: https://europeanbusinessmagazine.com/accessnewswire/clarity-voice-partners-with-creo-solutions-and-strolid-to-revolutionize-ai-powered-conversational-analytics-and-prescriptive-insights/  
  TeleCloud blog: https://telecloud.net/blog/what-are-vcons

- **Compliance & e-discovery** — sign (JWS) for integrity, encrypt (JWE), consent records, SAR automation.  
  Privacy primer: https://datatracker.ietf.org/doc/draft-ietf-vcon-privacy-primer/  
  Legal explainer: https://commlawgroup.com/2024/privacy-and-security-law-101-and-how-the-vcon-protocol-can-help-with-compliance/

- **Lifecycle provenance** — SCITT-backed audit trail of create/process/redact/delete.  
  https://datatracker.ietf.org/doc/draft-howe-vcon-lifecycle/

- **Providers adopting vCon**  
  Frontline Group 211 pilot: https://www.prnewswire.com/news-releases/frontline-group-launches-vcon-pilot-302472140.html  
  Phound (CarrierX) Magnum AI: https://channelvisionmag.com/phound-intros-magnum-ai-phone-service/  
  KweKwe vCon export: https://kwekwe.io/documentation/vcon-export/

---

## Related Standards & Tech

- **STIR/SHAKEN (PASSporT)** — attach caller identity tokens in `party.stir` for verified identities.  
  https://transnexus.com/blog/2020/passports/

- **JOSE (JWS/JWE)** — signatures and encryption for integrity & confidentiality.  
  JWE: https://datatracker.ietf.org/doc/html/rfc7516/

- **SCITT** — transparency log for vCon lifecycle and AI training lineage.  
  https://datatracker.ietf.org/doc/draft-howe-vcon-lifecycle/

- **MIMI** — interop for messaging; example mapping of chats to vCon.  
  https://rohanmahy.github.io/vcon-mimi-messages/draft-mahy-vcon-mimi-messages.html

- **SIPREC/WebRTC** — transport/recording complements; vCon is the after-the-fact container.  
  https://webrtc.org/

---

## Documentation & Tutorials

- **Docs hub** — approachable intro, FAQ, quick starts.  
  https://docs.vcons.org/

- **Conserver docs & cheat sheet**  
  https://www.conserver.io/vcon-library/cheat-sheet

- **py-vcon README & wiki** — quick start, release notes.  
  Repo: https://github.com/py-vcon/py-vcon  
  Wiki: https://github-wiki-see.page/m/py-vcon/py-vcon/wiki/py_vcon_server_release_0.4.0

- **Cavell guide** — third-party market/benefits overview.  
  https://www.cavell.com/a-comprehensive-guide-to-vcon-in-communications/

- **Talks & webinars**  
  ClueCon 2024 (Pulver & Howe): https://www.youtube.com/watch?v=CpE2ggaSm6c  
  IETF 121/123 sessions: https://www.youtube.com/watch?v=d5A7P5QdB0c  
  WeeklyWed intro: https://www.youtube.com/watch?v=d0X-5WlTfhU  
  TADSummit: “Geeky Side of vCon”: https://blog.tadsummit.com/2025/05/02/dan-petrie-the-geeky-side-of-vcon/

- **Events**  
  VON: Fall ’25 vCon: https://www.vonevolution.com/fall25vcon  
  TADHack resources: https://blog.tadhack.com/2024/02/22/tadhack-open-resources/  
  CASA25 Amsterdam: https://casa25.amsterdam/author/robkurver/

---

## Community & Events

- **vCon Open Forum** — community portal, Zulip chat, public Conserver sandbox.  
  https://vcons.org/

- **IETF WG mailing list & archives** — technical discussions, draft updates.  
  Mail archive: https://mailarchive.ietf.org/arch/browse/vcon/  
  WG page: https://datatracker.ietf.org/group/vcon/

- **GitHub orgs**  
  https://github.com/vcon-dev  
  https://github.com/py-vcon

---

## Name Collisions & Caveats

- **Not this “VCON”** — *vcon.io* (Cesanta) is an IoT OTA/serial tool and unrelated to Virtualized Conversations.  
  https://vcon.io/

- “VCON” also appears in legacy videoconferencing product slides on SlideShare; they’re unrelated to the IETF vCon standard.

---

## Contributing

PRs welcome! Please:

- Add resources that are **maintained**, **useful**, and **neutral**.
- Keep entries consistent: `[Name](link) — one-line description`.
- Avoid commercial fluff; prefer docs, code, and substantive write-ups.

---

## License

**MIT** — See [`LICENSE`](LICENSE).
