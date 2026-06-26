# AI Driving School Agent — Build Blueprint

Based on Serge Gatari's 1-Person AI Agency model, adapted for South African driving schools.

---

## 1. The Core Offer (What You Sell)

**Don't sell AI. Sell a result.**

| Instead of | You say |
|---|---|
| "I'll build you an AI chatbot" | "I'll set up a system that never misses a booking lead, even while you're in the car teaching." |
| "Automate your workflow" | "Get 10-15 extra paying students a month without hiring a receptionist." |

**Pricing:**
- Setup: R5,000 – R15,000 once-off (test the market, start lower)
- Monthly retainer: R2,000 – R5,000/mo
- Alternative: "Free first month, then R3,000/mo" — lowers risk for them, builds trust

---

## 2. What the System Does (Behind the Scenes)

```
Student messages on WhatsApp/FB
        ↓
AI Agent replies instantly (in English/Afrikaans/Zulu depending on lead)
        ↓
Asks: Code 8 or Code 10? Manual or auto? Availability?
        ↓
Checks instructor's Google Calendar / Cal.com in real-time
        ↓
Shows available slots
        ↓
Student picks a slot
        ↓
System sends PayFast/Yoco payment link via WhatsApp
        ↓
Payment received → slot locked → confirmation sent
        ↓
Auto-reminder 24h before lesson
```

90% of fulfillment runs on AI agents. You just handle onboarding and check in monthly.

---

## 3. Tools You Already Have (Your Skills Folder)

### n8n — The Engine (Free)
Self-host via Docker. Handles the entire workflow:
- WhatsApp webhook receiver
- Calendar API calls (Google Calendar, Cal.com)
- Payment link generation
- SMS/WhatsApp confirmations
- n8n AI Agent node for the conversational AI piece

### Composio — The Connectors (Free Tier)
Pre-built integrations for:
- WhatsApp Business API
- Google Calendar
- Gmail (follow-ups)
- Payment gateways
- Saves you coding each connector from scratch

### build-premium-website — The Landing Page (Free)
React + Vite + Tailwind + GSAP. Deploy on Vercel free tier.
- One-page site per driving school you partner with
- Showcases their services, prices, and "Book via WhatsApp" CTA
- You can spin one up in a day

### instantly-campaign — The Outreach Machine (~$30/mo)
Cold email sequence to driving school owners.
- 5-email sequence, soft-question CTAs
- Target: "You missed a booking inquiry at 7pm last night..."

### frontend-design — Polish for the Landing Page
Overrides generic AI aesthetics with distinctive design.

---

## 4. What Actually Costs Money

| Item | Cost | Notes |
|---|---|---|
| n8n (self-hosted) | **R0** | Docker on any machine. Oracle Cloud free tier VPS = also R0. |
| WhatsApp Business API (Twilio) | **~R1/student** | ~$0.005 inbound, ~$0.009 outbound per msg. A 10-msg convo = ~R0.70. |
| AI brain (GPT-4o-mini) | **~R0.05/conversation** | OpenAI API. 1,000 leads = ~R50. |
| VPS hosting (if not using free tier) | **R0 – R150/mo** | Oracle free tier is fine. DigitalOcean basic = ~$5/mo = R90. |
| Domain name | **R0 – R100/yr** | .co.za domains are ~R60/yr. Or use a free subdomain to start. |
| Landing page hosting | **R0** | Vercel free tier. |
| Instantly (cold email) | **~R550/mo ($30)** | Only if you run cold email. Skip and use WhatsApp outreach to save. |
| PayFast / Yoco fees | **2-3% per tx** | Standard merchant fees. Passed to the student, not you. |
| **Total startup cost** | **~R0 – R600/mo** | Self-hosted, no Instantly = near zero. |

**You can start for effectively R0 if you self-host n8n and use WhatsApp outreach instead of Instantly.**

---

## 5. Timeline to First Paying Client

