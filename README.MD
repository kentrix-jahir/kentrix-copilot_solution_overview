# Kentrix AI Sales Copilot
## Solution Overview & Business Case

---

## 1. In one paragraph

The Kentrix AI Sales Copilot is an always-on consultative pre-sales advisor for
kentrix.ai. A prospect describes a business problem — by typing **or speaking**
— and the copilot diagnoses the underlying decision, recommends the right
Kentrix product with reasoning, cites only verified proof points, and moves a
qualified conversation toward a working session with the sales team.

It runs at **effectively zero inference cost**, and the knowledge it works from
is owned by the business: a non-engineer edits it in a browser and the change
is live on the very next question, with no release and no engineering ticket.

---

## 2. The problem it solves

Kentrix sells ten products across eleven industries: four core products
(Kentrix LSI, GeoMarketeer, Karma, Persona 360) and six purpose-built decision
apps — StorePlannix, StorePerformix and StoreSKUMix for retail, MediaPlannix
for media, and, added to kentrix.ai in October 2026, BranchPlannix and
BranchPerformix for banks. That is a genuinely difficult catalogue for a
prospect to navigate alone.

| Today | With the copilot |
|---|---|
| A visitor lands on a product page and has to self-diagnose which of ten products fits | They describe their problem in plain language and get a reasoned recommendation |
| High-intent visitors leave without identifying themselves | Buying intent is scored every turn; a capture form appears only once earned |
| The sales team learns nothing about what visitors actually ask | Every question, recommendation and outcome is recorded and queryable |
| Product messaging changes require a website release | Marketing edits it in a browser and it is live immediately |
| A demo requires a human, in a timezone, with a calendar slot | The first consultative conversation happens at 2am, unattended |

**The commercial thesis:** the gap between "interested visitor" and "booked
demo" is where pipeline is lost. This closes it with a conversation rather than
a contact form.

---

## 3. What it does

### 3.1 Consultative chat
Answers appear word by word, the way a person types. It diagnoses before
recommending, asks a clarifying question when the need is ambiguous, and
recommends **at most two** products per answer — a four-product answer reads as
a brochure and destroys credibility.

### 3.2 Voice, both directions
Speak a question, hear the answer. Talking over the copilot stops it
immediately, the way a real conversation works. Voice is never the only path to
any action — everything works from the keyboard.

### 3.3 Product cards
When the copilot names a product, a card appears inline: value proposition,
three concrete use cases, and a call to action.

### 3.4 GTM brief generator
Four taps — industry, market, goal, scale — produce a one-page go-to-market
brief: market opportunity, recommended products with reasoning, a sequenced
strategy, success metrics, and a next action. Printable to PDF, and it can be
handed straight into the chat as context for follow-up questions.

### 3.5 Lead capture with intent scoring
Every turn is scored for buying signals. Above a threshold, an inline (never
modal) capture form appears, and the lead reaches the sales team within
seconds.

Nothing is scraped or inferred — the prospect types their own details. The
intelligence is in *when* the form appears. A visitor asking "what is Kentrix?"
never sees it; one who says "we want to pilot this next quarter" does.

### 3.6 Live knowledge editing
A password-protected admin area. Paste a new case study, save, and ask about it
in chat — the copilot already knows. No redeploy, no engineer.

On the hosted copy this is a *live* change, not yet a *permanent* one: the
free hosting tier resets the server's disk whenever the service restarts or
redeploys, which discards edits made in the admin area. Anything meant to last
is also committed to the repository (a two-minute job), and it then survives
every restart. See the risks in §7.

---

## 4. Who it is for

