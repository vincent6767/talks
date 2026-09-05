# Why Your Single-Player Game Might Still Want a Backend

Full Indie Monthly — September 2026

Vincent — 10-minute talk + 5-minute Q&A

Rehearsal script — v3

## How to use this script

The main text is written to be read aloud roughly as-is — it's your safety net, not a transcript to memorize word for word. Once you know the beats, paraphrase freely.

[Bracketed grey text] = delivery notes, not spoken.

SLIDE / VISUAL: orange lines = what should be on screen at that moment. A matching cue-card version of this talk was also built with the Claude Design skill for at-a-glance rehearsal.

## Timing map

| Time | Section | Length |
| :-: | :-: | :-: |
| 0:00–1:15 | Hook — the Games Link story | 1:15 |
| 1:15–2:25 | "Single-player" ≠ "offline" | 1:10 |
| 2:25–5:25 | What each kind of online gets you (4 rows) | 3:00 |
| 5:25–7:40 | What's the catch (PII/GDPR + complexity) | 2:15 |
| 7:40–8:45 | Build it or buy it | 1:05 |
| 8:45–9:15 | The ask + close | 0:30 |
| 9:15–10:00 | Buffer / transition to Q&A | 0:45 |

## 1. Hook — the Games Link story

0:00–1:15 · ~75 sec · target ~170 words

SLIDE / VISUAL: Title card. Optional: a photo from Games Link, or leave it blank/black so all eyes stay on you.

[Speak conversationally, like telling a friend about your week. Smile before the first word.]

A month ago I was at Games Link. Great people — honestly, the food alone was worth the trip.

[pause here, let the small laugh land]

I sat in on a talk about building a game studio — going from co-development work to shipping their own projects. At some point the speaker showed a tool they'd built for a narrative game they're working on: it lets players see how their choices stack up against everyone else's, and they're planning to open it up to other local studios later, so nobody else has to build it from scratch.

And I remember sitting there thinking: that's a single-player game. Nothing about that feature needs another player in the room. But it needs a backend — which, full disclosure, is close to what I spent eight years doing at AccelByte: building account, identity, and analytics systems for game studios.

[Say the AccelByte clause briskly, one breath — it's a credibility beat, not a resume recitation. Don't slow down for it.]

So how many of us, working on single-player games right now, have actually stopped to ask whether something like that belongs in our game? That's what I want to talk about today. I'm going to try to convince you to have that conversation early.

[This is the only story-driven beat in the talk — take your time here, it earns you the rest of the talk.]

## 2. "Single-player" ≠ "offline"

1:15–2:25 · ~70 sec · target ~160 words

SLIDE / VISUAL: The words "single-player" and "offline" side by side, with an ≠ between them.

Here's the assumption I want to name, because I think most of us make it without noticing.

We treat "single-player" like it's a synonym for "offline." They're not the same word. One is about how many people are playing. The other is about whether the game talks to a server. But we use them interchangeably, and that's a problem, because it means we make the offline decision by default — not on purpose.

And usually that decision gets made early. Way before launch. Which, honestly, is the cheapest time to make it — if you're making it on purpose instead of by accident. So let's talk about what's actually on the table when you decide "online" is allowed to mean something for a single-player game.

## 3. What each kind of online gets you

2:25–5:25 · ~3:00 · four rows, benefit-first

SLIDE / VISUAL: A 4-row grid/table, revealed one row at a time as you talk through it.

### Row 1 — Conveniences (~30 sec)

First, the simplest one: convenience. Cloud saves. Cross-platform accounts and progression. It sounds small, but it means your player can put the game down on their Steam Deck and pick it back up on their desktop that night. That's not a feature they'll ever thank you for out loud — but it's one they'll absolutely notice the day it's missing.

### Row 2 — LiveOps & content: a reason to reopen the game (~55 sec)

Second: LiveOps and live content. This is what lets you run events, rotate content, and flip a feature on or off — all without shipping a client update. It's the difference between a game you can only patch and a game you can actually operate after launch.

