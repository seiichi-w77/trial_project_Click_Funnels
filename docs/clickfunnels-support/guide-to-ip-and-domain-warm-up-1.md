# EXPLORE ARTICLES

**Source:** https://support.myclickfunnels.com/docs/guide-to-ip-and-domain-warm-up-1

---

Use this as a roadmap you can adapt based on list size, engagement quality, Email Service Provider (ESP), and your goals.

What is Warm-Up & Why It Matters

A new IP address (or a domain/subdomain with little sending history) has no or little reputation with ISPs. Without reputation, ISPs tend to throttle or block large volumes.

Domain reputation is also critical: even if your IP is clean, a domain with no history (or poor history) will be treated cautiously.

Warm-up builds “trust” gradually: sending small volumes, high engagement, good list hygiene, proper authentication. This allows ISPs to see positive signals (opens, replies, low bounces, low complaints).

Key Prerequisites Before Warm-Up

Make sure the following are in place, or warm-up will be much harder / riskier:

Authentication

Set up SPF correctly.


Set up DKIM.


Implement DMARC (with a monitoring policy initially).



Clean, engaged list

Use lists of people who have recently opted in.

Remove invalid email addresses.

Remove or delay sending to unengaged users (those who haven’t opened/clicked in a long time).


Segment your sending infrastructure

Consider using subdomains (e.g. for marketing vs. transactional). Each subdomain develops its own reputation.


If possible, keep critical/transactional sending separate from marketing/promo streams.


Good content & sending hygiene

Avoid spammy words or overly promotional language.

Include value, personalization, good design/layout.

Ensure unsubscribe options are present and easy.

Monitor complaints/unsubscribes closely.


Warm-Up Plan / Schedule

Here’s a sample / blueprint you can adapt. It shows gradual ramping of send volume, with checks (metrics) at each stage. Use your actual list size, engagement quality, and risk tolerance to decide the rates.

Phase

	

Who to Send To / Criteria

	

Approx Volume

	

Key Goals / Metrics to Watch




Phase 0 (Prep)

	

Internal / very engaged users only (staff, test accounts, recent opt-ins)

	

Very small (e.g. a few dozen to a few hundred)

	

Check authentication works; ensure deliverability, no blocks; get opens/replies.




Phase 1

	

Highly engaged subset of real audience (frequent openers, recent signups)

	

Start small: e.g. 10-100 emails/day, depending on list size.

	

Low bounce, very low complaints; good opens; recipients should reply / move out of spam if misclassified.




Phase 2

	

Broader engaged audience (recently active, but not top tier)

	

Increase gradually day to day or week to week. For example double volume when metrics stay good.

	

Watch bounce rate, complaint rate, spam filtering behavior; monitor ISPs’ feedback (if available).




Phase 3

	

Full intended sending population (excluding known risky / unengaged segments)

	

Ramp to your target regular sending volume

	

Maintain metrics in acceptable thresholds; avoid large spikes; consistently good engagement.

Sample Warm-Up Schedule (IP)

Twilio SendGrid offers a sample incremental warm-up schedule for IPs. The idea is: start very small, then escalate gradually.

Here is a simplified version adapted for illustrative purposes:

Day

	

Approx # of Emails Allowed (if all metrics are good)




Day 1

	

~20




Day 2

	

~40-50




Day 3

	

~70-100




Day 4-7

	

Increase each day (e.g. ~100 → several hundred)




By Day 10-14

	

Move toward low thousands (if metrics are healthy)




Over 20-30 days

	

Ramp to full volume, adjust based on bounce / complaint feedback.

Notes:

If at any point bounce rates, spam complaint rates, or blocks spike, slow the ramp or pause until fixed.

Keep sending at least every few days; letting an IP go idle for 30 days or more may force re-warmup.

Monitoring & Adjusting

You must continually monitor and adjust. Warm-up isn’t “set and forget.”

Track key metrics daily: bounce rate, complaint rate, unsubscribe rate, open rates, click rates.

Use ISP feedback tools (e.g. Google Postmaster Tools, Microsoft SNDS) to monitor reputation.

Look at whether your emails are landing in “Promotions” / “Spam” / being deferred etc.

If you see signs of “trouble” (e.g. a spike in bounces, blocks, complaints), slow down or roll back.

Keep your content stable; don’t change too many variables (sending times, subject style, content style) all at once when still warming up.


Common Pitfalls & How to Avoid Them

Pitfall

	

What Happens / Why It's Bad

	

What to Do Instead




Sending to too big a list too soon

	

ISPs see sudden volume spike → may block or deliver to spam

	

Start with small segments; gradually increase as reputation stabilizes.




Using stale/poor-quality / purchased lists

	

Higher bounce & complaint rates → damages reputation permanently

	

Only send to clean opt-in or recently verified lists. Remove inactive addresses.




Ignoring authentication issues

	

Emails may be more likely to be rejected or marked spam

	

Set up SPF, DKIM, DMARC before sending; test them.




Drastic changes in sending pattern (volume, content)

	

Triggers ISP heuristic filters; sudden negative signals

	

Make changes gradually; maintain consistency in schedule & content.




Low engagement content

	

Poor opens/clicks reduce reputation; recipients may mark as spam

	

Prioritize engaging content; make subject lines and body relevant; encourage replies.

Domain Warm-Up + Subdomains

If your domain is brand new or rarely used, use a domain warm-up process. Similar ramping principles apply.

Consider using subdomains to separate types of sends: marketing, transactional, cold outreach, etc. Reputation on one subdomain doesn’t automatically tarnish another.

Warm-up domain path: start with most trusted recipients (internal, team, recent engaged), then expand.


Rough Timeline

Depending on your starting point (how clean your list is, engagement rates, domain history, etc.), warm-up can take:

Fastest case: ~10–14 days, if the list is clean, the content is good, engagement is high.


Typical case: 3–4 weeks to reach moderate volume, then further weeks to full target.


Riskier / worst case: if the list is poor, content weak, or domain/IP untrusted, it could take 6–8+ weeks (or more) and may require remediations.