| Week | What You Do |
|---|---|
| **Week 1** | Set up n8n self-hosted (Docker). Build the core workflow: WhatsApp trigger → AI reply → calendar check → payment link. Test with your own WhatsApp. |
| **Week 2** | Build landing page template. Sign up for Twilio WhatsApp API + PayFast test account. Polish the AI conversation flow. |
| **Week 3** | Outreach begins. Target 10-15 driving schools/day on WhatsApp/Facebook. Use the "mystery shopper" angle. Refine pitch based on responses. |
| **Week 4-5** | Demo the system live for interested owners. Offer a free 2-week trial. Get 1-2 schools on trial. |
| **Week 6** | First school goes live. Collect R5,000 setup + R2,000 retainer. Now you have a case study. |
| **Week 7-12** | Use the case study to close 5 more schools. Monthly retainer income: R10,000 – R25,000/mo. |

**~4-6 weeks to first revenue if you grind outreach daily.**

---

## 6. How to Find Driving Schools (SA-Specific)

**Target list sources:**
- Google Maps — search "driving school [city]" in Joburg, Cape Town, Durban, Pretoria
- Facebook — join local community groups, search driving schools
- Kijiji / Gumtree SA — classifieds for driving lessons
- Walk testing grounds (Waltloo, AVTS, Green Point, etc.)
- K53 test centres — instructors hang around there

**Signs of a good prospect:**
- Long Google Maps queue / lots of reviews
- Active Facebook page that replies slowly (or auto-reply only)
- "Call us" only — no online booking
- Multiple instructors (means they're busy enough to need this)

---

## 7. The Outreach Scripts

### Cold WhatsApp (after mystery-shopping them)

> "Hey [Name], I messaged your page last night at 7pm to ask about Code 8 prices for my cousin. By the time you replied this morning, most people would've booked elsewhere already.
>
> I built an automated intake agent for SA driving schools that catches these late-night leads, checks instructor availability, and locks in the deposit on WhatsApp instantly.
>
> Are your instructors fully booked right now, or could you take on 10-15 extra students a month?"

### In-person (at a testing ground)

> "Hey chief, quick one. I'm setting up a student-intake system for a couple of driving schools here in the province — it handles the whole booking and PayFast deposit over WhatsApp so instructors don't miss leads while they're in the car.
>
> Before I open it up to [competitor], are your vehicles running flat out right now, or do you have room for more students?"

---

## 8. SA-Specific Nuances

- **Keep it on WhatsApp.** SA students won't download a separate app. Everyone has WhatsApp data.
- **Payment trust is everything.** Use PayFast or Yoco — NOT random EFT requests. The brand recognition of a known payment gateway makes people pay.
- **Language flexibility.** The AI should handle English, Afrikaans, Zulu, and Xhosa prompts. GPT-4o-mini does this well.
- **Load shedding.** Self-hosted n8n on a cloud VPS handles this. Your client's phone still works on cellular data.
- **Pricing sensitivity.** R15,000 upfront is steep for a small driving school. Lead with R0-R2,000 setup + monthly retainer. Prove value first.

---

## 9. Success Odds — Real Talk

**High chance of making it work technically** — your skills folder has all the building blocks.

**Medium chance of making money quickly** — depends entirely on outreach volume. If you message 100 schools, you'll close 3-5. If you message 10, you probably close 0. The SA driving school market is price-sensitive. Don't expect R15,000 setup from your first client. Do expect R2,000-R5,000/month retainer if you deliver results.

**The fastest path to money:**
1. Build the system in Week 1-2
2. Offer a free 2-week trial to one school
3. Get them results (actual booked students)
4. Use that case study to charge the next 5 schools
5. By month 3 you have R15,000+/mo in retainers

**You have the tools. The only variable is how many conversations you start.**

---

## 10. Quick Start Commands

```bash
# n8n self-hosted (Docker)
docker run -it --rm --name n8n -p 5678:5678 -v n8n_data:/home/node/.n8n docker.n8n.io/n8nio/n8n

# Landing page (Vite + React)
npm create vite@latest driving-school-site -- --template react
cd driving-school-site
npm install
npm install gsap lucide-react
npm install -D tailwindcss@3 postcss autoprefixer
npx tailwindcss init -p
```

---

*Generated from your Automation Skills folder analysis + Serge Gatari's 1-Person AI Agency model. Last updated: June 2026.*
