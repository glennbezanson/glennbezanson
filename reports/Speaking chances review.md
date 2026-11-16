# Speaking chances review

*15 November 2026. 112 calendar entries through December 2027, judged from the existing notes only.*

Ratings: 12 strong (six distinct opportunities), 31 possible with a specific ask, 17 pay-to-play, 52 no speaker path. No speaking record is assumed.

## The talk

Spine, from your LinkedIn post: "treat model quality the way you treat uptime. Baseline it. Monitor it. Have a fallback ready." Added since: build error correction ("ECC") or go on-prem; SLAs cover uptime, not behavior.

**Candidate titles**
1. Treat Model Quality Like Uptime: Baseline It, Monitor It, Have a Fallback
2. Uptime Is Not Behavior: What Your Model SLA Doesn't Cover
3. ECC for AI: Error Correction for Models That Drift
4. Nobody Emails You When the Dial Turns Down: ECC or On-Prem?

**Abstract.** Your model provider's SLA covers uptime, not behavior. Published data from nearly 7,000 coding-agent sessions showed reads-before-edits falling 70% in two months, and running a dozen concurrent sessions a day against Azure infrastructure I watched the same slide. This talk shows how to baseline and monitor model quality like uptime, the error correction to build around a hosted model (evals, guardrails, fallbacks), and when on-prem weights are the better answer.

**Lightning version (5-10 minutes).** The AMD session numbers on one slide, your own before-and-after on the next, then the three-step fix: baseline, monitor, fallback.

**Cautions.** The cause (cost-driven dial-back) is your theory and providers dispute it; lead with measured effect and present cause as "how I think it plays out". "Productivity fell to a tenth" is an impression, and Stella Laurenzo's data is hers: BSides, OWASP and DevOpsDays will want your own fixed eval set run over time. Check the figures against the source.

## Where it fits

| Audience | Fit | Why, or the frame it needs |
|---|---|---|
| Platform, DevOps, ML Ops (DevOpsDays, OAI) | Best | "Quality like uptime" is their language. OAI's 2027 focus is evals and agent harnesses |
| Azure rooms (Azure in the ATL, Global Azure, Atlanta Cloud+AI, M365 Community Days) | Best | APIM as the fallback layer and your Foundry tools make it concrete |
| CIO and infrastructure (TAG, Cisco Connect, ALIGN via NetApp) | Good | Lead with "ECC or on-prem"; Dell, Nutanix, NetApp, Cisco as co-presenters |
| Security and audit (OWASP, ISSA, BSides, ISACA, IIA, SecureWorld) | Needs a frame | See below |

From a reseller, the on-prem half reads as a pitch unless it is a neutral framework. OAI and AI Tinkerers ban pitches.

**Security framing.** Your words: "the security play is, when you build security around it and the model degrades." My reading: when a control depends on a hosted model (guardrails, AI code review, SOC triage, agents writing security config), a silent behavior change weakens it with no change record. ISMS angle to consider: the control changed outside change management, so auditors have nothing to test against; baselining and monitoring puts it back under change control. Title for these rooms: *The Control That Changed Itself*.

**Secondary abstracts:** shadow AI discovery (OWASP, DC404, SecureWorld); ISO 27001-to-42001 on a live ISMS (BSides, Geek Week, ISSA); AI gateway on Azure APIM (second submission to Azure rooms).

## Dated submission plan

1. **By Nov 22.** Submit to Azure in the ATL on Sessionize (rolling call, closes Jan 30, 2027); meet John Garland on Nov 17. Meet the OWASP Atlanta organizers on Nov 19. Skip the FabCon CFP (Nov 22): not a Fabric talk.
2. **By Nov 24.** Ask AI Tinkerers to demo (path inferred).
3. **Dec 8.** Atlanta Cybersecurity Holiday Party: ask OWASP, ISSA and DC404 organizers for a Q1 slot; email ISSA (issaatl.org).
4. **Dec 19.** Lightning slot at the Atlanta Generative AI Group; message Fleming Slone on Meetup.
5. **Nov 27.** Do not buy an OAI ticket: speakers attend free.
6. **By Jan 19, 2027.** DevOpsDays Atlanta CFP. The date is aggregator-only; confirm on devopsdays.org now.
7. **January.** Join ISACA Atlanta (ask about Geek Week) and TAG's Data Science & AI Society; email asccent@gtri.gatech.edu.
8. **By Feb 28, 2027.** OAI CFP on Sessionize, 20 minutes; submit after one live run.
9. **Feb to Apr 2027 (estimate).** Global Azure Atlanta and Atlanta Cloud+AI CFPs.
10. **Spring 2027 (estimate).** Ask SecureWorld and your Cisco and NetApp partner managers about slots.
11. **May to late July 2027 (estimate).** BSides Atlanta on pretalx, security framing.
12. **August 2027 (estimate).** M365 Community Days Atlanta CFP.

## Ladder

1. **Lightning slots, Nov-Jan:** Atlanta Generative AI Group, Wednesd.AI, Mond(AI)y Coffee, AI Tinkerers.
2. **Full meetup talk, Q1:** Azure in the ATL, then ISSA or OWASP.
3. **Community conferences, spring:** DevOpsDays (Apr 20-21), Global Azure, Atlanta Cloud+AI.
4. **Larger stages:** OAI (Mar 31 - Apr 1), BSides (October), M365 Community Days (November), then SecureWorld or a TAG panel.

## Pay-to-play or closed

**Sponsorship only (17):** Evanta summits; FutureCon; Official Cybersecurity Summit; Georgia Public Sector Cybersecurity Summit; Millennium Alliance; CDO Magazine; ALIGN AI; HMG Strategy; Atlanta Technology Summit; COLLIDE (inferred).

**No path (52):** vendor stages (Microsoft, Okta, Salesforce, CrowdStrike, Google Cloud and others); GPSEC (competing reseller); invite-only peer rooms (Evanta Inner Circles, IANS, ORBIE); law-firm, university and academic events; Devnexus (CFP closed); socials.

## Where the notes were too thin

No speaker window was found for SecureWorld, Geek Week, Hacker Halted, IIA or any TAG event. OWASP chapter leaders are unnamed. KSU Breakfast Club format, Atlanta AI Week 2027 dates and route, and ASCCENT's return are unknown. Every "possible" on a demo night or partner co-presentation is inferred, not documented.
