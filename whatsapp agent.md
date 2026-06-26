# WhatsApp Booking Agent — Definitive Build Plan

## The Offer
SA driving school automated intake system via WhatsApp.

**Price:** R8,000 setup + R2,500/month retainer
**Cost to run:** ~R300/month per client
**Target:** 1 client Week 4–5, 5 clients by Month 3

---

## Tech Stack

| Layer | Tool | Cost |
|---|---|---|
| Automation engine | n8n (self-hosted on your AWS EC2) | R0 |
| AI brain | GPT-4o-mini (OpenAI API) | ~R0.05/conversation |
| WhatsApp | Meta Cloud API (official) | Free under 1,000 conv/mo |
| Calendar | Cal.com free tier | R0 |
| Payments | PayFast | Free + 2-3% per tx |
| Landing page | Vercel free tier | R0 |
| Outlook | None — WhatsApp only | R0 |

**Total startup cost:** ~R15 (just the AI API tokens for testing)
**Monthly running per client:** ~R300 (AI + WhatsApp API volume)

---

## Week 1 — Build the Demo (7 Days)

### Day 1 — n8n on AWS EC2
- SSH into your EC2 instance
- Run Docker + n8n:
  ```
  docker run -d --name n8n -p 5678:5678 \
    -v n8n_data:/home/node/.n8n \
    docker.n8n.io/n8nio/n8n
  ```
- Open port 5678 in AWS Security Group
- Confirm n8n loads at `http://YOUR_EC2_IP:5678`
- Time: ~1 hour

### Day 2 — WhatsApp Connection
- Create Meta Developer account at developers.facebook.com
- Create WhatsApp Business App
- Connect a test WhatsApp number
- Send yourself a test message via n8n webhook
- Time: ~2 hours

### Day 3 — 5-Step Intake Flow (Core)
Build this conversation flow in n8n:
1. Student sends "Hi, I want to book lessons"
2. AI asks: "Code 8 or Code 10?"
3. AI asks: "Automatic or manual?"
4. AI asks: "What days work for you?"
5. AI asks: "What's your name?"
6. AI offers available slots from Cal.com

- Use GPT-4o-mini via OpenAI node in n8n
- Test the full conversation with your own phone
- Time: ~3 hours

### Day 4 — Calendar Integration
- Sign up for Cal.com free account
- Create a test event type (e.g. "60min driving lesson")
- Build n8n HTTP Request node to check availability
- Connect it to the WhatsApp flow so AI can ask for real slots
- Time: ~2 hours

### Day 5 — Payment Link + Confirmation
- Sign up for PayFast sandbox account
- Build payment link generation in n8n (PayFast ITN)
- When student picks a slot → send PayFast link via WhatsApp
- When payment received → lock slot in Cal.com → send "booking confirmed" WhatsApp
- Add retry logic (max 3 tries) on PayFast webhook
- Time: ~2 hours

### Day 6 — SSL + Webhook Polish
- Set up Caddy or Certbot on EC2 for HTTPS
- Without HTTPS, Meta and PayFast webhooks will refuse to connect
- Test the full end-to-end flow again
- Time: ~1 hour

### Day 7 — Demo Asset + First Outreach
- Record a 90-second Loom of the full flow running on your phone
- Deploy a one-page landing site on Vercel (React + Tailwind)
- **Send the Loom to 5 driving schools via WhatsApp at 7pm**
- Time: ~3 hours

---

## The WhatsApp Outreach Script

### Step 1 — Mystery Shopper (send at 7pm)
> "Hi, I wanted to ask about getting Code 8 lessons for my younger sister. She's 18, looking to start ASAP. What packages do you have available and how much for a full package?"

### Step 2 — Follow-Up Next Morning (when they reply)
> "Hey [Name], thanks for getting back. I actually sent that at 7pm last night — by the time you replied this morning, most people would've already booked at the next school.
>
> I build an automated student intake system for SA driving schools. It handles WhatsApp inquiries instantly, checks your instructor schedule, and takes a PayFast deposit — even at midnight, even while you're mid-lesson.
>
> You have room for more students, or are your instructors already maxed out?"

### Daily Outreach Target
- Message 10 new schools every day at 7pm
- Follow up with yesterday's 10 in the morning
- 50+ schools contacted by end of Week 2

---

## Client Onboarding Checklist

When a school says yes:

1. Client buys a new SIM (R5 at Checkers) — this becomes their business number
2. Register that SIM as a WhatsApp Business API number (you do this)
3. Set up Cal.com for the client (create their event types, hours)
4. Set up their PayFast account or link to yours
5. Configure call forwarding on their old number → their new business number
6. Test the full flow with a fake booking
7. Go live

Client only needs to do 2 things: buy the SIM and forward calls. You handle everything else.

---

## Month 2–3 — Scale

- Use client #1's results (bookings increased, leads captured) as your case study
- Send the case study + Loom to 50 more schools
- Same price: R8,000 setup + R2,500/mo. No discounts.
- Target 5 active clients

**At 5 clients:**
- Retainer income: R12,500/month
- Setup fees: R40,000 (one-off)
- Monthly costs: ~R1,500
- **Net profit: R11,000/month recurring + R40k setup**

---

## Rules to Follow

- Never use unofficial WhatsApp APIs (no Evolution API, no WAHA) — will get banned
- All pricing questions from students → AI says "The instructor will confirm pricing with you"
- Everything runs on AWS EC2 (not your laptop) — load shedding proof
- If client resists setup fee → offer R4,000 setup + R2,500/mo. Never go lower.
- If client still resists → offer free 14-day trial, then convert to retainer
- No voice agent, no cold email, no extra tools until you have 5+ clients

---

## Quick Reference — n8n Docker Command

```
docker run -d --name n8n -p 5678:5678 \
  -v n8n_data:/home/node/.n8n \
  docker.n8n.io/n8nio/n8n
```

Then set up SSL with Caddy for HTTPS.