| Persona | What they arrive with | What the copilot does |
|---|---|---|
| **Retail expansion manager** | "We want to open 20 more outlets next year" | Diagnoses a site-selection decision → **StorePlannix**: predicted revenue, ramp curve, cannibalisation |
| **QSR VP Strategy** | "Which of our stores are underperforming, and why?" | Separates a weak store from a weak catchment → **StorePerformix** |
| **Merchandising head** | "We don't know what to stock where" | Range gaps per store → **StoreSKUMix** |
| **D2C marketer** | "Our ROAS is poor, targeting is too broad" | Household-attribute targeting → **Persona 360** |
| **Media agency** | "How do we split budget across channels and prove it worked?" | Channel mix + matched-control measurement → **MediaPlannix** |
| **Bank analytics head** | "How do we grow wallet share in our existing base?" | Ranks the base by propensity → **Karma** |
| **Bank branch network head** | "We want to open 40 branches in UP and Bihar next year" | Predicted deposits, ramp-up and break-even, cannibalisation of existing branches, branch format → **BranchPlannix** |
| **Regional banking head** | "Some branches bring in far fewer deposits than others in similar towns" | Benchmarks each branch against its catchment and true peers, values each fix in deposits → **BranchPerformix** |
| **FMCG sales ops** | "Where is our distribution whitespace?" | Whitespace and TAM → **GeoMarketeer** |
| **Brand strategy** | "Who actually is our buyer?" | 9 lifestyle classes, 40+ archetypes → **Kentrix LSI** |

---

## 5. How it holds up in front of a client

Three properties matter commercially. Each is engineered, tested, and
verifiable.

**The knowledge is owned by the business.** Product messaging, proof points and
objection handling are maintained by marketing, not by engineering. When the
message changes, the change is live immediately — no release cycle.

**It never shows an error.** Whatever fails behind the scenes, the visitor
still gets a useful, on-brand answer and a route to the sales team — within the
same few seconds. **A demo cannot break in front of a client**; that is a
design requirement, not an aspiration.

**It cannot invent things.** It is constrained to state only figures that trace
to a published Kentrix source, and is explicitly barred from inventing pricing,
client names, statistics or contractual terms. We tested this adversarially:
asked to confirm a fabricated price, to name clients, and to abandon its role,
it refused every time.

### 5.1 Data & privacy posture

| Concern | Position |
|---|---|
| Prospect PII | Captured leads go to our database and the sales team. **They are never sent to an AI model.** |
| Audio | Held only for the moment it takes to transcribe. Never written to disk, never logged. |
| Logging | Message contents are never logged; emails and phone numbers are redacted. |
| Lead access | Password-gated. Analytics is gated too — it reports what prospects asked verbatim, which is commercially sensitive. |
| Prompt manipulation | A visitor cannot talk the copilot out of its role or its rules. Verified by adversarial testing. |
| Security review | Independent pre-launch audit completed — see §7. |
| AI provider training | On free tiers, prompts may be used to improve the provider's products. Acceptable for public product marketing; **paid tier should be enabled before this handles real prospect conversations.** This is a configuration change, not a rebuild. |

---

## 6. Running cost

| Component | Cost |
|---|---|
| AI conversation and speech-to-text | **$0** — free tiers |
| Spoken replies | **$0** — runs on the visitor's own device |
| Website hosting | **$0** |
| Application hosting | **$0** — Render free tier |
| Database | **$0** — Supabase free tier |
| **Total** | **$0/month** |

The free application tier idles out after about 15 minutes without traffic and
then takes 30–50 seconds to wake. An uptime monitor that checks the service
every five minutes keeps it awake (on 26 October 2026 it answered its first
request in under a second). Render's **$7/month** plan removes the idle-out
entirely; that is the recommended step before a high-stakes client demo or
public traffic, and it is the only thing the money buys.

At meaningful volume the first paid step lands in **low single-digit dollars
per thousand conversations**. There is no per-seat licence and no vendor
contract.

---

## 7. Current status

**Working and verified end to end:** streaming chat, voice in and out, product
cards, GTM briefs, lead capture and admin visibility, live knowledge editing,
analytics.

