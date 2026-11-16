# Speaking chances review

*15 November 2026. 112 calendar entries, November 2026 to December 2027, judged from the existing notes only.*

Ratings: 12 strong (six distinct opportunities), 31 possible with a specific ask, 17 pay-to-play, 52 no speaker path. No prior speaking record is assumed, so the plan builds proof in small rooms first.

## The talk

Your thesis: hosted foundation models are at their best at release and then degrade, across every provider. If you built expecting model X to behave way Y, you either build error correction into the system ("ECC": evals, guardrails, fallbacks, drift detection) or move to on-prem weights that do not change under you. Provider SLAs cover uptime, not behavior.

**Candidate titles**
1. ECC for AI: Building Error Correction for Models That Drift
2. Uptime Is Not Behavior: What Your Model SLA Doesn't Cover
3. Your Model Changed Last Night: Detect It, Absorb It, or Bring It Home
4. Rented Intelligence: Model Drift and the Case For (and Against) On-Prem

**Abstract.** A hosted model's SLA promises availability, not that it will answer next quarter the way it did at launch. This talk shows what behavior drift looks like in a production system, then the two responses: build error correction around the model (fixed evals run over time, guardrails, fallbacks, drift alarms) or run weights you control. It closes with a framework for which to choose, and when.

**Lightning version (5-10 minutes).** One fixed eval set, one hosted model, results plotted over months; then the one check that would have caught it.

**Two cautions.** The cause (deliberate cost-saving) is your inference and providers dispute it, so lead with the observable effect and treat cause as an open question. BSides, OWASP and DevOpsDays will ask for evidence: bring your own measurements, a fixed eval set run over time, if you have them. 
## Where it fits

| Audience | Fit | Why, or the frame it needs |
|---|---|---|
| Platform, DevOps, ML Ops (DevOpsDays, OAI) | Best | A reliability story: an SLO on a dependency you do not control. OAI's 2027 focus is evals and agent harnesses |
| Azure rooms (Azure in the ATL, Global Azure, Atlanta Cloud+AI, M365 Community Days) | Best | They live with model version changes; APIM as the fallback layer and your Foundry tools are concrete |
| CIO and infrastructure (TAG, Cisco Connect, ALIGN via NetApp) | Good | Lead with hosted versus on-prem. Dell, Nutanix, NetApp and Cisco are natural co-presenters |
| Security and audit (OWASP, ISSA, BSides, ISACA, IIA) | Needs a frame | Pitch it as supplier risk and uncontrolled change: the model provider as a critical vendor in an ISO 27001 ISMS |

From a reseller of on-prem infrastructure, the on-prem half reads as a pitch unless it is a neutral framework. OAI and AI Tinkerers ban pitches.

**Secondary abstracts:** shadow AI discovery (OWASP, DC404, SecureWorld); ISO 27001-to-42001 on a live ISMS (BSides, Geek Week, ISSA); AI gateway on Azure APIM (second submission to Azure rooms).

## Dated submission plan

1. **By Nov 22.** Submit to Azure in the ATL on Sessionize (rolling call, closes Jan 30, 2027); meet John Garland on Nov 17. Meet the OWASP Atlanta organizers on Nov 19. Skip the FabCon CFP (Nov 22): not a Fabric talk.
2. **By Nov 24.** Ask AI Tinkerers to demo on Nov 24 or the next night. The demo path is my inference.
3. **Dec 8.** Atlanta Cybersecurity Holiday Party: ask OWASP, ISSA and DC404 organizers for a Q1 slot. Email ISSA (issaatl.org) that week.
4. **Dec 19.** Lightning demo at the Atlanta Generative AI Group; message Fleming Slone on Meetup first.
5. **Nov 27.** Do not buy an OAI ticket. Speakers attend free; you likely qualify for the free Decision Makers pass.
6. **By Jan 19, 2027.** DevOpsDays Atlanta CFP. The date is aggregator-only; confirm on devopsdays.org now.
7. **January.** Join ISACA Atlanta and ask about Geek Week proposals; join TAG's Data Science & AI Society; email asccent@gtri.gatech.edu.
8. **By Feb 28, 2027.** OAI CFP on Sessionize, 20 minutes. Submit by late January, after one live run.
9. **Feb to Apr 2027 (estimate).** Global Azure Atlanta and Atlanta Cloud+AI CFPs.
10. **Spring 2027 (estimate).** Ask SecureWorld, and your Cisco and NetApp partner managers, about slots.
11. **May to late July 2027 (estimate).** BSides Atlanta on pretalx, risk framing.
12. **August 2027 (estimate).** M365 Community Days Atlanta CFP.

## Ladder

1. **Lightning demos, Nov-Jan:** Atlanta Generative AI Group, Wednesd.AI, Mond(AI)y Coffee, AI Builders Alpharetta, AI Tinkerers.
2. **Full meetup talk, Q1:** Azure in the ATL, then ISSA or OWASP.
3. **Community conferences, spring:** DevOpsDays (Apr 20-21), Global Azure, Atlanta Cloud+AI.
4. **Larger stages:** OAI (Mar 31 - Apr 1), BSides (October), M365 Community Days (November), then SecureWorld or a TAG panel.

## Pay-to-play or closed

**Sponsorship only (17):** all Evanta summits; FutureCon; Official Cybersecurity Summit; Georgia Public Sector Cybersecurity Summit; Millennium Alliance assemblies; CDO Magazine; ALIGN AI; HMG Strategy; Atlanta Technology Summit; COLLIDE (inferred).

**No path (52):** vendor stages (Microsoft, Okta, Salesforce, CrowdStrike, Cyera, Google Cloud, ServiceNow, Snowflake); GPSEC, run by a competing reseller; invite-only peer rooms (Evanta Inner Circles, IANS, NTSC/TAG, ORBIE); law-firm events; university and academic events; Devnexus (CFP closed); socials.

## Where the notes were too thin

No speaker window was found for SecureWorld, Geek Week, Hacker Halted, IIA or any TAG event. OWASP chapter leaders are unnamed. KSU Breakfast Club format, Atlanta AI Week 2027 dates and route, and ASCCENT's return are unknown. Every "possible" on a demo night or partner co-presentation is inferred, not documented.