And here's the part I think gets missed for single-player games specifically: it gives a finished, finite game a reason to reopen. Something to argue about with other players, even if you never play together.

Spelunky's Daily Challenge is the same seed for every player, one attempt, and a leaderboard at the end. It's still a single-player run. But suddenly everyone's racing the same cave on the same day. Crypt of the NecroDancer does something similar with its own daily seeded runs. Different mechanism, same idea: a shared, temporary version of a game that's otherwise entirely solo.

[Have the Spelunky daily-challenge screen or NecroDancer leaderboard ready as a visual if you can — it lands better shown than described.]

### Row 3 — Analytics & remote config: shrinking the fix loop (~65 sec)

SLIDE / VISUAL: Two side-by-side timelines: "patch" vs. "server-side." This is the visual money shot of the talk — don't skip building it.

Third, and this is the one I actually think matters most day-to-day: analytics and remote config. Let me walk through a scenario.

Say there's a boss in your single-player game that's too hard, and players are bailing at that fight. Without any of this, here's your loop: you dig through whatever telemetry you do have to confirm there's actually a problem. You find the cause — say, one attack is doing way more damage than intended, and most players are missing the perk that would've mitigated it. You fix the value. You build a new client. You submit that build to the platform holders for QA and certification. That's days to weeks of turnaround, and real engineering cost, to change one number.

Now run that same fix with the value living on the backend instead. You change it server-side. Every player gets the rebalanced fight the next time they load the game. No patch. No cert queue. No waiting.

### Row 4 — Accounts: a relationship that survives the storefront (~30 sec)

And fourth: accounts. A relationship with your player that survives the storefront. If a platform ever disappears from the picture — whether that's a policy change or the player just switching platforms — an account means you didn't lose them. The storefront was never the relationship. It was just where the relationship happened to start.

## 4. What's the catch

5:25–7:40 · ~2:15

SLIDE / VISUAL: "What's the catch?" on its own.

So that's the upside case, and I could keep going. But I'd be doing you a disservice if I stood up here and only told you the good news. There's a catch. Actually, two.

### Catch 1 — You are now storing personal data (~55 sec)

SLIDE / VISUAL: "You are now a company that stores personal data."

The first one: the moment you have accounts, cloud saves tied to a person, or even just analytics that can be linked back to an individual player — congratulations, you're now storing your players' personal data. That means GDPR if you have any players in the EU, and similar laws elsewhere, and those apply to you at your current headcount, not just to studios big enough to have a legal team.

Practically, that means: being upfront about what you collect and why, only collecting what you actually need, having a real answer for what happens when someone asks you to delete their data, and treating child accounts with extra care if minors can play your game. None of that is a startup cost you get to skip because you're small.

### Catch 2 — More to build, more to maintain (~50 sec)

SLIDE / VISUAL: "...and: more to build. more to maintain."

The second catch is just … more surface area. You're adding development and maintenance complexity to your game. And it compounds if you want to support both an offline mode and an online mode, because now you're maintaining two versions of some of your systems, not one. Every category I just walked through is a thing that can go down, drift out of sync, or need a version of itself that works when the network doesn't.

## 5. Build it or buy it

7:40–8:45 · ~1:05

SLIDE / VISUAL: "Build it yourself? Or buy it?"

Okay. So you've heard the upside, you've heard the catch, and maybe I've actually convinced you. Next question: do you build this yourself?

For most of us, no. Use off-the-shelf backend platform. Build your own only when you've got a genuinely unique need — something like your own custom global leaderboard rules that no existing platform supports out of the box.

The honest reason is that it takes a village to build and maintain a platform like this properly — auth, uptime, data compliance, scaling for a launch-day spike. That's not a weekend project, and it's usually not where your two- or three-person team's time is best spent.

## 6. The ask

8:45–9:15 · ~30 sec · close