| | |
|---|---|
| Time to first word of an answer | **~3–9 seconds** on the primary model, which reasons before it answers (measured 26 Oct 2026: 2.6–5.2 s in test runs, 8.9 s on the live site straight after a deploy); ~4 s when the faster backup answers |
| Speech transcription | **~580ms**, word-accurate |
| Product recommendation accuracy | **23 of 23** on a 23-question benchmark of real prospect phrasing, re-run 26 Oct 2026 after adding the banking products; the six banking and "branch" questions also went 6 of 6 on the primary model |

That third row matters commercially: it is a standing quality check that the
copilot still recommends the **right** product after the messaging is edited.
Wrong recommendations are the failure nobody would otherwise notice, and this
catches them before a prospect does.

### Honest risks

| Risk | Status | Mitigation |
|---|---|---|
| **Free-tier daily limits** | Managed | The service stays available if a provider is unavailable, and tells the visitor how long to wait rather than claiming an outage. The same chain absorbs the primary model's own capacity errors: on 26 October 2026 Google answered "high demand, try later" and the backup model delivered the answer instead. |
| Sustained public traffic | **Open** | Free tiers suit a demo and early traffic. Enable the paid tier before promoting this on the homepage. |
| AI provider training on free tiers | **Open** | Enable the paid tier before handling real prospect conversations. |
| Knowledge accuracy | Managed | Every claim traces to a published Kentrix source; the copilot is barred from inventing figures. |
| Knowledge falls behind the website | Managed | kentrix.ai added two banking products on 13 October 2026; the copilot was updated on 26 October. Checking the site's page list for new products is part of routine upkeep. |
| Free AI models are withdrawn without notice | Managed | Has happened three times, most recently on 26 October 2026: the backup model on OpenRouter was withdrawn by its host while still being listed. The pre-demo model check catches it, and the fix is a configuration change, not a code change. |
| Admin edits on the hosted copy are not permanent | **Open** | The free hosting tier resets the disk on every restart. Until the knowledge base moves into the database (a scoped change), permanent content changes are committed to the repository. |
| Admin access is a shared password | **Accepted for now** | Adequate for a demo and a small internal team. Proper per-user login (SSO) is a scoped, non-structural upgrade. |

---

## 8. Where this goes next

**Phase 2 — after approval**
Returning-visitor recognition · multilingual voice (Hindi, Marathi, Tamil) ·
conversation transcript emailed to the prospect · CRM integration in place of
a direct handoff · per-user admin login with an audit trail

**Phase 3 — website integration**
Embeddable widget for kentrix.ai · floating bubble with voice · white-label
mode for client-facing demos · live high-intent alerts to the sales team ·
the same engine answering questions inside GeoMarketeer about a user's actual
map view

Phase 3 is the one with the largest commercial upside: the same advisor sitting
*inside* the product, answering questions about the customer's own data.

---

## 9. The demo, in four minutes

1. **Land on the page.** Cycling headline, "Talk to our AI".
2. **Speak:** *"We run 80 QSR outlets in Maharashtra and want to open 20 more
   next year."* The answer streams back and is spoken aloud. A **StorePlannix**
   card slides in mid-answer. For a banking audience, say instead *"We are a
   small finance bank and want to open 40 branches in UP and Bihar next
   year"* — a **BranchPlannix** card appears.
3. **Switch to the GTM brief.** Four taps produce a full one-page brief.
4. **Click "Discuss this with AI".** The brief loads as context; ask a
   follow-up.
5. **Open the admin area.** Paste a new case study, save, and ask about it in
   chat. The copilot already knows it.

**Step 5 is the one that lands with a product leader.** It demonstrates that
the system's knowledge is owned by the business, not by engineering — and that
a message change ships in seconds, not sprints.

---

## Live Link :

Copilot : https://kentrix-copilot-web.onrender.com

Admin : https://kentrix-copilot-web.onrender.com/admin
