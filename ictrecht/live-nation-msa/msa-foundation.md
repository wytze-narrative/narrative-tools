## Overzicht — onderwerpen per fase

De onderwerpen hieronder vormen de structuur van de Decisions log verderop. Per onderwerp zijn de inhoudelijke keuzes, onderbouwing, voorbeeld-clausules en open vragen vastgelegd.

### Fase 0 — Scope & framework
| # | Onderwerp |
|---|-----------|
| 0 | MSA-scope: alleen Protocol Client Automations. Narrative-training én Protocol Owned Products vallen buiten MSA |

### Fase 1 — Foundations
| # | Onderwerp |
|---|-----------|
| 1 | Contracting entities (wie tekent aan welke kant) |
| 2 | Documentarchitectuur + order of precedence (MSA/SoW/DPA) |
| 3 | Term & renewal, termination for convenience, termination for cause |

### Fase 2 — Commercieel
| # | Onderwerp |
|---|-----------|
| 4 | Fees, payment terms, late interest, indexatie |
| 5 | IP model (dual perpetual license) |
| 6 | Acceptance-procedure + change control |

### Fase 3 — Risico
| # | Onderwerp |
|---|-----------|
| 7 | Liability cap-architectuur (aggregate vs per-SoW, super-cap, carve-outs) |
| 8 | Indemnification (IP, data breach, third-party claims) |
| 9 | Warranties (services, IP non-infringement, compliance) |
| 10 | Insurance obligations |

### Fase 4 — Data & Security
| # | Onderwerp |
|---|-----------|
| 11 | DPA-referentie + order of precedence bij conflict |
| 12 | Security baseline (wat commit Narrative minimaal) |
| 13 | Change-control clausule voor shared-infra systemen (gemerged in Sectie 6c) |

### Fase 5 — Operationeel / boilerplate
| # | Onderwerp |
|---|-----------|
| 14 | Confidentiality (mutual, termijn, exceptions) |
| 15 | Non-solicitation / non-poaching |
| 16 | Assignment, subcontracting, affiliates |
| 17 | Force majeure |
| 18 | Notices & escalatiepad |
| 19 | Dispute resolution, recht, jurisdictie |
| 20 | Miscellaneous (entire agreement, severability, waiver, counterparts) |

---

## Achtergrond — Entity-structuur en MSA-scope

Deze sectie legt vast hoe Narrative en Protocol zich tot elkaar verhouden, waarom de MSA alleen onder Protocol BV valt, en wat dit betekent voor toekomstige enterprise-relaties. Bewust royaal opgeschreven zodat ICTRecht én latere sessies hier voldoende context hebben.

### Drie commerciële trajecten — alleen één valt onder deze MSA

Het werk dat Narrative/Protocol levert valt uiteen in drie distincte commerciële trajecten. Elk traject heeft een eigen contract-stack, een eigen DPA-spoor, en een eigen leverende entity. **Alleen Traject 2 (Protocol Client Automations) valt onder deze LN-MSA.** Dit is een bewuste afbakening die de MSA scherp houdt en commercieel correct positioneert — vergelijkbaar met hoe SaaS-vendors als Salesforce, Stripe, Microsoft en Twilio dit afhandelen.

| | **Traject 1: Narrative Training & Advisory** | **Traject 2: Protocol Client Automations** | **Traject 3: Protocol Owned Products** |
|---|---|---|---|
| **Voorbeelden** | AI Fundamentals workshops, MT-sessies, AI Manifesto, AI Year Plan-coaching, advisory | Brand Shield, WhatsApp HR Agent, Mailbox Ticket Counting, custom n8n-workflows | Venue Vera (Booking Risk Agent), F&B Forecasting (toekomstig), Controle Carla, Draaiboek Donna |
| **Leverende entity** | Part of the Narrative B.V. | Part of the Protocol B.V. | Part of the Protocol B.V. |
| **Contract-stack** | Algemene Voorwaarden v1.3 + offerte + mutual NDA | **MSA + SoW + DPA-annex (deze template)** | Subscription Order Form + Protocol's Product Terms + Protocol's eigen DPA |
| **DPA-spoor** | n.v.t. (geen persoonsgegevens in scope) | Klant's DPA-template met de 5 redlines (zie `reference_ln_dpa_template.md` + Besluit 2) | **Protocol's eigen multi-tenant DPA** — niet onderhandelbaar per klant (zoals Microsoft/AWS dat doen) |
| **IP-positie** | Methodology blijft bij Narrative onder AV v1.3 Art 9 | Dual perpetual license: beide partijen eeuwigdurend gebruiksrecht op opgeleverde code; Protocol behoudt template/methodology | Protocol blijft 100% eigenaar; klant krijgt time-bounded license voor de duur van de subscription |
| **Hosting** | n.v.t. | Variabel — per SoW: óf in klant's tenant (bv. Brand Shield in MOJO's eigen n8n-tenant), óf in Protocol's tenant (bv. WhatsApp HR Agent voor AFAS) | Altijd Protocol's tenant (multi-tenant SaaS, één instantie meerdere klanten) |
| **Pricing-model** | Per offerte (workshop-fee, advisory day-rate, retainer) | Fixed-fee build per offerte + optionele managed support (retainer of on-demand uurtarief) | All-in subscription (bv. Venue Vera €7.500 onboarding + €6.500/jaar inclusief hosting + API-kosten + standaard support) |
| **Liability cap** | Standaard AV v1.3 | Onder MSA — zie Sectie 7 | Onder Protocol's eigen Subscription Terms (12 maanden subscription fee + verzekering, conform Besluit 1) |
| **Continuïteit na contract-einde** | Klant houdt training-output (slides, frameworks) onder license | Klant houdt eeuwig gebruiksrecht (dual perpetual) | Klant verliest toegang bij niet-verlengen — product blijft draaien voor andere klanten |

**Waarom Owned Products buiten MSA-scope vallen**:

1. **SaaS-conventie**: Geen serieuze SaaS-vendor accepteert klant-MSA op een product. Salesforce, Stripe, OpenAI, HubSpot, Twilio, AWS — ieder van hen heeft één eigen Subscription Agreement + DPA voor alle klanten. Als wij voor Venue Vera Jennifer's MSA-template zouden tekenen, wordt dat de blueprint voor elke volgende venue (Paradiso, 013, andere LN-venues, niet-LN-venues). Daarmee zou Venue Vera ophouden product te zijn en degraderen tot een reeks bespoke maatwerk-overeenkomsten.

2. **Multi-tenant architectuur vereist standaardisatie**: Venue Vera draait op één Protocol-stack (Vercel + Supabase + n8n self-hosted Hostinger Frankfurt + OpenAI/Apify/Resend) voor meerdere venues tegelijk. Subprocessor-lijst, security baseline, audit-rechten en breach-protocols moeten één keer goed staan — niet per klant heronderhandeld worden.

3. **Schaalbaarheid van het commerciële model**: All-in jaarprijs (€6.500 voor Venue Vera) bevat hosting, API-kosten en standaard managed support. Dit werkt alleen als die kostencomponenten centraal beheerd worden — niet als elke klant een eigen liability-cap of indemnity-structuur afdwingt.

4. **Strategisch al vastgelegd**: Besluit 1 (`dpa-strategy-decisions.md`, 24 apr 2026) bevat dit reeds expliciet. Deze MSA-scope-afbakening is een doorvertaling van die eerdere strategische keuze naar de juiste contract-architectuur.

**Praktische nuance — hosting-locatie ≠ ownership-classificatie**:

Een Client Automation kán in Protocol's tenant draaien zonder dat het daarmee een Owned Product wordt. Het canonieke voorbeeld is de **WhatsApp HR Agent voor AFAS Live**: Protocol bouwt en host (AFAS heeft geen geschikte eigen infra, en de Twilio-WhatsApp-integratie is operationeel makkelijker centraal te beheren), maar het is een custom build voor één klant met klant-specifieke prompts en HR-flows — geen multi-tenant SaaS, geen herverkoop aan andere klanten. **Conclusie**: hosting-locatie is een operationele as, ownership is een commerciële as. Een SoW onder deze MSA kan beide hosting-modellen omvatten zolang de IP-positie en het commerciële model conform Client Automation zijn.

Voor de DPA-annex onder de MSA betekent dit wel iets praktisch: Protocol-tenant-hosting (zoals HR Agent) vraagt om een uitgebreidere security-baseline-uitwerking in de annex — Protocol is dan technisch processor + hosting-infrastructure-provider in één rol. Klant-tenant-hosting (zoals Brand Shield in MOJO's eigen n8n-tenant met MS365-credentials) verlegt het zwaartepunt naar change-control en configuration-responsibility (zie ook Besluit 1's change-control clausule voor Brand Shield).

**Toekomstige enterprise-pattern**:

- **Klant wil Protocol Owned Product afnemen** (bv. een venue wil Venue Vera) → eigen Subscription stack, geen MSA-uitbreiding
- **Klant wil Custom Automation laten bouwen** (bv. nieuwe agent voor MOJO) → SoW onder bestaande LN-MSA als die er is, anders nieuwe MSA per blueprint
- **Klant wil training/advisory** → Narrative + AV v1.3, geen MSA

### De groepsstructuur (vanaf 1 juli 2026)

Per 1 juli 2026 bestaat de Narrative-groep uit twee werk-BV's:

- **Part of the Narrative B.V.** — Wytze de Haan en Xander Kranenburg, 50/50.
- **Part of the Protocol B.V.** — Wytze de Haan, Xander Kranenburg en Bjorn Veldmeijer, ieder 1/3.

Beide BV's zijn op dit moment in oprichting bij notaris Rosalie Wesseling en worden naar verwachting gepasseerd voordat deze MSA wordt ondertekend. Part of the Protocol B.V. wordt onder de MSA de leverende entiteit voor Client Automations; Part of the Narrative B.V. verzorgt training- en advisory-werk onder AV v1.3 en valt buiten de MSA-scope.

### Wat doet Narrative? Wat doet Protocol?

Korte definitie:

> *Waar Narrative zich richt op AI-training in de eventbranche, richt Protocol zich op AI-automatisering in die branche.*

Binnen Protocol bestaan vervolgens twee lijnen — Client Automations en Owned Products — met scherp verschillende commerciële architecturen:

| Activiteit | Onder welke BV | Type traject | Voorbeelden | Onder LN-MSA? |
|---|---|---|---|---|
| Workshops / trainingen | Part of the Narrative BV | Traject 1 (training/advisory) | AI Fundamentals workshops, MT-sessies, awareness-trainingen | Nee — AV v1.3 + offerte |
| AI-strategie / advisory | Part of the Narrative BV | Traject 1 | AI Manifesto/Beleid, jaarplannen-advisory, discovery sessies | Nee — AV v1.3 + offerte |
| AI Year Plan retainers (coaching/advisory-kant) | Part of the Narrative BV | Traject 1 | Coaching, governance, prioritering | Nee — AV v1.3 + retainer |
| Custom builds in klant-tenant | Part of the Protocol BV | Traject 2 (Client Automation) | Brand Shield (MOJO's eigen n8n-tenant), Mailbox Ticket Counting | **Ja** — onder deze MSA |
| Custom builds in Protocol-tenant (single-client) | Part of the Protocol BV | Traject 2 (Client Automation) | WhatsApp HR Agent (AFAS Live) — Protocol host, maar custom voor één klant | **Ja** — onder deze MSA |
| n8n workflow automation per klant | Part of the Protocol BV | Traject 2 | Custom workflow-builds in klant-tenant of Protocol-tenant | **Ja** — onder deze MSA |
| Managed support op Client Automations | Part of the Protocol BV | Traject 2 | Beheer, monitoring, finetuning, error handling | **Ja** — onder deze MSA (retainer of on-demand) |
| Multi-tenant SaaS-producten | Part of the Protocol BV | **Traject 3 (Owned Product)** | Venue Vera (Booking Risk Agent), F&B Forecasting (toekomstig), Controle Carla, Draaiboek Donna | Nee — eigen Subscription stack + eigen Protocol-DPA |

### Waarom alleen één MSA — en alleen voor Client Automations

MSA is alleen nodig waar het juridisch een MSA *vereist*. Dat is Client Automation-werk. Training valt buiten omdat AV v1.3 al volstaat. Owned Products vallen buiten omdat een klant-MSA op een SaaS-product een commercieel anti-pattern is (zie tabel "Drie commerciële trajecten" hierboven).

| MSA-functie | Nodig voor Client Automations? | Nodig voor Narrative-training? | Nodig voor Owned Products? |
|---|---|---|---|
| Liability cap voor data breach / system failure | Ja — HR Agent verwerkt persoonsgegevens, Brand Shield draait in MOJO-tenant met live data | Nee — workshop = geen software, geen data, geen breach-vector | Ja, maar geregeld in Protocol's eigen Subscription Terms (12 mnd subscription fee + verzekering, conform Besluit 1) |
| IP-clausules voor custom software | Ja — dual perpetual license tussen Protocol en klant | Nee — methodology-IP standaard bij Narrative onder AV v1.3 Art 9 | Niet relevant — IP blijft 100% bij Protocol; klant krijgt time-bounded license |
| DPA Art. 28 verplichting (GDPR) | Ja — Klant's DPA-template met de 5 redlines (Besluit 2) | Nee — workshops verwerken geen persoonsgegevens | Ja, maar via Protocol's eigen multi-tenant DPA (zoals Microsoft/Salesforce/AWS); niet onder klant-template |
| Acceptance-procedure / change control | Ja — bouwfase, go-live, bug-fix-cycli, scope-creep-risico | Nee — een workshop is een workshop | Niet als formele acceptance-procedure; product-iteraties via subscription-roadmap |
| SLAs / managed support | Ja — onderdeel van MSA | Nee | Inbegrepen in all-in subscription-fee |

**Track record bevestigt** voor training-zijde: Narrative levert al sinds maart 2025 training/advisory aan MOJO, AFAS Live, Ziggo Dome zonder MSA. Algemene Voorwaarden v1.3 + getekende offerte + mutual NDA dekken het. Geen incidenten, geen juridische open eindes.

### Wat valt buiten MSA-scope

**Traject 1 — Narrative training/advisory** blijft onder:
- Algemene Voorwaarden v1.3 (Part of the Narrative BV) als kader
- Offerte per opdracht (via /proposal skill)
- Mutual NDA waar al gesloten
- Voorbeelden: AI Fundamentals workshops, MT-sessies, in-house trainingen, AI Manifesto, AI Year Plan retainer-coaching, losse adviesopdrachten

**Traject 3 — Protocol Owned Products** komen onder:
- Subscription Order Form per klant (LN tekent aparte order voor bv. Venue Vera, niet onder MSA)
- Protocol's Product Terms & Conditions (multi-tenant, niet onderhandelbaar per klant)
- Protocol's eigen DPA (template van Narrative, niet klant-template — conform Besluit 1 in `dpa-strategy-decisions.md`)
- Voorbeelden: Venue Vera (Booking Risk Agent), F&B Forecasting (toekomstig), Controle Carla, Draaiboek Donna

### Wat valt binnen MSA-scope

Uitsluitend Traject 2 — Protocol Client Automations:
- Custom builds voor één klant (HR Agent voor AFAS, Brand Shield voor MOJO, Mailbox Ticket Counting voor MOJO, toekomstige custom systemen)
- n8n workflow-automation specifiek voor één klant
- Managed support op die Client Automations (retainer of on-demand uurtarief)
- Alle DPA-relevante custom-werk (klant's DPA-template met de 5 redlines; geen Protocol-template)

Hosting-locatie maakt voor MSA-scope niet uit — een Client Automation kan in klant-tenant draaien (Brand Shield in MOJO's eigen n8n-tenant) of in Protocol-tenant (HR Agent voor AFAS) zolang het een custom build voor één klant blijft.

---

## Decisions log

*Per standaard MSA-onderdeel heb ik geprobeerd vast te leggen welke positie of route het beste lijkt te passen bij de Protocol-praktijk, met korte onderbouwing waar relevant. Punten waar we expliciet jouw input op willen zijn gemarkeerd als **⚠️ Open vraag voor ICTRecht** — via de filterknop bovenaan zie je die ook losstaand op één pagina.*

> ⚠️ **Open vraag aan ICTRecht (cross-cutting — AI Act)**: Protocol is een AI-bouwer; vrijwel elke build die onder deze MSA valt gebruikt AI-modellen of -systemen. De AI Act (Reg. EU 2024/1689) is daarmee een dwarsdoorsnijdend kader voor dit hele document. We hebben de meest in het oog springende plekken al benoemd — **7h** (Provider/Deployer-rolverdeling Art 16/26), **7n** (per-SoW Annex III-classificatie), **7m** (PLD-readiness-evaluatieclausule), **9c** (AI-output-warranty-disclaimer) en **11e** (GDPR-rollen separaat van AI Act-rollen) — maar wij missen waarschijnlijk nuances. Graag in jouw pass van het document met een schuin oog meekijken of de geformuleerde clausules cross-cutting compatibel zijn met de AI Act-verplichtingen, met name **Art 6** (high-risk-classificatie), **Art 16** (Provider-verplichtingen, deadline 2 augustus 2026) en **Art 26** (Deployer-verplichtingen). Aanvullende clausules of aanscherpingen waar wij iets missen graag aandragen.

### Sectie 0 — Scope statement

**MSA dekt uitsluitend Protocol Client Automations**: custom builds, workflow-automation, managed support op die builds, en alle DPA-relevante custom-werk dat Protocol levert aan LN/affiliates. Twee categorieën vallen expliciet **buiten** MSA-scope:

1. **Narrative training & advisory** (Traject 1) — geleverd door Part of the Narrative BV onder Algemene Voorwaarden v1.3 + offerte + mutual NDA
2. **Protocol Owned Products** (Traject 3) — geleverd door Part of the Protocol BV onder Subscription Order Form + Protocol's Product Terms + Protocol's eigen multi-tenant DPA, zoals SaaS-vendors als Salesforce, Stripe, AWS en Twilio dat doen. Voorbeelden: Venue Vera (Booking Risk Agent), F&B Forecasting (toekomstig), Controle Carla, Draaiboek Donna.

**MSA-scope (concept-formulering voor opname in MSA preamble of Section 1, NL → ICTRecht naar EN)**:

> *"This Agreement governs custom software development, workflow automation, system integration, and managed support services delivered by Service Provider to Live Nation and its Authorized Affiliates on a project-by-project basis under one or more Statements of Work, including any related processing of Personal Data on behalf of Live Nation under the Master Data Processing Agreement annexed hereto.*
>
> *The following are expressly excluded from the scope of this Agreement:*
>
> *(a) **Training, advisory and consulting services** — including but not limited to AI fundamentals workshops, executive briefings, AI strategy advisory, AI manifesto development, and AI year-plan retainer coaching — which are provided by Service Provider's affiliate Part of the Narrative B.V. under separate quotations governed by its General Terms and Conditions; and*
>
> *(b) **Subscription-based access to Service Provider's proprietary multi-tenant products** — including but not limited to Venue Vera (Booking Risk Agent), F&B Forecasting, Controle Carla, and Draaiboek Donna, as well as any future product owned and operated by Service Provider on a multi-tenant basis — which are provided by Part of the Protocol B.V. under separate Subscription Order Forms governed by Service Provider's Product Terms and a Service-Provider-issued Data Processing Agreement applicable to all subscribers."*

Zie Achtergrond-sectie hierboven voor volledige onderbouwing en de tabel met de drie commerciële trajecten.

### Sectie 1 — Contracting entities

**Narrative-zijde (signing party)**:

- **MSA wordt getekend door**: `Part of the Protocol B.V.` (KvK-nummer in te vullen). Dit is de Nederlandse besloten vennootschap die alle Client Automation-opdrachten onder de MSA gaat leveren.
- **Aandeelhouders Part of the Protocol B.V.**: Wytze de Haan (1/3), Xander Kranenburg (1/3) en Bjorn Veldmeijer (1/3) — allen volledig op de hoogte van de Live Nation-engagement en mede-betrokken bij review van de MSA-concept vóór ondertekening.
- **Operationele actie richting Live Nation**: KvK-nummer van Part of the Protocol B.V. wordt aan Live Nation gecommuniceerd voor het LN-IT-vendor-risk-assessment-traject.

**LN-zijde (counterparty)**:
- **Primary signing party**: `Live Nation Entertainment Netherlands B.V.` (groepsmoeder NL). Jennifer mag definitieve entity-naam bevestigen of corrigeren tijdens review.
- **Authorized Affiliates-mechanisme**: Ziggo Dome B.V., AFAS Live B.V., MOJO Concerts B.V. (en eventueel andere LN NL-venues) kunnen SoWs ondertekenen onder deze MSA. De ondertekenende affiliate is contractspartij voor díe SoW; alle MSA-voorwaarden gelden onverkort.
- **Concept-formulering Authorized Affiliates** (laat ICTRecht juridisch aanscherpen):

> *"Live Nation may designate one or more affiliates within the Live Nation Entertainment Netherlands group ('Authorized Affiliates') to enter into Statements of Work under this Agreement. Each Authorized Affiliate executing a SoW shall become a party to that SoW and shall be bound by the terms of this Agreement with respect to that SoW. Live Nation Entertainment Netherlands B.V. and the Authorized Affiliate shall be jointly responsible for the performance of obligations arising under that SoW."*

> ⚠️ **Open vraag 1c (Authorized Affiliates — joint vs. several liability)**: Is "joint responsibility" tussen Live Nation Entertainment Netherlands B.V. en de ondertekenende venue-affiliate (Ziggo Dome B.V., AFAS Live B.V., MOJO Concerts B.V.) juridisch de juiste constructie voor SoW-aansprakelijkheid onder NL-recht, of is "several liability" (alleen de affiliate verantwoordelijk per individuele SoW) cleaner? Vervolgvraag: bij affiliate-failure of faillissement van een venue — kan Narrative recourse hebben op Live Nation Entertainment Netherlands B.V. als moederentiteit voor uitstaande facturen? Trade-off voor onderbouwing: jointly geeft Narrative een sterkere collection-positie, maar LN-Legal kan hierop pushbacken wegens administratieve last; several is simpeler maar zwakkere verhaalsmogelijkheid bij affiliate-insolventie.

### Sectie 2 — Documentarchitectuur + order of precedence

**Documentarchitectuur**: drielaags model met master-DPA en sub-annexen per systeem.

```
┌─────────────────────────────────────────────────────────────┐
│  Master Services Agreement (MSA)                            │
│  — algemene kaders, liability, IP, confidentiality, etc.    │
└─────────────────────────────────────────────────────────────┘
            │
            ├── Statement of Work (SoW) — per project
            │     bv. SoW HR Agent, SoW Brand Shield, SoW Venue Vera
            │     scope, planning, prijs, project-specifieke SLAs
            │
            └── Master Data Processing Agreement (Master-DPA)
                  — algemene Art. 28 GDPR-kaders
                  │
                  ├── DPA-annex Brand Shield
                  ├── DPA-annex HR Agent
                  ├── DPA-annex Venue Vera
                  └── DPA-annex [toekomstig systeem]
                        per-systeem: data-categorieën, sub-processors,
                        retention, security measures, transfer mechanisms
```

**Reden voor master-DPA + sub-annexen** (vs. losse DPA per systeem):
- Sluit aan bij Jennifer's LN-template (zie `reference_ln_dpa_template.md`) — zij denkt al in master + annex-structuur
- Schaalbaar: nieuw systeem = nieuwe annex, geen volledige DPA-heronderhandeling
- Consistent: één set master-clausules (sub-processors, audit rights, transfer mechanisms) voor alle systemen
- Per-systeem-detail blijft mogelijk (data-categorieën, retention, security) zonder de masterstructuur op te blazen

---

**Order of precedence (Optie C — layered)**:

Bij conflict tussen documenten geldt deze volgorde, hoog naar laag:

| Rang | Document | Reden |
|---|---|---|
| 1 | DPA-annex (per systeem) + Master-DPA | GDPR-verplichtingen zijn dwingend recht; mogen nooit overruled worden door commerciële afspraken |
| 2 | Statement of Work (SoW) | Project-specifieke afspraken (bv. afwijkende SLA voor Brand Shield) kunnen MSA-defaults overstijgen, mits expliciet overeengekomen |
| 3 | Master Services Agreement (MSA) | Algemeen contractueel kader; vangnet voor alles waar SoW zwijgt |
| 4 | Algemene Voorwaarden v1.3 | Vangnet voor wat MSA niet regelt; wordt overstemd zodra MSA/SoW iets bepaalt |

**Concept-formulering (NL → ICTRecht naar EN)**:

> *"In the event of any conflict or inconsistency between the documents governing the relationship between the Parties, the following order of precedence shall apply, from highest to lowest: (1) any DPA-Annex applicable to the system or service in question, together with the Master Data Processing Agreement; (2) the applicable Statement of Work; (3) this Master Services Agreement; (4) Service Provider's General Terms and Conditions (version 1.3 or any successor version), which shall apply only to matters not addressed in the foregoing documents."*

---

**Safeguard-clausule (locked sections)**:

Voorkomt dat een SoW (of een Authorized Affiliate die een SoW tekent) de constitutionele MSA-bescherming uitholt. Vijf MSA-secties zijn alleen-aanpasbaar via een MSA-niveau amendment, getekend door de oorspronkelijke contracterende partijen.

**Locked sections**:

| Sectie | Waarom locked |
|---|---|
| Liability / aansprakelijkheidscap | Voorkomt dat SoW unlimited liability creëert |
| IP-ownership / dual perpetual license | Beschermt template-recht (AV v1.3 Art 9) |
| Confidentiality | Geen verzwakking van NDA-bescherming per project |
| Indemnification | Geen open vrijwaringen per SoW |
| Governing law / dispute resolution | Forum shopping voorkomen |

**Concept-formulering (NL → ICTRecht naar EN)**:

> *"Notwithstanding the order of precedence set out above, no Statement of Work or DPA-Annex may modify, waive, or supersede the provisions of this Agreement governing (i) Liability and Liability Cap, (ii) Intellectual Property Ownership and License, (iii) Confidentiality, (iv) Indemnification, or (v) Governing Law and Dispute Resolution. Any modification, waiver, or supersession of these provisions requires a written amendment to this Agreement, signed by authorized representatives of the original contracting parties to this Agreement (and not by Authorized Affiliates) at MSA-level."*

**Reden voor "(not by Authorized Affiliates)"-toevoeging**:
- We hebben in Sectie 1 vastgelegd dat LN-affiliates (MOJO, AFAS Live, Ziggo Dome) SoW's mogen tekenen onder de MSA
- Zonder deze uitsluiting zou een affiliate-medewerker een SoW kunnen tekenen die liability-cap of IP-ownership wijzigt
- Met deze uitsluiting kan alleen de oorspronkelijke MSA-tekenaar (Wytze + LNVN-bestuur) de "constitutie" wijzigen
- Standard pattern in vendor-protective MSAs (Atlassian, Salesforce, IT-vendors)

---

> ⚠️ **Open vraag 2a (layered precedence — formulering NL-conform)**: Is een "layered precedence"-clausule (DPA-Annex → Master-DPA → SoW → MSA → AV) zoals voorgesteld in 2 een gangbare en juridisch sterke constructie onder Nederlands contractenrecht voor MSA's met meerdere onderliggende SoW's en DPA-annexen, of bestaat er een alternatieve formulering (bijv. een single integrated agreement clause met expliciete waiver-mechanismen) die voor onze positie verdedigbaarder is?

> ⚠️ **Open vraag 2b (safeguard "not by Authorized Affiliates" — rechtsgeldigheid)**: Houdt de toevoeging *"and not by Authorized Affiliates"* in de safeguard-clausule onder NL-recht stand? Concreet: kan een venue-affiliate (Ziggo Dome, AFAS Live, MOJO) die een SoW tekent in theorie nog steeds toekomstige aanspraken tegen Live Nation Entertainment Netherlands B.V. doen op grond van het constitutionele MSA-niveau, ondanks deze contractuele beperking? Deze constructie is bedoeld om te voorkomen dat een SoW-tekenende affiliate de MSA-bescherming uitholt — graag pressure-testen op afdwingbaarheid.

> ⚠️ **Open vraag 2c (Master-DPA + sub-annexen — compatibiliteit Jennifer's template)**: Is de voorgestelde "Master-DPA + sub-annexen per systeem"-structuur compatibel met Jennifer Quik's LN-group DPA Addendum-template (zoals ontvangen 20 april 2026)? Indien niet volledig compatibel: welk compromis is het cleanest om alignment te bereiken zonder Narrative's wens om per-systeem-detail in annexen te behouden op te geven? (Onderbouwing AVG Art 28(3)-conformiteit zelf zit in open vraag 11a — deze vraag betreft template-alignment, niet AVG-naleving.)

### Sectie 3 — Term & termination

Vier sub-componenten: looptijd, termination-for-convenience, termination-for-cause, en effect van termination. Onderbouwing per sub-component opgenomen zodat ICTRecht het Nederlandse-rechtelijk kan beoordelen en eventueel andere termijnen kan voorstellen.

---

**3a. Initial term + renewal**

| Onderdeel | Vastgelegd |
|---|---|
| Initial term | 3 jaar |
| Renewal | Automatisch 1-jaarsverlengingen tenzij opgezegd |
| Notice voor non-renewal | 90 dagen vóór einde term/renewal-periode |

**Waarom 3 jaar (en niet 1 of 5)**:

Drie afwegingen drijven deze keuze:

1. **Aard van het werk vraagt om meerjarige horizon.** De systemen die onder deze MSA vallen (HR Agent, Brand Shield, Booking Risk Agent / Venue Vera, F&B Forecasting, n8n workflow-automation) zijn geen one-shot delivery — het zijn live productie-systemen die continuous managed support, finetuning, security-updates en monitoring vereisen. Een 1-jaars term zou betekenen dat elke SLA, elke security baseline en elke pricing-structuur jaarlijks heronderhandeld moet worden. Dat is administratief belastend voor beide partijen en geeft Narrative geen voorspelbaarheid om in tooling/personeel te investeren ten behoeve van LN.

2. **Drie jaar is gangbare master-template-praktijk.** Onderzoek naar enterprise SaaS- en services-MSAs (zie `dpa-industry-practice-research.md`) laat zien dat 3 jaar een markt-conventie is voor Master-templates met meerjarige operationele componenten. Vendor-MSAs zoals Atlassian, Workday, en Salesforce-master-templates hanteren standaard 2 of 3 jaar initial. Een 1-jaars term is gangbaar voor losse SaaS-subscriptions, maar niet voor MSA's met SoW's en managed support eronder. Een 5-jaars term is gebruikelijk in infrastructuur-deals (datacenter, hardware-leasing) of strategische outsourcing — niet voor onze schaal.

3. **LN-legal pushback-risico is laag bij 3 jaar.** Bij 5 jaar zou Jennifer redelijkerwijs pushback geven (te lang voor relatief jonge vendor, té veel commitment). Bij 1 jaar zou Narrative legitiem terugduwen (operationele instabiliteit). 3 jaar is de marktconforme middenweg waarop beide partijen geen sterk argument tegen kunnen voeren — wat het onderhandelingstraject versnelt.

**Renewal mechanism**: automatische 1-jaars renewal in plaats van automatische 3-jaars renewal. Reden: na het 3-jaars initial heeft beide partijen genoeg ervaring met de relatie. 1-jaars renewal-cadans geeft beide partijen een natuurlijk evaluatiemoment zonder een nieuwe 3-jaars commitment af te dwingen. 90 dagen non-renewal-notice geeft genoeg tijd voor transitieplanning.

---

**3b. Termination for convenience**

| Onderdeel | Vastgelegd |
|---|---|
| Opzegtermijn | 90 dagen schriftelijke notice |
| Wie mag opzeggen | Beide partijen (symmetrisch) |
| Effect op lopende SoW's | Lopende SoW's lopen door tot einde-SoW óf eerder einde-MSA + 60 dagen wind-down |
| Vergoeding | Geen kill-fee. Wel: betaling van geleverd werk tot opzegmoment + non-cancellable third-party costs (server-licenties, sub-processor commitments, etc.) |

**Waarom 90 dagen**:
- 30 dagen is te kort: Narrative kan resources niet redelijkerwijs herallokkeren, bestaande server-/license-commitments kunnen niet worden afgebouwd
- 180 dagen is te lang: marktstandaard is 60–90 dagen; 180 zou pushback krijgen van LN-legal
- 90 dagen geeft Narrative tijd om team te herallokkeren, third-party commitments af te wikkelen, en eventueel nog laatste deliverables af te ronden. Geeft LN tijd om transitie naar interne resources of andere vendor te plannen zonder operationele schade.

**Waarom symmetrisch**:
- Asymmetrische termination (alleen LN mag, Narrative niet) is standaard pushback van LN-legal als opening positie. Symmetrie houdt onderhandelingsbalans en is juridisch verdedigbaar.
- In de praktijk gebruikt Narrative deze clausule niet snel — maar de optie hebben beschermt tegen scenario's waarin de relatie commercieel niet meer werkt.

**Waarom geen kill-fee**:
- Kill-fees (vaste vergoeding bij convenience-termination) zijn typisch in lange-termijn outsourcing-deals waar de vendor initiële investeringen heeft gedaan. Onze deals werken niet zo: prijs zit in de SoW, betaald per fase of mijlpaal.
- Wel: betaling van geleverd-maar-onbetaald werk + non-cancellable third-party costs is redelijk en standaard.

---

**3c. Termination for cause**

| Trigger | Cure period | Effect |
|---|---|---|
| Material breach (remediable) | 30 dagen schriftelijke notice + cure-window | Termination als niet hersteld |
| Insolvency / faillissement / surséance | Geen cure | Immediate termination |
| Persistent breach (3× dezelfde breach in 12 maanden) | Geen cure (de 3× telt als waarschuwing) | Immediate termination |
| Material data breach door grove nalatigheid van Narrative | 30 dagen mits remediable; immediate als data-verlies onomkeerbaar | Conform DPA-eisen |
| Material breach door LN (non-payment 60+ dagen) | 30 dagen na written demand for payment | Immediate termination + recovery uitstaande facturen + late interest |

**Waarom 30 dagen cure period (en niet 14 of 60)**:
- 14 dagen is in de praktijk te kort om een material breach te diagnosticeren, fixen en aantonen — vooral bij technische breaches op live systemen
- 60 dagen is te lang vanuit LN-perspectief: een breach die 60 dagen mag voortduren ondergraaft het hele cause-mechanisme
- 30 dagen is markt-conventie en geeft beide partijen redelijke tijd voor diagnose + remediation + verificatie

**Waarom "no cure" voor insolvency**:
- Bij faillissement of surséance van betaling is herstel feitelijk onmogelijk en wordt het juridisch behandeld door curator. Cure period zou betekenisloos zijn.
- Standaard provision in alle enterprise-MSAs.

**Waarom "no cure" voor persistent breach (3× in 12 maanden)**:
- Voorkomt dat een partij dezelfde breach steeds herhaalt en telkens binnen cure-period oplost — patroon van slechte performance.
- 3× / 12 maanden is een standaard threshold; geeft genoeg ruimte voor incidentele fouten maar niet voor structureel falen.

**Waarom non-payment 60+ dagen voor LN-breach**:
- Onder Algemene Voorwaarden v1.3 hanteert Narrative 30-dagen-betalingstermijn. Na 30 dagen begint late interest. Na 60 dagen is non-payment material.
- 30 dagen written-demand-cure daarna geeft LN nog een laatste herstelmogelijkheid voordat termination van kracht wordt.

---

**3d. Effect of termination**

| Onderdeel | Vastgelegd |
|---|---|
| Surviving sections | Liability, IP-ownership/license, Confidentiality, Indemnification, alle DPA-obligaties — blijven van kracht na termination |
| Lopende SoW's | Lopen door tot natuurlijk einde-SoW, tenzij beide partijen anders overeenkomen of MSA-termination ze raakt (zie 3b/3c) |
| Transition assistance | Narrative biedt redelijke transitie-hulp gedurende max 90 dagen na termination, tegen reguliere day-rate. Geen verplichte gratis support. |
| Data return / deletion | Per DPA-annex per systeem: terugleveren of verwijderen binnen 30 dagen na schriftelijk verzoek |
| Source code / artefacten | Per dual perpetual license (AV v1.3 Art 9): LN behoudt eeuwig gebruiksrecht op opgeleverde systemen; Narrative behoudt eigen IP / methodology / template-recht |

**Waarom transition assistance tegen day-rate (en niet gratis)**:
- "Free transition" is een standaard LN-legal-vraag bij opening positie
- Narrative's positie: redelijke transitie-hulp tegen marktconforme day-rate is juridisch correct (we zijn dienstverlener, niet leverancier van een product met built-in support)
- Free-transition-uren creëren scope-creep en geven LN onbeperkt recht op senior-tijd zonder commerciële tegenprestatie
- Wel onderhandelbaar als concessie tijdens negotiation: optioneel "20 transition hours included in good-faith handover" als gesture, maar niet als voorkeurspositie. Wytze houdt voorkeur op pure day-rate; ICTRecht kan beoordelen of een symbolische goodwill-bandwidth juridisch sterker is voor de relatie.

**Waarom dual perpetual license bij termination niet vervalt**:
- Dit is conform AV v1.3 Art 9 en al een gevestigd Narrative-IP-model
- LN moet erop kunnen rekenen dat opgeleverde productie-systemen na MSA-einde blijven werken — anders zou LN nooit een MSA tekenen
- Narrative behoudt template- en methodology-recht zodat dezelfde architecturen herbruikbaar zijn voor andere klanten

---

> ⚠️ **Open vraag 3a (3-jaars initial term — verdedigbaarheid)**: Is een 3-jaars initial term met 1-jaars automatische renewals onder Nederlands contractenrecht en gangbare LN-vendor-praktijk een verdedigbare opening positie voor een MSA met meerjarige operationele componenten, of is 2 jaar + renewals juridisch én commercieel beter onderhandelbaar gegeven Protocol's status als relatief jonge vendor?

> ⚠️ **Open vraag 3b (cure-mechanisme — NL-rechtelijke houdbaarheid)**: Houdt het cure-mechanisme (30 dagen schriftelijke notice + remediation + verificatie, met no-cure-categorieën voor insolventie/fraude/gross misconduct) onder Nederlands recht stand? Achtergrond: de Nederlandse rechter beoordeelt "redelijke termijn voor herstel" soms strenger dan de Anglo-Saksische standaardpraktijk — graag toetsen of 30 dagen voor materiële breach NL-rechtelijk verdedigbaar is, of dat een ander mechanisme (bijv. 60 dagen + early-termination-right voor opzet) sterker staat.

> ⚠️ **Open vraag 3c (non-payment 60+30 vs. wettelijke handelsrente)**: Is de "(non-payment 60 dagen + 30 dagen demand)"-termination-trigger sterker dan een directe verwijzing naar de wettelijke handelsrente + verzuim-regeling onder BW 6:119a/119b? Welke constructie is contractrechtelijk cleanest voor een MSA tussen NL-zakelijke partijen, gegeven dat Protocol vooraf-betalings-bescherming wil bij grote SoW's?

> ⚠️ **Open vraag 3d (transition assistance — formulering)**: Welke transition-assistance-formulering verdient juridisch en commercieel de voorkeur: (a) "redelijke transitie-hulp gedurende max 90 dagen tegen reguliere day-rate", of (b) "20 free transition hours + day-rate daarna"? Trade-off: (a) geeft Protocol zekerheid van betaling vanaf uur 1; (b) geeft LN comfort dat termination niet onmiddellijk consultancy-kosten triggert.

### Sectie 4 — Fees & payment

Vier sub-componenten: pricing-structuur per SoW-type, payment terms, late interest, en indexatie. Alle bedragen zijn richtprijzen op basis van het huidige Protocol-model — concrete cijfers per SoW worden bij ondertekening van die SoW vastgesteld. MSA legt het kader vast, niet de prijzen.

---

**4a. Pricing-structuur — Client Automations onder MSA**

> **Scope-reminder**: deze MSA dekt uitsluitend **Client Automations** (Traject 2 in de Achtergrond-sectie). Owned Products (Traject 3) vallen onder een aparte Protocol Subscription-stack en worden hier dus niet gepricet. Narrative training (Traject 1) idem onder AV.

**Categorie A — Build-werk (Client Automations)**

Specifieke automation-builds en agents die Protocol bouwt voor één klant. Voorbeelden binnen LN-portfolio: **Brand Shield** (MOJO), **WhatsApp HR Agent** (AFAS Live), **Mailbox Ticket Counting** (MOJO), custom n8n-workflow-builds.

| Component | Pricing-model |
|---|---|
| Discovery / scoping | **Vooraf en onbetaald.** Resulteert in offerte. Wordt expliciet niet gefactureerd, ook niet retroactief. |
| Build/oplevering | **Fixed-fee per SoW** dekt het hele build-traject. Géén T&M voor builds. |
| Indicatieve build-prijzen (richtbedragen, finaal in SoW) | n8n workflow simpel: ~€3.750 / WhatsApp HR Agent V1: ~€5.000 / Custom GPT: ~€4.000 |
| Mijlpalen-betaling | Standaard 3 fasen: bv. 25% bij start, 50% bij oplevering technisch, 25% bij final acceptance |
| Wijzigingen op scope tijdens build | Via change-control-procedure (Sectie 6) → resultant in addendum-SoW met eigen fixed-fee. Niet als T&M-bijschrijving. |
| IP-positie | Dual perpetual license (AV v1.3 Art 9): beide partijen eeuwigdurend gebruiksrecht; Protocol behoudt template/methodology-recht |

**Hosting-as is een aparte dimensie binnen Client Automations**

Een Client Automation kan op twee manieren gehost worden — dat raakt de DPA-annex en security-baseline meer dan de pricing-structuur, maar is contractueel relevant om scherp te hebben:

| Hosting-model | Voorbeeld | Wat verandert er commercieel/contractueel |
|---|---|---|
| **Klant-tenant-hosting** | Brand Shield draait in MOJO's eigen n8n-tenant (via MOJO's MS365-credentials voor SharePoint/Outlook-toegang); Mailbox Ticket Counting in MOJO-systemen | Protocol levert configuratie + code, MOJO is operator. Change-control-clausule essentieel: Protocol's aansprakelijkheid alleen voor configuratie die expliciet door Protocol als productie-ready bevestigd is. |
| **Protocol-tenant-hosting (custom build)** | WhatsApp HR Agent voor AFAS Live: Protocol host, beheert Twilio-integratie, draait op Protocol-stack — maar **blijft een custom build voor één klant**, geen multi-tenant SaaS, geen herverkoop | Protocol is hier processor + hosting-infrastructure-provider. Vraagt uitgebreidere security-baseline in DPA-annex. Optionele hosting-fee als component in maandelijkse retainer. |

**Belangrijk voor scope-bewaking**: Protocol-tenant-hosting maakt een Client Automation niet automatisch tot Owned Product. De definiërende as is **eigendom + multi-tenancy + herverkoop**, niet hosting-locatie. WhatsApp HR Agent voor AFAS = custom build (Categorie A), ondanks Protocol-hosting; Venue Vera voor diezelfde AFAS = Owned Product (buiten MSA), omdat het multi-tenant is en aan andere venues wordt verkocht.

**Categorie B — Managed support na oplevering (apart commercieel kader binnen MSA)**

Na go-live van een Client Automation biedt Protocol twee support-opties. Keuze ligt bij klant per SoW.

| Optie | Pricing | Wat zit erin |
|---|---|---|
| Maandelijkse retainer — workflow-niveau | ~€195/maand | Monitoring, bug fixes, prompt updates, kleine aanpassingen, support tijdens kantooruren |
| Maandelijkse retainer — platform-niveau | ~€395/maand | Idem als boven, maar voor dashboards + meerdere agents |
| On-demand support | ~€195/uur | Alleen wanneer ingeschakeld; geen vaste maandelijkse fee |
| Standaard inbegrepen | Eerste maand support gratis na oplevering | Standaardpraktijk |

**Het uurtarief van ~€195/uur duikt uitsluitend op bij on-demand support en post-termination transition-begeleiding** — niet bij builds, niet bij discovery, en niet bij maandelijkse retainer.

**Reden voor dit pricing-model**:

1. **Discovery-niet-apart-factureren is een bewuste positionering**: Wytze investeert pre-sales-tijd in discovery omdat dit (a) Narrative's expertise zichtbaar maakt, (b) de offerte realistisch maakt, (c) langere klantrelaties bouwt. Dit moet expliciet in de MSA staan zodat het niet impliciet "free consulting" wordt — voorkomt latere claims dat pre-sales-uren toch als consulting gefactureerd hadden moeten worden.

2. **Fixed-fee voor builds (geen T&M)**: dit is de sterkste positie voor Narrative én voor LN. Narrative draagt het uitvoeringsrisico van scope-discipline, LN heeft prijszekerheid. Pushback van LN-legal op T&M-builds is daarmee al ondervangen — Protocol biedt het simpelweg niet aan voor builds.

3. **Scope-changes via change-control, niet via T&M-bijschrijving**: als de klant tijdens een build aanvullende scope wil, gaat dat via een change-order (zie Sectie 6) met een eigen fixed-fee. Hiermee blijft de pricing-discipline en scope-helderheid intact gedurende het build-traject.

4. **Hourly rate alleen voor managed support en transition**: bij on-demand support is T&M de redelijke vorm — anders zou klant een retainer moeten kopen voor onzeker volume. Hetzelfde geldt voor transition assistance na MSA-einde. Geen scope-creep-risico bij build-werk.

5. **Optionele managed-fee uplift voor DPA-dragende klanten**: conform Besluit 3 (`dpa-strategy-decisions.md`) draagt managed support voor klanten met getekende DPA een uplift van 15-20% — dekt insurance allocation, compliance-overhead en incident-reserve. Dit wordt per SoW transparant gemaakt, niet impliciet doorgerekend.

**Concept-formulering MSA Section "Fees" (NL → ICTRecht naar EN)**:

> *"Fees for services rendered under this Agreement shall be as set out in the applicable Statement of Work. Custom builds and workflow automations are delivered on a fixed-fee basis, payable per acceptance milestone as specified in the applicable Statement of Work. Managed support services may be procured either on a monthly retainer basis or on an on-demand time-and-materials basis at the hourly rate set out in the applicable Statement of Work.*
>
> *Discovery, scoping and pre-contractual consultation activities preceding the execution of a Statement of Work are not chargeable unless expressly included in a Statement of Work.*
>
> *Hourly time-and-materials rates apply only to (i) on-demand support services where the parties have not agreed a monthly retainer, and (ii) post-termination transition assistance pursuant to Section [Term & Termination]. Time-and-materials billing shall not apply to build, configuration, or implementation services, which shall always be quoted on a fixed-fee basis."*

---

**4b. Payment terms**

| Onderdeel | Vastgelegd |
|---|---|
| Betalingstermijn | 30 dagen na factuurdatum |
| Build-werk (Client Automations) | Per acceptance-milestone (typisch 25% / 50% / 25%) |
| Maandelijkse retainer (managed support) | Maandelijks vooraf, eerste 5 dagen van de maand |
| On-demand T&M support | Maandelijks achteraf op basis van geregistreerde uren |
| BTW | 21% standaard, conform NL-fiscaalrecht |
| Valuta | EUR |
| Disputed invoice | LN moet binnen 14 dagen na factuurdatum schriftelijk betwisten; daarna geldt factuur als geaccepteerd |

**Reden 30 dagen**: marktstandaard B2B in NL onder de Wet Late Betalingen. Aansluitend op AV v1.3.

**Reden 14-dagen-dispute-window**: voorkomt late-stage betalingsdiscussies. Standaardpraktijk in enterprise-MSAs.

---

**4c. Late interest + collection costs**

| Trigger | Gevolg |
|---|---|
| Betaling > 30 dagen na factuurdatum | Wettelijke handelsrente (art. 6:119a BW) + €40 forfaitaire incassokosten conform Wet Incassokosten |
| Betaling > 60 dagen na factuurdatum | Recht tot opschorting van diensten + termination-trigger zoals besproken in Sectie 3 |

**Reden wettelijke handelsrente in plaats van fixed %**:
- Wettelijke handelsrente (art. 6:119a BW) is dwingend recht — geen onderhandelingspunt voor LN-legal
- Per Q1 2026 ~12,5% per jaar, dus financieel goed beschermd
- Eenvoudiger formuleren in MSA dan een eigen rentestructuur — sluit elke discussie uit
- €40 forfaitaire incassokosten is wettelijk vastgesteld minimum (kan hoger bij hogere vorderingen, conform de Wet Incassokosten)

---

**4d. Indexatie**

| Onderdeel | Vastgelegd |
|---|---|
| Indexatie-formule | CBS Consumentenprijsindex (CPI), alle huishoudens, jaar-op-jaar |
| Frequentie | Eén keer per jaar, op 1 januari |
| Cap | Maximaal 5% per jaar |
| Floor | Geen verlaging bij negatieve CPI (deflatie-risico ligt niet bij Narrative) |
| Toepassing | Op alle vaste tarieven (on-demand uurtarief, maandelijkse retainer-fee, fixed-fees in nieuwe SoW's). Lopende fixed-fee build-SoW's worden niet retroactief geïndexeerd. |
| Notificatie | Schriftelijke notice van nieuwe tarieven uiterlijk 1 december voorafgaand aan ingang |

**Reden CPI + 5% cap**:
- Pure CPI zonder cap → bij hoge inflatie (zoals 2022–2023) kunnen tarieven 10–15%/jr stijgen, LN-legal pusht hard tegen
- Fixed % (bv. altijd 3%) → in deflatie-jaren overcompenseert Narrative; in hoge inflatie undercompenseert het
- CPI met 5% cap is markt-balans: volgt economische realiteit, maar geeft LN voorspelbaarheid in worst-case scenario's

**Reden geen retroactieve indexatie op lopende fixed-fee-SoW's**:
- Een Client Automation-SoW die getekend is voor €5.000 blijft €5.000, ook als de bouw langer loopt dan een kalenderjaar
- Anders ontstaat scope-debate over wat "lopend" betekent en hoe je tussentijdse indexatie verrekent
- Owned Product-licenties zijn jaarlijks (bv. Venue Vera €6.500/jaar) — die volgen de indexatie elk renewal-moment automatisch

**Reden 5% cap (en niet 3% of 10%)**:
- 3% is te krap bij langdurige inflatie-pieken — Narrative draagt het verlies
- 10% biedt LN onvoldoende voorspelbaarheid; LN-legal pusht hier vrijwel zeker terug
- 5% is een gangbare middenweg in NL-enterprise-services-contracten en geeft beide partijen rationele verwachtingen

---

> ⚠️ **Open vraag 4a (Owned-Products-uitsluiting — effectiviteit)**: Sluit de huidige MSA-scope-formulering (Sectie 0 + Achtergrond-tabel "Drie commerciële trajecten") Owned Products (Venue Vera, F&B Forecasting, Controle Carla, Draaiboek Donna) juridisch effectief uit, zodat geen SoW onder deze MSA per ongeluk een Owned Product kan raken? Owned Products vallen onder Protocol's eigen Subscription Order Form + Subscription Terms + Protocol-DPA; de scope-clausule moet voorkomen dat LN-affiliates dat traject onder deze MSA proberen te trekken.

> ⚠️ **Open vraag 4b (Discovery niet-factureerbaar — NL-houdbaarheid)**: Houdt de "Discovery is not chargeable unless explicitly scoped in a SoW"-formulering onder Nederlands recht stand? Concreet: voorkomt deze formulering latere claims door Live Nation dat pre-sales-uren of scoping-werk toch als consulting-uren gefactureerd hadden moeten worden, of zijn er aanvullende voorwaarden (bijv. expliciete waiver-clausule of redelijkheidsstandaard onder BW 6:248) nodig om deze positie verdedigbaar te maken?

> ⚠️ **Open vraag 4c (dispute-window 14 dagen — NL-handhaafbaarheid)**: Is een 14-dagen-dispute-window (waarbinnen Live Nation een factuur moet betwisten) onder NL-recht handhaafbaar in een B2B-context tussen gelijkwaardige zakelijke partijen, of is de standaard van 30 dagen onder Burgerlijk Wetboek sterker voor onze positie als leverancier (sneller closure = sterkere cashflow-positie)?

> ⚠️ **Open vraag 4d (CPI-indexatie + 5% cap — recente NL-jurisprudentie)**: Toets de voorgestelde CPI-indexatie met 5% cap aan recente Nederlandse jurisprudentie over indexatie-clausules in B2B-contracten. Specifiek: is een 5% jaarlijks cap een verdedigbare middenweg (LN-vendor-praktijk), of bestaat er risico dat NL-rechter de cap-clausule pas-toepasselijk verklaart bij significante CPI-stijgingen?

### Sectie 5 — IP model

> **Scope-reminder**: deze sectie geldt alleen voor Client Automations (Traject 2). Training-IP zit onder AV v1.3 Art 9 (Traject 1); Owned Products-IP onder Protocol's eigen Subscription stack (Traject 3). Beide buiten deze MSA.

Vier sub-componenten: default IP-positie, Background IP-definitie, klant-data + confidentiality, en IP-warranty + indemnity. Sluit aan op AV v1.3 Art 9 en `narrative-non-negotiables-briefing.md` Sectie 3.2.

---

**5a. Default IP-positie — dual perpetual license**

Voor Foreground IP (alles wat specifiek voor de klant ontwikkeld wordt onder een SoW) geldt een dual perpetual license. Beide partijen krijgen eeuwigdurend gebruiksrecht. Deze positie ligt in lijn met AV v1.3 Art 9 en is jaren toegepast zonder klant-conflict.

| Wat | Eigendom | Gebruiksrecht klant | Gebruiksrecht Protocol |
|---|---|---|---|
| **Foreground IP** (specifiek voor klant ontwikkeld: code, prompts, configuratie, custom integraties) | Gedeeld via dual perpetual license | Eeuwigdurend, niet-exclusief, niet-overdraagbaar, intern gebruik door LN/affiliates | Eeuwigdurend recht voor hergebruik in andere klant-engagements (mits niet klant-specifieke data/branding) |
| **Background IP** (Protocol's methodology, frameworks, prompt-architecturen, code-libraries, n8n-blueprints, helper-modules) | 100% Protocol | Beperkt: alleen voor zover ingebouwd in geleverde Foreground IP, gekoppeld aan klant-license | Volledig — vrij hergebruik, doorontwikkeling, inzet bij andere klanten |
| **Klant-data en klant-specifieke configuratie** | 100% LN/affiliate | n.v.t. — eigenaar | Alleen processor-rol onder DPA; geen ander gebruik |
| **Premium-optie: full IP-transfer naar klant** | 100% LN tegen meerprijs | Volledig | Geen — Protocol verliest gebruiksrecht op het specifieke product |

**Reden dual perpetual als default**:

1. **AV v1.3 Art 9 is al ons gevestigde model** — jaren toegepast, zonder klant-claim of -conflict. Bewezen werkbaar voor ons businessmodel én voor klanten.
2. **LN moet kunnen rekenen op continuïteit** — bij MSA-einde mag een geleverd HR Agent-systeem niet onbruikbaar worden voor LN. Eeuwigdurend klant-gebruiksrecht is de juiste klant-bescherming.
3. **Protocol's businessmodel-fundament** — zonder hergebruiksrecht op methodology/code-libraries kunnen we volgende klanten niet efficiënt bedienen. Elke nieuwe klant zou vanaf scratch een prompt-architecture en n8n-blueprint moeten financieren.
4. **Markt-conventie voor agency-builds** — standaard pattern bij IT-bouwers; LN-legal kent dit model.

**Premium-optie — full IP-transfer (+25-40% op bouwsom)** conform AV v1.3 Art 9g blijft beschikbaar als opt-in bij expliciet klant-verzoek met aparte schriftelijke overeenkomst. Niet de default. Voor LN waarschijnlijk niet aan de orde, maar de optie houden geeft commerciële flexibiliteit.

---

**5b. Background IP — brede definitie, expliciet vastgelegd**

Background IP omvat alles wat Protocol meebrengt vóór de SoW óf parallel als onderdeel van eigen R&D ontwikkelt — onafhankelijk van of het tijdens dít project voor het eerst zichtbaar wordt:

- Prompt-architectures, prompt-libraries, prompt engineering-technieken (templates, niet klant-specifieke ingevulde prompts)
- n8n-workflow-blueprints en orchestratie-patronen (logica-patronen, niet klant-data)
- AI-agent-orchestratiepatronen (multi-agent communicatie, error handling, retry-logic)
- Code-libraries, helper-functies, integratie-modules (Twilio-, OpenAI-, Supabase-, Apify-modules)
- Tooling, deployment-scripts, infrastructure-as-code
- Methodology, runbooks, architecture-patronen

**Cruciale concept-formulering (NL → ICTRecht naar EN, gebaseerd op `narrative-non-negotiables-briefing.md` 3.2)**:

> *"Service Provider's methodology, architecture, code patterns, prompt engineering techniques, prompt libraries, orchestration patterns, generic modules, helper functions, integration libraries, tooling, deployment scripts, runbooks, and any improvements, derivatives, or extensions thereof developed by Service Provider in the course of performing services under this Agreement, shall remain Service Provider's exclusive Background Intellectual Property. For the purposes of this Agreement and any Data Processing Annex, such Background Intellectual Property is not considered Personal Data, Customer Data, Customer Confidential Information, or Foreground IP, and shall not be subject to any return, deletion, transfer, or destruction obligations. Only Customer-specific data, configuration, branding, and business information constitute Confidential Information of the Customer subject to the obligations set out in this Agreement and any applicable Data Processing Annex."*

**Reden voor brede formulering**:
- Voorkomt dat een DPA-termination-clausule per ongeluk Protocol's methodology raakt
- Beschermt tegen "alle door Vendor geleverde materialen moeten worden vernietigd"-claims
- Nederlandse jurisprudentie kent het Background-IP-concept; ICTRecht weet dit goed te formuleren
- Maakt expliciet dat Protocol's eigen R&D (zelfs tijdens een LN-project ontwikkeld) niet impliciet door LN gefinancierd wordt

---

**5c. Klant-data en klant-Confidentiality**

| Type | Eigenaar | Protocol's recht onder MSA |
|---|---|---|
| **Persoonsgegevens** (employees, customers, vendors) | LN/affiliate | Alleen processor-rol onder DPA-annex; geen ander gebruik |
| **Klant-business-data** (bookings, financials, employee-records, supplier-data) | LN/affiliate | Alleen voor operationele werking van het systeem; geen aggregatie of cross-client-gebruik |
| **Klant-branding en visuele identiteit** | LN/affiliate | Alleen binnen het opgeleverde systeem; geen marketing of portfolio-gebruik zonder schriftelijke toestemming |
| **Klant-specifieke prompts** (bv. MOJO tone-of-voice in Brand Shield, AFAS HR-policies in HR Agent) | LN/affiliate | Mag niet hergebruikt worden bij andere klanten |
| **Anonieme/aggregated insights afgeleid van klant-data** | LN/affiliate (default) | Niet automatisch — onderhandelbaar per SoW als opt-in voor benchmarking/product-improvement; nee tenzij expliciet ingewilligd |

**Aansluiting op DPA-annex en Besluit 2** (`dpa-strategy-decisions.md`): de anonymisation-redline (P38 in Jennifer's template) wordt opgelost via pseudonymisation-where-feasible + Annex X met scope-architectuur. Voor klant-data is dat het correcte mechanisme; deze MSA-clausule is de complementaire commercieel/IP-laag erboven.

**Cruciale aanvulling — geen "training Protocol's models"-clausule** (pre-emptief opnemen):

> *"Service Provider shall not use any Customer Data, Customer-specific prompts, or Customer Confidential Information to train, fine-tune, or otherwise develop any machine learning model, AI system, or product offering for use by other customers or third parties, except where such use is expressly authorized in writing by Customer in the applicable Statement of Work."*

Reden voor pre-emptief opnemen: dit is een steeds vaker gevraagde clausule door enterprise-klanten in 2026 (post-OpenAI-data-discussies). Liever vooraf in MSA dan via redline-pushback.

---

**5d. IP-warranty + indemnity**

| Onderdeel | Vastgelegd |
|---|---|
| **Protocol's warranty** | Alle door Protocol geleverde code, prompts, dashboards, methodology zijn Protocol's eigendom of worden onder geldige license gebruikt |
| **Indemnity bij IP-claim van derde** | Protocol verdedigt LN op eigen kosten, vergoedt damages, vervangt of past aan |
| **Cap op deze indemnity** | Gelijk aan algemene liability-cap (Sectie 7), tenzij expliciete carve-out via super-cap |
| **Carve-out optie** | IP-indemnity krijgt Super-Cap (2× General Cap) per Sectie 7b — procedure in Sectie 8 |
| **LN's reciproke warranty** | LN warrants dat door LN aangeleverde data, content, branding, en derde-partij-tooling geen third-party-rechten schendt |
| **Carve-outs aan beide kanten (geen indemnity voor)** | (a) door klant doorgevoerde wijzigingen op opgeleverde code, (b) gebruik buiten de scope van de SoW, (c) integratie met derde-partij-software die Protocol niet heeft goedgekeurd |

**Reden voor wederzijdse warranty**: voorkomt dat Protocol aansprakelijk wordt voor IP-claims op door LN aangeleverde AFAS-data of MOJO-branding. Symmetrisch en juridisch standaard.

**Reden voor change-control-carve-out**: directe link met de change-control-clausule uit `narrative-non-negotiables-briefing.md` Sectie 5 — Protocol kan geen IP-warranty geven op code die de klant zelf heeft gewijzigd.

---

> ⚠️ **Open vraag 5a (dual perpetual license + Background-IP — NL-houdbaarheid)**: Staan de voorgestelde dual perpetual license-constructie en de Background-IP-formulering onder NL-recht zo sterk als nu geformuleerd, of helpt aanvullende formulering ("ondeelbaar van het methodology-IP", expliciete non-exclusiviteit, of een eigen waiver-clausule) om de constructie meer pressure-test-bestendig te maken bij eventuele LN-Legal-bezwaren?

> ⚠️ **Open vraag 5b (no-training-Protocol's-models — clausule-formulering)**: Laat de "no training Protocol's models"-clausule juridisch verfijnen zodat deze (a) Protocol blokkeert om klant-data te gebruiken voor model-training over andere klanten heen, maar (b) niet onbedoeld OpenAI/Anthropic-style API-gebruik blokkeert waar Protocol per SoW persoonsgegevens via API doorstuurt voor productie-doeleinden onder DPA Annex Y subprocessor-listing. Welke formulering vermijdt dit grijze gebied het beste?

> ⚠️ **Open vraag 5d (change-control-carve-out — NL-recht)**: Houdt de change-control-carve-out (geen IP-indemnity bij door klant zelfstandig doorgevoerde wijzigingen op deliverables) onder NL-recht stand? Deze carve-out sluit aan op de change-control-clausule (Sectie 6c) als verplicht element in de MSA — graag pressure-testen of de combinatie 5d-carve-out + 6c-procedure juridisch sluitend is, of dat aanvullende bewijslast-clausules nodig zijn.

### Sectie 6 — Acceptance & change control

> **Scope-reminder**: deze sectie geldt alleen voor Client Automations (Traject 2). Owned Products (Traject 3) hebben hun eigen Subscription-stack met eigen acceptance- en change-mechanismen; Training (Traject 1) valt onder AV v1.3 + offerte-acceptance.

Vier sub-componenten: acceptance-procedure (incl. AI-specifieke aanvulling), defect-management binnen warranty (incl. third-party-provider risk), change-control bij operationele wijzigingen (klant-tenant en Protocol-tenant), en change-order-procedure bij scope-wijzigingen (incl. drie-tier formaliteit en emergency-mechanisme). Sluit aan op Sectie 4a (mijlpalen-betaling), Sectie 5d (IP-warranty change-control-carve-out) en `narrative-non-negotiables-briefing.md` Sectie 5 (verplichte change-control-clausule).

---

**6a. Acceptance-procedure per milestone**

Acceptance-procedure regelt hoe een opgeleverde milestone wordt goedgekeurd, hoeveel tijd klant heeft om te testen, wat er gebeurt bij stilzwijgen, en hoe defect-rapportage eruitziet. Dit raakt direct de mijlpalen-betalingsstructuur uit Sectie 4a (typisch 25/50/25%).

| Element | Vastgelegd |
|---|---|
| Acceptance-window per milestone | **10 werkdagen** vanaf schriftelijke oplevering door Protocol |
| Deemed acceptance | Geen schriftelijk antwoord van klant binnen window = milestone geaccepteerd |
| Defect-rapportage door klant | Schriftelijk, met reproduceerbare beschrijving + verwijzing naar specifieke acceptance-criteria uit SoW |
| Cure window (material defect) | **15 werkdagen** voor Protocol om te repareren |
| Re-test cyclus | Maximaal **2 cycli** voor dezelfde defect; daarna escalatie naar Sectie 18 (notices & escalatie) |
| Acceptance-criteria zelf | **Per SoW gedefinieerd**, niet generiek in MSA |
| Final acceptance triggert | (a) start warranty-periode (Sectie 6b), (b) laatste betalingsmilestone uit Sectie 4a |

**Aanvulling specifiek voor AI-builds**

Voor Client Automations met substantiële AI-component (HR Agent, Brand Shield, Mailbox Ticket Counting, agent-based workflows) is "werkend" niet binair. Acceptance-criteria voor deze builds vereisen objectiveerbare meetbaarheid in de SoW:

| Element | Vastgelegd |
|---|---|
| Test-set | Klant levert representatieve cases pre-acceptance (bv. 50-100 typische input-cases voor de specifieke use-case) |
| Accuracy-target | Per SoW concreet meetbaar gedefinieerd (bv. "≥90% van test-cases krijgt correcte response", "≤2% hallucinatie-rate gemeten op test-set") |
| Drift over tijd | Gedragsverandering door derde-partij-model-updates (OpenAI, Anthropic) is **geen defect** — zie 6d (third-party-provider risk) |
| Subjective preferences | Antwoorden die afwijken van klant-voorkeur maar binnen accuracy-target vallen, gelden als geaccepteerd; aanpassing via change-order (6e) |

**Reden voor 10 werkdagen acceptance-window**:
- Korter (5 dagen) is voor enterprise-klanten als LN niet haalbaar — multiple stakeholders moeten testen, vakantieperiodes spelen mee bij MOJO/AFAS Live/Ziggo Dome
- Langer (20-30 dagen) blokkeert Protocol's cashflow en houdt projecten te lang in limbo
- 10 werkdagen is markt-standaard voor B2B-software-acceptance in NL, juridisch verdedigbaar

**Reden voor deemed acceptance**:
- Voorkomt dat klant kan blijven uitstellen — als LN niet test, kan Protocol niet eeuwig wachten op laatste betaling
- Beschermt tegen klant-tactiek "we hebben het nog niet getest dus we betalen niet"
- Standaard in enterprise-MSAs onder NL-recht; LN-legal kent dit pattern

**Reden voor "acceptance-criteria per SoW, niet in MSA"**:
- Brand Shield's acceptance-criteria zijn fundamenteel anders dan HR Agent's
- Generieke MSA-criteria zouden óf te vaag zijn (waardeloos in conflict) óf te specifiek (passen niet bij elke build)
- SoW is de juiste plek; MSA legt alleen het procedurele kader vast

**Reden voor AI-specifieke test-set + accuracy-target**:
- Bij traditionele software-acceptance is "deze functie werkt" objectief testbaar; bij AI is dat onmogelijk zonder vooraf vastgelegde criteria
- Zonder dit beland Protocol in eindeloze "ja maar het antwoordde niet zoals ik wilde"-discussies bij elke acceptance-cycle
- Test-set + accuracy-target dwingt klant pre-launch over te denken wat "werkend" betekent — dat is precies de discipline die we willen forceren
- Beschermt zowel klant (objectieve meting) als Protocol (geen subjectieve afkeuring)

**Concept-formulering MSA Section "Acceptance" (NL → ICTRecht naar EN)**:

> *"Each milestone deliverable shall be subject to acceptance testing by Customer against the acceptance criteria set out in the applicable Statement of Work. Customer shall have ten (10) business days from written notice of delivery (the 'Acceptance Period') to either (i) accept the deliverable in writing, or (ii) provide a written notice of defect identifying with reasonable specificity the alleged failure to conform to the acceptance criteria. If Customer provides no written response within the Acceptance Period, the milestone shall be deemed accepted.*
>
> *Where a deliverable comprises an AI-driven service, agent, or workflow, the applicable Statement of Work shall define (a) a representative test-set provided by Customer, and (b) an objective accuracy or performance threshold against which acceptance shall be measured. Variations in output that fall within the agreed accuracy threshold shall not constitute a defect.*
>
> *Service Provider shall have fifteen (15) business days from receipt of a valid defect notice to remediate the identified defect (the 'Cure Period'). Following remediation, the corrected deliverable shall be subject to re-testing within a further five (5) business days. A maximum of two (2) cure cycles shall apply to any single defect; thereafter the matter shall be escalated pursuant to Section [Notices & Escalation]."*

---

**6b. Defect-management binnen warranty-periode**

Na final acceptance start een gedefinieerde warranty-periode waarin Protocol kosteloos defects repareert. Hierna gaan defects via managed support uit Sectie 4a (retainer of on-demand T&M).

| Element | Vastgelegd |
|---|---|
| Warranty-periode (default) | **30 dagen na final acceptance** |
| Verlenging per SoW | Optioneel tot 60 dagen, typisch bij Clean Handover-model (Besluit 4) |
| Wat is een defect | Niet-conform de acceptance-criteria; niet-werkend zoals SoW beschrijft; reproduceerbaar |
| Wat is GEEN defect | (a) Wijzigingsverzoek; (b) door klant doorgevoerde wijziging (sluit aan op 6c en 5d-IP-carve-out); (c) scope-uitbreiding; (d) gedrag dat afwijkt van klant-verwachting maar binnen SoW + accuracy-target valt |
| Severity-tiers | **Material** (production-blocker / security-issue): 5 werkdagen fix / **Non-material**: 15 werkdagen fix |
| Tijdens warranty | Defect-fix kosteloos voor klant |
| Na warranty | Via managed support (retainer of on-demand T&M, Sectie 4a) |

**Reden voor 30 dagen default warranty**:
- Aansluitend op Besluit 4 (`dpa-strategy-decisions.md`) — Clean Handover-model heeft 30-60 dagen warranty
- 30 dagen is voldoende voor klant om alle functionaliteit in productie te raken en defects te ontdekken
- Korter is voor klant onveilig; langer is voor Protocol commercieel onaantrekkelijk (verhoogt bouwsom-uplift bij Clean Handover)
- Bij Full Managed Support-model (Besluit 4 model A) loopt support sowieso door via retainer — warranty-periode is dan minder kritiek; 30 dagen volstaat

**Reden voor expliciete "wat is GEEN defect"-lijst**:
- Sluit direct aan op de change-control-carve-out uit Sectie 5d (IP-indemnity vervalt bij door klant doorgevoerde wijzigingen)
- Voorkomt dat warranty oneigenlijk gebruikt wordt voor scope-uitbreiding ("kunnen jullie er even een veld bij maken, het werkt nog niet helemaal voor ons")
- Beschermt tegen "het werkt niet zoals ik wilde"-claims (= wijzigingsverzoek, geen defect)
- Voor AI-builds essentieel: gedrag binnen accuracy-target = geaccepteerd, niet defect

**Reden voor 2-tier severity (niet 1- of 4-tier)**:
- 1-tier (alles binnen X dagen) is praktisch onhaalbaar — production-blockers vereisen sneller respons dan cosmetische issues
- 4-tier (P1/P2/P3/P4) is overengineered voor Protocol's schaal en de typische scope van Client Automations
- 2-tier model is markt-standaard voor mid-market builds en juridisch werkbaar in NL-rechtelijke context

---

**6c. Change-control bij operationele wijzigingen (shared-infra-bescherming)**

Change-control-clausule regelt wat er gebeurt als wijzigingen aan een operationeel systeem worden doorgevoerd buiten Protocol om. Dit is **verplicht** voor shared-infra-systemen waar klant operationele controle heeft over de tenant of het systeem (Brand Shield in MOJO's eigen n8n-tenant, Mailbox Ticket Counting in MOJO-systemen, toekomstige builds op klant-tenants). Maar de clausule heeft ook betekenis voor Protocol-gehoste builds — als Protocol zelf de operator is, gelden andere procedures voor backend-wijzigingen.

**Kern-clausule (gebaseerd op `narrative-non-negotiables-briefing.md` Sectie 5)**:

> *"Vendor is liable solely for the configuration, code, workflows, and integrations that Vendor has deployed and confirmed in writing as production-ready. Changes to the system made by Controller, Controller's personnel, or third parties other than Vendor's authorized representatives, fall outside the scope of Vendor's liability. Upon detection of unauthorized or unplanned changes, Vendor shall notify Controller within a reasonable time and may suspend support obligations until the system is returned to a documented state."*

**Toepassing per hosting-model**:

| Hosting-model | Procedure |
|---|---|
| **Klant-tenant-hosting** (Brand Shield in MOJO's eigen n8n-tenant, Mailbox Ticket Counting in MOJO-systemen) | Klant notifieert Protocol **vooraf** bij geplande wijzigingen. Bij ongeplande wijzigingen: Protocol mag suspension-recht uitoefenen + re-baseline-fee in rekening brengen via change-order (6e). |
| **Protocol-tenant-hosting** (HR Agent voor AFAS Live, Venue Vera-architectuur) | Protocol is feitelijk operator. Klant heeft beperkte directe wijzigingstoegang; risico is lager. Clausule blijft nuttig voor klant-doorgevoerde wijzigingen via API-toegang of admin-portal. |

**Backend-wijzigingen door Protocol zelf (Protocol-tenant-hosting)**

Bij hosted-by-Protocol-builds is Protocol vendor én operator. Daarom moet expliciet vastgelegd worden welke door Protocol-geïnitieerde wijzigingen welke procedure vereisen:

| Type backend-change door Protocol | Procedure |
|---|---|
| Patch-versies, bugfixes, security-updates **zonder** functionele impact | Geen change-order, geen notificatie verplicht — onderdeel van normale operationele werking |
| Minor versie-upgrades van dependencies (bv. n8n 1.50 → 1.55) **zonder** functionele impact | Schriftelijke notice binnen 5 werkdagen na implementatie, geen acceptance vereist |
| Major-version-upgrades, vervanging van AI-provider (bv. GPT-4 → Claude), infrastructuur-migratie | Change-order vereist (6e) — zelfs als Protocol initieert. Klant moet pre-implementation akkoord geven. |
| Subprocessor-changes (nieuwe data-verwerker, bv. Vercel → Hetzner) | DPA-annex-procedure (Sectie 11), los van change-order |

**Reden voor MSA-niveau-clausule (niet alleen per SoW)**:
- Geldt voor alle huidige én toekomstige Client Automations onder deze MSA — niet alleen Brand Shield
- Toekomstige LN-builds (nieuwe MOJO-modules, AFAS-uitbreidingen, Ziggo Dome-integraties) erven dit kader automatisch
- Per SoW kan een specifieke uitwerking volgen (welke MOJO IT-medewerkers zijn "authorized representatives", welke wijzigingen zijn vooraf-toegestaan-buckets), maar het kader staat in MSA

**Reden voor pre-emptieve klant-notificatieplicht (in plaats van alleen "achteraf melden")**:
- Bij klant-tenant-hosting is preventie veel goedkoper dan repair — een MOJO-IT-medewerker die ongevraagd een API-key wijzigt kan Brand Shield in één keer breken
- Vooraf notifieren geeft Protocol kans om mee te denken vóór het probleem ontstaat
- Achteraf melden is acceptabel als compromis als MOJO IT hier bezwaar tegen maakt — op te nemen als fallback per SoW (bv. "schriftelijk binnen 5 werkdagen na de wijziging" voor reguliere systeem-wijzigingen, vooraf-notificatie alleen voor wijzigingen aan Protocol-componenten)

**Reden voor expliciete Protocol-tenant-procedure**:
- Zonder dit ontstaat ambiguïteit: bij HR Agent-hosting kunnen wij in principe alles veranderen zonder iemand te informeren — dat is voor LN-legal onaanvaardbaar bij productie-systemen
- 3-tier op functionele impact (geen / notice / change-order) geeft beide partijen helderheid
- Beschermt klant tegen verrassingen, beschermt Protocol tegen "jullie hebben zomaar wat veranderd"-claims

---

**6d. Third-party-AI-provider risk (model-deprecation, breaking changes)**

Specifiek risico-scenario voor Client Automations: derde-partij-AI-providers (OpenAI, Anthropic, Apify, Twilio) deprecate'n modellen of introduceren breaking changes in hun API-specs. Dit is voor traditionele software-bouwers zelden relevant; voor AI-builds een dagelijkse realiteit. MSA moet dit risico expliciet alloceren.

| Scenario | Classificatie | Wie betaalt |
|---|---|---|
| Third-party-AI-provider deprecate't model dat we gebruiken (bv. OpenAI deprecate't GPT-4-turbo) | **Geen defect**, geen warranty-claim | Migration-werk via change-order (6e) met eigen fixed-fee |
| Third-party-API breaking change die binnen warranty-periode (Sectie 6b) optreedt en die redelijkerwijs niet voorzien kon worden bij oplevering | **Defect** voor zover Protocol's code aanpassing nodig heeft | Binnen warranty: kosteloos |
| Third-party-API breaking change na warranty-periode | **Geen defect** | Migration-werk via managed support (Sectie 4a) of change-order |
| Third-party-provider service-disruption (downtime, outage) | **Geen aansprakelijkheid Protocol** — service-level-risico provider zelf | Geen — klant draagt downstream risico |
| Subprocessor-wijziging op verzoek klant (bv. vervang OpenAI met Anthropic) | **Change-order** (6e) + DPA-annex-update (Sectie 11) | Klant betaalt migration |
| Klant-doorgevoerde provider-keuze (bv. klant kiest specifiek voor model-X tegen Protocol's advies) | **Geen aansprakelijkheid Protocol** voor gevolgen van die keuze | Klant draagt risico |

**Concept-formulering MSA Section "Third-Party Provider Risk"**:

> *"Modifications to or deprecation of services provided by third-party AI providers, model providers, scraping services, communication providers, or other technology subprocessors used in the delivery of Client Automations under this Agreement (including but not limited to OpenAI, Anthropic, Apify, Twilio, and similar providers) shall not constitute a defect under this Agreement, except where such breaking change occurs within the warranty period set out in Section [Warranty] and could not reasonably have been foreseen at the time of acceptance.*
>
> *Where modifications to third-party providers require adaptation work to maintain functionality of a deployed Client Automation outside the warranty period, such adaptation shall be addressed via the change-order procedure set out in Section [Change Orders] or under managed support pursuant to Section [Managed Support].*
>
> *Service-level disruptions, outages, or downtime affecting third-party providers fall outside Service Provider's liability scope. Service Provider shall use commercially reasonable efforts to monitor third-party provider service status and to notify Customer of material disruptions affecting Customer's deployed services."*

**Reden voor expliciete provider-risk-allocatie**:
- Zonder dit beland elke OpenAI model-deprecation in een potentiële defect-claim — dat is voor Protocol's businessmodel verwoestend
- Voor LN-legal is dit een redelijke risico-allocatie omdat Protocol geen controle heeft over OpenAI/Anthropic; het is een externe-vendor-realiteit
- Voor klant is het zichtbaar gemaakt: provider-risk wordt expliciet erkend in de MSA, niet stilzwijgend op klant geschoven via boilerplate
- Markt-conform: de meeste enterprise-AI-MSAs in 2026 hebben vergelijkbare clausules (post-OpenAI-deprecation-incidenten van 2024-2025)

**Reden voor warranty-window-uitzondering**:
- Bij oplevering moet Protocol redelijkerwijs gebruik maken van producten die op dat moment actief en supported zijn
- Als binnen 30 dagen na oplevering OpenAI plotseling iets deprecate't dat Protocol gebruikt, valt dat onder professional-vendor-due-diligence — Protocol moet redelijkerwijs voorzien hebben dat het deprecated zou worden
- Buiten warranty-periode is dit niet redelijk; modellen kunnen jaren later deprecated worden zonder dat Protocol dat had kunnen voorzien

---

**6e. Change-order-procedure bij scope-wijzigingen (drie-tier formaliteit)**

Change-order-procedure regelt hoe scope-wijzigingen tijdens een actieve SoW vastgelegd worden. Sluit direct aan op Sectie 4a (geen T&M voor builds — alle scope-wijzigingen krijgen eigen fixed-fee). **Kernprincipe**: change-order is altijd schriftelijk vastgelegd, maar de formaliteit schaalt met de zwaarte van de wijziging — drie-tier-systeem.

**Drie-tier-formaliteit (kern-innovatie van deze MSA t.o.v. boilerplate)**

| Tier | Trigger | Vereiste formaliteit |
|---|---|---|
| **Tier 1 — Project-update** | Onder de minimis (≤4 uur werk) | Schriftelijke notice in projectupdate (email of vergelijkbaar kanaal naar Authorized Representative). Geen formele acceptance vereist. |
| **Tier 2 — Email-change-order** | Tussen 4 uur en de zware-wijziging-grens | Email-thread met de **vijf minimumvereisten** (zie hieronder). Schriftelijke "akkoord" of woorden van die strekking van Authorized Representative. |
| **Tier 3 — E-signature change-order** | Zware wijziging (zie definitie hieronder) | Apart change-order-document, getekend door beide partijen via DocuSign of vergelijkbare elektronische ondertekenoplossing |

**De vijf minimumvereisten voor een geldige Tier 2 email-change-order**

Een email-change-order is alleen rechtsgeldig en bewijskrachtig als de email-thread bevat:

1. **Expliciete verwijzing naar SoW** (bijvoorbeeld "Change Order #3 for SoW: Brand Shield V2")
2. **Scope-beschrijving** — concrete omschrijving wat verandert
3. **Fixed-fee** — uitsluitend bedrag (geen "we zien wel achteraf")
4. **Tijdlijn-impact** — schuift de oplevering, of niet
5. **IP/license-impact** — vermelding "geen impact" of expliciet wat verandert

Acceptance-zijde van klant: schriftelijk "akkoord" of vergelijkbare bewoording, vanuit een Authorized Representative-emailadres (Sectie 18 notices). Beide partijen archiveren de email-thread. De email-thread vormt addendum bij de SoW.

**Wanneer Tier 3 (e-signature) verplicht is**

| Trigger | Reden |
|---|---|
| Wijziging raakt een van de 5 locked sections (Liability, IP, Confidentiality, Indemnification, Governing Law — Sectie 2 safeguard) | Vereist MSA-niveau-handtekening, niet SoW-niveau |
| Wijziging raakt de DPA-annex (privacy/security-scope) | Compliance-niveau-bewijs nodig |
| Wijziging > €25.000 op de SoW-waarde, óf > 50% scope-uplift t.o.v. originele SoW-waarde | Materiële financiële impact rechtvaardigt zwaar-bewijs |
| Wijziging die looptijd van het project of de Authorized Affiliates wijzigt | Raakt MSA-niveau, niet alleen SoW |

**Algemene change-order-procedure (alle Tiers)**

| Stap | Vastgelegd |
|---|---|
| 1. Verzoek | Klant of Protocol initieert wijzigingsverzoek (mondeling of schriftelijk toegestaan) |
| 2. Protocol-response | Protocol levert binnen **5 werkdagen** een change-order-document (Tier 2 of 3) of projectupdate-notice (Tier 1) |
| 3. Klant-acceptatie | Schriftelijke acceptance (email "akkoord" voor Tier 2 / e-signature voor Tier 3) voordat extra werk start |
| 4. Status | Geaccepteerde change-order = addendum bij betreffende SoW; alle MSA-bepalingen blijven van kracht |
| Geen werk zonder akkoord | Protocol start geen extra werk vóór acceptance, behalve onder Emergency-procedure (zie hieronder) |

**Reden voor drie-tier-formaliteit (kern-positionering van deze MSA)**:
- 80% van de wijzigingen valt in Tier 1 of 2. Daarvoor wil Protocol geen DocuSign-overhead — dat is operationeel disfunctioneel en voor enterprise-werkbaarheid een dealbreaker
- Onder NL-recht is email-akkoord rechtsgeldig als wilsovereenstemming (BW 6:217); ontbreken handtekening is geen geldigheidsprobleem maar een bewijsversterker
- Tier 3 dwingt e-signature waar het werkelijk telt — bij wijzigingen die financiële of compliance-positie materieel raken
- Markt-conform: enterprise-MSA's gebruiken dit pattern al jaren; LN-legal kent het patroon

**Reden voor de vijf minimumvereisten (Tier 2)**:
- Voorkomt dat losse "kunnen jullie even X erbij doen?"-emails als change-order kunnen worden gekwalificeerd in conflict
- Maakt de email-thread bewijskrachtig zonder e-signature-overhead
- Forceert basis-discipline aan beide kanten (scope, prijs, tijdlijn, IP — vier dimensies waar de meeste conflicten over ontstaan)
- Voldoet aan NL-rechtelijke bewijslast-eisen voor contractwijzigingen

**Reden voor 4-uur de-minimis-grens (Tier 1)**:
- Voorkomt formele overhead voor échte kleine tweaks ("kun je die headline veranderen?")
- 4 uur is laag genoeg om "death by 1000 cuts" te voorkomen — geen accumulatie van mini-wijzigingen onder de radar
- Schriftelijke vastlegging in projectupdate blijft verplicht voor traceability
- Alternatief overwegen door ICTRecht: 0-uur-grens (alles via change-order). Strenger maar bureaucratischer; voor LN-werkbaarheid waarschijnlijk overdreven

**Reden voor change-order = addendum bij SoW (niet bij MSA)**:
- Wijziging raakt één specifiek project, niet het hele MSA-kader
- Houdt MSA stabiel; alle wijzigingen leven in de juiste SoW-laag
- Sluit aan op layered-precedence (Sectie 2): SoW (incl. change-orders) > MSA voor scope, MSA > SoW voor de 5 locked sections
- Vermijdt MSA-amendement voor elke kleine projectwijziging — dat is operationeel ondoenlijk

**Concept-formulering MSA Section "Change Orders"**:

> *"Any modification to the scope, timeline, fees, or deliverables of a Statement of Work shall be effected by a written change order ('Change Order'), prepared by Service Provider within five (5) business days of a request initiated by either party.*
>
> *Change Orders shall be classified into three categories:*
>
> *(a) **De Minimis Changes**: scope adjustments requiring four (4) hours or less of additional work may be addressed by a written project notice from Service Provider documenting the change. No formal acceptance signature is required, provided that such changes are recorded in the project documentation.*
>
> *(b) **Standard Change Orders**: scope adjustments exceeding the de minimis threshold but not constituting a Material Change Order shall be effected by a written email exchange specifying (i) reference to the applicable Statement of Work, (ii) the scope adjustment, (iii) the fixed-fee for the modification, (iv) any timeline impact, and (v) any intellectual property or license impact. Acceptance by Customer's Authorized Representative via written affirmative response shall constitute binding acceptance.*
>
> *(c) **Material Change Orders**: scope adjustments shall be effected by a separate written change order document executed by both parties using qualified electronic signature where the change (i) modifies any provision governing the matters set out in Section [Safeguard Clause], (ii) modifies the Data Processing Annex, (iii) increases the Statement of Work fees by more than €25,000 or by more than 50% of the original Statement of Work value, or (iv) modifies the term of the project or the Authorized Affiliates.*
>
> *No additional work outside the scope of an executed Statement of Work shall commence prior to acceptance of the applicable Change Order, except as provided under Section [Emergency Change Orders]."*

---

**6f. Emergency change-order (urgente productie-issues)**

Specifiek scenario: production-blocking issues, security-issues, of compliance-incidenten waarbij de standaard change-order-procedure (5 werkdagen response) niet redelijk is. Zonder emergency-mechanisme moet Protocol kiezen tussen werken zonder dekking (juridisch onveilig) of klant 5 dagen laten wachten (reputatie- en relatie-schade).

| Element | Vastgelegd |
|---|---|
| Emergency-trigger | Production-blocking issue, security-issue, of compliance-incident waarbij standaard change-order-procedure (5 werkdagen) niet redelijk is, EN dat buiten warranty-periode valt of buiten warranty-defect-definitie (geen reguliere defect, dus warranty-fix is niet van toepassing) |
| Procedure starten | Mondeling of schriftelijk akkoord (telefoon/Slack/email) van Authorized Representative volstaat voor onmiddellijke start |
| Pricing tijdens emergency | T&M tegen het hourly rate uit de toepasselijke SoW (typisch €195/uur uit Sectie 4a) |
| Cap zonder formalisering | Maximaal **20 uur** emergency-werk zonder achteraf-formalisering. Bij overschrijding: standstill tot change-order getekend is |
| Formalisering achteraf | Binnen **5 werkdagen** na start emergency-werk: schriftelijke change-order op Tier 2-niveau (email-thread met de vijf minimumvereisten). Alle gewerkte uren worden hierin retrospectief vastgelegd. |
| Niet bedoeld voor | Reguliere defect-fixes binnen warranty (die gaan via 6b) of reguliere scope-wijzigingen (die gaan via 6e) |

**Reden voor emergency-mechanisme**:
- Production-systemen (vooral Brand Shield in MOJO's eigen n8n-tenant en HR Agent op Protocol-tenant) kunnen incidenten hebben die niet onder warranty vallen maar wel onmiddellijke actie vereisen
- Zonder dit mechanisme moet Protocol kiezen tussen onveilig werken (zonder commerciële dekking) of klant 5 dagen laten wachten op formaliteit (relatieschade)
- Cap op 20 uur voorkomt scope-creep onder emergency-vlag — als het werk groter wordt, moet alsnog formaliteit volgen

**Reden voor T&M-pricing tijdens emergency**:
- Emergency-werk is per definitie niet vooraf in te schatten in scope of tijd
- Fixed-fee zou ofwel ondervergoed (Protocol risico) ofwel overgepriced (klant-irritatie) zijn
- T&M is hier de redelijke vorm — sluit aan op Sectie 4a uitzondering ("hourly rate alleen bij on-demand support en transition")
- Hourly rate komt uit de toepasselijke SoW, dus voorspelbaar voor klant

**Reden voor 20-uur-cap**:
- Onder 20 uur is de financiële exposure beheersbaar (bij €195/uur = €3.900) — beide partijen kunnen dit risico dragen zonder formaliteit-vooraf
- Boven 20 uur is het werk substantieel genoeg om alsnog formele dekking te vereisen
- 5 werkdagen-formalisering-window dwingt discipline: emergency mag niet maandenlang doorlopen zonder change-order

**Concept-formulering MSA Section "Emergency Change Orders"**:

> *"Where a production-blocking incident, security incident, or compliance event affecting a deployed Client Automation requires immediate remediation that cannot reasonably await the standard Change Order procedure set out in Section [Change Orders], either party may invoke the Emergency Change Order procedure. Upon oral or written approval by Customer's Authorized Representative, Service Provider may commence remediation work immediately, billable on a time-and-materials basis at the hourly rate set out in the applicable Statement of Work.*
>
> *Emergency Change Order work shall be capped at twenty (20) hours absent retrospective formalization. Within five (5) business days of commencement of Emergency Change Order work, the parties shall execute a Standard Change Order pursuant to Section [Change Orders] documenting the scope of work performed and the corresponding fees.*
>
> *The Emergency Change Order procedure shall not apply to defects subject to the warranty obligations set out in Section [Warranty] or to ordinary scope modifications, both of which shall follow their respective procedures."*

---

> ⚠️ **Open vraag 6a (10-werkdagen acceptance + deemed acceptance — NL-houdbaarheid)**: Staat een 10-werkdagen-acceptance-window met deemed acceptance (klant moet binnen die termijn bezwaar maken of deliverable geldt als geaccepteerd) onder NL-recht goed in een enterprise-context met multi-affiliate-structuur (LN-NL + Ziggo Dome + AFAS Live + MOJO)? Markt-standaard, maar graag specifiek toetsen of een enterprise-klant met meerdere stakeholders deze termijn juridisch zou kunnen aanvechten als "te kort voor redelijke beoordeling".

> ⚠️ **Open vraag 6b (AI-acceptance-mechanisme — defect-grond bij threshold-afwijking)**: Laat de AI-acceptance-formulering (test-set + accuracy-target, bijv. 92% accuracy op een vooraf overeengekomen evaluatie-set) juridisch verfijnen zodat onomstreden vaststaat dat individuele afwijkingen *binnen* de accuracy-threshold géén defect-grond zijn — ook al ervaart een eindgebruiker een specifieke output als onbevredigend. Dit is nieuw juridisch terrein specifiek voor AI-builds; welke formulering bindt klant het sterkst aan het statistische acceptance-criterium?

> ⚠️ **Open vraag 6d (third-party-AI-provider warranty-window — afgrenzing)**: De third-party-AI-provider-risk-clausule (uitsluiting van warranty-claims voor schade veroorzaakt door OpenAI/Anthropic/Twilio-zijde uitvallen) is markt-conform in 2026. De warranty-window-uitzondering — Protocol redelijkerwijs voorzienbaarheid van third-party-risico bij oplevering — moet juridisch goed afgegrensd worden om ambiguïteit te vermijden. Welke formulering legt de bewijslast helder bij de klant (LN moet aantonen dat het risico voorzienbaar was) zonder Protocol onbedoeld aan een algemene best-efforts-warranty te binden?

> ⚠️ **Open vraag 6e (drie-tier change-order-formaliteit — bewijskracht + €25k-grens)**: Valideer de drie-tier-change-order-formaliteit onder NL-recht. Twee deelvragen: (1) Is het "vijf minimumvereisten voor Tier 2"-mechanisme (email-thread met expliciete acceptance, scope, prijs, deadline, identiteit) sluitend bewijskrachtig onder NL-recht, of moet er expliciet verwezen worden naar Wet elektronische handtekeningen (eIDAS) voor Tier 3? (2) Kan de €25.000 / 50% scope-uitbreiding-grens voor Tier 3 als hard criterium worden gebruikt, of zijn aanvullende formuleringen nodig ("inclusief BTW", "cumulatief over alle Change Orders binnen één SoW", "berekend op gemiddeld kwartaal-volume") om interpretatie-disputes te vermijden?

> ⚠️ **Open vraag 6f (Emergency Change Order — mondeling akkoord NL-bewijslast)**: Het Emergency Change Order-mechanisme staat een mondeling akkoord toe (telefoon/Slack) voor onmiddellijke start, met 5-werkdagen achteraf-formalisering. Het mondelinge-akkoord-deel is juridisch grijs onder NL-recht. Hoe regelt de Emergency CO-clausule de bewijslast het beste — bijv. via een verplichte gespreksnotitie binnen 4 uur met email-bevestiging door de klant, of via een achteraf-DocuSign-formalisering met expliciete erkenning dat mondeling akkoord op X-datum gegeven is?

### Sectie 7 — Liability cap-architectuur

**Datum vastgelegd**: 2026-05-03 (research-pass via deep-research agents tegen ICTRecht/NLdigital 2025/AI Act/PLD 2024/2853)

#### Methodologische context

ICTRecht heeft geen eigen publieke standaard-template voor liability caps in IT-services-contracten. Hun gepubliceerde positie verwijst consistent naar **NLdigital Voorwaarden 2025** als branchestandaard voor IT-leveranciers in Nederland. Deze sectie sluit aan bij NLdigital 2025 (art. 15-16) waar zinvol, met expliciete afwijkingen waar onze AI-specifieke situatie dat vereist.

**Sources voor onderbouwing**:
- NLdigital Voorwaarden 2025 art 15-16 (cap, time-bar, opzet-carve-out)
- ICTRecht-blogs: "Beperking aansprakelijkheid", "Belangrijkste valkuilen aansprakelijkheidsregeling", "Beperken van uw aansprakelijkheid", "AI en contractuele aansprakelijkheid"
- Engelfriet (iusmentis.com): factuurbedrag of laatste 3 facturen als universele formule
- EU AI Act art 16 (provider) + art 26 (deployer)
- Product Liability Directive 2024/2853 (in werking dec 2024, NL-omzetting deadline dec 2026)
- AILD ingetrokken 6 oktober 2025 — geen automatische bewijslast-omkering meer voor AI-claims

---

#### 7a. General cap — 12 maanden aggregate fees, rolling window

| Element | Positie |
|---|---|
| **Cap-grondslag** | Aggregate fees betaald door LN aan Protocol over de **rolling 12-month window** voorafgaand aan de claim |
| **Scope** | Geldt over alle SoW's onder MSA gezamenlijk, niet per-SoW |
| **Berekening** | Bij claim op tijdstip T: som van fees over (T-12 maanden, T) |
| **Valutair** | Euro |
| **Geen vaste floor** | Bij kleine SoW's (bijv. €5.000 single-project) is cap = €5.000. Geen contractuele minimum-floor. Insurance (€2M aggregate / €1M per claim) is de feitelijke backstop voor materiële incidenten. |

**Reden — waarom rolling 12-month window**:
NLdigital 2025 art 15.1 hanteert "jaarcontractwaarde" als grondslag voor directe schade, met absolute cap van €500.000. Engelfriet (ICTRecht) adviseert "factuurbedrag of laatste 3 facturen". Een rolling 12-month window is de slimmere variant voor MSA's met variabele intensiteit:
- Bij uitbreiding van samenwerking groeit de cap automatisch mee — voorkomt argument dat lage early-stage cap onredelijk is als de samenwerking later substantieel wordt
- Sluit naadloos aan bij NLdigital's jaargrondslag — ICTRecht zal dit als marktconform herkennen
- Voorkomt reset-discussies tussen contractjaren (vs. calendar-year cap)
- Auto-schaling betekent dat de cap **alleen wordt wat er werkelijk aan fees is gefactureerd** onder de MSA — niet wat ooit voorgesteld is. Bij €30k feitelijke jaaromzet = General Cap €30k. Bij €100k feitelijke jaaromzet = General Cap €100k. Geen vaste blootstelling op basis van projecties.

**Reden — waarom geen vaste floor**:
Veel Protocol-deals zijn klein-volume (€5.000-€25.000 single-build). Een contractuele floor (bijv. €100k) zou disproportioneel zijn t.o.v. de werkelijke risico-blootstelling van zulke deals — en zou bij faillissement een onredelijk groot deel van de boedel beslag leggen. Insurance-polis (€2M agg / €1M per claim) is de feitelijke backstop bij materiële incidenten ongeacht deal-grootte. LN-juristen kunnen vragen om floor — counter via "insurance-polis dekt €2M aggregate ongeacht contractuele cap".

**Reden — waarom aggregate, niet per-SoW**:
Engelfriet expliciet: *"Een limiet 'per jaar' is dan ook zeer aan te bevelen."* Per-incident of per-SoW-caps genereren discussies over clustering van fouten. Aggregate over rolling 12-month window is helder, eenduidig en pro-Protocol bij parallel-lopende SoW's.

**EN concept-formulering voor ICTRecht**:
> *"Subject to Section 7c (Carve-Outs) and Section 7b (Super-Cap), the aggregate liability of each Party arising out of or in connection with this Agreement, all Statements of Work issued hereunder, and any related instrument, shall not exceed the total fees paid or payable by Customer to Protocol under this Agreement during the twelve (12) months immediately preceding the date on which the cause of action first arose (the 'General Cap'). The General Cap shall apply to all claims, whether based in contract, tort (including negligence), strict liability, or any other theory of liability, and whether arising from a single event or a series of related events, on an aggregate basis across all Statements of Work."*

---

#### 7b. Super-cap — 2× general cap voor specifieke breach-categorieën

| Categorie | Multiplier | Reden |
|---|---|---|
| **Data breach door Protocol** (opzet/grove nalatigheid) | 2× General Cap | Single-incident-blootstelling kan aggregate fees overstijgen; AVG art 82 schadevergoeding aan betrokkenen |
| **IP-inbreuk** door Protocol's deliverables (Foreground IP) | 2× General Cap | Cross-link met Sectie 5d IP-warranty + Sectie 8 indemnification |
| **Schending vertrouwelijkheid** (mutual) | 2× General Cap | Background-IP-leakage LN-zijde + bedrijfsgegevens Protocol-zijde |

**Reden — waarom 2× en niet 3×**:
Markt varieert 1.5×-3×. NLdigital 2025 kent geen super-cap (één cap voor directe schade, indirect uitgesloten). 2× is defensief reëel volgens beide research-passes:
- Voor 2-persoons-vendor onverzekerbaar boven 2× zonder forse premie-stijging
- LN kan duwen richting 3× — counter-argument: super-cap is per definitie additioneel boven NLdigital-standaard, dus 2× is al concession
- Insurance-polis (€2M agg / €1M per claim) dekt feitelijk het 2×-niveau voor de feitelijke deal-omvang die Protocol bij LN haalt — bij elke realistische jaaromzet onder LN-MSA blijft 2× super-cap binnen polis-limiet

**Reden — waarom geen super-cap voor GDPR-fines**:
Zie Sectie 7g hieronder. AVG-boetes zijn administratieve sancties van toezichthouder — niet contractueel doorbelastbaar. Vallen buiten MSA, geregeld via DPA.

**Reden — waarom super-cap mutual is**:
Symmetrische cap-architectuur. LN-zijde super-cap voor confidentiality dekt het scenario waarin LN Protocol's Background-IP (methodology, prompt-architectures, n8n-blueprints — Sectie 5b) onrechtmatig gebruikt of lekt. NLdigital is eigenlijk eenzijdig (vendor-only), maar wederzijdse cap is verdedigbare keuze in MSA-niveau-relatie tussen gelijkwaardige zakelijke partijen.

**EN concept-formulering voor ICTRecht**:
> *"Notwithstanding Section 7a, the aggregate liability of a Party for any of the following categories shall not exceed two (2) times the General Cap (the 'Super-Cap'): (i) Data breaches caused by such Party's wilful misconduct or gross negligence in its capacity as Processor or Controller (as applicable); (ii) Intellectual Property infringement claims arising out of such Party's deliverables under any Statement of Work, subject to the indemnification procedure set forth in Section 8; (iii) Breaches of confidentiality obligations under Section 14, including unauthorized use or disclosure of the other Party's Background IP. The Super-Cap is in lieu of, not in addition to, the General Cap for matters falling within these categories."*

---

#### 7c. Carve-outs — uitzonderingen op alle caps

**Unlimited liability** (geen cap, juridisch niet uit te sluiten onder NL-recht):
- Opzet
- Bewuste roekeloosheid (grove schuld)
- Fraude

**Reden**: NL-recht (BW 6:248, HR-arrest 2006-garagezaak) verklaart aansprakelijkheidsbeperking nietig bij opzet/bewuste roekeloosheid — als deze carve-out ontbreekt wordt **de gehele cap-clausule nietig**. NLdigital 2025 art 15.6 bevestigt deze carve-out expliciet. Dit is verplicht juridisch onderhoud, geen onderhandelingsruimte.

**Onder Super-Cap (2× General Cap)** (zie 7b):
- Schending vertrouwelijkheid
- IP-indemnity Sectie 8

**Onder DPA-aansprakelijkheidsregeling** (separate van MSA-cap):
- AVG-overtredingen door Protocol als verwerker — geregeld in Master-DPA cap-clausule
- Reden: zie Sectie 7g

**Reden — waarom geen unlimited carve-out voor confidentiality**:
Eerste voorstel had vertrouwelijkheid als unlimited carve-out. Beide research-passes flagde dit als over-concessie:
- NLdigital 2025 kent geen unlimited confidentiality-carve-out
- Onverzekerbaar voor 2-persoons-vendor
- Niet juridisch nodig (geen wettelijke verplichting zoals bij opzet)
- Super-cap (2×) is voldoende substantieel om LN-IT-juristen comfort te bieden

**EN concept-formulering voor ICTRecht**:
> *"The General Cap and Super-Cap shall not apply to liability arising from: (i) wilful misconduct or gross negligence (opzet of bewuste roekeloosheid) of a Party or its officers; (ii) fraud or fraudulent misrepresentation; (iii) breach of mandatory provisions of Dutch law that cannot be limited by contract. Liability under the Data Processing Agreement shall be governed exclusively by the liability provisions set forth therein and shall not be subject to the caps in Sections 7a or 7b of this Agreement."*

---

#### 7d. Aggregate scope — rolling 12-month window over alle SoW's

Reeds beschreven onder 7a. Expliciet geformuleerd ter voorkoming van interpretatie-discussies:
- Cap geldt **aggregate over alle SoW's onder MSA**, niet per-SoW
- Window is **rolling**: 12 maanden voorafgaand aan de date-of-claim (niet calendar-year)
- Bij meerdere SoW's parallel: één gezamenlijke cap, geen reset per SoW

**EN concept-formulering**:
> *"For the avoidance of doubt, the General Cap and Super-Cap operate on an aggregate basis across all Statements of Work and other instruments executed under this Agreement. A claim arising under one Statement of Work shall draw down against the aggregate cap available to all Statements of Work; no separate or additional cap shall be deemed to apply per Statement of Work."*

---

#### 7e. Time-bar — claim-verjaringstermijn

| Termijn | Periode |
|---|---|
| **Tijdens MSA-looptijd** | 24 maanden na **datum van redelijke kennis** van schade en aansprakelijke partij |
| **Na MSA-einde** | 36 maanden post-termination tail (claims die voortvloeien uit acties tijdens MSA-looptijd) |

**Reden — waarom 24 mnd na "datum van redelijke kennis"**:
NLdigital 2025 hanteert "24 maanden na het ontstaan van de vordering" — strenger dan onze positie (NLdigital meet vanaf incident-datum, wij meten vanaf discovery). De NL-wettelijke verjaringstermijn is 5 jaar (BW 3:310 lid 1) waarbij de termijn loopt vanaf "de dag waarop de benadeelde redelijkerwijs op de hoogte was of had kunnen zijn van de schade en de aansprakelijke partij".

Voor AI-builds is discovery-rule belangrijker dan event-datum:
- Hallucination-schade kan pas maanden na deployment manifest worden (drift)
- Datalek kan onontdekt blijven voor lange tijd
- Discovery-rule is bovendien NL-wettelijk equivalent — geen pretentieuze afwijking

24 maanden is vergelijkbaar met NLdigital's contractuele inkorting (van 5 jaar wettelijk naar 24 mnd contractueel). 36 mnd post-MSA-tail is ruimer dan branchestandaard maar logisch voor MSA's die 3+ jaar lopen — claims uit 2026-incident moeten in 2029 nog kunnen worden geladen als MSA in 2027 eindigt.

**EN concept-formulering**:
> *"Any claim arising out of or in connection with this Agreement must be commenced within twenty-four (24) months from the date on which the claiming Party first knew or reasonably should have known of (i) the damage and (ii) the identity of the liable Party (the 'Claim Period'). For claims arising from acts or omissions occurring during the Term but discovered after termination or expiration of this Agreement, the Claim Period shall be the earlier of (a) twenty-four (24) months from such discovery, or (b) thirty-six (36) months from the effective date of termination or expiration. Any claim not commenced within the applicable Claim Period shall be irrevocably waived. This provision constitutes a contractual shortening of the statutory limitation period under Article 3:310 of the Dutch Civil Code."*

---

#### 7f. Indirect damages — uitsluiting + dataverlies-definitie

**Uitgesloten als indirecte schade** (NLdigital 2025 art 16.4-conform):
- Lost profits / gederfde winst
- Business interruption / bedrijfsstagnatie
- Loss of goodwill / verminderde goodwill
- Reputational harm / reputatieschade
- Lost savings / gemiste besparingen

**Dataverlies — expliciete definitie nodig**:
NLdigital 2025 heeft de expliciete uitsluiting van dataverlies **verwijderd** uit de indirecte-schade-lijst (was wel in 2020-versie). Grijs gebied. Onze positie:

| Type dataverlies | Behandeling |
|---|---|
| Direct dataverlies door Protocol's verwerking onder een SoW (verwijderd door bug, ongeoorloofde overschrijving, etc.) | Onder General Cap |
| Dataverlies door opzet/grove nalatigheid Protocol | Onder Super-Cap (7b) |
| Dataverlies als gevolg van downstream business-onderbreking (bijv. LN kon transactie niet voltooien omdat tool down was) | **Uitgesloten** als indirecte gevolgschade |

**Reden — waarom expliciete behandeling**:
Beide research-passes flagde dit. Zonder definitie kan rechter dataverlies bij AI-systemen kwalificeren als "direct" omdat AI-systeem proximate cause is. Door zelf de definitie vast te leggen voorkomen we ICTRecht-discussie bij review.

**EN concept-formulering**:
> *"Neither Party shall be liable for any indirect, consequential, or special damages, including but not limited to lost profits, lost savings, business interruption, loss of goodwill, or reputational harm, regardless of whether such damages were foreseeable. For purposes of this Section, 'data loss' shall be classified as follows: (i) loss of data directly caused by Protocol's processing operations under a Statement of Work, including erroneous deletion, overwriting, or corruption attributable to Protocol's deliverables, shall constitute direct damage subject to the General Cap; (ii) loss of data resulting from Protocol's wilful misconduct or gross negligence shall be subject to the Super-Cap; (iii) loss of data manifested as downstream business interruption (e.g., transactions Customer could not complete due to system unavailability) shall constitute consequential damage and is excluded from compensable damages."*

---

#### 7g. AVG-boetes — buiten MSA, alleen via DPA

**Positie**:
> *AVG-boetes vallen buiten deze MSA. Protocol's aansprakelijkheid voor AVG-overtredingen door Protocol als verwerker is uitsluitend geregeld in de DPA en de daarin opgenomen aansprakelijkheidsregeling. Schadevergoeding aan betrokkenen onder Art 82 AVG die LN heeft betaald en die voortvloeit uit Protocol's verwerkersfout valt onder de MSA-cap-architectuur (General Cap, met Super-Cap voor data breach door Protocol's opzet/grove nalatigheid per Sectie 7b).*

**Reden — waarom GDPR-fines uit MSA halen**:
Eerste voorstel had GDPR-fine pass-through onder super-cap (2×). Beide research-passes wezen dit krachtig af:

1. **Juridisch problematisch onder NL-recht**: AVG-boetes zijn administratieve sancties die de toezichthouder direct oplegt aan de overtreder voor diens eigen AVG-falen. Contractueel doorbelasten van regulatoire boetes is in beginsel niet houdbaar — Linklaters-analyse: alleen "innocent/negligent conduct" indemnity is afdwingbaar, niet boete-pass-through bij opzettelijk falen.

2. **Onverzekerbaar**: E&O-polissen dekken typisch geen contractueel overgenomen administratieve sancties. Inhoudelijk kan vendor de blootstelling dus niet absorberen.

3. **ICTRecht-positie**: ICTRecht's [verwerkersartikel](https://www.ictrecht.nl/blog/kun-je-in-een-verwerkersovereenkomst-afspraken-maken-over-je-aansprakelijkheid) bevestigt dat aansprakelijkheidsbeperkingen tussen partijen toegestaan zijn, maar boete-pass-through wordt impliciet als niet-houdbaar behandeld. Agent 1: *"ICTRecht zal de huidige formulering [pass-through onder super-cap] terugsturen."*

4. **AP-praktijk**: Autoriteit Persoonsgegevens past zelf al pro-rata-allocatie toe bij gedeelde aansprakelijkheid — boete wordt opgelegd aan de partij met de meeste zeggenschap. Pre-contractueel oplossen is onnodig.

5. **LN-juridische realiteit**: bij €20M-class-fines is 2× super-cap feitelijk symbolisch — ongeacht of dat super-cap nu €30k, €100k of €500k is. LN-juristen prikken hier doorheen — beter om dit gesprek niet aan te gaan.

**Wat WEL onder MSA valt**:
Schadevergoeding aan betrokkenen onder Art 82 AVG die LN heeft betaald en die aantoonbaar voortvloeit uit Protocol's verwerkersfout. Dit is geen boete maar civiele schade — valt onder normale cap-architectuur (General Cap, Super-Cap bij opzet/grove nalatigheid).

**EN concept-formulering**:
> *"Administrative fines imposed by supervisory authorities under Articles 83 GDPR or under any equivalent regulatory framework, whether levied on Customer or on Protocol, fall outside the scope of this Agreement. Each Party shall bear administrative fines imposed on it directly. Liability for breach of data protection obligations between the Parties shall be governed exclusively by the liability provisions of the Data Processing Agreement. Compensation paid by Customer to data subjects pursuant to Article 82 GDPR, to the extent such compensation arises from Protocol's processing failure as Processor, shall be recoverable under this Agreement subject to the General Cap (or Super-Cap, in the case of wilful misconduct or gross negligence by Protocol)."*

---

#### 7h. AI-output liability — MSA-baseline + SoW-detail

**MSA-baseline (deze sectie)**:
1. **AI Act-rollen vastleggen**: Protocol = "aanbieder" (Provider, Art 16 AI Act), LN = "gebruiksverantwoordelijke" (Deployer, Art 26 AI Act)
2. **Third-party-AI-provider risk**: Protocol niet aansprakelijk voor model-deprecation, breaking changes of service-disruption door OpenAI/Anthropic/etc. (cross-ref Sectie 6d — al vastgelegd)
3. **AI-output accuracy disclaimer**: Protocol staat er niet voor in dat AI-outputs feitelijk correct zijn in alle gevallen. Outputs zijn probabilistisch.
4. **Human-in-the-loop verplichting**: LN als deployer verplicht zich tot redactionele verificatie van AI-outputs voordat deze worden gebruikt voor externe communicatie of formele beslissingen.
5. **AI-system risk-classification per SoW**: Voor elke build wordt in de SoW vastgelegd of het AI-systeem onder Annex III AI Act valt (high-risk). Bij Annex III: Protocol levert technische documentatie + instructies aan LN per Art 16; LN draagt deployer-verplichtingen per Art 26.

**SoW-detail (per build vast te leggen)**:
- Test-set + accuracy-target (cross-ref Sectie 6a — al vastgelegd voor acceptance)
- Drift-procedure: hoe wordt accuracy in productie gemonitord, en wat is de procedure bij accuracy-degradatie?
- Disclaimer-taal specifiek voor de build: *"This tool produces AI-generated outputs intended to support [X]. Final operational decisions remain with Customer's authorized personnel."*

**Reden — waarom MSA-baseline naast SoW-detail**:
Eerste voorstel: alleen SoW-disclaimer. Beide research-passes wezen dit als onvoldoende af:
- ICTRecht's AI-Act-artikel adviseert AI-rollen contractueel vastleggen op MSA-niveau
- PLD 2024/2853 (NL-omzetting dec 2026): AI-software wordt expliciet "product"; B2B-uitsluiting jegens injured persons (LN-medewerkers) niet mogelijk
- AI Act Art 26 deadline aug 2026: deployer-verplichtingen voor Annex III-systemen — die scheiding moet pre-emptief contractueel
- WhatsApp HR Agent grenst aan Annex III punt 4 (workplace decisions). Positionering "informeert, beslist niet, human-in-the-loop verplicht" houdt het buiten Annex III — moet expliciet contractueel

**Waarom AILD-context relevant is**:
AI Liability Directive (AILD) is **formeel ingetrokken op 6 oktober 2025**. Geen automatische bewijslast-omkering meer voor AI-claims onder EU-recht. Gunstig voor Protocol — bij AI-claim moet eiser zelf causaliteit en defectiviteit bewijzen. Geen contractuele clausule nodig hierover, wel handig om in onderhandeling te kunnen bevestigen als LN ernaar verwijst.

**EN concept-formulering MSA-baseline**:
> *"For each Statement of Work involving deployment of AI systems by Protocol, the Parties acknowledge and agree as follows: (i) Protocol acts as 'Provider' and Customer acts as 'Deployer' within the meaning of Articles 16 and 26 of Regulation (EU) 2024/1689 (the 'AI Act'); (ii) The Statement of Work shall specify whether the AI system constitutes a high-risk AI system under Annex III of the AI Act, and if so, Protocol shall provide the technical documentation and instructions required under Article 16 to enable Customer to fulfil its Deployer obligations under Article 26; (iii) Protocol does not warrant that AI-generated outputs are factually accurate in all instances; outputs are probabilistic in nature and Customer shall implement editorial verification procedures for AI outputs used in external communications, formal decisions, or operational actions affecting third parties; (iv) Modifications, deprecations, or service disruptions affecting third-party AI providers, model providers, scraping services, communication providers, or other infrastructure suppliers shall be governed by Section 6d (Third-Party AI Provider Risk) of this Agreement and shall not constitute a defect or breach by Protocol unless caused by Protocol's failure to implement reasonably available mitigation."*

---

#### 7i. Insurance backing — €2M aggregate / €1M per claim minimum

| Element | Positie |
|---|---|
| **Polis-type** | Beroeps- en bedrijfsaansprakelijkheid (E&O) + cyber liability |
| **Aggregate cap** | Minimum €2.000.000 |
| **Per-claim cap** | Minimum €1.000.000 |
| **Verzekeraars** | Hiscox, Chubb, Markel of equivalent A-rated NL/EU-verzekeraar |
| **Term** | Onderhouden gedurende hele MSA-looptijd + 36 mnd run-off post-termination |
| **Certificaat** | Op verzoek COI (Certificate of Insurance) verstrekken |

**Reden — waarom €2M agg / €1M per claim (en niet €3M/€2M)**:
Agent 2 adviseerde €3M/€2M voor LN-enterprise-schaal op basis van een aangenomen €270k jaaromzet. **Wytze's correctie (2026-05-03)**: we werken met **LN Netherlands en subsidiaries** (AFAS Live, MOJO, Ziggo Dome), niet LN Global ($22B). Bovendien is €270k een geparkeerd voorstel — feitelijke jaaromzet onder MSA zal vermoedelijk een fractie zijn (€30-100k range). €2M/€1M zit comfortabel:
- Boven ARBIT-rijksinkoopstandaard (€1.25M per claim)
- Ver boven realistische super-cap-niveaus (2× General Cap blijft binnen €60k-€200k bij realistische jaaromzet onder MSA)
- Per-claim limiet €1M dekt vrijwel elk denkbaar enkelvoudig incident

Als Paul Meester (LN-NL) tijdens onderhandeling verhoging vraagt, optie open: **LN draagt mee aan premie-verhoging** boven Protocol's huidige polis-niveau. Premie-delta voor 2-persoons-bedrijf om naar €3M/€2M te gaan is ~€2-5k/jaar — verdedigbare kostendeelregeling als LN het echt wil.

**EN concept-formulering**:
> *"Throughout the Term and for thirty-six (36) months following termination or expiration of this Agreement, Protocol shall maintain professional indemnity (E&O) and cyber liability insurance with an A-rated insurer authorized to operate in the Netherlands or elsewhere in the European Union, with minimum coverage of €1,000,000 per claim and €2,000,000 in aggregate. Protocol shall provide a Certificate of Insurance (COI) to Customer upon written request. If Customer requires Protocol to maintain coverage above this baseline level, the Parties shall negotiate in good faith a reasonable contribution by Customer to the incremental premium cost."*

---

#### 7j. Mutuality — wederzijdse cap-architectuur

**Positie**: cap-architectuur is symmetrisch, met enkele scope-verschillen die de aard van elke partij weerspiegelen.

| Element | Protocol → LN | LN → Protocol |
|---|---|---|
| General Cap | 12 mnd aggregate fees | 12 mnd aggregate fees |
| Super-Cap voor data breach | Ja | Ja (LN als controller) |
| Super-Cap voor IP-inbreuk | Ja (Foreground IP, Sectie 5d) | N.v.t. — LN levert geen IP aan Protocol |
| Super-Cap voor confidentiality | Ja | Ja (Background-IP-leakage Sectie 5b) |
| Carve-out opzet/grove schuld/fraude | Ja (NL-wettelijk verplicht) | Ja (NL-wettelijk verplicht) |
| Carve-out niet-betaling fees | N.v.t. | Ja — LN's betaalverplichting valt niet onder cap |

**Reden — waarom mutual ondanks NLdigital eenzijdig is**:
NLdigital Voorwaarden zijn leveranciersgericht (vendor-only beperkt, klant unlimited). Voor MSA-niveau-relatie tussen gelijkwaardige zakelijke partijen is asymmetrische cap commercieel onhoudbaar (BW 6:248 redelijkheid-en-billijkheidstoets) en ook onverdedigbaar:
- Protocol's Background-IP heeft significante economische waarde — LN-leak zou Protocol fundamenteel kunnen schaden
- Protocol-medewerkers hebben toegang tot LN's productie-systemen — symmetrische zorgvuldigheidsplicht is logisch
- LN-side fees-verplichting al apart geregeld (Sectie 4 — wettelijke handelsrente)

LN-juristen accepteren mutuality als marktconform voor MSA's. Eenzijdige cap is alleen marktstandaard bij off-the-shelf SaaS, niet bij maatwerk-MSA.

**EN concept-formulering**:
> *"The General Cap, Super-Cap, and Carve-Outs set forth in this Section 7 shall apply mutually to both Parties, with each Party's liability to the other Party limited as set forth herein. Where a specific Super-Cap category is, by its nature, applicable to only one Party (e.g., IP infringement of deliverables, which is generated only by Protocol), the Super-Cap applies only to that Party. The mutuality of caps does not extend to Customer's obligation to pay fees due and payable under this Agreement, which obligation is unconditional and not subject to any liability cap."*

---

#### 7k. Subprocessor-aansprakelijkheidsketen [TOEVOEGING]

**Positie**: Protocol accepteert aansprakelijkheid voor schade veroorzaakt door geautoriseerde subprocessors (OpenAI, Apify, Resend, Hostinger, Vercel, Supabase, etc.) als ware het Protocol's eigen handelen, tot het niveau van Protocol's contractuele caps. Protocol bedingt flow-down-rights op subprocessors waar contractueel mogelijk.

**Reden — waarom expliciete subprocessor-clausule**:
OpenAI's eigen DPA cap't aansprakelijkheid op 12 maanden API-fees richting Protocol (~€1-6k/jaar voor typische builds). Als OpenAI een model-fout maakt die bij LN tot €1M schade leidt, kan Protocol nooit volledig verhaal halen — Protocol absorbeert het verschil. Marktstandaard in NL: vendor accepteert subprocessor-fouten als eigen ("step-in liability") binnen de eigen cap-architectuur, met flow-down-rights waar mogelijk.

Sectie 6d dekt model-deprecation (geen defect). Deze 7k-clausule dekt **operationele fouten** van subprocessors (bug in API-response, datalek bij subprocessor, etc.).

**EN concept-formulering**:
> *"Protocol shall be liable for the acts and omissions of its authorized subprocessors (as listed in the applicable DPA-Annex) as if such acts and omissions were those of Protocol itself, subject to the General Cap and Super-Cap. Protocol shall use commercially reasonable efforts to obtain flow-down rights from its subprocessors and shall, on Customer's request and at Customer's cost, pursue recovery against subprocessors for damages exceeding Protocol's cap, sharing any recovery on a pro rata basis. Subprocessor failures arising from third-party model deprecation, breaking changes, or service disruption are governed exclusively by Section 6d and do not constitute a breach by Protocol under this Section 7k."*

> ⚠️ **Open vraag aan ICTRecht (toegevoegd 2026-05-03)**: Protocol is een 2-persoons-vendor met beperkt eigen vermogen. Het cap-gap-risico tussen Protocol's contractuele cap (12 mnd aggregate fees onder MSA, max 2× via super-cap) en wat Protocol kan verhalen op subprocessors (OpenAI cap't op ~€1-6k/jr API-fees, andere subprocessors vergelijkbaar) is structureel asymmetrisch. Insurance-polis dekt het meeste, maar bij meerdere incidenten in één jaar of polis-uitsluitingen kan Protocol uit eigen vermogen moeten bijstaan.
>
> **Vraag**: is het in NL/EU enterprise-IT-praktijk verdedigbaar om subprocessor-veroorzaakte schade onder 7k te cap'pen op een **lager niveau** dan de algemene caps — bijvoorbeeld 50% van de General Cap, of een vaste sub-cap van [bedrag] — als expliciete erkenning dat Protocol de subprocessor-keten niet contractueel kan beheersen? Concrete varianten om te overwegen:
>
> a) **Subprocessor sub-cap = lower of (i) General Cap, of (ii) waarde van de specifieke SoW** waarin de subprocessor werd ingezet (zorgt dat klein-volume-deals geen aggregate-cap-niveau-blootstelling creëren via subprocessor-routing)
>
> b) **Subprocessor sub-cap = 50% van General Cap** (vaste fractie, makkelijk uit te leggen)
>
> c) **Geen sub-cap** — accepteren dat 7k onder de algemene cap-architectuur valt (huidige formulering, marktstandaard)
>
> Zou ICTRecht de juridische haalbaarheid en marktconformiteit van varianten (a) en (b) willen beoordelen? Onze voorkeur is variant (a) als verdedigbaar, anders houden we (c). De achtergrond: Wytze heeft persoonlijke risk-aversie tegen scenario waarin één subprocessor-incident — over een dienst die Protocol contractueel niet kan beheersen — Protocol BV's eigen vermogen volledig opmaakt voorbij polis-dekking. Dit is geen technische show-stopper, wel een kwaliteitsvraag voor jullie professionele beoordeling.

---

#### 7l. Force majeure — third-party-AI-API-outage [TOEVOEGING]

**Positie**: aantoonbare unavailability van third-party-AI-providers (OpenAI, Azure, Anthropic, etc.), scraping-services (Apify), of communicatie-providers (Resend, Twilio, WhatsApp Business API) gedurende >X uur in een kalendermaand wordt behandeld als force majeure-gebeurtenis. Service-level-degradatie zonder boeteclausule. Geen aansprakelijkheid Protocol voor downtime-gevolgschade.

**Specifieke X-uur-grens** wordt per SoW vastgelegd in de SLA-sectie (typisch 4-8 uur per maand voor non-critical builds, strenger voor Brand Shield-achtige live-monitoring).

**Reden — waarom force majeure-clausule specifiek voor third-party-AI**:
Sectie 17 (Force Majeure) dekt traditioneel "acts of God, war, government action". Third-party-API-outage past niet automatisch onder die definitie — rechter kan oordelen dat OpenAI-outage "binnen Protocol's redelijke controle" was omdat Protocol OpenAI heeft gekozen. Specifieke clausule pre-empt deze discussie.

**EN concept-formulering**:
> *"For purposes of Section 17 (Force Majeure), the following events shall constitute Force Majeure events: (i) verifiable unavailability or service disruption of third-party AI providers, model providers, scraping services, communication providers, or hosting infrastructure suppliers identified in the relevant Statement of Work, where such unavailability exceeds the thresholds set forth in the applicable Statement of Work; (ii) breaking changes to third-party APIs that render Protocol's deliverables temporarily inoperable, where Protocol has implemented reasonable mitigation measures within commercially reasonable timeframes. During such Force Majeure events, Protocol's service-level obligations are suspended without liability for damages arising from the disruption, provided Protocol provides timely notice to Customer and uses commercially reasonable efforts to restore service or implement workarounds."*

---

#### 7m. PLD-readiness-evaluatieclausule [TOEVOEGING]

**Positie**: Partijen erkennen dat de Herziene Productaansprakelijkheidsrichtlijn (Richtlijn (EU) 2024/2853, hierna "PLD") in werking is sinds december 2024 met implementatiedeadline december 2026 voor lidstaten, en dat Nederland op het moment van ondertekening van deze MSA de PLD nog niet heeft omgezet. Bij omzetting in NL-recht wordt door Protocol geleverde AI-software expliciet een "product" onder de PLD. Partijen verplichten zich op het moment van NL-omzetting de MSA te evalueren en waar nodig aan te passen om PLD-conform te zijn.

**Reden — waarom PLD-readiness-clausule**:
PLD beschermt eindgebruikers/consumenten en personen die direct schade lijden door defecte producten. Tussen Protocol↔LN (B2B) blijft contractuele beperking mogelijk; jegens **eindgebruikers van LN** (medewerkers, deelnemers, etc.) niet. De clausule zorgt dat partijen niet plotseling met een gebroken contract zitten als NL de PLD omzet — proactieve evaluatie-verplichting voorkomt geschillen over compliance-verantwoordelijkheid.

**Belangrijk — wat NIET in deze clausule staat**:
We doen geen pre-emptieve aanpassing. PLD-implementatie hangt af van NL-omzetting (verwacht 2026) — eerder aanpassen creëert onnodige complexiteit en kan uitkomen op posities die niet matchen met finale NL-implementatiewet.

**EN concept-formulering**:
> *"The Parties acknowledge that Directive (EU) 2024/2853 on liability for defective products (the 'Revised Product Liability Directive' or 'PLD') entered into force on 8 December 2024, with a transposition deadline of 9 December 2026 for Member States. Upon the Netherlands transposing the PLD into national law, software supplied by Protocol under this Agreement may qualify as a 'product' within the meaning of the PLD. The Parties agree to review this Agreement within ninety (90) days following the effective date of Dutch national PLD-implementation legislation and to negotiate in good faith any amendments necessary to ensure compliance with the implementing law, including but not limited to provisions regarding liability towards third-party injured persons (which liability cannot be contractually excluded under the PLD)."*

---

#### 7n. AI-system risk-classification per SoW [TOEVOEGING — cross-link met 7h]

**Positie**: voor elke SoW wordt vastgelegd of het AI-systeem onder Annex III AI Act valt (high-risk). Bij Annex III: Protocol levert technische documentatie + instructies aan LN per Art 16 AI Act; LN draagt deployer-verplichtingen per Art 26. Bij niet-Annex III: lichtere documentatie-verplichtingen.

**Specifieke aandacht**: WhatsApp HR Agent (AFAS Live) zit dicht tegen Annex III punt 4 (workplace decisions). Positionering in SoW: tool **informeert HR-medewerkers**, neemt geen autonome beslissingen, human-in-the-loop verplicht. Met deze positionering blijft het buiten Annex III. Brand Shield (MOJO) is geen Annex III-systeem.

**Reden — waarom per-SoW-classificatie**:
AI Act Art 6 (high-risk-classificatie) moet pre-deployment worden vastgesteld. Verkeerde classificatie kan leiden tot: (a) niet-compliance bij Annex III-systeem dat als niet-high-risk werd geclassificeerd, (b) onnodige overhead bij niet-Annex III-systeem dat als high-risk werd behandeld. Per-SoW-vastlegging dwingt tot expliciete classificatie pre-deployment.

**EN concept-formulering** (al opgenomen onder 7h, hier samenvattend):
> *"Each Statement of Work shall specify the AI Act risk classification of the deployed AI system, indicating whether such system constitutes a high-risk AI system under Annex III of the AI Act, and shall allocate the resulting Provider obligations (Article 16) to Protocol and Deployer obligations (Article 26) to Customer accordingly."*

---

#### Samenvattend — Sectie 7 finale structuur

| Element | Positie |
|---|---|
| 7a General Cap | 12 mnd aggregate fees rolling window, geen vaste floor |
| 7b Super-Cap (2×) | Data breach (opzet/grove nalatigheid), IP-inbreuk, confidentiality |
| 7c Carve-outs unlimited | Opzet, bewuste roekeloosheid, fraude (NL-wettelijk verplicht) |
| 7c Carve-out via DPA | AVG-overtredingen Protocol als verwerker — separate cap-regeling |
| 7d Aggregate scope | Rolling 12-month window over alle SoW's |
| 7e Time-bar | 24 mnd na "redelijke kennis" + 36 mnd post-termination tail |
| 7f Indirect damages | Uitgesloten incl. lost profits, business interruption, reputational. Dataverlies expliciet gedefinieerd (3-tier) |
| 7g GDPR-fines | Buiten MSA. AVG-aansprakelijkheid via DPA. Art 82-schadevergoeding via cap-architectuur |
| 7h AI-output liability | MSA-baseline (rollen + disclaimer) + SoW-detail (test-set + accuracy + drift) |
| 7i Insurance | €2M agg / €1M per claim Hiscox/Chubb/Markel; LN-medefinanciering optie bij verhoging |
| 7j Mutuality | Wederzijdse cap-architectuur met scope-aanpassing per categorie |
| 7k Subprocessor | Protocol step-in voor subprocessor-fouten, flow-down-rights bedongen |
| 7l Force majeure third-party-AI | API-outage/breaking-change als FM, SLA-degradatie zonder boete |
| 7m PLD-readiness | Evaluatie-verplichting bij NL-omzetting (verwacht dec 2026) |
| 7n AI-system risk-class | Per SoW Annex III ja/nee + provider/deployer-verdeling |

---

#### Onderbouwing & onderhandelingsruimte

**Strategische keuzes die expliciete onderbouwing behoeven**:

1. **Geen vaste floor op General Cap** — bewuste keuze gegeven Protocol's mix van klein-volume-deals (€5k single-builds) en grotere MSA-werk (jaaromzet typisch €30-100k range). Insurance-polis is feitelijke backstop, niet contractuele floor. Concession-ruimte: minimum €X opnemen als LN het vraagt, maar niet pre-emptief.

2. **Super-cap 2× i.p.v. 3×** — verdedigbaar als pakket met (a) NL-recht-verplichte opzet/grove-schuld carve-out, (b) €2M insurance-polis als feitelijke buffer boven super-cap, (c) GDPR-fines buiten MSA. LN-juristen kunnen 3× pushen voor data breach — counter via insurance-onderbouwing.

3. **GDPR-fines buiten MSA, alleen via DPA** — bewust juridisch zuiver. Eerste voorstel had pass-through onder super-cap; research-pass wees dit af als (a) niet houdbaar onder NL-recht, (b) onverzekerbaar voor 2-persoons-vendor, (c) feitelijk symbolisch bij €20M-class-fines. Beter geen contractueel doorbelastingsmechanisme dan een dat ICTRecht terugstuurt.

4. **AI-output liability hybride: MSA-baseline + SoW-detail** — niet alles in MSA (ICTRecht zou dat te ongedifferentieerd vinden), niet alles in SoW (te zwak — disclaimer alleen is juridisch onvoldoende voor PLD/AI Act-context). Hybride sluit aan bij ICTRecht's AI-Act-blogpost-advies.

5. **Confidentiality van unlimited naar super-cap (2×)** — eerste voorstel was te ruim. NLdigital 2025 kent geen unlimited confidentiality-carve-out. Super-cap is voldoende substantieel om LN-IT-juristen comfort te bieden zonder onverzekerbare blootstelling te creëren.

6. **AILD-context expliciet vermelden** — ingetrokken 6 oktober 2025. Geen automatische bewijslast-omkering meer voor AI-claims. Dit is gunstig voor Protocol bij AI-incident — eiser draagt volledige bewijslast voor causaliteit + defectiviteit. Geen contractuele clausule nodig, wel handig in onderhandeling als LN ernaar verwijst.

7. **Mutuality ondanks NLdigital-eenzijdigheid** — bewuste afwijking van branchestandaard. NLdigital is leveranciersgericht; voor MSA-niveau-relatie tussen gelijkwaardige zakelijke partijen is asymmetrische cap commercieel onhoudbaar. Toch markeren als "concession boven NLdigital" in onderhandeling.

8. **Per-SoW AI-classificatie** — pre-emptieve compliance-keuze voor AI Act Art 6 (high-risk-classificatie). Voorkomt dat MSA-template gefixeerd raakt op één classificatie terwijl Protocol's portfolio (HR Agent vs Brand Shield vs Venue Vera) verschillende risico-niveaus heeft.

**Cross-references binnen MSA**:
- Sectie 5b (Background IP-definitie) ↔ 7b/7j Super-cap voor confidentiality
- Sectie 5d (IP-warranty change-control-carve-out) ↔ 7b Super-cap voor IP-inbreuk
- Sectie 6a (acceptance + accuracy-target) ↔ 7h SoW-detail accuracy-target
- Sectie 6d (third-party-AI-provider risk) ↔ 7h MSA-baseline + 7l Force majeure
- Sectie 8 (Indemnification — ✅ vastgelegd 2026-05-11) ↔ 7b Super-Cap voor IP/data breach, 7c carve-outs, 7g GDPR-routering, 7k subprocessor-cascade
- Sectie 10 (Insurance — ✅ vastgelegd 2026-05-11) ↔ 7i Insurance-eisen detailing (10b synchroon met 7i)
- Sectie 17 (Force majeure — to be drafted) ↔ 7l Third-party-AI-API-outage
- Master-DPA ↔ 7c, 7g (AVG-aansprakelijkheid via DPA-cap)

**Sources die ICTRecht moet kunnen verifiëren**:
- NLdigital Voorwaarden 2025 art 15-16: https://www.nldigital.nl/kennis-producten/nldigital-voorwaarden-2025/
- ICTRecht-blog "Belangrijkste valkuilen aansprakelijkheidsregeling": https://www.ictrecht.nl/blog/de-belangrijkste-valkuilen-in-de-aansprakelijkheidsregeling
- ICTRecht-blog "AI en contractuele aansprakelijkheid": https://www.ictrecht.nl/blog/ai-en-contractuele-aansprakelijkheid-in-de-praktijk-woorden-doen-er-toe
- ICTRecht-blog "Aansprakelijkheid in verwerkersovereenkomst": https://www.ictrecht.nl/blog/kun-je-in-een-verwerkersovereenkomst-afspraken-maken-over-je-aansprakelijkheid
- EU AI Act (Reg. 2024/1689), specifiek Art 6, 16, 26, Annex III
- PLD 2024/2853: https://eur-lex.europa.eu/eli/dir/2024/2853/oj/eng
- AILD-intrekking bevestiging: https://www.twobirds.com/en/insights/2025/proposed-eu-ai-liability-rules-withdrawn

---

### Sectie 8 — Indemnification

**Datum vastgelegd**: 2026-05-11

#### Methodologische context

Sectie 7 regelt **hoeveel** een partij maximaal aansprakelijk is (cap-architectuur). Sectie 8 regelt **wie wat doet** wanneer een derde partij een claim indient — de procedurele invulling van de scope die in 7b (Super-Cap voor IP-inbreuk en data breach) en 5d (IP-warranty) al qua omvang is afgesproken.

Sluit aan op NLdigital Voorwaarden 2025 art 17 (vrijwaring) als procedurele branchestandaard, met expliciete aanvullingen voor (a) AI-builds (subprocessor-cascade), (b) symmetrische scope tussen Protocol en LN, en (c) DPA-routering voor data breach-procedure.

---

#### 8a. Scope per partij

| Richting | Wat dekt indemnitor | Onder welke cap |
|---|---|---|
| **Protocol → LN** (IP-inbreuk) | Third-party claims dat Foreground IP geleverd door Protocol third-party rechten schendt | **Super-Cap (2× General Cap)** per 7b |
| **Protocol → LN** (data breach) | Third-party claims voortvloeiend uit Protocol's processing als verwerker — civiele schadevergoeding aan betrokkenen onder Art 82 AVG | **General Cap** of **Super-Cap (2×)** bij opzet/grove nalatigheid per 7b |
| **Protocol → LN** (subprocessor-fout) | Third-party claims voortvloeiend uit subprocessor-fout (OpenAI, Apify, Resend, etc.) | Per 7k step-in onder algemene caps — zie 8g |
| **Protocol → LN** (overige third-party claims) | Claims voortvloeiend uit Protocol's eigen handelen onder een SoW die niet vallen onder bovenstaande categorieën | **General Cap** per 7a |
| **LN → Protocol** (klant-data/content) | Third-party claims op door LN aangeleverde data, content of branding (auteursrecht, merkenrecht, privacy van LN-aangeleverde persoonsgegevens) | **Super-Cap (2×) bij IP-claims**, anders **General Cap** |
| **LN → Protocol** (Background IP misuse) | Misuse van Protocol's Background IP (Sectie 5b) — onrechtmatig hergebruik methodology/prompt-architectures/blueprints | **Super-Cap (2×) confidentiality** per 7b |
| **LN → Protocol** (scope-overschrijding) | Claims voortvloeiend uit LN's gebruik van Protocol's deliverables **buiten de scope van de SoW** of in combinatie met door Protocol niet-goedgekeurde third-party software | **General Cap** per 7a |

**Beide kanten — niet gedekt** (carve-outs uit indemnification):
- Door indemnitee zelf doorgevoerde wijzigingen op opgeleverde code/configuratie (sluit aan op 5d carve-out)
- Gebruik in strijd met de SoW of de overeengekomen acceptance-criteria
- Claims voortvloeiend uit opzet/bewuste roekeloosheid van indemnitee zelf
- AVG-boetes onder Art 83 AVG (vallen buiten MSA per 7g — elke partij draagt eigen boete)

**Reden — waarom expliciete tabel-vorm**:
Voorkomt interpretatie-discussies tussen MSA en SoW's. ICTRecht ontvangt direct duidelijke mapping welke claim-categorie onder welke cap valt. Sluit aan op de "mix-aanpak" uit 7b/7c — niet één algemene indemnification-cap maar koppeling naar de relevante cap-categorie.

**EN concept-formulering**:
> *"Subject to the cap architecture set forth in Section 7, each Party (the 'Indemnitor') shall defend, indemnify, and hold harmless the other Party (the 'Indemnitee'), its officers, directors, employees, and Authorized Affiliates against any third-party claim, suit, or proceeding (a 'Claim') arising out of: (i) in the case of Protocol as Indemnitor: (a) any allegation that Foreground IP delivered by Protocol infringes any third party's intellectual property rights, subject to the Super-Cap; (b) any claim brought by a data subject against Customer pursuant to Article 82 GDPR arising from Protocol's processing failures as Processor, subject to the General Cap or, in case of Protocol's wilful misconduct or gross negligence, the Super-Cap; (c) any claim arising from acts or omissions of Protocol's authorized subprocessors, as if such acts were Protocol's own, in accordance with Section 7k; (ii) in the case of Customer as Indemnitor: (a) any allegation that Customer-supplied data, content, or branding infringes any third party's rights, subject to the Super-Cap for IP-infringement claims and otherwise the General Cap; (b) any unauthorized use, disclosure, or reproduction of Protocol's Background IP, subject to the Super-Cap for confidentiality breaches; (c) any claim arising from Customer's use of Protocol's deliverables outside the scope of the applicable Statement of Work or in combination with third-party software not approved by Protocol, subject to the General Cap. Neither Party shall be required to indemnify the other for Claims arising from (x) modifications to deliverables made by the Indemnitee, (y) use in breach of the Statement of Work, (z) the Indemnitee's own wilful misconduct or gross negligence, or (zz) administrative fines under Article 83 GDPR."*

---

#### 8b. Notification — termijn + vorm

| Element | Positie |
|---|---|
| Termijn | **10 werkdagen** vanaf "datum van redelijke kennis" van de Claim |
| Vorm | Schriftelijk (email is voldoende), met kopie van de schriftelijke third-party-claim of dagvaarding |
| Sanctie op late melding | Indemnitor's verdediging mag niet zijn verzwakt door late melding. Verlies van indemnification **alleen voor het deel** van de schade dat aantoonbaar is verhoogd door de late melding — niet de gehele claim |

**Reden — waarom 10 werkdagen + "alleen verhoogd-deel"-sanctie**:
NLdigital 2025 art 17.2 hanteert "onverwijld". Wij maken expliciet 10 werkdagen omdat dat (a) duidelijker is, (b) aansluit op acceptance-window in 6a, (c) ICTRecht's Engelfriet-positie volgt ("redelijke termijn — typisch 5-10 werkdagen"). "Alleen-verhoogd-deel"-sanctie is NL-rechtelijke standaard (BW 6:89 redelijkheid + 6:101 eigen schuld) en voorkomt dat een procedurele slordigheid een hele claim vernietigt.

**EN concept-formulering**:
> *"The Indemnitee shall notify the Indemnitor in writing of any Claim within ten (10) business days from the date on which the Indemnitee first knew or reasonably should have known of the Claim, providing a copy of any written demand, complaint, or other instrument received from the third party. Failure to provide timely notice shall not relieve the Indemnitor of its obligations under this Section 8 except to the extent that the Indemnitor's ability to defend the Claim has been materially prejudiced by such delay, and only to the extent of such prejudice."*

---

#### 8c. Control of defense

| Element | Positie |
|---|---|
| Wie voert verdediging | **Indemnitor** (degene die betaalt) — heeft control |
| Indemnitee's recht | Eigen counsel inschakelen **op eigen kosten** naast indemnitor's counsel toegestaan |
| Override-trigger | Indemnitee mag control overnemen indien indemnitor (i) na schriftelijke waarschuwing + **15 werkdagen** geen actieve verdediging voert, of (ii) counsel inzet met materieel conflict-of-interest |
| Counsel-keuze | Indemnitor kiest counsel; indemnitee mag schriftelijk bezwaar maken bij materieel conflict-of-interest |
| Defense costs | **Binnen de cap** (Sectie 7) — defense + damages samen geplafonneerd. Insurance-polis (€2M aggregate / €1M per claim per 7i) dekt feitelijk beide |

**Reden — waarom defense costs binnen cap**:
NLdigital 2025-conform. Voorbeeld: General Cap €50k, third-party IP-claim €100k, defense costs €80k. Onder "binnen cap": indemnitee krijgt totaal €50k uit Protocol's vermogen, plus insurance-polis dekt tot €1M per claim. Onder "buiten cap": indemnitee krijgt €80k defense + €50k damages = €130k uit Protocol's vermogen — voor 2-persoons-vendor onverzekerbaar. Concession-ruimte: indien LN-Legal hier specifiek op pusht, defense costs buiten cap is bespreekbaar tegen iets striktere cap-niveaus elders.

**Reden — waarom indemnitor's control**:
Standaardpattern in NL-IT-contracten. Indemnitor draagt economisch risico, dus krijgt strategische control. Indemnitee's eigen-counsel-recht op eigen kosten is essentieel voor LN-Legal comfort — Jennifer Quik kan op afstand monitoren zonder Protocol's keuzes te dwingen.

**EN concept-formulering**:
> *"The Indemnitor shall have the right and obligation to assume sole control of the defense and settlement of the Claim, using counsel of its choice (subject to the Indemnitee's reasonable approval, which shall not be unreasonably withheld). The Indemnitee may participate in the defense at its own cost with counsel of its own choosing. The Indemnitee may assume control of the defense if (i) the Indemnitor, after receiving written notice of the Claim and a fifteen (15) business day cure period, fails to actively defend the Claim, or (ii) the Indemnitor's counsel has a material conflict of interest. All defense costs, including attorneys' fees, expert fees, and litigation expenses, shall be borne by the Indemnitor and shall count towards the applicable cap under Section 7."*

---

#### 8d. Settlement rights

| Wie | Mag schikken zonder akkoord andere partij | Voorwaarden |
|---|---|---|
| **Indemnitor** | Ja, mits | (i) **volledige financiële kwijting** van indemnitee; (ii) **geen erkenning van fout** door indemnitee; (iii) **geen toekomstige verplichting** voor indemnitee |
| **Indemnitee** | Nee | Schikking zonder schriftelijk akkoord indemnitor = **verlies van recht op indemnification** |
| **Reputationele schikkingen** | Beide partijen: altijd schriftelijk akkoord andere partij vereist | Geldt voor schikkingen met (a) publieke erkenning, (b) press release, (c) impact op merk-imago LN of Protocol |

**Reden — waarom de drie indemnitor-voorwaarden**:
NLdigital 2025 art 17.4-conform. Beschermt indemnitee tegen schikking die juridisch indemnitee belast. Voorbeeld: Protocol schikt IP-claim met clausule "LN erkent fout" — dat is voor LN-Legal onaanvaardbaar omdat het in andere procedures tegen LN kan worden gebruikt. Drie-voorwaarden-test is markt-standaard.

**Reden — waarom reputationele clausule expliciet toegevoegd**:
MOJO/AFAS Live/Ziggo Dome merk-imago is een aparte factor. Een AI-incident dat publiek wordt kan voor LN reputationeel gevoeliger zijn dan financieel — en kan voor Protocol via media-aandacht ook impact hebben. Symmetrische bescherming.

**EN concept-formulering**:
> *"The Indemnitor may settle a Claim without the Indemnitee's prior written consent only if the settlement (i) provides for full and unconditional release of the Indemnitee from all liability, (ii) does not require the Indemnitee to admit fault or wrongdoing, and (iii) imposes no future obligation on the Indemnitee (whether financial, operational, or otherwise). The Indemnitee may not settle a Claim without the Indemnitor's prior written consent; any such unauthorized settlement shall void the Indemnitor's indemnification obligations with respect to such Claim. Notwithstanding the foregoing, any settlement involving (a) a public statement, (b) press release, or (c) any acknowledgment that could reasonably be expected to impact the brand or reputation of either Party requires the prior written consent of both Parties."*

---

#### 8e. Mitigation duty bij IP-claims

**Indemnitor's keuze** (Protocol bij IP-inbreuk van Foreground IP):

| Optie | Wanneer |
|---|---|
| (i) **Workaround** leveren die de claim wegneemt zonder bruikbaarheid van deliverable wezenlijk aan te tasten | Default keuze, indien technisch redelijk haalbaar |
| (ii) **License kopen** van eiser tegen indemnitor's kosten | Indien (i) niet werkbaar of disproportioneel duur |
| (iii) **Feature verwijderen** + pro-rata refund van SoW-fees voor het verwijderde onderdeel | Last resort wanneer (i) en (ii) niet haalbaar zijn |

**Indemnitee's plicht**: redelijke mitigation-oplossing aanvaarden, **tenzij** dat de bruikbaarheid van de deliverable wezenlijk aantast voor het beoogde gebruik onder de SoW. Geschil over "wezenlijke aantasting" loopt via Sectie 19 (dispute resolution).

**Reden — waarom indemnitor's choice**:
Indemnitor draagt economisch risico → kiest cost-effective mitigation. Indemnitee houdt veto-recht alleen waar dat business-impact heeft, niet als algemene comfort-clausule. LN-Legal accepteert dit pattern standaard.

**EN concept-formulering**:
> *"In the event of a Claim alleging that Foreground IP delivered by Protocol infringes a third party's intellectual property rights, Protocol may, at its sole option and expense: (i) procure for Customer the right to continue using the affected deliverable; (ii) modify the affected deliverable to be non-infringing while preserving substantially equivalent functionality; or (iii) remove the affected deliverable and refund Customer a pro rata portion of the fees paid for such deliverable. Customer shall accept any commercially reasonable mitigation provided by Protocol under (i) or (ii), unless such mitigation would materially impair the functionality of the deliverable for the purpose set forth in the applicable Statement of Work."*

---

#### 8f. Cooperation duty

| Element | Positie |
|---|---|
| Wat | Redelijke beschikbaarheid van documenten, getuigen, witness statements, en relevante medewerkers voor verdediging |
| Op wiens kosten | **Indemnitor's kosten**, inclusief redelijke out-of-pocket-vergoeding aan indemnitee voor tijd en reis-kosten |
| Duur | Tijdens MSA-looptijd **+ 36 maanden post-termination** (matched aan time-bar tail in 7e) |
| Vertrouwelijkheid | Documenten en informatie uitgewisseld in indemnification-procedure vallen onder Sectie 14 confidentiality |

**Reden — waarom 36 maanden post-termination**:
Time-bar voor claims is 36 maanden post-MSA (7e). Cooperation duty moet daar synchroon mee lopen — anders verliest indemnitor verdediging-capaciteit tegen vorderingen die nog binnen de time-bar vallen.

**EN concept-formulering**:
> *"Each Party shall provide reasonable cooperation to the other Party in the defense of any Claim subject to indemnification under this Section 8, including providing access to relevant documents, making employees available for interviews and depositions, and assisting with witness statements and expert testimony where applicable. The Indemnitor shall reimburse the Indemnitee for reasonable out-of-pocket costs (including time and travel) incurred in providing such cooperation. The cooperation obligation shall survive termination or expiration of this Agreement for thirty-six (36) months, matching the post-termination claim period in Section 7e. All documents and information exchanged in the course of indemnification proceedings shall be deemed Confidential Information under Section 14."*

---

#### 8g. Subprocessor-cascade — koppeling 7k step-in

**Scenario**: LN ontvangt third-party claim die voortvloeit uit een fout van een Protocol-subprocessor (bijv. OpenAI bug die hallucinatie veroorzaakt in HR Agent output, of Apify-datalek bij Brand Shield-monitoring).

| Stap | Wat | Wie |
|---|---|---|
| 1 | Protocol blijft **eerste-lijn-indemnitor** per 7k step-in — geen "doorverwijzing" naar OpenAI als excuus | Protocol |
| 2 | Protocol mag LN cooperation vragen om subprocessor mee te procederen waar contractueel haalbaar | Beide |
| 3 | Recovery van subprocessor wordt **pro-rata gedeeld** naar aandeel in geleden schade (typisch: indemnification-bedrag Protocol uitkeerde + LN's eigen niet-vergoede schade) | Beide |
| 4 | Protocol bedingt **flow-down-rights** op subprocessors waar contractueel haalbaar — best-effort, niet absolute verplichting (OpenAI/Apify staan dit beperkt toe) | Protocol |

**Reden — waarom Protocol eerste-lijn blijft**:
Sluit aan op 7k step-in. LN heeft één aanspreekpunt (Protocol), geen verplichting om zelf met OpenAI's legal team te onderhandelen. Cap-gap-risico (Protocol kan beperkt verhalen op subprocessor) is reeds geadresseerd in 7k via insurance-polis — open ICTRecht-vraag over sub-cap is daar geparkeerd, niet hier herhaald.

**Reden — waarom pro-rata recovery**:
Eerlijk mechanisme bij gedeeld risico. Voorkomt dat een van beide partijen kan free-riden op het ander's recovery-effort. Bedingt expliciet dat als Protocol €100k uitkeert aan LN en €60k terughaalt van OpenAI, beide partijen pro-rata-aandeel krijgen i.p.v. dat Protocol €60k volledig zelf houdt.

**EN concept-formulering**:
> *"Where a Claim subject to indemnification by Protocol arises out of an act or omission of one of Protocol's authorized subprocessors (as listed in the applicable DPA-Annex), Protocol shall remain the first-line indemnitor in accordance with Section 7k (Subprocessor Step-In Liability) and shall not be entitled to redirect Customer to the subprocessor. Protocol may request Customer's reasonable cooperation to join the subprocessor in the relevant proceedings where contractually feasible. Any recovery obtained from a subprocessor shall be shared pro rata between Protocol and Customer in proportion to the indemnification amount paid by Protocol and any additional unindemnified damages suffered by Customer. Protocol shall use commercially reasonable efforts to obtain flow-down rights from its subprocessors enabling such pass-through claims, acknowledging that such rights may be limited by subprocessors' standard contractual terms."*

---

#### 8h. DPA-cross-link — data breach indemnity

**Routering** voor verschillende soorten data-incident-claims:

| Type | Onder welke regeling | Toelichting |
|---|---|---|
| Data breach-procedure (notificatie binnen 72 uur, mitigation-stappen, regulatoire melding aan AP) | **DPA Annex X** (data breach procedure) | Procedurele invulling van AVG Art 33-34 |
| Art 82 AVG-schadevergoeding aan betrokkenen — civiele schade die LN heeft uitgekeerd | **MSA cap-architectuur** (General Cap of Super-Cap per 7b/7g) | Civiele schade, contractueel doorbelastbaar |
| Art 83 AVG-boetes (administratieve sancties van AP) | **Buiten MSA** (per 7g) | Elke partij draagt eigen boete |
| Defense costs in toezichthouder-onderzoek (AP-onderzoek tegen LN of tegen Protocol) | **Eigen kosten elke partij** | Geen mutual indemnity — sluit aan op AP-praktijk pro-rata-allocatie |
| Class-action namens betrokkenen (verzamelclaim Art 80 AVG) | **MSA cap-architectuur** mits voortvloeiend uit Protocol's processing failure | Idem Art 82 individuele claims |

**Reden — waarom zuivere routering**:
Voorkomt dubbel-claimen tussen MSA en DPA. Sluit aan op 7g (GDPR-fines buiten MSA) en op de master-DPA + Annex X-structuur uit Sectie 2. ICTRecht kan deze tabel direct overnemen in de DPA cross-reference-clausule.

**Reden — waarom defense costs in toezichthouder-onderzoek eigen kosten**:
Beide partijen kunnen onafhankelijk door AP onderzocht worden. Mutual indemnity hier creëert moral hazard (ene partij voert luxe-verdediging op kosten andere partij). Eigen kosten met cooperation-duty (8f) is cleaner.

**EN concept-formulering**:
> *"The Parties acknowledge and agree the following routing of data-related claims: (i) Personal data breach notification, mitigation, and regulatory reporting procedures are governed exclusively by the Data Processing Agreement and its Annexes; (ii) Civil compensation paid by Customer to data subjects pursuant to Article 82 GDPR, to the extent arising from Protocol's processing failures as Processor, shall be recoverable under this Section 8 subject to the cap architecture in Section 7 (General Cap or, in the case of wilful misconduct or gross negligence, the Super-Cap); (iii) Administrative fines imposed under Article 83 GDPR are excluded from indemnification under this Agreement and shall be borne by the Party on which they are imposed (consistent with Section 7g); (iv) Defense costs incurred by either Party in regulatory investigations by supervisory authorities shall be borne by the investigated Party; (v) Class actions or representative actions under Article 80 GDPR brought by data subjects against Customer shall be treated as compensation claims under (ii) above, subject to the same cap architecture."*

---

#### Samenvattend — Sectie 8 finale structuur

| Element | Positie |
|---|---|
| 8a Scope per partij | Mutual, met expliciete mapping naar 7b Super-Cap vs 7a General Cap per categorie |
| 8b Notification | 10 werkdagen vanaf "redelijke kennis", schriftelijk, sanctie alleen op verhoogd-deel |
| 8c Control of defense | Indemnitor controleert, defense costs binnen cap, indemnitee mag eigen counsel op eigen kosten, override na 15 werkdagen no-action |
| 8d Settlement | Indemnitor mag schikken bij volledige kwijting + geen schulderkenning + geen toekomstige verplichting indemnitee; reputationele schikkingen beide partijen vereisen consent |
| 8e Mitigation IP-claims | Indemnitor's keuze tussen workaround / license / remove + pro-rata refund |
| 8f Cooperation | Op indemnitor's kosten, tijdens MSA + 36 mnd post-termination |
| 8g Subprocessor-cascade | Protocol eerste-lijn (per 7k), pro-rata recovery van subprocessor, flow-down-rights best-effort |
| 8h DPA-cross-link | Data breach-procedure via DPA, Art 82-schade via MSA-cap, Art 83-boetes buiten MSA |

---

#### Onderbouwing & onderhandelingsruimte

**Strategische keuzes die expliciete onderbouwing behoeven**:

1. **Defense costs binnen cap** — NLdigital 2025-conform, sluit aan op insurance-polis structuur (defense + damages binnen €1M per claim). Concession-ruimte: defense costs buiten cap is bespreekbaar als LN-Legal hierop staat, tegen iets striktere cap-niveaus elders. Niet pre-emptief loslaten.

2. **Mitigation = indemnitor's keuze** — workaround / license / remove. Indemnitee's veto alleen bij "wezenlijke aantasting bruikbaarheid". Standaardpattern, geen onderhandelingsruimte verwacht.

3. **Cap-mapping in 8a expliciet** — voor elke claim-categorie staat in 8a-tabel onder welke cap (7a General of 7b Super) deze valt. Geen separate cap voor indemnification. Voorkomt interpretatie-discussies tussen MSA en SoW's.

4. **Symmetrische scope LN→Protocol** — niet alle MSA's hebben dit. Voor Protocol relevant omdat LN aangeleverde klant-data/branding (AFAS HR-policies, MOJO tone-of-voice, etc.) third-party rechten kan schenden buiten Protocol's controle. Sluit aan op 5d wederzijdse warranty.

5. **Subprocessor-cascade pro-rata recovery** — voorkomt dat Protocol €100k uitkeert + €60k terughaalt van OpenAI en alle €60k zelf houdt. Eerlijk mechanisme bij gedeeld risico. LN-Legal kan vragen "waarom niet alle recovery naar LN?" — counter via "Protocol heeft economisch risico geabsorbeerd op moment van uitkering, deelt recovery in zelfde verhouding".

6. **Reputationele settlement-veto beide partijen** — niet standaard in NLdigital 2025. Toegevoegd omdat MOJO/AFAS Live/Ziggo Dome merk-imago een aparte factor is. ICTRecht kan beoordelen of dit te ver gaat richting LN-asymmetrische bescherming.

7. **DPA-routering expliciet** — voorkomt dubbel-claimen. Sluit aan op de master-DPA + Annex X-structuur uit Sectie 2 (order of precedence: DPA wint bij conflict over data-onderwerpen).

**Cross-references binnen MSA**:
- Sectie 5b (Background IP-definitie) ↔ 8a LN→Protocol indemnity voor Background IP misuse
- Sectie 5d (IP-warranty + carve-outs) ↔ 8a Protocol→LN IP-indemnity scope, 8e mitigation
- Sectie 6a (acceptance) ↔ 8b notification (10 werkdagen-window matched)
- Sectie 7a/7b (cap-architectuur) ↔ 8a cap-mapping per claim-categorie
- Sectie 7e (time-bar) ↔ 8f cooperation duty 36 mnd post-termination
- Sectie 7g (GDPR-fines/AVG buiten MSA) ↔ 8h DPA-routering
- Sectie 7k (subprocessor step-in) ↔ 8g subprocessor-cascade
- Sectie 14 (Confidentiality — to be drafted) ↔ 8f cooperation-documenten vertrouwelijk
- Sectie 19 (Dispute resolution — to be drafted) ↔ 8e mitigation-geschil "wezenlijke aantasting"
- Master-DPA ↔ 8h data breach-procedure routering

**Sources die ICTRecht moet kunnen verifiëren**:
- NLdigital Voorwaarden 2025 art 17 (vrijwaring): https://www.nldigital.nl/kennis-producten/nldigital-voorwaarden-2025/
- ICTRecht-blog "Indemnification in IT-contracten" — algemene positie volgt NLdigital
- BW 6:89 (klachtplicht), 6:101 (eigen schuld) — NL-rechtelijke grondslag voor "alleen verhoogd-deel"-sanctie
- AVG Art 82 (civielrechtelijke aansprakelijkheid jegens betrokkenen) vs Art 83 (administratieve sancties)
- AVG Art 80 (representatieve actie/class action)

### Sectie 9 — Warranties services

**Datum vastgelegd**: 2026-05-11

#### Methodologische context

Sectie 9 regelt **wat Protocol garandeert** over de levering. Sluit aan op 5d (IP-warranty — al vastgelegd), 6a/6b (acceptance + defect-management), 7h (AI-output liability) en 8 (indemnification-koppeling voor warranty-claims). Methodologisch: NLdigital Voorwaarden 2025 art 13 (garantie) als procedurele branchestandaard, met AI-specifieke uitsluitingen.

Belangrijk onderscheid:
- Sectie 5d = **IP-warranty** (Foreground IP schendt geen third-party rechten)
- Sectie 9 = **service + deliverables warranty** (uitvoering en werking conform afspraak)

---

#### 9a. Service warranty — uitvoering door Protocol

| Element | Positie |
|---|---|
| Standaard | "Reasonable skill and care, consistent with professional standards for AI consultancy and software development in the EU" |
| Personeel | Behoorlijk geschoolde en bekwame medewerkers, met relevante ervaring voor het type build (AI-engineering, prompt-architecture, n8n-orchestration, etc.) |
| Karakter | **Inspanningsverplichting** (BW 7:401), geen resultaatsverplichting |
| Cross-link | 6a acceptance-criteria definiëren *wat* "behoorlijk" betekent per SoW |

**Reden — waarom "reasonable skill and care" i.p.v. "best efforts" of "highest standards"**:
NL-marktstandaard. BW 7:401 verplicht opdrachtnemer tot "zorg van een goed opdrachtnemer" — dat is wettelijk een inspanningsverplichting die niet kan worden uitgesloten. "Best efforts" is Anglo-Amerikaans en zwakker dan "reasonable skill and care" onder NL-recht. "Highest professional standards" neigt naar resultaatsverplichting wat voor 2-persoons-vendor onverdedigbaar is.

NLdigital 2025 art 13.1 hanteert exact deze formulering. Concession-ruimte: "industry-leading" alleen toevoegen als LN-Legal hierop staat (te interpreteren als marketing-taal, niet juridisch resultaatsverplichting).

**EN concept-formulering**:
> *"Protocol warrants that the Services shall be performed with reasonable skill and care, consistent with generally accepted professional standards for AI consultancy and software development in the European Union, and using personnel with appropriate qualifications and experience for the type of build specified in the applicable Statement of Work. This warranty constitutes an obligation of best efforts (inspanningsverplichting) under Article 7:401 of the Dutch Civil Code and shall not be construed as an obligation to achieve a specific result, except where a specific result is expressly set forth in the acceptance criteria of a Statement of Work."*

---

#### 9b. Deliverables warranty — werking van het opgeleverde

| Element | Positie |
|---|---|
| Scope | Deliverables functioneren **conform de in de SoW vastgelegde acceptance-criteria** gedurende het warranty-window |
| Geen bredere warranty | Geen warranty op functionaliteit buiten acceptance-criteria — voorkomt scope-creep via "het werkt toch niet zoals ik dacht"-claims |
| Cross-link | 6a (acceptance-criteria), 6b (defect-management), 9d (duur), 9e (remedies) |

**Reden — waarom alleen acceptance-criteria-scope**:
Warranty volgt acceptance. Als acceptance is doorlopen op specifieke criteria, geldt de warranty op precies dezelfde criteria. Dit voorkomt dat klant na acceptance alsnog brede "moest beter werken"-claims indient. LN kan duwen richting "conform documentation + acceptance-criteria" — counter via "documentation IS de SoW + acceptance-criteria, geen aparte juridische standaard".

**EN concept-formulering**:
> *"Protocol warrants that, during the warranty period set forth in Section 9d, the deliverables furnished under each Statement of Work shall conform in all material respects to the acceptance criteria specified in such Statement of Work. This warranty is limited to the acceptance criteria expressly set forth in the Statement of Work and does not extend to (i) functionality not specified in the acceptance criteria, (ii) implied or assumed functionality, or (iii) functionality alleged to arise from documentation other than the Statement of Work itself."*

---

#### 9c. AI-specifieke warranty-uitsluitingen

Expliciet **uitgesloten** van warranty (cross-link 7h en 6d):

| Categorie | Reden |
|---|---|
| Output-accuracy in alle gevallen | Outputs zijn probabilistisch; volledige feitelijke juistheid niet garandeerbaar. Accuracy-target per SoW (6a) is de meetlat |
| Drift over tijd binnen accuracy-target | Modellen evolueren; als accuracy binnen target blijft is dat geen warranty-breach |
| Hallucinaties van generatieve modellen | Inherent aan AI-architectuur — wel: redelijke mitigatie via prompt-engineering, retrieval-grounding, human-in-the-loop |
| Third-party model behavior (OpenAI/Anthropic/Apify) | Reeds onder 6d (provider risk) en 7l (force majeure) |
| Veranderend gebruikersgedrag waardoor accuracy-target niet langer realistisch is | Geen Protocol-warranty; resolutie via 6c change-control of nieuwe SoW |

**Reden — waarom AI-warranty-uitsluitingen expliciet**:
ICTRecht's AI-Act-artikel adviseert deze uitsluiting expliciet contractueel vast te leggen. Zonder expliciete uitsluiting kan rechter een impliciete warranty op output-juistheid afleiden uit het feit dat Protocol een AI-systeem heeft geleverd. Pre-emptief uitsluiten voorkomt deze discussie.

PLD 2024/2853 maakt AI-software jegens injured persons (eindgebruikers) een "product" — die warranty kan niet contractueel uitgesloten worden (7m). Tussen Protocol↔LN (B2B) wel uitsluitbaar. De PLD-context is opgenomen in Sectie 7m evaluatie-clausule.

**EN concept-formulering**:
> *"Notwithstanding Section 9b, Protocol does not warrant: (i) the factual accuracy of AI-generated outputs in all instances, given the probabilistic nature of AI systems; the accuracy target set forth in the applicable Statement of Work (Section 6a) constitutes the contractual benchmark; (ii) the absence of model drift over time, provided that accuracy remains within the target set forth in the Statement of Work; (iii) the absence of hallucinations inherent to generative AI architectures, provided that Protocol has implemented commercially reasonable mitigation measures (including prompt engineering, retrieval grounding, and human-in-the-loop verification); (iv) the continued availability, performance, or behavior of third-party AI providers, model providers, scraping services, or other infrastructure suppliers, which are governed by Sections 6d and 7l; (v) continued suitability of accuracy targets in the event of materially changed end-user behavior, which shall be addressed via the change-control procedure in Section 6c or a new Statement of Work. The warranties set forth in this Section 9 are without prejudice to Protocol's liability for wilful misconduct or gross negligence under Section 7c."*

---

#### 9d. Duur van de warranty

| Element | Positie |
|---|---|
| Default duur | **30 dagen** vanaf final acceptance per milestone (identiek aan 6b) |
| Uitbreidbaar tot 60 dagen | Bij Clean Handover-SoW's (identiek aan 6b) |
| Uitbreidbaar via SoW | Langere warranty mogelijk tegen meerprijs of inclusief in onderhoudscontract |
| Geen rolling warranty | Reparatie binnen warranty-window verlengt warranty niet — voorkomt eindeloos verlengen |
| Trigger | Start vanaf **final acceptance** per milestone (deemed acceptance per 6a indien klant niet reageert binnen 10wd) |

**Reden — waarom synchroon met 6b**:
Eén procedure houdt MSA helder. Defect-management onder 6b en warranty-handhaving onder 9 lopen door dezelfde cure-procedure (zie 9e). Aparte warranty-duur zou de procedure splitsen wat onnodige juridische complexiteit creëert.

**EN concept-formulering**:
> *"The warranties set forth in Sections 9a and 9b shall apply for a period of thirty (30) days from the date of final acceptance (or deemed acceptance per Section 6a) of each milestone (the 'Warranty Period'), unless a longer Warranty Period is expressly agreed in the applicable Statement of Work, in which case the agreed period applies (typically up to sixty (60) days for Clean Handover deliveries). Repairs or cures performed by Protocol during the Warranty Period shall not extend the Warranty Period. Warranty obligations beyond the Warranty Period are available only through a separate paid support contract or a new Statement of Work."*

---

#### 9e. Remedies binnen warranty-window — sole remedy

| Stap | Remedy |
|---|---|
| 1. Klant meldt material defect | Schriftelijk, conform 6b (reproduceerbare beschrijving + verwijzing naar specifieke acceptance-criteria) |
| 2. Protocol's verplichting | **Cure** binnen 15 werkdagen (material) of 20 werkdagen (non-material) — identiek aan 6b |
| 3. Re-test cyclus | Maximaal 2 cycli voor hetzelfde defect — identiek aan 6b |
| 4. Indien cure niet lukt na max 2 cycli | **Pro-rata refund** van SoW-fees voor het defecte onderdeel |
| 5. Sole remedy-clausule | Cure-of-refund is **enige remedy** binnen warranty-window. Geen aanvullende damages naast cure/refund, behalve via 7c carve-outs (opzet/grove schuld/fraude) |
| 6. Buiten warranty-window | Paid support-contract of separate SoW |

**Reden — waarom sole remedy**:
Voorkomt double-dipping (warranty-cure + damages onder cap). Sole-remedy-clauses zijn onder NL-recht houdbaar voor MSA-relaties tussen gelijkwaardige zakelijke partijen mits opzet/grove schuld als carve-out blijft (al in 7c geregeld) en mits de remedy daadwerkelijk uitvoerbaar is (cure-procedure 6b is concreet).

LN kan vragen om "damages voor onbruikbaarheid systeem tijdens cure-window". Counter-positie: dat valt onder indirecte schade/bedrijfsstagnatie (uitgesloten per 7f), of bij wezenlijke onbruikbaarheid via opt-out termination per 3b (al in Sectie 3 geregeld).

**EN concept-formulering**:
> *"In the event of a material defect identified during the Warranty Period, Customer's sole and exclusive remedy shall be: (i) cure by Protocol within fifteen (15) business days for material defects or twenty (20) business days for non-material defects, in accordance with the defect-management procedure set forth in Section 6b; and (ii) if Protocol fails to cure the defect within the cure window after a maximum of two (2) re-test cycles, a pro rata refund of the fees paid for the defective deliverable. No other remedies, including damages for business interruption, loss of profits, or consequential damages, shall be available within the Warranty Period, save for liability arising under Section 7c (wilful misconduct, gross negligence, fraud). Warranty claims arising after the Warranty Period shall be addressed exclusively through a separate paid support contract or a new Statement of Work."*

---

#### 9f. Disclaimer of implied warranties

**Expliciete uitsluiting** van impliciete garanties voor zover NL-rechtelijk uit te sluiten:

| Impliciete garantie | Behandeling |
|---|---|
| Merchantability / verkoopbaarheid | Uitgesloten |
| Fitness for particular purpose (buiten SoW) | Uitgesloten — fitness wordt gedefinieerd via SoW-acceptance-criteria |
| Non-infringement beyond Sectie 5d | Uitgesloten — 5d is de IP-warranty |
| BW 7:401 inspanningsverplichting (goed opdrachtnemer) | **Wettelijk niet uitsluitbaar** — wel ingevuld via 9a "reasonable skill and care" |
| Conformiteit met acceptance-criteria (BW 7:17 conformiteit) | **Niet uit te sluiten voor consumenten; wel inkleurbaar in B2B-context via SoW-criteria** — dat is 9b zelf |

**Reden — waarom NL-rechtelijke beperking erkennen**:
Geen Anglo-Amerikaanse "AS IS"-clause die in NL nietig kan zijn. NL-recht kent inspanningsverplichting onder BW 7:401 die niet contractueel kan worden uitgesloten — wel concreet invulbaar via 9a-formulering. Door dit expliciet te erkennen voorkomen we dat de hele warranty-disclaimer in geheel nietig wordt verklaard wegens onredelijke bezwarendheid (BW 6:233).

**EN concept-formulering**:
> *"Except for the express warranties set forth in this Section 9 and in Section 5d (IP Warranty), Protocol disclaims all other warranties, whether express, implied, statutory, or otherwise, to the maximum extent permitted by Dutch law, including without limitation any implied warranties of merchantability, fitness for a particular purpose beyond the acceptance criteria set forth in the applicable Statement of Work, and non-infringement beyond Section 5d. The Parties acknowledge that the obligation of a good contractor (obligation of best efforts, inspanningsverplichting) under Article 7:401 of the Dutch Civil Code cannot be contractually excluded and is fulfilled through Protocol's compliance with Section 9a above."*

---

#### Open vragen aan ICTRecht

> ⚠️ **Open vraag 1 (sole remedy-houdbaarheid)**: Sectie 9e koppelt cure-of-refund als **enige** remedy binnen warranty-window, met damages alleen via 7c carve-outs (opzet/grove schuld). Voor MSA-relatie tussen gelijkwaardige zakelijke partijen verdedigbaar als marktstandaard. Zou ICTRecht specifieke NL-jurisprudentie willen toetsen die deze positie verzwakt — bijvoorbeeld redelijkheid-en-billijkheid-toets (BW 6:248) bij scenario "systeem onbruikbaar tijdens cure-window van 15 werkdagen", waar LN substantieel operationeel verlies lijdt zonder een formele schade-claim te kunnen indienen? Concession-ruimte: damages voor *aantoonbare directe* operationele schade tijdens cure-window opnemen als beperkte uitzondering, gecapped op een fractie van de SoW-fees voor het defecte onderdeel.

> ⚠️ **Open vraag 2 (AI-output-warranty-disclaimer)**: Sectie 9c sluit output-accuracy, drift en hallucinaties uit van warranty. Sectie 7m bevat de PLD-readiness-evaluatieclausule voor B2C-eindgebruikers. Vraag aan ICTRecht: is de uitsluiting in 9c voldoende juridisch sluitend voor B2B-relatie Protocol↔LN, zonder met PLD-bescherming jegens injured persons (LN-medewerkers, deelnemers, etc.) in conflict te komen? Specifiek: als een LN-medewerker schade lijdt door hallucinerende HR Agent output, kan LN dan terugvallen op 9c om verhaal op Protocol te beperken, of moet de PLD-bescherming hier doorwerken? Onze positie: PLD werkt jegens injured person, niet jegens LN; LN↔Protocol blijft contractueel gereguleerd. ICTRecht-bevestiging gewenst.

---

#### Samenvattend — Sectie 9 finale structuur

| Element | Positie |
|---|---|
| 9a Service warranty | Reasonable skill and care + geschoold personeel; inspanningsverplichting BW 7:401 |
| 9b Deliverables warranty | Conform SoW-acceptance-criteria, geen bredere scope |
| 9c AI-specifieke uitsluitingen | Output-accuracy, drift binnen target, hallucinaties, third-party model behavior, veranderend gebruikersgedrag |
| 9d Duur warranty | 30 dagen default / 60 dagen bij Clean Handover (synchroon met 6b) |
| 9e Sole remedy | Cure-of-refund per 6b; geen aanvullende damages binnen warranty-window, behalve 7c carve-outs |
| 9f Disclaimer implied warranties | Merchantability/fitness/non-infringement uitgesloten voor zover NL-rechtelijk mogelijk; BW 7:401 erkend |

---

#### Onderbouwing & onderhandelingsruimte

**Strategische keuzes die expliciete onderbouwing behoeven**:

1. **Service-standaard "reasonable skill and care" i.p.v. "best efforts"** — NL-marktstandaard, BW 7:401-conform. Concession-ruimte: "industry-leading" toevoegen als LN-Legal hierop staat (te lezen als marketing, niet juridisch sterker).

2. **Deliverables warranty beperkt tot SoW-acceptance-criteria** — voorkomt scope-creep. LN kan duwen richting "conform documentation + acceptance-criteria" — counter via "documentation IS de SoW + acceptance-criteria".

3. **Sole remedy cure/refund — geen aanvullende damages binnen warranty-window** — ICTRecht moet houdbaarheid bevestigen onder NL-recht voor MSA-relatie gelijkwaardige zakelijke partijen. Open vraag 1 hierboven.

4. **Duur synchroon met 6b (30/60 dagen)** — één procedure, één cure-flow. Voorkomt MSA-complexiteit.

5. **AI-warranty-uitsluitingen in 9c expliciet** — ICTRecht's AI-Act-blogpost adviseert pre-emptief uitsluiten. Open vraag 2 hierboven over PLD-interactie.

6. **Disclaimer implied warranties — NL-rechtelijke beperking expliciet erkend** — geen "AS IS"-clause die nietig kan zijn. BW 7:401 inspanningsverplichting niet uitsluitbaar — wel ingekleurd via 9a.

**Cross-references binnen MSA**:
- Sectie 5d (IP-warranty) ↔ 9f disclaimer non-infringement beyond 5d
- Sectie 6a (acceptance-criteria) ↔ 9b deliverables warranty + 9c accuracy-target
- Sectie 6b (defect-management + cure-procedure) ↔ 9d duur + 9e remedies
- Sectie 6c (change-control) ↔ 9c veranderend gebruikersgedrag
- Sectie 6d (third-party-AI-provider risk) ↔ 9c third-party model behavior
- Sectie 7c (opzet/grove schuld carve-outs) ↔ 9e sole remedy uitzondering
- Sectie 7f (indirect damages excluded) ↔ 9e "geen damages tijdens cure-window"
- Sectie 7h (AI-output liability) ↔ 9c AI-output-disclaimer
- Sectie 7l (force majeure third-party-AI) ↔ 9c third-party model behavior
- Sectie 7m (PLD-readiness) ↔ 9c AI-output-disclaimer + open vraag 2
- Sectie 8 (Indemnification) ↔ 9 warranty-claims-procedure (niet hetzelfde — indemnification is third-party claims, warranty is between MSA-partijen)

**Sources die ICTRecht moet kunnen verifiëren**:
- NLdigital Voorwaarden 2025 art 13 (garantie): https://www.nldigital.nl/kennis-producten/nldigital-voorwaarden-2025/
- BW 7:401 (zorg van een goed opdrachtnemer)
- BW 7:17 (conformiteit) — B2B-context
- BW 6:233 (onredelijk bezwarende bedingen)
- BW 6:248 (redelijkheid en billijkheid)
- ICTRecht-blog "AI en contractuele aansprakelijkheid" (al opgenomen bij Sectie 7)
- PLD 2024/2853 (al opgenomen bij Sectie 7m)

### Sectie 10 — Insurance baseline

**Datum vastgelegd**: 2026-05-11

#### Methodologische context

Sectie 10 is de **procedurele uitwerking** van wat in 7i al qua bedragen is afgesproken (€2M aggregate / €1M per claim Hiscox/Chubb/Markel). Methodologisch: NLdigital Voorwaarden 2025 art 14.3 als branchestandaard, met expliciete AI-specifieke uitsluiting-eisen die in 2024-2026 een nieuwe issue zijn geworden (sommige polissen beginnen AI-uitsluitingen op te nemen).

Sluit aan op 7i (insurance backing als feitelijke buffer boven super-cap), 7e (time-bar matched aan 36 mnd run-off), 7k (subprocessor-cascade — verzekering moet dit dekken), 7l (force majeure third-party-AI), 8c (defense costs binnen cap).

---

#### 10a. Polis-typen vereist

| Polis | Verplicht? | Reden |
|---|---|---|
| **E&O** (beroepsaansprakelijkheid) | **Ja** | Dekt professionele fouten in service-levering: foute prompt-architectuur, faulty AI-output configuratie, gebrekkige IP-due-diligence, etc. Kerndekking voor AI-consultancy |
| **Cyber liability** | **Ja** | Dekt data breach, ransomware, business interruption door cyber incident. Essentieel voor verwerker-rol onder DPA |
| **Algemene bedrijfsaansprakelijkheid (AVB)** | **Niet vereist** in MSA | AVB dekt bodily injury en property damage — voor 2-persoons-digital-vendor niet primaire dekking. Protocol heeft sowieso standaard zakelijk-pakket. Geen toegevoegde waarde voor AI-consultancy-relatie |

**Reden — waarom geen AVB-eis in MSA**:
NLdigital 2025 art 14.3 vereist alleen "beroepsaansprakelijkheidsverzekering". Cyber expliciet toevoegen omdat verwerker-rol onder DPA dit logisch maakt. AVB niet expliciet vereisen voorkomt onnodige overhead — Protocol heeft dit reeds via standaard zakelijke pakketten.

**EN concept-formulering**:
> *"Protocol shall maintain the following insurance coverage throughout the Term and for thirty-six (36) months following termination or expiration of this Agreement: (i) Professional Indemnity Insurance (E&O) covering errors and omissions in the provision of services under this Agreement and any Statement of Work; (ii) Cyber Liability Insurance covering data breaches, ransomware incidents, and business interruption arising from cyber events. Customer acknowledges that Protocol may, but is not required under this Agreement, maintain General Liability Insurance (AVB); Protocol's compliance with the E&O and Cyber Liability requirements satisfies its insurance obligations under this Agreement."*

---

#### 10b. Minimum-bedragen + grondslag

| Element | Positie | Grondslag |
|---|---|---|
| Per-claim limiet | **€1.000.000** | Boven ARBIT-rijksinkoop (€1.25M minimum aanbeveling); €1M dekt vrijwel elk denkbaar enkelvoudig incident bij realistische MSA-omvang |
| Aggregate limiet | **€2.000.000** | Comfortabel boven 2× super-cap-niveau bij realistische jaaromzet (€30-100k range → Super-Cap €60k-€200k blijft ruim binnen polis) |
| Eigen risico (per claim) | **Maximaal €25.000** per incident | Beperkt out-of-pocket Protocol bij claim; werkelijke Hiscox/Chubb/Markel-polissen voor 2-persoons-vendors zitten typisch op €5k-€10k |
| Defense costs | **Binnen limits inbegrepen** | Sluit aan op 8c defense costs binnen cap — geen aparte ringfencing |

**Reden — waarom eigen risico-cap €25k**:
Eigen risico is een polis-keuze van Protocol bij de verzekeraar. €25k is een veilige bovengrens die niet pre-emptief Protocol dwingt naar een hogere premie-polis. In de praktijk zit Hiscox/Chubb/Markel voor Protocol-omvang op €5-10k eigen risico — €25k-cap geeft commerciële flexibiliteit zonder LN-Legal-discomfort.

**EN concept-formulering**:
> *"The insurance coverage required under Section 10a shall meet the following minimum thresholds: (i) per-claim limit of one million euro (€1,000,000); (ii) aggregate annual limit of two million euro (€2,000,000); (iii) deductible (eigen risico) not exceeding twenty-five thousand euro (€25,000) per incident; (iv) defense costs and attorneys' fees shall be included within the policy limits, consistent with Section 8c of this Agreement."*

---

#### 10c. Verzekeraar-kwaliteitseisen

| Element | Positie |
|---|---|
| Rating | **A-rated** (S&P, Moody's, AM Best, of Fitch) of equivalent door NL/EU-erkende rating agency |
| Jurisdictie | NL of EU-gevestigde verzekeraar (geen offshore) |
| Genoemde verzekeraars (illustratief) | Hiscox, Chubb, Markel, AIG, Allianz, Zurich, Munich Re — non-exhaustive lijst |
| Verzekeraar-wisseling | Toegestaan, mits nieuwe verzekeraar voldoet aan dezelfde criteria en LN binnen 10 werkdagen schriftelijk wordt geïnformeerd |

**Reden — waarom illustratieve lijst i.p.v. limitatieve lijst**:
Voorkomt dat een specifieke verzekeraar contractueel locked-in raakt — als Hiscox bijvoorbeeld in 2027 marketwijzigt of A-rating verliest, kan Protocol switchen zonder MSA-amendment. A-rating + NL/EU-vestiging als basis-criteria, met illustratieve namen voor LN-Legal-comfort.

**EN concept-formulering**:
> *"The insurance coverage required under Section 10a shall be underwritten by an insurer (i) rated A or better by Standard & Poor's, Moody's, AM Best, or Fitch (or equivalent rating by a recognized rating agency in the Netherlands or the European Union), and (ii) authorized to operate in the Netherlands or elsewhere in the European Union. Acceptable insurers include, but are not limited to, Hiscox, Chubb, Markel, AIG, Allianz, Zurich, and Munich Re. Protocol may change insurers during the Term provided the new insurer meets the foregoing criteria; Protocol shall notify Customer in writing within ten (10) business days of any such change."*

---

#### 10d. Certificate of Insurance (COI)-procedure

| Element | Positie |
|---|---|
| Levering bij MSA-ondertekening | Eenmalig COI bij signing |
| Jaarlijkse renewal | Automatische COI binnen **30 dagen na polis-renewal-datum** |
| Op verzoek | Op redelijk verzoek LN, binnen **10 werkdagen** |
| Inhoud COI | Verzekeraar, polis-nummer, bedragen, looptijd, expliciete vermelding "coverage extends to services provided under [MSA-referentie]" |

**Reden — waarom jaarlijkse automatische renewal-COI**:
Enterprise-standard. Voorkomt dat LN-Legal moet chasen na elke polis-jaarperiode. Sluit aan op LN-vendor-management-praktijk (Jennifer Quik / Paul Meester monitoren vendor-insurance compliance).

**EN concept-formulering**:
> *"Protocol shall provide Customer with a Certificate of Insurance (COI) evidencing compliance with this Section 10: (i) upon execution of this Agreement; (ii) within thirty (30) days following each annual policy renewal; and (iii) within ten (10) business days following any reasonable written request by Customer. Each COI shall include the insurer's name, policy number, coverage amounts, policy period, and an explicit reference indicating that coverage extends to services provided under this Agreement."*

---

#### 10e. Run-off period — tail coverage

| Element | Positie |
|---|---|
| Run-off duur | **36 maanden** post-termination |
| Cross-link | Synchroon met time-bar 7e (24 mnd na "redelijke kennis" + 36 mnd post-termination tail) en 8f cooperation duty (36 mnd post-termination) |
| Dekking tijdens run-off | Claims voor acties tijdens MSA-looptijd, gemeld na MSA-einde |
| Kosten | Protocol's last (typisch inbegrepen in E&O-polis, of via Extended Reporting Period-rider) |

**Reden — waarom 36 maanden**:
Matched aan 7e zodat claim-dekking parallel loopt met claim-mogelijkheid. Geen gat tussen "LN kan nog claim indienen" (tot 36 mnd post-MSA per 7e) en "Protocol's polis dekt het" (alleen tijdens MSA-looptijd zonder tail-coverage).

**EN concept-formulering**:
> *"The insurance coverage required under this Section 10 shall be maintained throughout the Term of this Agreement and for an additional thirty-six (36) months following termination or expiration of the Agreement (the 'Run-Off Period'), matching the post-termination claim period set forth in Section 7e. Coverage during the Run-Off Period may be provided through Protocol's then-current insurance policy or through an Extended Reporting Period (ERP) rider, at Protocol's discretion, provided the coverage meets the requirements of Sections 10b and 10c."*

---

#### 10f. Wijzigingen aan polis — notificatieplicht

| Wijziging | Notificatie-vereiste |
|---|---|
| **Downgrade onder MSA-baseline** (lager bedrag, lichtere dekking, hoger eigen risico boven €25k) | **Schriftelijk akkoord LN vooraf** vereist |
| Verzekeraar-wisseling met behoud van baseline (10b/10c) | Schriftelijke notificatie binnen **10 werkdagen** |
| Renewal met identieke voorwaarden | Geen notificatie, alleen COI-renewal (10d) |
| **Materiële uitsluiting toegevoegd** die Protocol-services raakt (zie 10i) | **Schriftelijk akkoord LN vooraf** vereist |
| Routine polis-administratie (adreswijziging, contactpersoon, etc.) | Geen notificatie |

**Reden — alleen materiële wijzigingen vereisen actie**:
Voorkomt dat routine renewal-administratie LN-Legal overbelast. Materiële wijzigingen (downgrade of nieuwe uitsluiting) krijgen veto-recht — wat LN-Legal redelijk vindt en wat voor Protocol nauwelijks beperkend is omdat Protocol toch al motiverend kan zijn dergelijke wijzigingen niet door te voeren.

**EN concept-formulering**:
> *"Protocol shall obtain Customer's prior written consent before: (i) reducing any coverage amount below the minimum thresholds in Section 10b, (ii) increasing the deductible above twenty-five thousand euro (€25,000), or (iii) adding any material exclusion to the policy that would affect coverage of services provided under this Agreement (as further specified in Section 10i). Protocol shall notify Customer in writing within ten (10) business days of any change of insurer that meets the requirements of Sections 10b and 10c. Routine policy renewals on identical terms require no notification beyond the annual COI delivery under Section 10d."*

---

#### 10g. LN-medefinanciering bij uitbreiding boven baseline

Als LN tijdens MSA-looptijd verhoging van polis-bedragen of dekking vraagt boven de baseline (Sectie 10b):

| Element | Positie |
|---|---|
| Wie draagt premie-delta | **LN draagt 100% van incremental premium cost** (omdat het LN's verzoek is) |
| Cap op LN-bijdrage | Maximum **€10.000/jaar** op LN's premium-delta-bijdrage (voorkomt eindeloze escalatie) |
| Procedure | Protocol levert quote van verzekeraar; LN bevestigt schriftelijk; premie-delta wordt apart gefactureerd of bij volgende SoW-invoice toegevoegd |
| Bij MSA-einde | LN-financierde uitbreiding eindigt automatisch; Protocol keert terug naar baseline-niveau zonder verdere LN-bijdrage |

**Reden — 100/0 verdeling met cap**:
Eerlijk: LN wil verhoging, LN betaalt. Protocol blijft bij baseline anders. Cap van €10k/jaar beschermt LN tegen Protocol-keuzes die de delta onverwacht opdrijven (bijv. duurdere verzekeraar zonder eerst alternatieven te checken). Voor Protocol de logische positie — baseline-polis is voldoende voor Protocol's risk-management, hogere niveaus zijn LN's eis.

**EN concept-formulering**:
> *"If Customer requires Protocol to maintain insurance coverage above the baseline set forth in Section 10b (whether higher limits, additional coverage types, or specific endorsements), Customer shall bear one hundred percent (100%) of the incremental premium cost, subject to an annual cap of ten thousand euro (€10,000) on Customer's contribution. Protocol shall provide Customer with a written quote from its insurer; upon Customer's written confirmation, Protocol shall procure the requested coverage and invoice Customer for the incremental premium separately or as part of the next applicable Statement of Work invoice. Upon termination or expiration of this Agreement, any Customer-financed coverage extension shall lapse, and Protocol shall return to the baseline coverage levels without further obligation to Customer."*

---

#### 10h. Authorized Affiliate-coverage

| Element | Positie |
|---|---|
| Additional insured-status voor LN-affiliates | **Niet vereist** onder MSA-baseline |
| Hoe LN-affiliates wel gedekt zijn | E&O-polis dekt schade aan "contracting party and its named beneficiaries under the contract". Authorized Affiliates per Sectie 1c kwalificeren als named beneficiary onder MSA |
| Indien LN specifiek additional insured-status wenst | Onder LN-medefinanciering (10g) — premie-delta voor specifieke endorsement gedragen door LN |

**Reden — waarom geen additional insured-vereiste**:
Marktstandaard NL voor E&O-polissen is NIET additional insured maar contractual liability coverage. Werkt voor LN-affiliates omdat MSA-clausule (Sectie 1c Authorized Affiliates) hen als named beneficiary kwalificeert. Vermijdt hogere premies en complexere polis-administratie. Als LN-Legal additional insured-status echt wenst, kan dat via 10g LN-medefinanciering-pad.

**EN concept-formulering**:
> *"Protocol shall not be required to name Customer or Customer's Authorized Affiliates (as defined in Section 1c) as additional insureds on its insurance policies. Customer's Authorized Affiliates shall be covered under Protocol's policies as named beneficiaries through the contractual liability coverage extending to all parties for whose benefit this Agreement operates. If Customer requires additional insured-status for one or more Authorized Affiliates, Protocol shall obtain such endorsement subject to the cost-sharing procedure in Section 10g."*

---

#### 10i. Uitsluitingen — wat NIET acceptabel is

Protocol bevestigt dat de polis **GEEN** uitsluitingen bevat voor:

| Uitsluiting | Reden waarom non-acceptabel |
|---|---|
| AI of generative AI services | Zonder dit zou hele Protocol-werk effectief unverzekerd zijn onder MSA — fundamenteel non-acceptable |
| Third-party AI provider failures (OpenAI, Anthropic, Apify, etc.) | Sluit aan op 7l force majeure + 7k subprocessor-cascade; insurance moet dit dekken anders zit Protocol onverzekerd in subprocessor-keten |
| Automated decision-making outputs | Sluit aan op 7h AI-output liability |
| Cyber incidents inclusief social engineering / BEC / phishing | Cyber-polis moet phishing/BEC-incidents dekken (standaard issue 2024+ in enterprise cyber-polissen) |

**Acceptabele standaard-uitsluitingen** die geen MSA-impact hebben:
- War, terrorism, nuclear (industry-standard exclusions)
- Bodily injury (gedekt door AVB elders indien Protocol AVB heeft)
- Property damage > €X (gedekt door AVB elders indien Protocol AVB heeft)
- Pre-existing claims bekend bij polis-start
- Opzettelijke wetsovertreding (sluit aan op 7c carve-out — opzet is sowieso buiten cap)

**Reden — waarom expliciet uitsluitingen-lijst**:
In 2024-2026 zijn AI-uitsluitingen verschenen in sommige polissen (vooral USA-markt; enkele EU-verzekeraars beginnen ook). Voor NL-markt zijn Hiscox/Chubb/Markel-polissen typisch AI-inclusive. Expliciet contractueel vastleggen dat deze uitsluitingen NIET in Protocol's polis zitten, geeft LN-Legal sterk comfort en voorkomt dat een polis-wijziging stilzwijgend de MSA-bescherming uitholt.

**EN concept-formulering**:
> *"Protocol represents and warrants that the insurance policies maintained under this Section 10 do NOT contain exclusions for: (i) services involving artificial intelligence or generative AI; (ii) failures, errors, or outages of third-party AI providers, model providers, scraping services, or communication providers used by Protocol in performing services under this Agreement; (iii) automated decision-making outputs produced by AI systems delivered or operated by Protocol; (iv) cyber incidents arising from social engineering, business email compromise, or phishing attacks. Protocol acknowledges that the addition of any such exclusion to its policies during the Term constitutes a material policy change requiring Customer's prior written consent under Section 10f. Standard industry exclusions (including war, terrorism, nuclear events, bodily injury, property damage, pre-existing claims, and intentional misconduct) are acceptable and not subject to this representation."*

---

#### Open vraag aan ICTRecht

> ⚠️ **Open vraag (Authorized Affiliate-coverage construct)**: Sectie 10h kiest voor "named beneficiary"-route i.p.v. "additional insured"-status voor LN-Authorized Affiliates onder MSA. Onze positie: E&O-polis dekt schade aan contracting party + named beneficiaries, en Sectie 1c MSA-clausule kwalificeert LN-affiliates als named beneficiary. Geeft Protocol commercieel comfort (geen hogere premie, geen complexere polis). Vraag aan ICTRecht: is deze construct NL-rechtelijk sluitend voor LN-affiliates die zelf geen contracting party zijn? Specifiek: kan een LN-affiliate (bijv. MOJO BV, Ziggo Dome BV) een directe claim onder Protocol's polis instellen als named beneficiary, of moet de claim eerst via LN-NL als signatory lopen?
>
> Achtergrond: LN-Legal kan vragen om additional insured-status. Onze pre-emptieve positie is "niet nodig" — als ICTRecht bevestigt dat named beneficiary-route juridisch werkbaar is, houden we 10h zoals voorgesteld. Anders wordt 10h een 10g-pad (LN-medefinanciering voor specifieke additional insured-endorsement).

---

#### Samenvattend — Sectie 10 finale structuur

| Element | Positie |
|---|---|
| 10a Polis-typen | E&O + cyber verplicht; AVB niet expliciet vereist in MSA |
| 10b Minimum-bedragen | €1M per claim / €2M aggregate / eigen risico max €25k / defense costs binnen limits |
| 10c Verzekeraar-kwaliteit | A-rated NL/EU; illustratieve lijst (Hiscox/Chubb/Markel/AIG/Allianz/Zurich/Munich Re) |
| 10d COI-procedure | Bij signing + jaarlijks automatisch binnen 30 dagen na renewal + op verzoek binnen 10 wd |
| 10e Run-off period | 36 mnd post-termination (matched aan 7e time-bar tail) |
| 10f Polis-wijzigingen | Downgrade of materiële uitsluiting = schriftelijk akkoord LN vooraf; verzekeraar-wisseling = notificatie 10 wd; routine renewal = COI only |
| 10g LN-medefinanciering | 100% delta LN, cap €10k/jaar, lapse bij MSA-einde |
| 10h Authorized Affiliate-coverage | Named beneficiary-route (geen additional insured); LN-medefinanciering-pad als LN echt wenst |
| 10i Uitsluitingen | AI/third-party AI/automated decisions/social engineering NIET acceptabel; standaard industry-exclusions wel |

---

#### Onderbouwing & onderhandelingsruimte

**Strategische keuzes die expliciete onderbouwing behoeven**:

1. **AVB niet expliciet vereisen** — Protocol heeft standaard zakelijk-pakket. Geen toegevoegde waarde voor AI-consultancy-relatie, alleen administratieve last in MSA.

2. **Eigen risico-cap €25k** — werkelijke Protocol-polis zit op €5-10k. €25k is veilige bovengrens die Protocol commerciële flexibiliteit geeft zonder LN-Legal-discomfort.

3. **LN-medefinanciering 100/0 met €10k cap** — bouwt voort op 7i good faith negotiation. Concretiseert tot eerlijke verdeling: LN wil hogere dekking, LN betaalt. Cap voorkomt onverwachte premie-explosies.

4. **Named beneficiary-route i.p.v. additional insured** — open vraag aan ICTRecht hierboven. Pre-emptieve positie pro-Protocol (lagere premie, simpelere polis-administratie).

5. **Polis-uitsluitingen hard afdwingen (10i)** — Protocol garandeert AI/third-party AI/automated decisions/social engineering NIET in polis uitgesloten zijn. LN-Legal krijgt sterke garantie; Protocol kan dit hard maken want NL-markt-Hiscox/Chubb/Markel-polissen hebben deze uitsluitingen typisch niet.

6. **36 mnd run-off matched aan 7e** — geen gat tussen "claim kan nog ingediend" en "polis dekt". Standaard E&O-ERP-rider of doorlopende polis dekt dit.

**Cross-references binnen MSA**:
- Sectie 1c (Authorized Affiliates) ↔ 10h named beneficiary-construct
- Sectie 7e (time-bar 36 mnd post-termination) ↔ 10e run-off period
- Sectie 7i (insurance baseline-bedragen) ↔ 10b minimum-bedragen (volledig synchroon)
- Sectie 7k (subprocessor step-in) ↔ 10i no AI-provider-exclusion
- Sectie 7l (force majeure third-party-AI) ↔ 10i no third-party AI-exclusion
- Sectie 7h (AI-output liability) ↔ 10i no AI/automated decision-exclusion
- Sectie 8c (defense costs binnen cap) ↔ 10b defense costs binnen limits
- Sectie 8f (cooperation 36 mnd post-termination) ↔ 10e run-off matched

**Sources die ICTRecht moet kunnen verifiëren**:
- NLdigital Voorwaarden 2025 art 14.3 (verzekeringsverplichting): https://www.nldigital.nl/kennis-producten/nldigital-voorwaarden-2025/
- ARBIT (rijksinkoop-voorwaarden, insurance-baseline)
- NL-rechtelijke positie named beneficiary onder E&O — BW 6:253 derdenbeding-leerstuk

### Sectie 11 — DPA-referentie

**Datum vastgelegd**: 2026-05-11

#### Methodologische context

**Belangrijk onderscheid**: Sectie 11 specificeert de **MSA-zijde van de MSA-DPA-relatie** (bridge, order of precedence, cross-references, amendment-procedure). De inhoudelijke DPA-content (verwerkersverplichtingen, beveiligingsmaatregelen, sub-processor-procedure, audit-rights, breach-procedure) wordt geleverd door de **LN-group DPA Addendum-template** (sent by Jennifer Quik, 20 april 2026, bestand: `agreements/templates/LNVN-x-POTN-Verwerkersovk-template-20260420.docx`) — geredlined conform DPA-strategie-Besluit 2. Sectie 11 stelt het kader; de redlines werken in Jennifer's tekst.

**Scope-statement**: De DPA waarnaar deze sectie verwijst dekt uitsluitend **Protocol Client Automations (Traject 2)** — HR Agent (AFAS), Brand Shield (MOJO), custom builds. Protocol Owned Products (Traject 3 — Venue Vera, F&B, Carla, Donna) vallen buiten LN-MSA-scope en hebben hun eigen Narrative product-DPA per Besluit 1.

**Status-legenda voor elke sub-component**:
- 🟢 **Compatibel** met Jennifer's template — geen conflict verwacht
- 🟡 **Onderhandelingspunt** — onze positie moet door ICTRecht in redline worden voorgesteld
- 🔴 **Conflict reeds als redline geïdentificeerd** in DPA-strategie-Besluit 2 — onze counter-positie staat klaar

Methodologisch: AVG Art 28 als basis + ICTRecht's verwerkersovereenkomst-positie + DPA-strategie-Besluit 2 (drie harde redlines op Jennifer's template: P57 unlimited indemnity, P52/P54 flow-down mirror, P109 externe pen-test).

Sluit aan op Sectie 2 (document-architectuur + order of precedence), 7g (GDPR-fines/AVG buiten MSA via DPA), 8h (DPA-routering data breach), Jennifer's bestaande LN-DPA-template.

---

#### 11a. Master-DPA + sub-annexen-structuur 🟡 onderhandelingspunt

| Element | Positie |
|---|---|
| **Master-DPA** | Jennifer's LN-group DPA Addendum-template (geredlined) wordt de Master-DPA. Geldt voor alle SoW's onder MSA. Bevat algemene AVG Art 28-verplichtingen, beveiligingsmaatregelen, sub-processor-procedure, data subject rights-procedure, audit-rights, breach-procedure |
| **Annex X per SoW** | Verwerkingsregister-detail per build: aard van verwerking, soorten persoonsgegevens, categorieën betrokkenen, doeleinden, bewaartermijnen, locatie verwerking. Voorstel om P15-P19 (scope-onderwerpen) uit Jennifer's template-body naar Annex X te verhuizen |
| **Annex Y subprocessor-lijst** | Gedeelde lijst van geautoriseerde subprocessors (OpenAI, Apify, Resend, Hostinger, Vercel, Supabase, etc.), update-procedure via 11f |
| **Annex Z beveiligingsmaatregelen** | Technische en organisatorische maatregelen (TOM's): encryption, access control, logging, etc. — sluit aan op Sectie 12 Security baseline |

**Reden — waarom Master + Annex-structuur i.p.v. per-systeem DPA**:
Jennifer's template is al opgezet als "Addendum onder onderliggende Agreement" met `[LNE ENTITY]` placeholders — geschikt voor multi-systeem-toepassing. Annex-per-SoW maakt verwerkingsregister-werk per build mogelijk zonder hele DPA te heronderhandelen. Sluit aan op 6c change-control (per-tenant changes). Onderhandelingspunt omdat we niet weten of LN deze annex-routing accepteert; ICTRecht moet dit in redline voorstellen.

**EN concept-formulering**:
> *"The Parties shall enter into the Data Processing Agreement attached to this Agreement as the 'Master-DPA' (based on the LN-group DPA Addendum template provided by Live Nation, as redlined by the Parties). The Master-DPA shall apply to all Statements of Work executed under this Agreement. The Master-DPA shall be supplemented by the following annexes: (i) Annex X (per Statement of Work) specifying the processing register details for each build (nature of processing, categories of personal data, categories of data subjects, purposes, retention periods, location); (ii) Annex Y (shared) listing authorized sub-processors and the update procedure; (iii) Annex Z (shared) setting forth technical and organizational measures (TOMs), aligned with Section 12 of this Agreement."*

---

#### 11b. Cross-reference language in MSA 🟢 compatibel

**Positie**: DPA is "incorporated by reference and forms an integral part of this Agreement". Niet "separate document with cross-reference" maar "onderdeel van MSA via incorporated-by-reference-construct".

**Reden — waarom integral part i.p.v. losse cross-reference**:
- Stronger juridische binding dan losse cross-reference
- Sluit aan op Sectie 2 order of precedence (DPA wint bij conflict over data-onderwerpen)
- Jennifer's template is al "Addendum onder een onderliggende Agreement" — incorporated-by-reference is precies hoe Jennifer het zelf framet
- ICTRecht's standaard-formulering voor LN-class enterprise-MSAs

**EN concept-formulering**:
> *"The Data Processing Agreement (Master-DPA) and its Annexes, as referenced in Section 11a, are incorporated by reference into this Agreement and form an integral part of this Agreement. Any reference to 'this Agreement' shall include the Master-DPA and its Annexes, except where the context expressly requires otherwise (e.g., the order of precedence in Section 11c)."*

---

#### 11c. Order of precedence-bevestiging 🟢 compatibel

| Conflict | Welk document wint |
|---|---|
| Data-onderwerp (verwerkingsdoeleinde, beveiliging, sub-processor, breach-procedure, data subject rights, AVG-aansprakelijkheid) | **DPA wint** |
| Commercieel onderwerp (fees, IP, change-control buiten data-aspecten, warranties, indemnification van non-data-claims) | **MSA wint** |
| Beide raken het onderwerp | DPA wint voor data-aspect, MSA voor commercieel-aspect (gesplitst toepassen) |

**Reden — waarom DPA wint over data-onderwerpen**:
Al in Sectie 2 vastgelegd. Sluit aan op 7c (AVG-aansprakelijkheid via DPA-cap-clausule, niet MSA-cap), 7g (GDPR-fines buiten MSA), 8h (DPA-routering data breach-procedure). ICTRecht's standaard-positie voor MSA-DPA-stacking.

**EN concept-formulering**:
> *"In the event of any conflict or inconsistency between this Agreement and the Master-DPA: (i) the Master-DPA shall prevail with respect to matters concerning the processing of personal data, including purposes and means of processing, security measures, sub-processor procedures, personal data breach procedures, data subject rights procedures, and liability for personal data protection compliance; (ii) this Agreement shall prevail with respect to all other matters, including fees, intellectual property ownership and licensing, change control (other than data-related aspects), warranties, and indemnification of non-data-related claims; (iii) where a single subject matter is addressed by both documents, each document shall apply to its respective aspect (data versus commercial) on a split-application basis."*

---

#### 11d. DPA-amendment-procedure — hybrid via 6c 🟡 onderhandelingspunt

| Wijziging | Procedure | Toelichting |
|---|---|---|
| **DPA-body wijziging** (algemene verplichtingen, scope, beveiligingsmaatregelen, audit-rights) | **6c Tier 3** (e-signature MSA-niveau) | Locked-section per Sectie 2 safeguard-clausule |
| **Annex X wijziging** (verwerkingsregister-detail per SoW) | **6c Tier 2** (email-thread met 5 minimumvereisten) | Verwerkingsregister-detail logisch koppelen aan SoW-niveau |
| **Annex Y wijziging** (subprocessor-toevoeging/-verwijdering) | **6c Tier 2** + AVG Art 28 lid 2 notificatieplicht + verzetsrecht 15 werkdagen | Standaard AVG-procedure |
| **Annex Z wijziging** (TOM-maatregelen) | **6c Tier 2** mits upgrade; **Tier 3** bij downgrade | Beveiligingsmaatregelen mag wel sterker, niet zwakker zonder formele review |

**Reden — waarom hybrid procedure**:
Voorkomt dat elke DPA-aanpassing een DocuSign-procedure wordt (operationeel disfunctioneel), maar dwingt e-signature af bij wijzigingen die kerncompliance raken. Onderhandelingspunt omdat Jennifer's template een eigen amendment-procedure kan hebben — door 11c (DPA wint over data-onderwerpen) wint Jennifer's DPA-amendment-procedure dan voor DPA-content. Onze 11d hybrid blijft gelden voor MSA-content.

Open vraag aan ICTRecht (zie hieronder) over AVG Art 28-conformiteit van deze hybrid procedure.

**EN concept-formulering**:
> *"Amendments to the Master-DPA and its Annexes shall follow the change-control procedures set forth in Section 6c, applied as follows: (i) amendments to the body of the Master-DPA (general Processor obligations, scope, security framework, audit rights) require Tier 3 (e-signature at MSA level), as these constitute Locked Sections under Section 2; (ii) amendments to Annex X (per-SoW processing register details) may be effected via Tier 2 (written agreement via email, including the minimum required elements per Section 6c); (iii) amendments to Annex Y (sub-processor list) follow Tier 2 plus the notification and objection procedure under Article 28(2) GDPR, with a fifteen (15) business day objection period; (iv) amendments to Annex Z (technical and organizational measures) may be effected via Tier 2 where they constitute an upgrade in security, and require Tier 3 where they constitute a downgrade."*

---

#### 11e. GDPR-rolverdeling controller/processor per SoW 🟢 compatibel

| Default rolverdeling | Positie |
|---|---|
| **LN/affiliate** | Controller (verwerkingsverantwoordelijke) |
| **Protocol** | Processor (verwerker) |
| **Override per SoW** | Bij joint controller-scenarios kan per SoW expliciete erkenning + verdeling verplichtingen worden vastgelegd. Niet pre-emptief in MSA — Joint controller komt zelden voor in Protocol's portfolio en pre-emptieve clausule creëert onnodige complexiteit |
| **AI-rollen separaat** | Sluit aan op 7h AI Act Art 16 (Provider) / Art 26 (Deployer) — GDPR-rollen en AI-Act-rollen zijn aparte concepten, soms dezelfde partij, soms verschillend |

**Reden — waarom default + SoW-override**:
Default processor/controller is standaard voor agency-builds. Joint controller is uitzondering voor specifieke use cases (bijv. anonimisering-onderzoek waar Protocol mede-doeleinden bepaalt) — alleen per SoW vastleggen, niet pre-emptief in MSA. Voorkomt dat elke SoW de rolverdeling moet herbevestigen voor standaard cases.

**EN concept-formulering**:
> *"Unless otherwise expressly agreed in a Statement of Work, with respect to processing of personal data under this Agreement: (i) Customer (or its applicable Authorized Affiliate) shall be the Controller within the meaning of Article 4(7) GDPR; (ii) Protocol shall be the Processor within the meaning of Article 4(8) GDPR. Where a specific Statement of Work involves processing for which Protocol determines, jointly with Customer, the purposes and means of processing, the Parties may expressly designate themselves as Joint Controllers under Article 26 GDPR in that Statement of Work and shall execute the Joint Controller arrangement required thereunder. The role allocation under this Section 11e is independent of the AI Act Provider/Deployer allocation under Section 7h, which is determined separately for each AI system deployed."*

---

#### 11f. Sub-processor-listing in Annex Y 🔴 conflict reeds als redline geïdentificeerd

| Element | Positie |
|---|---|
| Locatie | Annex Y van DPA (niet MSA-body) |
| Initial list | Bij MSA-ondertekening (OpenAI, Apify, Resend, Hostinger, Vercel, Supabase, etc. per SoW relevant) |
| Update-procedure | AVG Art 28 lid 2: schriftelijke notificatie + verzetsrecht binnen **15 werkdagen** |
| Cross-link | Sluit aan op 7k subprocessor-cascade (Protocol step-in) + 10i polis-uitsluitingen (subprocessor-failures gedekt) |

**Reden — waarom Annex Y i.p.v. DPA-body**:
Annex-Y-listing maakt updates via 6c Tier 2 (email-thread) mogelijk i.p.v. e-signature voor elke nieuwe subprocessor. Standaard AVG-procedure.

**Reden — waarom 15 werkdagen verzetsrecht**:
AVG Art 28 lid 2 zegt "redelijke termijn". NL-marktstandaard varieert van 10 tot 30 werkdagen. 15 werkdagen balanceert tussen LN-comfort en Protocol's onboardingsflexibiliteit.

**Conflict met Jennifer's template (P52/P54)**:
Jennifer's template P52/P54 wil flow-down "woord-voor-woord mirror" + jaarlijkse audits van elke subprocessor. Per DPA-strategie-Besluit 2 is de counter: "Annex Y met subprocessor-exhibit + EDPB Opinion 22/2024-beroep op substantively equivalent via publieke DPA's (OpenAI, Meta, Twilio) + SCC's voor international transfers". Onze 11f formulering ondersteunt deze counter-positie maar de redline op Jennifer's template-body blijft het zwaartepunt van de onderhandeling.

**EN concept-formulering**:
> *"The authorized sub-processors used by Protocol in the provision of services under this Agreement and any Statement of Work shall be listed in Annex Y to the Master-DPA. Protocol shall provide written notice to Customer of any intended addition or replacement of sub-processors. Customer shall have a period of fifteen (15) business days from receipt of such notice to object on reasonable grounds related to the protection of personal data. If Customer objects, the Parties shall use good faith efforts to resolve the objection, including consideration of alternative sub-processors or scope adjustments. Protocol shall flow down to its sub-processors data protection obligations substantively equivalent to those contained in the Master-DPA, recognizing that direct word-for-word mirroring may not be feasible with major third-party providers (e.g., OpenAI, Meta, Twilio), in which case Protocol shall rely on such providers' published Data Processing Agreements and Standard Contractual Clauses as the contractual flow-down mechanism, consistent with EDPB Opinion 22/2024."*

---

#### 11g. Data subject rights-procedure — DPA-detail, MSA cross-link only 🟢 compatibel

**Positie**: MSA verwijst naar DPA voor inzage, rectificatie, verwijdering, beperking, dataportabiliteit, bezwaar (AVG Art 12-22). Geen herhaling in MSA-body — DPA dekt de procedurele invulling.

**Reden — waarom alleen cross-link**:
Voorkomt dubbele documentatie. ICTRecht-standaard: DPA is the source of truth voor data subject rights-procedure. Jennifer's template heeft hier waarschijnlijk al een eigen sectie voor — geen reden om dat in MSA te dupliceren.

**EN concept-formulering**:
> *"The procedures for handling data subject rights requests under Articles 12-22 GDPR (including access, rectification, erasure, restriction, portability, and objection) shall be governed by the Master-DPA. This Agreement does not duplicate or modify those procedures."*

---

#### 11h. Audit rights — gesplitste behandeling 🔴 conflict reeds als redline geïdentificeerd

| Type audit | Locatie | Toelichting |
|---|---|---|
| **AVG Art 28 lid 3(h) audit** (verwerker-compliance) | **In DPA detail** | Standaard processor-audit-right voor controller. Max 1× per jaar mits schriftelijk verzoek en redelijke termijn |
| **Commercieel audit-right** (financial, performance, security beyond AVG) | **Niet in DPA, niet in Sectie 11** — verschuiven naar Sectie 12 Security baseline waar audit-onderwerpen logischer thuishoren | Aparte clausule mogelijk in Sectie 12 of in SoW per build |
| **Toezichthouder-audit** (AP-onderzoek) | DPA cooperation-clausule | Protocol verleent redelijke medewerking aan AP-onderzoek tegen LN; LN idem |

**Reden — waarom gesplitst**:
AVG Art 28-audit ≠ commercieel audit. Door dit te splitsen blijft DPA AVG-conform, en kan LN aparte commercial audit-clausule bedingen in Sectie 12 zonder DPA-overhead.

**Conflict met Jennifer's template (P109)**:
Jennifer's P109 wil externe pen-test + remediation proof voor go-live + jaarlijkse pen-tests. Per DPA-strategie-Besluit 2 is de counter: "SOC2/ISO-reports op verzoek, niet on-site audits voor sub-processors; eigen Protocol-applicatie-laag pen-test binnen 90 dagen na go-live + jaarlijks". Deze counter-positie zit in DPA-body (audit-rights-clausule), niet in MSA Sectie 11.

Sectie 11h regelt alleen de **routering**: AVG-audit in DPA, commercieel audit in Sectie 12, toezichthouder-audit in DPA. De inhoudelijke audit-eisen (frequency, scope, methodology) staan in DPA-body — niet in 11h.

**EN concept-formulering**:
> *"Audit rights under this Agreement and the Master-DPA shall be allocated as follows: (i) audits of Protocol's compliance with its Processor obligations under Article 28(3)(h) GDPR are governed exclusively by the Master-DPA, including the procedural requirements (frequency, notice, scope, confidentiality) set forth therein; (ii) commercial audit rights (covering financial, performance, and security matters beyond GDPR Processor compliance) are governed by Section 12 of this Agreement or by the applicable Statement of Work; (iii) cooperation in supervisory authority investigations (including investigations by the Autoriteit Persoonsgegevens) is governed by the cooperation clause in the Master-DPA, with each Party bearing its own defense costs as set forth in Section 8h of this Agreement."*

---

#### Open vragen aan ICTRecht

> ⚠️ **Open vraag 1 (DPA-amendment-procedure hybrid)**: Sectie 11d kiest voor hybrid amendment-procedure — DPA-body via Tier 3 e-signature, annexen via Tier 2 email-thread, met specifieke regels voor Annex Y (subprocessor — AVG Art 28(2)-procedure) en Annex Z (TOM's — Tier 2 upgrade / Tier 3 downgrade). Vraag aan ICTRecht: is deze hybrid procedure AVG Art 28-conform, met name in scenario's waarin Jennifer's template een striktere amendment-procedure voorschrijft? Verwachting: door 11c order of precedence (DPA wint over data-onderwerpen) wint Jennifer's procedure waar relevant. Bevestiging gewenst dat onze 11d-architectuur niet conflicteert met Jennifer's template-body.

> ⚠️ **Open vraag 2 (Master-DPA + Annex-per-SoW-structuur AVG-conform)**: Sectie 11a stelt een Master-DPA (Jennifer's geredlinede template) met Annex X per SoW (verwerkingsregister), Annex Y (subprocessor list), Annex Z (TOM's) voor. Vraag aan ICTRecht: is dit AVG Art 28(3)-conform, met name het criterium dat de DPA "the subject-matter and duration of processing, the nature and purpose of the processing, the type of personal data and categories of data subjects" moet specificeren — vereist dit een volledige DPA per SoW, of is een Master-DPA + per-SoW-Annex X-architectuur juridisch sluitend? Onze positie: Annex X-route is sluitend en sluit aan op marktpraktijk bij multi-SoW-MSAs. Bevestiging gewenst.

---

#### Samenvattend — Sectie 11 finale structuur

| Element | Status | Positie |
|---|---|---|
| 11a Master-DPA + sub-annexen | 🟡 onderhandelingspunt | Jennifer's template als Master-DPA + Annex X (per SoW) + Y (subprocessor) + Z (TOMs) |
| 11b Incorporated by reference | 🟢 compatibel | DPA + Annexen incorporated, integral part |
| 11c Order of precedence | 🟢 compatibel | DPA wint over data-onderwerpen, MSA over commercieel, split bij dubbel onderwerp |
| 11d DPA-amendment hybrid | 🟡 onderhandelingspunt | Tier 3 DPA-body; Tier 2 Annex X/Y; Tier 2 Annex Z mits upgrade |
| 11e Rolverdeling | 🟢 compatibel | Default LN=controller, Protocol=processor; SoW-override voor joint controller; AI-rollen separaat per 7h |
| 11f Sub-processor listing | 🔴 conflict reeds als redline | Annex Y, 15 wd verzetsrecht, EDPB Opinion 22/2024-beroep op substantively equivalent |
| 11g Data subject rights | 🟢 compatibel | MSA cross-link only, geen herhaling |
| 11h Audit rights gesplitst | 🔴 conflict reeds als redline | AVG Art 28-audit in DPA; commercieel audit in Sectie 12; toezichthouder-audit in DPA |

---

#### Onderbouwing & onderhandelingsruimte

**Strategische keuzes die expliciete onderbouwing behoeven**:

1. **DPA-content komt uit Jennifer's template, niet uit Narrative** — fundamenteel onderscheid. Sectie 11 is MSA-zijde van de bridge; DPA-zijde komt uit Jennifer's LN-group DPA Addendum-template (sent 20 apr 2026) met onze redlines per DPA-strategie-Besluit 2.

2. **Hybrid amendment-procedure (11d)** — Tier 3 voor DPA-body, Tier 2 voor annexen. Open vraag 1 aan ICTRecht over AVG Art 28-conformiteit.

3. **Master-DPA + Annex-per-SoW-structuur (11a)** — Jennifer's template als Master, onze Annex-architectuur eronder. Open vraag 2 aan ICTRecht over AVG Art 28(3)-conformiteit.

4. **Sub-processor verzetsrecht 15 werkdagen (11f)** — balanceert LN-comfort en Protocol-flexibiliteit. NL-marktstandaard.

5. **Default rolverdeling met SoW-override (11e)** — voorkomt herbevestiging per SoW voor standaard cases. Joint controller pre-emptief vermijden — pas in SoW vastleggen.

6. **Audit-rights gesplitst (11h)** — AVG-audit (DPA), commercieel audit (Sectie 12), toezichthouder-audit (DPA). Houdt DPA AVG-conform zonder commercial-audit-overhead.

7. **Conflict-zones (11f en 11h)** — al via DPA-strategie-Besluit 2 voorbereid met counter-formuleringen (EDPB Opinion 22/2024 + SOC2/ISO i.p.v. on-site audits).

**Cross-references binnen MSA**:
- Sectie 2 (document-architectuur + order of precedence) ↔ 11b/11c (incorporated by reference + DPA wint over data)
- Sectie 6c (3-tier change-control) ↔ 11d (hybrid amendment via Tier 2/3)
- Sectie 7c (AVG-aansprakelijkheid via DPA, niet MSA-cap) ↔ 11c order of precedence
- Sectie 7g (GDPR-fines buiten MSA) ↔ 11c order of precedence
- Sectie 7h (AI Act rollen Provider/Deployer) ↔ 11e (GDPR-rollen separaat)
- Sectie 7k (subprocessor step-in) ↔ 11f (Annex Y)
- Sectie 8h (DPA-routering data breach) ↔ 11c order of precedence + 11g/11h DPA-detail
- Sectie 10i (geen subprocessor-uitsluitingen in polis) ↔ 11f subprocessor-listing
- Sectie 12 (Security baseline — to be drafted) ↔ 11h commercieel audit + Annex Z TOMs
- Jennifer's DPA-template ↔ 11a Master-DPA + alle DPA-content

**Sources die ICTRecht moet kunnen verifiëren**:
- LN-group DPA Addendum template (bestand: `agreements/templates/LNVN-x-POTN-Verwerkersovk-template-20260420.docx`)
- DPA-strategie-Besluit 2 (drie harde redlines): `agreements/dpa-strategy-decisions.md`
- AVG Art 28 (Verwerker-verplichtingen), Art 26 (Joint Controllers), Art 32 (beveiliging)
- EDPB Opinion 22/2024 (substantively equivalent flow-down)
- NLdigital Voorwaarden 2025 (referentie marktstandaard)
- ICTRecht-blog "Aansprakelijkheid in verwerkersovereenkomst" (al opgenomen bij Sectie 7)

### Sectie 12 — Security baseline

> **Inleidende paragraaf — relatie met DPA-zijde**
>
> Sectie 12 specificeert Protocol's security-baseline aan **MSA-zijde**. Specifieke AVG-technische beveiligingsmaatregelen onder Art 32 worden uitgewerkt in DPA Annex Z (TOM's), die onderdeel is van Jennifer's LN-group DPA Addendum-template (20 apr 2026) zoals geredlined per DPA-strategie-Besluit 2. Status-markering per sub-component reflecteert positie t.o.v. Jennifer's template: 🟢 compatibel / 🟡 onderhandelingspunt / 🔴 conflict reeds als redline geïdentificeerd.
>
> **Scope**: geldt voor Traject 2 (Protocol Client Automations). Owned Products (Venue Vera, F&B, Carla, Donna) vallen onder eigen Narrative product-DPA per Besluit 1.

**12a. Baseline-TOM's (technische en organisatorische maatregelen)** 🟡 onderhandelingspunt

| Categorie | Baseline |
|---|---|
| Encryption at rest | AES-256 op Supabase database, Vercel storage, n8n credentials store |
| Encryption in transit | TLS 1.2+ voor alle API-calls en data-overdracht |
| Access control | Role-based access (RBAC) op alle systemen; least-privilege principe |
| MFA | Verplicht op alle Protocol-systemen die toegang hebben tot LN-data (Vercel, Supabase, n8n, OpenAI, GitHub) |
| Logging + monitoring | Centralized logging van alle data-access; minimaal 12 maanden retention |
| Backup + recovery | Daily encrypted backups; max 24u RPO; max 8u RTO bij incident |
| Incident response | Documented runbook + 24u-melding aan LN bij bevestigd incident |

**Reden — counter op P37**: Jennifer's template-clausule P37 ("TPV-only-encryption cannot be decrypted by government authorities") is onhoudbaar voor SaaS-LLMs. Onze baseline encrypteert alles wat onder Protocol's controle valt, met expliciete erkenning dat third-party-AI-providers server-side verwerken. Door zelf scherp te formuleren voorkomen we tekenen onder onhaalbare bewoording.

**12b. Industry-standaard-referenties** 🟢 compatibel

| Standaard | Toepassing | Reden |
|---|---|---|
| **ISO 27001** | Doel-referentie voor information security; **geen hard certification-vereiste** | €15-25k initial + €5k/jaar maintenance disproportioneel voor 2-persoons-vendor |
| **OWASP ASVS Level 2** | Concrete development-standaard (Application Security Verification Standard) | NIST 800-218 (SSDF) erkent; EU AI Act-context geaccepteerd |
| **SOC 2 Type II** | Verplicht van subprocessors waar relevant (Vercel ✅, Supabase ✅, OpenAI ✅) | Sub-processors hebben deze certificering al |
| **NIST 800-53** | Niet vereist | Gov-grade, disproportioneel voor Protocol-omvang |

**Bewijslast voor "documented adherence without certification"**: paper trail Second Brain + Notion + GitHub commits + Vercel logs + Supabase audit logs = demonstrable equivalent assurance.

**12c. Annex Z-structuur** 🟡 onderhandelingspunt

| Element | Positie |
|---|---|
| Locatie | Annex Z van DPA (per 11a) |
| Inhoud | Gemapped TOM-lijst tegen ISO 27001-controle-categorieën (A.8 cryptografie, A.9 access control, A.12 operations security, A.16 incident management, A.17 business continuity) |
| Update-procedure | Per 11d: Tier 2 mits upgrade, Tier 3 bij downgrade |
| Reviewfrequentie | Jaarlijks, samen met DPA-renewal |

**Reden**: ISO 27001-mapping geeft Jennifer en ICTRecht direct herkenbare structuur; voorkomt "is dit voldoende?"-discussie omdat de Annex zichzelf positioneert tegen branche-standaard.

**12d. Commercieel audit-right** 🟢 nieuw (verschoven uit 11h)

| Element | Positie |
|---|---|
| Scope | Financial audit (kosten-onderbouwing per SoW), performance audit (SLA-naleving), security audit beyond AVG (TOM-implementatie) |
| Frequentie | Maximaal **1× per jaar** mits schriftelijk verzoek + 30 wd redelijke termijn vooraf |
| Methode | **SOC 2 Type II-rapport** + aangepaste vragenlijst — **geen on-site audit** |
| Kosten | LN draagt audit-kosten (requester pays); Protocol draagt eigen people-time max 5 werkdagen; kosten 50/50 gedeeld + Protocol funded remediation **bij wezenlijke tekortkoming** |
| Tijdsbeperking | Audit-medewerking maximaal 5 werkdagen per audit; niet hindering of operations |

**Reden — SOC 2-rapport i.p.v. on-site audit**: NL-marktstandaard voor enterprise-MSAs zonder onnodige overhead. Voorkomt operationele onderbreking; concreet voor LN-Legal.

**12e. Security-incident-procedure cross-link met DPA** 🟢 compatibel

| Type incident | Routering |
|---|---|
| Personal data breach (AVG Art 33-34) | DPA-procedure (Jennifer's template-body), 72u-melding aan AP |
| Security incident zonder personal data-impact | MSA Sectie 12 — 24u-melding aan LN |
| Cyber-event onder verzekering (10a) | Insurance claim-procedure via 10d COI |

**Reden — routering i.p.v. herhaling**: voorkomt dubbele documentatie. DPA dekt AVG-procedure; MSA dekt alleen security-incidents zonder data-impact; verzekering loopt apart.

**12f. Personnel security** 🟡 onderhandelingspunt (P100-aanpassing)

**12f1. Protocol-direct personeel** (Wytze + Xander + toekomstige Protocol-employees):
- VOG bij toegang tot LN-data (NL-residents)
- Standaard pre-employment screening (referenties, identiteitsverificatie)
- Signed NDA's verplicht onderdeel arbeidsovereenkomst
- Jaarlijkse security-awareness training; specifieke training bij toegang tot productie-systemen

**12f2. Sub-processor-personeel** (AY Automate-detachering, toekomstige sub-processors):
- **Sub-processor levert attestation** in Annex Y: "Sub-processor confirms that all personnel assigned to Protocol's services apply standard pre-employment screening per applicable local employment law (US Delaware standards voor AY Automate), including identity verification, work history reference checks, and signed NDA."
- **Protocol verifies**: signed sub-DPA + listed in Annex Y + Wytze's attestation ("Daniel works for Protocol via AY Automate sinds [datum], scope-limited access, no incidents")
- **Géén directe VOG-eis aan AY Automate-personnel** (technisch onmogelijk voor non-NL-citizens)
- **Identity verification op sub-processor-niveau** (paspoort/ID gezien door sub-processor bij employment)
- **Role-scoped access control**: least-privilege principe — Daniel krijgt alleen access tot strikt noodzakelijk voor specifieke build-werk

**12f3. Onafhankelijk van laag**:
- Alle access tot LN-data via Protocol's centralized RBAC + MFA + audit logging — activiteiten altijd traceerbaar via Protocol's logging
- Access wordt direct gerevoked bij beëindiging van Protocol↔sub-processor detachering

**Reden — counter op P100**: Jennifer's P100 ("background checks voor alle personnel + subcontractors") is operationeel onhaalbaar voor 2-persoons-vendor met internationale contractors. Scoped variant (Protocol-direct VOG, sub-processor-attestation) is functioneel equivalent zonder overhead. AVG-conform via Art 28(3) sub-processor flow-down.

**12g. Security baseline + penetration test-eisen** 🔴 conflict reeds als redline P109

**12g1. Protocol-baseline (eigen kosten, included in MSA fee)**:

| Element | Implementatie |
|---|---|
| **OWASP ASVS Level 2** | Doel-referentie voor secure development; OWASP Top 10 als minimum-coverage |
| **Automated continuous monitoring** | Dependabot (auto-PR's voor dependency-updates), CodeQL via GitHub Actions (gratis voor private repos), Vercel security headers, Snyk free tier optioneel |
| **Documented SDLC** | Automated quality gates op elke commit/PR (linting, type checking, SAST, dependency scanning); gedocumenteerde merge-rules per repository proportioneel aan project-risico; minimum 60% test-coverage op kritieke paden; deployment via versioned CI/CD met audit log. **Geen verplicht 4-eyes review op iedere commit** — Protocol bepaalt review-praktijk per project-risico |
| **Vulnerability disclosure** | `security@partofthenarrative.com` email-alias + documented response-policy (5 wd acknowledgment, remediation per severity-classification). `security.txt` per RFC 9116 op `.well-known/` **alleen verplicht voor producten met publieke onboarding-functionaliteit**; voor auth-only-B2B (zoals Venue Vera, alle Traject 2 MSA-builds): email-alias + policy volstaat |
| **Annual self-assessment** | Protocol levert jaarlijks security self-assessment-rapport aan LN (TOM-status, monitoring-output, eventuele incidents). AI-assisted opstellen acceptabel |

**12g2. Third-party penetration test (LN-funded indien LN het wenst)**:

| Element | Positie |
|---|---|
| Verplichte initial Protocol-funded pen-test | **Nee** — Protocol-baseline rust op OWASP + continuous monitoring; pen-test is requester-pays per NL-marktstandaard audit-rights |
| Pre-go-live pen-test (LN-initiated) | LN-funded 100%; scope per LN binnen Protocol-applicatie-laag |
| Periodieke pen-test (jaarlijks/biennial) | LN-initiated + LN-funded; vooraf schriftelijk opdracht voor komend jaar |
| Trigger-based ad-hoc | Negotiable per case; standaard LN-funded **tenzij major incident aantoonbaar Protocol-attributable** (dan Protocol-funded) |
| Cap | Max **€15k/jaar** LN-funded pen-test (security-specifiek, **boven** 10g cap van €10k voor insurance-uplift) |
| Auditor | A-rated NL/EU-bureau (Computest, Securify, Outflank, of equivalent); Protocol mag auditor weigeren bij belangenconflict |
| Time-window | 60 wd vooruit-melding; niet samenvallend met major releases of pieken in operations |
| Resultaat | Full report naar Protocol; executive summary naar LN |
| Remediation-deadlines | Critical findings binnen 30 dagen; high binnen 60 dagen; medium/low per release-cyclus |
| Stapeling | LN-funded uplift kan niet "stapelen": als LN één jaar overslaat, geen retro-recovery |

**12g3. Subprocessor-infrastructuur pen-test**:
- Vercel/Supabase/OpenAI/Cloudflare: **SOC 2 Type II-rapport op verzoek** — geen on-site audit (technisch onmogelijk + niet onder LN-funded mechanisme)

**Reden — counter op P109**: NL-marktstandaard "requester pays" voor audit/inspection-rights (ICTRecht model, NLdigital 2025). Protocol's OWASP + automated monitoring = baseline; externe pen-test is LN-requested = LN-funded. Geeft LN volledige scheduling-controle zonder vendor-margin op te eten. NLdigital 2025 erkent expliciet proportionaliteit aan vendor-omvang.

**12h. Sub-processor-security-eisen** 🟡 onderhandelingspunt (cross-link 11f)

| Eis aan elke sub-processor | Positie |
|---|---|
| SOC 2 Type II OF ISO 27001 certification | Verplicht (Vercel ✅, Supabase ✅, OpenAI ✅, Resend ✅, Apify 🟡 alternative attestation, Hostinger 🟡 alternative attestation) |
| Geldige sub-DPA met Protocol | Verplicht |
| Standard Contractual Clauses voor US-transfers | Verplicht voor US-subprocessors (cross-link 12i) |
| Notificatie aan Protocol bij sub-processor security-incident | Verplicht in sub-DPA |
| Cross-link Sectie 11f Annex Y subprocessor-listing | Bevestigt status + verzetsrecht 15 wd |

**Reden — gedifferentieerde aanpak**: niet alle subprocessors hebben SOC 2/ISO. Voor "🟡"-categorie (Apify, Hostinger) verricht Protocol aanvullende due-diligence en documenteert in Annex Y welke alternatieve assurance is toegepast. Sluit aan op EDPB Opinion 22/2024-beroep op "substantively equivalent" in 11f.

**12i. Data-residency + internationale doorgifte** 🔴 conflict reeds als redline P41

| Element | Positie |
|---|---|
| Primary data storage location | **NL/EU** (Supabase EU-region, Hostinger Frankfurt, Vercel EU-edge) |
| US-transfers | Beperkt tot **noodzakelijke AI-processing** (OpenAI US, xAI US) + **communicatie** (Resend US) |
| Transfer-mechanism | **EU Standard Contractual Clauses (SCC's)** + **Transfer Impact Assessment (TIA)** per US-subprocessor |
| Disclosure obligation | Volledige transparency in Annex Y subprocessor-list met data-categorie per transfer |
| Klant-controle | LN mag specifieke US-subprocessor blokkeren via verzetsrecht 11f (15 wd) |

**Reden — transparency + SCC's i.p.v. P41 warranty**: Jennifer's P41 ("TPV does not engage in Restricted International Transfer") is feitelijk onjuist voor onze stack. Counter via Besluit 2: open over alle US-transfers, gebruik EU SCC's als legal-transfer-mechanism, plus TIA (EDPB Recommendations 01/2020). Dat geeft LN-Legal compliance-comfort zonder onmogelijke warranty.

---

> ⚠️ **Open vraag 1 ICTRecht (ISO 27001-attestation zonder certification)**: 12b gebruikt ISO 27001 als doel-referentie zonder Protocol-certification-vereiste (€15-25k disproportioneel voor 2-persoons-vendor). Vraag: is deze "referentie-frame zonder certificering"-construct juridisch sluitend voor enterprise-MSA met paper-trail-bewijslast (Second Brain + Notion + GitHub-commits + Vercel/Supabase logs), of moet Protocol een gelijkwaardige bewijslast leveren (bijv. third-party security assessment-rapport ~€5-8k)?

> ⚠️ **Open vraag 2 ICTRecht (TIA-frequency)**: 12i vereist TIA per US-subprocessor per EDPB Recommendations 01/2020 ("regelmatig" updaten). Pragmatic-voorstel: jaarlijks + ad-hoc bij subprocessor-toevoeging of materiële stack-wijziging. Vraag: AVG-conform? Of strikter (per kwartaal, per release)?

> ⚠️ **Open vraag 3 ICTRecht (pen-test cost allocation Protocol-baseline + LN-funded uplift)**: NL-marktstandaard "requester pays" voor audit-rights. Counter-positie op P109: Protocol's OWASP + automated monitoring = baseline; externe pen-test is LN-requested = LN-funded met €15k/jaar cap. Vraag: (a) deze positie verdedigbaar in MSA-onderhandeling als counter op P109? (b) zou ICTRecht een initial Protocol-funded pen-test adviseren als minimum-baseline-vereiste, of OWASP ASVS + continuous monitoring voldoende voor 2-persoons-vendor? (c) zo niet pure-LN-funded, wat is een redelijke split (50/50 op initial pen-test)?

---

**Strategische keuzes vastgelegd**:

| Keuze | Motivatie | Wytze-akkoord |
|---|---|---|
| ISO 27001 als referentie-frame zonder certification | €15-25k disproportioneel; paper trail in Second Brain = equivalent demonstrable assurance | ✅ |
| OWASP ASVS Level 2 als development-baseline + Dependabot + CodeQL (gratis GitHub Actions) | Daniel-friendly: automated quality gates, geen verplicht 4-eyes review, blokkeert PR's alleen bij CRITICAL findings | ✅ |
| Vulnerability disclosure lichtgewicht voor auth-only-B2B | `security@`-alias + response-policy voldoet voor Vera-class apps zonder publieke onboarding; `security.txt` alleen verplicht voor public-onboarding-producten | ✅ |
| Personnel security gedifferentieerd: Protocol-direct VOG + sub-processor-attestation | Daniel/AY Automate ↔ NL-VOG technisch onmogelijk; sub-processor flow-down via DPA Annex Y AVG-conform | ✅ |
| Alle third-party pen-tests LN-funded (€15k/jaar cap, boven 10g cap) | "Requester pays" NL-marktstandaard audit-rights; Protocol-margin behouden voor Vera year-1 economics | ✅ |
| Commercieel audit: LN draagt kosten tenzij wezenlijke tekortkoming | NLdigital 2025 + ICTRecht model — verdedigbaar enterprise-standaard | ✅ |
| Data-residency: NL/EU preferred + transparent US-transfers met SCC's + TIA | Counter op P41 onhoudbare warranty; volledige openheid + EDPB-compliance | ✅ |
| Open vragen ICTRecht: ISO-attestation + TIA-frequency + pen-test cost allocation | Drie focus-areas voor professionele review | ✅ |

---

**Cross-references**:
- Sectie 1c Authorized Affiliates → relevant voor 12d audit-scope per affiliate
- Sectie 2 documentarchitectuur → DPA Annex Z verhouding tot MSA Sectie 12
- Sectie 6c change-control → SDLC-aanpassingen via change-order
- Sectie 7k subprocessor cap → 12h sub-processor-eisen + 11f Annex Y
- Sectie 7m PLD-readiness → 12g security-related defects
- Sectie 8h DPA-routering → 12e security-incident cross-link
- Sectie 10a/10i cyber-polis → 12g cyber-incident response + claim-procedure
- Sectie 10g LN-medefinanciering → 12g2 separate €15k/jaar pen-test cap boven insurance €10k/jaar cap
- Sectie 11a/11h Annex Z TOM's → 12c Annex Z-structuur
- Sectie 11d hybrid amendment → 12c Annex Z update-procedure
- Sectie 11f subprocessor listing → 12h sub-processor-eisen + 12i data-residency
- DPA Jennifer's template P37/P41/P100/P109 → counters in 12a/12i/12f/12g

**Implementatie-actiepunten voor Risk Analysis-repo (Venue Vera)**:
- GitHub issue #20 aangemaakt op `partofthenarrative/risk-analysis`, toegewezen aan daniel-ayautomate
- On-hold totdat MSA-onderhandelingen afgerond zijn
- Bevat: Dependabot config + CodeQL workflow + `security@`-alias + privacy policy + DPA-page (placeholder/Lorem Ipsum acceptabel; Wytze schrijft definitieve content na MSA-finalisatie)
- Tijdsraming: ~2-3 uur totaal

**Bronnen / verwijzingen**:
- DPA-strategie-Besluit 2 (drie harde redlines P37/P41/P52/P54/P57/P100/P109): `agreements/dpa-strategy-decisions.md`
- OWASP ASVS Level 2: `https://owasp.org/www-project-application-security-verification-standard/`
- ISO 27001:2022 controle-categorieën A.5-A.18
- NIST 800-218 SSDF (Secure Software Development Framework)
- EDPB Recommendations 01/2020 on measures supplementing transfer tools
- EDPB Opinion 22/2024 (substantively equivalent flow-down — al opgenomen bij Sectie 11)
- NLdigital Voorwaarden 2025 art 13 (security baseline + audit-rights)
- AVG Art 28 (Verwerker-verplichtingen), Art 32 (Beveiliging), Art 33-34 (Incident notification)

### Sectie 13 — Change-control

*Gemerged in Sectie 6c (Acceptance & Change Control) — Tier 1/2/3-amendments met klant-tenant + Protocol-tenant scenario's, third-party AI-provider risk, change-order formaliteit, emergency change-order procedure. Zie Sectie 6c voor volledige uitwerking.*

### Sectie 14 — Confidentiality

Vastgelegd 2026-05-11. Mutual confidentiality met hybride termijn-structuur. Sluit aan op de Sectie 2 safeguard-clausule (Confidentiality is een van vijf locked sections, niet wijzigbaar via SoW of DPA-Annex).

**Vier sub-componenten met status-markering** (🟢 standaard / 🟡 onderhandelingspunt / 🔴 redline):

**14a. Termijn vertrouwelijkheid post-termination** 🟡

Hybride structuur:
- **Generieke Confidential Information**: 5 jaar na termination
- **Trade secrets**: perpetueel zolang trade-secret-status onder NL-recht behouden blijft (Wet bescherming bedrijfsgeheimen)
- **Personal Data**: perpetueel via DPA (geen MSA-termijn — verwerkingsbasis vervalt automatisch)

Voorbeeld-clausule (basis voor ICTRecht):

> *"The confidentiality obligations set out in this Section 14 shall survive termination or expiration of this Agreement for a period of five (5) years, except that (i) obligations relating to Trade Secrets shall continue for as long as such information retains its status as a trade secret under applicable Dutch law (including but not limited to the Dutch Trade Secrets Act / Wet bescherming bedrijfsgeheimen), and (ii) obligations relating to Personal Data shall be governed by the applicable Data Processing Annex without time limitation."*

Status 🟡 want LN-IT-juristen zullen mogelijk 5 jaar generiek als kort ervaren; perpetual-deel voor trade secrets en personal data biedt extra comfort.

**14b. Default-protection scope** 🟢

Geen marking-eis. Alle Confidential Information is by default beschermd, tenzij specifiek vrijgegeven of onder een exception (14d).

Voorbeeld-clausule:

> *"Confidential Information means all non-public information disclosed by or on behalf of one Party (the "Disclosing Party") to the other Party (the "Receiving Party") in connection with this Agreement, whether disclosed orally, in writing, electronically, visually, or in any other form, and regardless of whether such information is marked or identified as confidential. Confidential Information includes, without limitation, technical, financial, operational, commercial, personnel, customer, supplier, and strategic information, as well as the existence and terms of this Agreement."*

Sluit aan op werkbare praktijk (Granola-transcripts, Slack-channels, email-threads) — geen marking-overhead. NLdigital 2025 hanteert ook default-protection.

**14c. Return / destruction-procedure** 🟢

| Categorie | Termijn | Bron |
|---|---|---|
| **Customer Data** (personal + business) | 30 dagen post-termination | Cross-link 5c + DPA Annex X |
| **Confidential business info** (niet-data) | 60 dagen post-termination, op schriftelijk verzoek | Sectie 14 |
| **Archief-carve-out** | Verplichte retentie onder wet/accountant/insurance | Sluit aan op 7e time-bar tail (36 mnd post-termination) — bewijslast moet beschikbaar blijven |
| **Bewijs van vernietiging** | Schriftelijke verklaring op verzoek (geen audit-right) | Marktstandaard |

Voorbeeld-clausule:

> *"Upon termination or expiration of this Agreement, each Party shall, within sixty (60) days of receipt of a written request from the other Party, either return or destroy (at the Receiving Party's election) all Confidential Information of the Disclosing Party in its possession or control, except that: (a) Customer Data shall be returned or destroyed within thirty (30) days in accordance with Section 5c and the applicable Data Processing Annex; (b) the Receiving Party may retain copies required to be retained under applicable law, accounting standards, insurance obligations, or for the purpose of defending claims under Section 7e, provided that such retained copies remain subject to the confidentiality obligations of this Agreement; (c) backup copies and electronic records created in the ordinary course of business that cannot reasonably be deleted shall remain subject to the confidentiality obligations until naturally overwritten."*

**14d. Standard exceptions** 🟢

| Exception | Beschrijving |
|---|---|
| **Publiek bekend** | Was al publiek bekend voor disclosure, of werd publiek bekend zonder schending door Receiving Party |
| **Onafhankelijk ontwikkeld** | Door Receiving Party ontwikkeld zonder gebruik van Confidential Information (bewijslast bij Receiving Party) |
| **Rechtmatig verkregen** | Door Receiving Party verkregen van derde zonder NDA-restrictie en zonder schending |
| **Wettelijk verplichte disclosure** | Court order, regulator, AVG-DPIA-procedure — met notificatie aan Disclosing Party vooraf **tenzij wettelijk verboden** |

**Compelled disclosure-clausule**:

> *"If the Receiving Party is required by law, regulation, court order, or administrative or regulatory authority to disclose Confidential Information, the Receiving Party shall, to the extent legally permitted, provide the Disclosing Party with prompt prior written notice and reasonable cooperation to enable the Disclosing Party to seek a protective order or other appropriate remedy. The Receiving Party shall disclose only that portion of the Confidential Information that is legally required and shall use commercially reasonable efforts to ensure that such information receives confidential treatment."*

---

**Cross-references**:
- **Sectie 2 safeguard-clausule**: Confidentiality is een van vijf locked sections (Liability, IP, Confidentiality, Indemnification, Governing Law) — niet wijzigbaar via SoW of DPA-Annex
- **Sectie 3 surviving sections**: Confidentiality blijft van kracht post-termination
- **Sectie 5b Background IP**: Service Provider's prompt-libraries, methodology, code patterns — eigen Confidential Info, niet onderworpen aan return-obligatie onder 14c
- **Sectie 5c klant-data en klant-Confidentiality**: geen training op klant-data — afzonderlijke beperking bovenop Sectie 14
- **Sectie 7b Super-Cap**: Confidentiality breach valt onder Super-Cap 2× (NLdigital 2025-marktconform, geen unlimited carve-out)
- **Sectie 8f Indemnification cooperation-documenten**: documenten uitgewisseld in indemnification-procedure zijn automatisch Confidential
- **Sectie 11 DPA-referentie**: personal data wordt geregeerd door DPA (geen termijn-limit in 14a)

---

**Strategische keuzes vastgelegd**:

| Keuze | Motivatie |
|---|---|
| **Hybride termijn (5 jr + perpetueel trade secrets/personal data)** | 5 jr is voldoende voor LN-comfort op generieke info; perpetueel voor trade secrets sluit aan op 5b Background IP-bescherming; perpetueel voor personal data sluit aan op DPA |
| **Geen marking-eis, default-protection** | Sluit aan op werkbare praktijk (Granola/Slack/email); NLdigital 2025-marktconform |
| **Return-procedure met archief-carve-out** | 7e time-bar tail vereist bewijs-retentie; zonder carve-out kun je claims niet verdedigen |
| **Confidentiality breach onder Super-Cap (2×)** | Reeds vastgelegd in 7b — geen unlimited carve-out (NLdigital 2025-marktconform) |

**Geen nieuwe open vragen aan ICTRecht** — basis-architectuur is markt-conform.

### Sectie 15 — Non-solicitation / Non-poaching

Vastgelegd 2026-05-11. Mutual non-solicitation met focus op werknemers + key contractors. Speciaal aandachtspunt: Daniel (AY Automate) werkt structureel met LN-systemen, dus expliciete contractor-bescherming.

**Vijf sub-componenten met status-markering** (🟢 standaard / 🟡 onderhandelingspunt):

**15a. Scope: werknemers + key contractors** 🟢

Definitie key contractor: "any individual or entity providing services to a Party that performs more than twenty (20) hours of work per month on average over any rolling three-month period, or is expressly identified as a key contractor in any Statement of Work."

Dekt expliciet AY Automate / Daniel + toekomstige Protocol BV-werknemers + freelancers met structurele rol.

Voorbeeld-clausule:

> *"During the term of this Agreement and for a period of twelve (12) months following the termination or expiration of the applicable Statement of Work under which the relevant individual provided services, neither Party shall directly or indirectly solicit, hire, engage, or otherwise enter into an employment, consulting, contracting, or service relationship with any employee or key contractor of the other Party who was involved in the performance of services under this Agreement."*

**15b. Duur: 12 maanden post-SoW-termination** 🟢

Niet vanaf MSA-termination, maar vanaf laatste dag van de specifieke SoW waar de persoon op werkte. NL-marktstandaard (NLdigital 2025); 24 mnd wordt door NL-rechter typisch teruggebracht.

**15c. Mutual** 🟢

Beide kanten beschermd. LN-event-managers vallen onder de bescherming richting LN; Daniel + Narrative-team vallen onder de bescherming richting Protocol. Symmetrie sterkt NL-juridische houdbaarheid.

**15d. Sanctie: liquidated damages 12× bruto maandsalaris per persoon** 🟡

Direct opeisbaar, geen schade-bewijslast nodig. Plus cross-link 7c carve-outs: bij **opzet** (bewust poaching met intentie tot schade) blijft unlimited liability mogelijk.

Voorbeeld-clausule:

> *"In the event of a breach of Section 15a, the breaching Party shall pay to the non-breaching Party, as liquidated damages and not as a penalty, an amount equal to twelve (12) months of the gross monthly compensation (including base salary, bonus, and equity vested in the prior twelve months) of the solicited or hired individual at the time of the breach. The Parties acknowledge that actual damages from such breach are difficult to quantify and that this amount represents a reasonable pre-estimate. This remedy is in addition to, and not in lieu of, any right to seek injunctive relief. In the event of breach involving intentional or grossly negligent conduct, the unlimited liability carve-outs of Section 7c shall apply."*

Status 🟡 want LN-IT-juristen kunnen liquidated damages soms terugschuiven naar werkelijke schade; voorpositie blijft 12× bruto met fallback naar werkelijke schade indien NL-rechter het terugbrengt.

**15e. Carve-outs** 🟢

| Carve-out | Beschrijving |
|---|---|
| **General-pool recruitment** | Publieke job ad (LinkedIn ads, eigen vacaturepagina) — toegestaan, mits niet specifiek getarget op individuen van de andere partij |
| **Unsolicited applications** | Persoon meldt zichzelf zonder benadering — toegestaan, mits aantoonbaar via correspondentie |
| **Pre-MSA-relationships** | Personen die je al kende of waarmee je al een werkrelatie had vóór MSA-signing — uitgezonderd |
| **Beëindigd dienstverband** | Na 6 mnd zonder werk bij de oorspronkelijke partij — carve-out |

Voorbeeld-clausule:

> *"Section 15a shall not apply to: (i) general solicitations made to the public through job postings, recruiter networks, or media advertisements that are not specifically targeted at employees or key contractors of the other Party; (ii) individuals who, without solicitation by the hiring Party, respond to such general solicitations; (iii) individuals with whom the hiring Party had an established employment, consulting, or service relationship prior to the Effective Date of this Agreement, evidenced by documentation; or (iv) individuals whose employment or engagement with the other Party terminated at least six (6) months prior to the hiring Party's first contact regarding employment or engagement."*

---

**Cross-references**:
- **Sectie 7c carve-outs**: opzet/grove schuld blijft unlimited boven liquidated damages
- **Sectie 11f subprocessor listing** (Annex Y van DPA): AY Automate/Daniel staat in subprocessor-listing als sub-processor van Protocol; non-solicitation beschermt persoonsniveau-relatie aanvullend
- **Sectie 14 Confidentiality**: namen + rollen van key contractors vallen onder Confidential Information

---

**Strategische keuzes vastgelegd**:

| Keuze | Motivatie |
|---|---|
| **Scope inclusief key contractors** | Daniel/AY Automate-bescherming is praktisch het meest waardevol voor Wytze |
| **12 mnd post-SoW (niet post-MSA)** | NL-rechtelijk houdbaar; lange MSA-duur mag niet leiden tot oneindige claim-window |
| **Mutual** | Symmetrie versterkt NL-juridische houdbaarheid; LN niet asymmetrisch in voordeel |
| **Liquidated damages 12× bruto** | NL-marktstandaard, direct opeisbaar, geen complexe schade-bewijslast |
| **Carve-out beëindigd dienstverband 6 mnd** | Voorkomt oneindige beperking als persoon zelf al uit dienst is |

**Geen open vragen aan ICTRecht** — standaard NL-marktstructuur.

### Sectie 16 — Assignment, Subcontracting & Affiliates

Vastgelegd 2026-05-11. Blanket assignment binnen Narrative-groep + symmetrisch Customer-side + change-of-control bescherming + subcontracting-regiem.

**Vijf sub-componenten met status-markering** (🟢 standaard / 🟡 onderhandelingspunt):

**16a. Assignment Service Provider — blanket binnen corporate group** 🟢

Voorbeeld-clausule:

> *"Service Provider may assign this Agreement and any Statement of Work, without the consent of Customer, to (i) any Affiliate of Service Provider, (ii) any successor entity arising from a merger, consolidation, or restructuring of Service Provider's group, or (iii) any acquirer of all or substantially all of Service Provider's assets relating to the services hereunder, provided that Service Provider notifies Customer within thirty (30) days. Any other assignment requires Customer's prior written consent, not to be unreasonably withheld."*

Dekt toekomstige restructuring binnen de Narrative-groep (bv. Part of the Narrative B.V. doorzak na 1 juli 2026) zonder herhandtekening. Status 🟢 — NL-marktstandaard.

**16b. Assignment Customer — mirror van 16a** 🟢

Voorbeeld-clausule:

> *"Customer may assign this Agreement and any Statement of Work, without the consent of Service Provider, to (i) any Affiliate of Customer (as defined in Section 1c), (ii) any successor entity arising from a merger, consolidation, or restructuring of Customer's group, or (iii) any acquirer of all or substantially all of Customer's assets relating to the services hereunder, provided that Customer notifies Service Provider within thirty (30) days. Any other assignment requires Service Provider's prior written consent, not to be unreasonably withheld."*

Symmetrie versterkt NL-juridische houdbaarheid. Sluit aan op 1c Authorized Affiliates — 16b regelt assignment buiten de Authorized Affiliate-set.

**16c. Change of Control — termination right bij CoC naar Material Competitor** 🟡

Wat gebeurt bij overname van een van beide partijen:

| Element | Inhoud |
|---|---|
| **Notice plicht** | 30 wd schriftelijke kennisgeving aan andere partij |
| **Termination right** | Andere partij heeft 60 wd termination right indien CoC is naar "Material Competitor" |
| **Material Competitor definitie** | Lijst van 5-10 named entities, opgenomen als Annex bij signing |
| **Voor Service Provider** | Material Competitors = grote AI-consultancies (AnyAI/Mendix-class) + event-tech-vendors die jullie verdienmodel kannibaliseren |
| **Voor Customer** | Material Competitors = direct concurrerende ticketing/event-platforms (Eventbrite-class) |

Voorbeeld-clausule:

> *"In the event of a Change of Control of either Party, the affected Party shall notify the other Party within thirty (30) days. "Change of Control" means any transaction or series of transactions resulting in (i) more than fifty percent (50%) of the voting securities of the Party being held by a single person or coordinated group not previously holding such interest, or (ii) the sale of all or substantially all of the assets of the Party. If the Change of Control results in the affected Party becoming controlled by, or merged into, a Material Competitor of the other Party (as listed in Annex [X] to this Agreement, as updated by mutual agreement no more than once per calendar year), the other Party may terminate this Agreement and all Statements of Work upon sixty (60) days' written notice. Annex [X] (Material Competitors) is attached at signing and may be amended only by written agreement of both Parties."*

Status 🟡 want Material Competitor-lijst is onderhandelingsonderwerp aan signing en kan jaarlijks worden bijgewerkt.

**16d. Subcontracting (niet-data)** 🟢

Data-subcontracting valt onder DPA Annex Y (Sectie 11f). Niet-data subcontracting heeft eigen regiem:

| Categorie | Regiem |
|---|---|
| **Subcontractors >€10k/jaar of structurele rol** | Benoemd in SoW; LN heeft 10wd bezwaarrecht bij ondertekening SoW |
| **Subcontractors <€10k/jaar of ad-hoc** | Vrij — geen notice nodig |
| **Aansprakelijkheid** | Service Provider blijft volledig aansprakelijk voor subcontractor-performance (back-to-back) |

Voorbeeld-clausule:

> *"Service Provider may engage subcontractors to perform portions of the services under this Agreement, provided that: (a) any subcontractor expected to receive fees exceeding ten thousand euros (€10,000) per calendar year, or performing a structural role in the delivery of services under any Statement of Work, shall be identified in the applicable Statement of Work, and Customer shall have ten (10) business days from execution of such Statement of Work to object on reasonable grounds; (b) subcontractors processing Personal Data are governed by the applicable Data Processing Annex; (c) Service Provider remains fully responsible and liable for the acts and omissions of its subcontractors as if they were its own."*

**16e. Authorized Affiliates — cross-reference 1c** 🟢

Al vastgelegd in Sectie 1c: LN-affiliates (Ziggo Dome BV, MOJO BV, AFAS Live BV, e.a.) kunnen onder dezelfde MSA SoW's uitvoeren onder dezelfde voorwaarden. Sectie 16e bevestigt cross-reference zonder herhalen.

Voorbeeld-clausule:

> *"Authorized Affiliates of Customer, as set forth in Section 1c, may enter into Statements of Work under this Agreement on the same terms and conditions, and the rights and obligations under this Section 16 apply equally to such Statements of Work. For the avoidance of doubt, the entry into a Statement of Work by an Authorized Affiliate does not constitute an assignment under Section 16b."*

---

**Cross-references**:
- **Sectie 1c Authorized Affiliates** (LN-side group entities): 16b/16e bouwen voort op deze definitie
- **Sectie 7c carve-outs**: opzettelijke assignment-schendingen blijven unlimited
- **Sectie 11f subprocessor listing** (DPA Annex Y): data-subcontracting separaat geregeld
- **Sectie 14 Confidentiality**: identiteit van subcontractors valt onder Confidential Information
---

**Strategische keuzes vastgelegd**:

| Keuze | Motivatie |
|---|---|
| **Blanket assignment binnen corporate group** | Dekt toekomstige restructuring (bv. doorzak Part of the Narrative B.V. na 1 juli 2026) zonder herhandtekening |
| **Material Competitor-lijst als Annex** | Beide partijen weten precies welke CoC een exit triggert; jaarlijks aanpasbaar |
| **Subcontracting €10k-drempel** | Voorkomt notice-overhead voor ad-hoc freelancers; LN behoudt grip op structurele leveranciers |

**Geen open vragen aan ICTRecht** — standaard NL-marktstructuur.

**Operationele actiepunten** (buiten MSA-tekst):

1. **Stuur KvK-nummer POTP** aan Paul/LN-IT zodra beschikbaar, zodat het vendor-risk-assessment direct op de juiste entiteit kan starten.
2. **Material Competitor-lijst** opstellen vóór ICTRecht-briefing: 5-10 entities per kant.

### Sectie 17 — Force Majeure

Vastgelegd 2026-05-11. Brede definitie met expliciete AI-specifieke uitwerking via cross-link 7l. Inclusief third-party AI/cloud-infrastructure-outages, niet-limitatieve lijst, 60d termination-recht na continue force majeure.

**Vier sub-componenten met status-markering** (🟢 standaard / 🟡 onderhandelingspunt):

**17a. Definitie force majeure — breed met niet-limitatieve lijst** 🟢

Brede formulering met "including but not limited to"-lijst. Voorkomt dat outage van OpenAI/AWS/Vercel buiten definitie valt.

Voorbeeld-clausule:

> *"Force Majeure Event means any event or circumstance beyond the reasonable control of a Party that prevents or materially impairs that Party's performance of its obligations under this Agreement, including but not limited to: (a) acts of war, armed conflict, terrorism, civil unrest, or insurrection; (b) natural disasters, fires, floods, earthquakes, or extreme weather events; (c) epidemics, pandemics, or public health emergencies; (d) acts of government, regulatory actions, or changes in law materially affecting the services; (e) cyberattacks, ransomware events, or denial-of-service attacks on the infrastructure on which the Service Provider reasonably relies; (f) sustained outages or material service degradations of third-party artificial intelligence service providers, cloud infrastructure providers, or other third-party service providers identified in the Data Processing Annex or relevant Statement of Work; (g) internet routing failures, certificate authority outages, or domain name system failures affecting the global infrastructure; and (h) any other event of similar nature beyond the reasonable control of the affected Party."*

**17b. AI-specifieke uitwerking (cross-link 7l)** 🟢

Sectie 7l regelt aansprakelijkheidsbeperking; 17b regelt performance-opschorting.

| Element | Inhoud |
|---|---|
| **Scope** | Outage / materiële service-degradation bij named third-party AI-providers (OpenAI, Anthropic, Google) of cloud-infra (AWS, Supabase, Vercel) — gedefinieerd in DPA Annex Y |
| **Trigger** | >4 uur sustained outage tijdens business hours, of >24 uur cumulatief in 30 dagen |
| **Effect** | Performance-verplichting opgeschort; geen verzuim; SLA-credits niet verschuldigd voor outage-periode |
| **Cure-plicht SP** | Best-effort failover naar alternatieve provider waar technisch mogelijk binnen redelijke termijn — geen verplichting om fundamentele herarchitectuur uit te voeren |

Voorbeeld-clausule:

> *"For the avoidance of doubt, a Force Majeure Event affecting Service Provider expressly includes any sustained outage exceeding four (4) hours during business hours, or twenty-four (24) cumulative hours within any thirty (30) day rolling period, of any third-party artificial intelligence model provider, cloud infrastructure provider, or other named third-party service provider identified in the applicable Statement of Work or Data Processing Annex. During the period of such Force Majeure Event: (a) Service Provider's performance obligations are suspended without breach; (b) no service-level credits or penalties shall accrue against Service Provider; (c) Service Provider shall use commercially reasonable efforts to failover to alternative providers where technically feasible, but is not required to undertake fundamental rearchitecting of the affected services. This Section 17b shall be read in conjunction with Section 7l (third-party AI service liability limitation)."*

**17c. Notice + cure + termination** 🟢

| Element | Termijn |
|---|---|
| **Notice** | 5 werkdagen na event, of korter zodra event-impact duidelijk is |
| **Cure period** | 30 dagen verlenging + nog 30 dagen indien Service Provider aantoonbaar mitigeert |
| **Termination right andere partij** | Na 60 dagen continue force majeure, zonder boete of damages |
| **Pro-rata refund** | Vooruitbetaalde fees voor niet-geleverde periode worden gerefund |

Voorbeeld-clausule:

> *"The Party affected by a Force Majeure Event shall notify the other Party within five (5) business days of becoming aware of such event, providing reasonable details of the nature, expected duration, and impact on its obligations. The affected Party's performance obligations shall be suspended for the duration of the Force Majeure Event, up to a maximum initial period of thirty (30) days, which may be extended for an additional thirty (30) days if the affected Party demonstrates ongoing mitigation efforts. If the Force Majeure Event continues for more than sixty (60) consecutive days, the unaffected Party may terminate this Agreement or any affected Statement of Work upon written notice, without penalty or damages, and the affected Party shall promptly refund any prepaid fees for services not rendered."*

**17d. Mitigation duty + betalingsverplichtingen** 🟢

| Element | Inhoud |
|---|---|
| **Mitigation** | "Redelijke commerciële inspanningen" — geen verplichting tot duurder alternatief of fundamentele herarchitectuur |
| **Betalingsverplichtingen reeds geleverde services** | Blijven van kracht onder force majeure |
| **Betalingsverplichtingen niet-geleverde periode** | Customer niet verplicht te betalen voor periode waarin services niet zijn geleverd |
| **Carve-out** | Betalingsverplichtingen niet algemeen opgeschort onder force majeure (LN-marktconform) |

Voorbeeld-clausule:

> *"The affected Party shall use commercially reasonable efforts to mitigate the impact of the Force Majeure Event and resume performance as soon as reasonably practicable, provided that such efforts shall not require the affected Party to incur disproportionate costs, undertake fundamental rearchitecting of its services, or breach other contractual or regulatory obligations. Notwithstanding any Force Majeure Event, Customer's obligation to pay for services duly rendered prior to or unaffected by the Force Majeure Event shall remain in full force and effect. Customer shall not be obligated to pay for services not rendered due to a Force Majeure Event affecting Service Provider, and Service Provider shall promptly refund any prepaid fees for such non-rendered services."*

---

**Cross-references**:
- **Sectie 7l Third-party AI-API-outage**: aansprakelijkheidsbeperking; 17b regelt performance-opschorting (complementair)
- **Sectie 6 Acceptance**: force majeure pauzeert acceptance-windows
- **Sectie 11f Subprocessor listing (DPA Annex Y)**: definitie "named third-party providers" voor 17b
- **Sectie 4 Fees & payment**: pro-rata refund-mechanisme in 17c/17d

---

**Strategische keuzes vastgelegd**:

| Keuze | Motivatie |
|---|---|
| **Brede definitie met niet-limitatieve lijst** | Voorkomt dat OpenAI/AWS-outage buiten definitie valt (limitatieve lijst = alles erbuiten = verzuim) |
| **AI-specifieke trigger >4u sustained / >24u cumulatief** | Niet open-eindig (LN-comfort), maar realistisch voor AI-architectuur |
| **60d termination right** | NLdigital 2025-marktstandaard; redelijk voor beide partijen |
| **Mitigation = commercieel redelijk, geen herarchitectuur** | Beschermt kleine SP tegen onbetaalbare cure-plicht |
| **Betalingen voor reeds geleverde services blijven** | Voorkomt eindeloze gratis-service-zone bij langdurige force majeure |

**Geen open vragen aan ICTRecht** — standaard NL-marktstructuur, AI-specifieke uitwerking sluit aan op 7l.

### Sectie 18 — Notices & Escalatiepad

Vastgelegd 2026-05-11. Drielaagse escalatie + email-first voor routine + registered mail / qualified e-signature voor material notices. Sluit aan op Sectie 19 dispute resolution mediation-first patroon.

**Vier sub-componenten met status-markering** (🟢 standaard / 🟡 onderhandelingspunt):

**18a. Notice-medium per type** 🟢

| Type notice | Medium |
|---|---|
| **Routine operational** (SoW-coordinatie, status updates, project-communicatie) | Email aan named addresses |
| **Material notices** (termination, material breach, force majeure, change of control, indemnification claim, payment default) | Email **+** registered mail (PostNL of equivalent) **of** qualified electronic signature |
| **Algemene contractuele wijzigingen** (Tier 3 amendments per 6c) | Qualified electronic signature |

Voorbeeld-clausule:

> *"All notices, requests, consents, and other communications required or permitted under this Agreement shall be in writing. Routine operational communications regarding day-to-day performance of the services shall be deemed validly given when sent by email to the addresses specified in Section 18b. Material notices, including notices of termination, material breach, force majeure events, change of control, indemnification claims, and payment default, shall be deemed validly given only when sent by both (i) email to the addresses specified in Section 18b, and (ii) either registered mail (or equivalent carrier providing delivery confirmation) or qualified electronic signature in accordance with eIDAS Regulation (EU) 910/2014. Amendments to this Agreement at Tier 3 amendment level (as defined in Section 6c) shall be executed exclusively by qualified electronic signature."*

**18b. Notice-recipients** 🟢

| Rol | Service Provider | Customer |
|---|---|---|
| **Primary** | Wytze de Haan (wytze@partofthenarrative.com) | Paul Meester (P.Meester@mojo.nl) |
| **Legal / Data** | wytze@partofthenarrative.com (geen separate legal-functie) | Jennifer Quik (J.Quik@ziggodome.nl) — functie-gebonden: "LN-NL Legal Counsel" |
| **Escalation** | Xander Kranenburg (xander@partofthenarrative.com) | "LN-NL Director Legal" (functie) |
| **Address changes** | 10 werkdagen notice-plicht aan andere partij | 10 werkdagen notice-plicht aan andere partij |

Belangrijke nuance: voor LN-Legal wordt functie genoemd, niet alleen Jennifer's persoonlijke email — blijft correct als zij wisselt. Voor Service Provider zijn named individuals correct want kleine team.

Voorbeeld-clausule:

> *"Notices shall be addressed to: For Service Provider: Wytze de Haan (wytze@partofthenarrative.com) for primary and legal/data matters, with escalation to Xander Kranenburg (xander@partofthenarrative.com). For Customer: Paul Meester (P.Meester@mojo.nl) for primary matters, the holder of the role of "LN-NL Legal Counsel" (currently J.Quik@ziggodome.nl) for legal and data matters, with escalation to the holder of the role of "LN-NL Director Legal." Either Party may update its notice addresses by providing ten (10) business days' prior written notice to the other Party."*

**18c. Escalatiepad — 3-laags** 🟢

| Tier | Service Provider | Customer | Trigger |
|---|---|---|---|
| **1. Operational** | Wytze | Paul Meester / Jan Willem Ruijs / Henk (per SoW-context) | Day-to-day issues, SoW-coordinatie, klein-budget-vragen |
| **2. Commercial / Director** | Wytze + Xander | LN-NL Commercial Lead / Account Director | Scope-disputes, fee-disputes, performance-zorgen |
| **3. Executive / Legal** | Xander Kranenburg + Bjorn Veldmeijer (POTP) | LN-NL Director Legal + LN Group Legal | Material breach, termination intent, indemnification claim, dispute resolution preparation |

**Cooldown tussen tiers**: 14 werkdagen — eerst lager escalatie-tier echt geprobeerd voordat hoger.

Voorbeeld-clausule:

> *"Before any matter is escalated to a higher tier, the Parties shall use commercially reasonable efforts to resolve it at the current tier for a period of at least fourteen (14) business days from the date the matter is first formally raised in writing. Escalation to the next tier may proceed earlier upon mutual written agreement, or immediately in cases of material breach, alleged indemnification claim, or imminent material harm. This escalation procedure is a prerequisite to formal dispute resolution under Section 19, except for matters requiring urgent injunctive relief or where one Party has materially breached this Agreement."*

**18d. Effective timing notices** 🟢

| Medium | Effective moment |
|---|---|
| **Email** | Bij ontvangst, of 24 uur na verzending — whichever earlier (LN-marktconform) |
| **Registered mail** | 3 werkdagen na verzending (PostNL-conform) |
| **Qualified electronic signature** | Bij ontvangst |

Out-of-office / vacation: niet verlengend voor effective timing — wel reden voor herhaal-notice via tweede medium.

Voorbeeld-clausule:

> *"A notice shall be deemed validly given and effective: (a) if sent by email, at the earlier of (i) confirmed receipt by the recipient or (ii) twenty-four (24) hours after transmission to a valid email address per Section 18b, provided no bounce or delivery failure notification is received; (b) if sent by registered mail, three (3) business days after dispatch to the addresses per Section 18b; (c) if sent by qualified electronic signature, upon receipt as confirmed by the e-signature service provider. Automatic out-of-office responses, vacation notifications, or similar shall not affect the effective timing of notices, but the sending Party shall be entitled (though not required) to resend the notice via an alternative medium specified in Section 18a."*

---

**Cross-references**:
- **Sectie 6c Tier 3 amendments**: qualified e-signature vereist (consistent met 18a)
- **Sectie 7e Time-bar tail**: notices voor claim-aankondigingen onder 36 mnd post-termination procedure
- **Sectie 16c Change of Control**: notice 30wd procedure cross-link
- **Sectie 17c Force majeure notice**: 5wd procedure cross-link
- **Sectie 19 Dispute resolution**: mediation-first patroon vereist eerst 18c-escalatiepad afgerond

---

**Strategische keuzes vastgelegd**:

| Keuze | Motivatie |
|---|---|
| **Email-first voor routine + dual (email + registered/e-signature) voor material** | Praktisch werkbaar zonder LN-formaliteit op te offeren |
| **Functie-gebaseerde recipients voor LN-Legal** | Blijft correct bij personeelswisselingen |
| **Named individuals voor Service Provider** | Kleine team, geen functie-overhead |
| **14wd cooldown tussen escalatie-tiers** | Voorkomt premature escalatie; sluit aan op 19 dispute resolution |
| **Out-of-office geen verlenging effective timing** | LN-marktstandaard; voorkomt strategisch gebruik van OOO als notice-blokkade |

**Geen open vragen aan ICTRecht** — standaard NL-marktstructuur.

### Sectie 19 — Dispute Resolution

Vastgelegd 2026-05-11. Nederlands recht + Rechtbank Amsterdam + mediation-first 30 dagen + kort geding altijd open + cooling-off 30 dagen voor termination.

**Vier sub-componenten met status-markering** (🟢 standaard / 🟡 onderhandelingspunt):

**19a. Toepasselijk recht + forum** 🟢

| Element | Voorstel |
|---|---|
| **Toepasselijk recht** | Nederlands recht (eerder gevestigd) |
| **Forum (exclusief bevoegd)** | Rechtbank Amsterdam |
| **UN Convention on International Sale of Goods (CISG)** | Expliciet uitgesloten |
| **Conflict-of-laws-regels** | Uitgesloten (Rome I/II) — geen renvoi |

Voorbeeld-clausule:

> *"This Agreement and any non-contractual obligations arising out of or in connection with it shall be governed by and construed in accordance with the laws of the Netherlands, excluding (i) its conflict-of-laws principles, and (ii) the United Nations Convention on Contracts for the International Sale of Goods. The Parties irrevocably submit to the exclusive jurisdiction of the District Court of Amsterdam (Rechtbank Amsterdam) for the resolution of any disputes arising out of or in connection with this Agreement, subject to the dispute resolution procedure set out in this Section 19."*

**19b. Mediation-first 30 dagen** 🟢

Verplichte mediation vóór litigation, na voltooiing escalatiepad (18c Tier 3):

| Element | Inhoud |
|---|---|
| **Trigger** | Na voltooien 18c Tier 3-escalatie zonder oplossing |
| **Mediator** | NMI-erkende mediator, gezamenlijk gekozen; bij geen overeenstemming aangewezen door Mediatorsfederatie Nederland |
| **Window** | Maximum 30 dagen mediation |
| **Kosten** | 50/50 gedeeld |
| **Spoedeisende uitzondering** | Kort geding / injunctive relief blijft beschikbaar — niet geblokkeerd |

Voorbeeld-clausule:

> *"Before commencing any litigation under this Agreement, and following completion of the escalation procedure set out in Section 18c, the Parties shall first attempt in good faith to resolve the dispute through mediation. The Parties shall jointly appoint a mediator accredited by the Nederlandse Mediator Federatie (NMI), or, failing agreement within ten (10) business days, request appointment of a mediator by the Mediatorsfederatie Nederland. The mediation shall take place at a mutually agreed location in the Netherlands and shall be conducted under the Mediation Rules of the NMI. The mediation period shall not exceed thirty (30) days from the date of appointment of the mediator, unless extended by mutual written agreement. The Parties shall share the costs of the mediator equally; each Party shall bear its own legal and other costs. If the dispute is not resolved through mediation, either Party may commence litigation. Notwithstanding the foregoing, this Section 19b shall not preclude either Party from seeking urgent injunctive relief, conservatory measures, or similar provisional remedies before a competent court at any time."*

**19c. Spoedeisende maatregelen (injunctive relief)** 🟢

| Element | Voorstel |
|---|---|
| **Kort geding** | Altijd toegelaten, ongeacht escalatie-tier of mediation-status |
| **Toepassingsbereik** | IP-inbreuk, confidentiality breach, non-solicitation breach, dataverlies, spoedeisende veiligheid |
| **Forum** | Voorzieningenrechter Rechtbank Amsterdam |
| **Cross-border** | Conservatoir beslag in andere jurisdicties toegelaten ter veiligstelling |

Voorbeeld-clausule:

> *"Notwithstanding any other provision of this Agreement, either Party may at any time seek urgent injunctive relief, conservatory measures, attachment orders, or similar provisional remedies before the Voorzieningenrechter of the District Court of Amsterdam or before any other competent court (including for the purpose of conservatory attachment in another jurisdiction) without first completing the escalation procedure of Section 18c or the mediation procedure of Section 19b. Such application shall not constitute a waiver of either Party's rights under this Section 19 with respect to the underlying dispute."*

**19d. Aanvullende mechanica** 🟢

| Element | Voorstel |
|---|---|
| **Kosten litigation** | Loser pays — Rechtbank Amsterdam standaard liquidatietarief (Wet WW + cap) |
| **Class actions** | Uitgesloten — alleen individuele claims tussen MSA-partijen |
| **Settlement-privilege** | Settlement-gesprekken niet toelaatbaar als bewijs — "without prejudice"-bescherming |
| **Cooling-off voor termination** | 30 dagen tussen Tier 3-notice en daadwerkelijke termination |
| **Jury trial waiver** | N.v.t. (NL kent geen jury) |

Voorbeeld-clausule:

> *"In any litigation arising out of or in connection with this Agreement, the prevailing Party shall be entitled to recover its reasonable legal costs and expenses in accordance with the standard liquidation tariffs of the District Court of Amsterdam (liquidatietarief), subject to applicable statutory caps under the Dutch Civil Procedure Act. The Parties waive any right to bring or participate in class action proceedings or representative actions; all claims under this Agreement shall be brought solely on an individual basis. All settlement discussions, offers, and communications between the Parties (whether oral or written) shall be conducted on a "without prejudice" basis and shall not be admissible as evidence in any subsequent legal proceedings, except for the limited purpose of enforcing a concluded settlement agreement. Before terminating this Agreement for cause under Section 3 (Term & Termination), the terminating Party shall provide a final cooling-off period of thirty (30) days following Tier 3 escalation notice under Section 18c, during which the Parties shall attempt good-faith resolution; this cooling-off period shall not apply in cases of insolvency, material data breach, intentional misconduct, or other circumstances making continued performance commercially or legally untenable."*

---

**Cross-references**:
- **Sectie 3 Term & Termination**: 30d cooling-off matched aan termination-procedure
- **Sectie 7c Carve-outs**: opzet/grove schuld/fraude — cooling-off uitzonderingen
- **Sectie 14 Confidentiality, 15 Non-solicitation**: kort geding-scope (acute schending vereist injunctive relief)
- **Sectie 18c Escalatiepad Tier 3**: prerequisite voor mediation 19b
- **Sectie 11 DPA**: AVG-toezichthouder-procedures lopen separaat (niet via 19)

---

**Strategische keuzes vastgelegd**:

| Keuze | Motivatie |
|---|---|
| **Rechtbank Amsterdam (niet Den Haag/Rotterdam)** | LN-NL daar gevestigd; jij operationeel ook in regio; logisch voor beide partijen |
| **Mediation-first vóór litigation** | NL-marktconform; voorkomt onnodige rechtszaken; behoudt commerciële relatie |
| **Kort geding altijd open** | Anders kun je IP/data/confidentiality niet beschermen tijdens mediation-window |
| **Geen arbitrage** | Te duur (ICC/NAI €25k+), niet sneller, geen appeal — niet proportional voor MSA-omvang |
| **CISG expliciet uitgesloten** | Standaard NL B2B-praktijk; CISG is voor goederen, niet voor diensten |
| **Loser pays NL-tarief (geen full indemnity)** | Marktconform; full indemnity zou ICTRecht waarschijnlijk afwijzen onder NL-recht |

**Geen open vragen aan ICTRecht** — standaard NL-marktstructuur.

### Sectie 20 — Miscellaneous

Vastgelegd 2026-05-11. Standaard NL B2B-boilerplate. Acht sub-componenten, allemaal 🟢 standaard. **Contracttaal: Engels** (uitsluitend, geen bilingual versie).

**Acht sub-componenten 20a-20h** (allemaal 🟢):

**20a. Entire agreement**

MSA + DPA + alle SoW's + Annexen + ondergeschikte documenten = complete overeenkomst. Eerdere mondelinge/schriftelijke afspraken vervallen. **Uitzondering**: AV v1.3 voor Traject 1 (training/advisory) + Subscription Order Forms voor Traject 3 (Owned Products) blijven separaat van kracht — die vallen buiten MSA-scope (Sectie 0).

Voorbeeld-clausule:

> *"This Agreement, together with the Data Processing Annex, all Statements of Work executed hereunder, and all other Annexes referenced herein, constitutes the entire agreement between the Parties with respect to the Client Automation services described in Section 0 and supersedes all prior or contemporaneous oral or written agreements, understandings, representations, and warranties relating to such subject matter. For the avoidance of doubt, this Agreement does not supersede or modify (i) Service Provider's General Terms and Conditions version 1.3 governing training, advisory, and consulting services provided by Part of the Narrative B.V. (as referenced in Section 0), or (ii) Subscription Order Forms and Product Terms governing subscription-based access to Service Provider's proprietary multi-tenant products provided by Part of the Protocol B.V. (as referenced in Section 0), which shall continue in full force and effect as separate agreements."*

**20b. Severability**

Voorbeeld-clausule:

> *"If any provision of this Agreement is held to be invalid, illegal, or unenforceable by a court of competent jurisdiction, the remaining provisions shall continue in full force and effect. The Parties shall negotiate in good faith to replace the invalid, illegal, or unenforceable provision with a valid, legal, and enforceable provision that achieves, to the greatest extent possible, the original economic and legal intent of the affected provision."*

**20c. Waiver**

Voorbeeld-clausule:

> *"No failure or delay by either Party in exercising any right, power, or remedy under this Agreement shall operate as a waiver of such right, power, or remedy, nor shall any single or partial exercise preclude any other or further exercise. Any waiver must be in writing and signed by an authorized representative of the waiving Party to be effective, and shall apply only to the specific instance and purpose for which it was given."*

**20d. Counterparts + electronic signature**

Cross-link 18a (qualified e-signature voor material notices). Voorbeeld-clausule:

> *"This Agreement may be executed in one or more counterparts, each of which shall be deemed an original, and all of which together shall constitute one and the same instrument. The Parties agree that this Agreement, any Statement of Work, any Annex, and any amendment hereto may be executed by qualified electronic signature in accordance with Regulation (EU) No 910/2014 (eIDAS) and shall have the same legal force and effect as a handwritten signature on paper."*

**20e. No partnership / joint venture**

Voorbeeld-clausule:

> *"Nothing in this Agreement shall be construed to create a partnership, joint venture, agency, employer-employee, or fiduciary relationship between the Parties. Each Party shall act and remain an independent contractor at all times, and neither Party shall have any authority to bind, represent, or create any obligation on behalf of the other Party, except as expressly authorized in writing."*

**20f. No third-party beneficiaries (met uitzonderingen)**

Voorbeeld-clausule:

> *"Except as expressly provided in this Agreement, no person or entity other than the Parties shall have any rights or remedies under this Agreement. The following limited third-party beneficiary rights are expressly recognized: (i) Authorized Affiliates of Customer (as defined in Section 1c) may enter into and enforce Statements of Work under this Agreement; (ii) Authorized Affiliates of Customer named as beneficiaries under Section 10h (Insurance) may claim under Service Provider's insurance policies in accordance with that Section; (iii) Indemnitees identified in Section 8 (Indemnification) may directly enforce indemnification rights against the Indemnitor. No other person, including without limitation employees, contractors, or end users of either Party, shall have any direct rights of action under this Agreement."*

**20g. Language — Engels** (Wytze-bevestigd 2026-05-11)

Contracttaal: Engels uitsluitend. Geen bilingual versie. Voor NL-rechtbank kan vertaling worden gevorderd op kosten van de vorderende partij.

Voorbeeld-clausule:

> *"This Agreement is executed in the English language only. Any translation into another language is provided for convenience only and shall not be deemed an official version. In the event of any inconsistency between the English version and any translation, the English version shall prevail. The Parties acknowledge that they have had the opportunity to review this Agreement with their respective professional advisors and waive any right to invoke the contra proferentem rule of interpretation. Notwithstanding the foregoing, in any proceeding before a Dutch court, the Parties acknowledge that the court may require translation of this Agreement or relevant portions thereof, the cost of which shall be borne by the Party invoking the proceeding."*

**20h. Headings + construction**

Voorbeeld-clausule:

> *"The headings, captions, and table of contents in this Agreement are inserted for convenience and reference only and shall not affect the interpretation or construction of this Agreement. The Parties acknowledge that this Agreement has been negotiated by both Parties with the benefit of independent professional advice and that no rule of construction or interpretation requiring ambiguities to be resolved against the drafting Party (including the doctrine of contra proferentem under Dutch law) shall apply to this Agreement."*

---

**Cross-references**:
- **Sectie 0 Drie commerciële trajecten**: 20a entire-agreement-uitzondering voor Traject 1 (AV v1.3) en Traject 3 (Subscription)
- **Sectie 1c Authorized Affiliates**: 20f third-party beneficiary-uitzondering
- **Sectie 6c Tier 3 amendments**: 20d e-signature consistent
- **Sectie 8 Indemnification**: 20f Indemnitees als third-party beneficiaries
- **Sectie 10h Insurance named beneficiary**: 20f third-party beneficiary-uitzondering
- **Sectie 18a Notice-medium**: 20d e-signature consistent

---

**Strategische keuzes vastgelegd**:

| Keuze | Motivatie |
|---|---|
| **Entire agreement met expliciete uitzondering AV v1.3 + Subscription** | Voorkomt dat MSA per ongeluk Traject 1 + 3 overschrijft — kerngedachte van drie-trajectenmodel (Sectie 0) |
| **Severability met replacement-duty** | NL-rechtelijk standaard; voorkomt dat single invalid clausule de hele MSA onbruikbaar maakt |
| **Waiver alleen schriftelijk** | Voorkomt impliciete waiver via gedrag — belangrijk voor consistente handhaving |
| **E-signature eIDAS-compliant** | NL-rechtsgeldig; consistent met 18a + 6c |
| **No partnership** | Voorkomt onbedoelde joint employer / partnership-claim |
| **Third-party beneficiaries met expliciete uitzonderingen** | Authorized Affiliates / Indemnitees / Insurance beneficiaries krijgen wel rechten; rest niet |
| **Engels-only contracttaal** | Wytze-keuze 2026-05-11: één versie, geen dubbele drafting, ICTRecht reviewt in Engels |
| **No contra proferentem** | Beide partijen hebben professionele review (jij via ICTRecht, LN via interne legal) — voorkomt later interpretatie-bias |

**Geen open vragen aan ICTRecht** — standaard NL-marktstructuur.

<!-- internal sections (Voortgangsstatus interview, Open vragen / to-do voor Wytze) removed for ICTRecht-facing version — see canonical document in second-brain -->