SLIDE / VISUAL: "Spend an hour. Write down your no's." then a closing/thank-you slide.

So here's the ask. Your game almost certainly doesn't need all four categories on day one. But it's worth spending an hour, early, deciding which of them you actually want — and writing down the deliberate no's. Not the no's you fell into by assuming "single-player" meant "offline." The no's you chose on purpose.

That tool I saw at Games Link two weeks ago? It started as one person's answer to that exact question. I'd love for more of us to be asking it this early.

Thanks.

[Pause. Let it land. Don't rush into Q&A — take a breath and a sip of water while the moderator opens the floor.]

## Anticipated Q&A

[A running scratchpad for your 5-minute Q&A — add to it as more questions come up in rehearsal or from other Full Indie folks. Keep live answers to ~20–30 sec; these are prep notes, not a script to read verbatim.]

**Q: "If I only use the backend for global remote config — not tied to specific players — am I still subject to GDPR?"**

Spoken-ready answer (~30s): "Less than you'd think, but probably not zero. GDPR doesn't care which feature you're using the backend for — it cares whether personal data touches the system anywhere. If your config values are identical for every player, you've killed the biggest risk: no profiles, no targeting, nothing player-linked to protect. But the request that fetches those values still comes from a device with an IP address, and if your host or CDN logs that by default — most do — that's still personal data under GDPR case law. So: a much lighter compliance load, not a full exemption. Worth checking your host's log retention rather than assuming you're in the clear."

[If pressed further: GDPR's territorial scope (Article 3) turns on whether you have EU players at all, not on which feature you built — a studio with EU players is in scope in principle regardless of the remote-config question. The narrower point is that identical, non-targeted config data isn't personal data itself, but IP addresses in server/CDN logs generally are (Breyer v. Germany), so "just remote config" reduces exposure a lot without eliminating it. Point anyone who wants a definitive answer for their setup to a lawyer or privacy consultant — this is general information, not legal advice.]

Sources: Art. 3 GDPR – Territorial scope: https://gdpr-info.eu/art-3-gdpr/ · Is an IP address considered personal data? (TechGDPR): https://techgdpr.com/blog/is-an-ip-address-considered-personal-data/ · EDPB Guidelines 3/2018 on territorial scope: https://www.edpb.europa.eu/sites/default/files/files/file1/edpb_guidelines_3_2018_territorial_scope_after_public_consultation_en_1.pdf

**Q: "Do I need to handle child accounts with extra care if minors can play my game?"**

**Q: "Isn't this a lot of extra work for one person? Isn't it scope creep?"**

That's actually the ask at the end of the talk in disguise. I'm not telling you to build all four rows, I'm telling you to spend an hour deciding which ones you want, on purpose, instead of ending up offline by default. Saying no to all four is a completely legitimate outcome of that hour.

**Q: "Steam already gives me cloud saves, achievements, and leaderboards. Why add a separate backend?"**

For a lot of games, Steam's version is genuinely enough, and I'd say use it. Where it stops working is the moment you want something Steam doesn't offer: cross-platform saves if you're ever on Epic or console, a leaderboard that's harder to fake, or player data you can actually act on instead of just a dashboard number. The four rows are for when you outgrow Steamworks or know upfront you will, not a replacement for it on day one.

**Q: "What's actually free or cheap if I have basically no budget?"**

Most of the platforms people reach for here, things like PlayFab, Supabase, or LootLocker, have free tiers that cover a small studio's player count comfortably. I won't rank them for you, it genuinely depends on which rows you need and what your team already knows. Web dev background points you toward something like Supabase, no backend experience points you toward a game-specific platform. Check current pricing before committing, free tiers change.

**Q: "You spent eight years at AccelByte. Isn't this basically a pitch for your old employer?"**

Fair question to ask directly. There's no product recommendation in this talk, and wherever I do name platforms I list several side by side on purpose. The AccelByte years are why I've seen this problem up close, studios treating "single-player" and "offline" as the same decision, not a reason to buy anything in particular.

**Q: "Can I add this after I've already shipped, or does it need to be day one?"**

Spoken-ready answer (~25s): Technically yes, but it gets harder the longer you wait, especially anything touching save data or player identity, because now you're migrating people instead of just launching with it. The cheapest version of "day one" isn't turning every row on before launch, it's making a few early architecture choices, like keeping tunable values out of hardcoded constants, that keep the door open for later. You can flip the switch when you're ready. You just can't retrofit the door.

**Q: "I have never seen a feature to download player personal data on Steam. What's the catch here? Why should I care then?"**

Spoken-ready answer (~25s): "The short answer: it depends whose system the data lives in. Steam already built account data export and deletion tools, because for data Steam itself stores, like achievements, Steam is the controller. But the moment you plug in your own backend, say for leaderboards, on something like PlayFab, you're now the controller for whatever lives there, even if the only thing you stored was their Steam ID. So if your game uses Steam for achievements and a separate backend for leaderboards, you need your own export and delete flow for that backend. Steam's tooling doesn't cover it. Bottom line: you inherit the obligation the moment the data touches your system, not Steam's."

**Q: "Which backend platform do you recommend?"**

Spoken-ready answer (~25s): "Thanks for the great question. The answer is it depends. It depends on your team's skills, your timeline, your online requirements, and your team's budget. For example, if you're just about to launch your first single-player game, you might start with a backend platform that offers a free tier, such as PlayFab, Supabase, or LootLocker. This lets you explore what a backend platform offers without heavy commitment upfront."

## Appendix — sources & further reading

[Not spoken — background reading / credibility check, and material to draw on during Q&A.]

- AccelByte — "What Is a Game Backend (and What Isn't)": https://accelbyte.io/blog/what-is-a-game-backend-and-what-isnt — the identity / state ownership / untrusted logic / scale framing behind Row 4 and the catch section.
- AccelByte — "Why Your Single-Player Game Needs a Backend": https://accelbyte.io/blog/why-your-single-player-game-needs-a-backend — source for the LiveOps and community-features material in Row 2.
- Microsoft Game Dev — "Why Should a Single-Player Game Have a Backend?": https://developer.microsoft.com/en-us/games/articles/2022/01/why-should-a-single-player-game-have-a-backend/ — source for the telemetry-first framing and the retention curve behind Row 3.
- Spelunky Daily Challenge Mode — Spelunky Wiki: https://spelunky.fandom.com/wiki/Daily_Challenge_Mode_(HD) — confirms same-seed-for-everyone, one attempt per day, final-score leaderboard.
- Crypt of the NecroDancer — Wikipedia: https://en.wikipedia.org/wiki/Crypt_of_the_NecroDancer — daily seeded-run community leaderboards.
- Oxenfree — end-game choice statistics are a known, frequently-discussed feature (see community discussion threads on Steam); exact on-screen wording wasn't independently verified — soften language in the talk if pressed on specifics, or swap for Spelunky/NecroDancer only.
- XCOM 2 — aggregate/global stats surfaced via Steam community stats pages; treat this example as optional colour rather than a load-bearing citation, since a dedicated in-game "global stats" screen wasn't confirmed.
- LootLocker — "Essential Law for Game Devs: A Game Dev's Guide to Data Privacy": https://lootlocker.com/blog/essential-law-for-game-devs-a-game-dev-s-guide-to-data-privacy — source for the practical GDPR obligations list (transparency, lawful basis, data minimization, security, child-data protections).

### Fact-check flags for you

Two examples in Row 2 are backed by strong sources (Spelunky, NecroDancer). The Oxenfree and XCOM 2 references are directionally accurate but the exact UI details weren't confirmed word-for-word during research — keep them as light colour ("games like Oxenfree do something similar with choice stats") rather than quoting specific numbers on stage, unless you verify from your own playthrough before the talk.
