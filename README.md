# Awesome Bot Recipes [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> 263 tested setups for AI agents and bots: the job, the tools, the steps, the prompt, what it costs and what goes wrong. Maintained by [Supa Humans](https://botrecipe.com).

Every recipe is free to read on [botrecipe.com](https://botrecipe.com). Your agent can also search them over MCP.

## Contents

- [Connect via MCP](#connect-via-mcp)
- [Recipes by category](#recipes-by-category)
- [Sample recipes](#sample-recipes)
- [Full pack](#full-pack)
- [Directory of MCP servers and bots](#directory-of-mcp-servers-and-bots)
- [Contributing](#contributing)

## Connect via MCP

Remote server, Streamable HTTP, no key needed: `https://botrecipe.com/api/mcp`

Tools: `search_recipes`, `get_recipe`, `list_directory`, `buy_pack`. Listed in the [official MCP Registry](https://registry.modelcontextprotocol.io) as `com.botrecipe/recipes`.

### Claude Desktop

Settings → Connectors → Add custom connector, and paste the URL. Or add it to `claude_desktop_config.json` through the `mcp-remote` bridge:

```json
{
  "mcpServers": {
    "botrecipe": {
      "command": "npx",
      "args": ["-y", "mcp-remote", "https://botrecipe.com/api/mcp"]
    }
  }
}
```

### Cursor

Add to `~/.cursor/mcp.json` (or `.cursor/mcp.json` in a project):

```json
{
  "mcpServers": {
    "botrecipe": { "url": "https://botrecipe.com/api/mcp" }
  }
}
```

### Claude Code

```sh
claude mcp add --transport http botrecipe https://botrecipe.com/api/mcp
```

### Any MCP client

Point it at `https://botrecipe.com/api/mcp` with the Streamable HTTP transport. Quick test:

```sh
curl -s https://botrecipe.com/api/mcp -H 'content-type: application/json' \
  -H 'accept: application/json, text/event-stream' \
  -d '{"jsonrpc":"2.0","id":1,"method":"tools/list"}'
```

No MCP? Use [llms.txt](https://botrecipe.com/llms.txt) or [recipes.json](https://botrecipe.com/recipes.json).

## Recipes by category

### Bot Infrastructure

- [AI cost per bot tracker](https://botrecipe.com/recipes/ai-cost-per-bot-tracker/) - Tracks what each bot spends on AI calls each week.
- [Bot instructions version history](https://botrecipe.com/recipes/bot-instructions-version-history/) - Keeps every change to a bot's prompt with the date and reason.
- [Bot output review queue](https://botrecipe.com/recipes/bot-output-review-queue/) - Bots put work in a review queue; a human approves before anything goes out.
- [Bot run log in one sheet](https://botrecipe.com/recipes/bot-run-log-in-one-sheet/) - Every bot writes one row per run so you can see what ran and what failed.
- [Cron health check with a dead man's switch](https://botrecipe.com/recipes/cron-health-check-with-a-dead-man-s-switch/) - Get alerted when a scheduled job stops running, not only when it fails.
- [Error alerts that group repeats](https://botrecipe.com/recipes/error-alerts-that-group-repeats/) - Get one alert per kind of failure, not one per run.
- [Give each bot a one-page job card](https://botrecipe.com/recipes/bot-instructions-one-page/) - Each bot gets a one-page card: its job, what it may do, what it must never do, and who it reports to.
- [Hourly check on all your bots](https://botrecipe.com/recipes/hourly-fleet-check/) - One bot looks at every other bot once an hour and only pings you when something is stuck or failing.
- [Incident write-up from the chat log](https://botrecipe.com/recipes/incident-write-up/) - After an outage, drafts a blameless write-up from the incident chat: timeline, impact, open questions, fixes.
- [Kill switch for every automation](https://botrecipe.com/recipes/kill-switch-for-every-automation/) - A single sheet cell that pauses all your bots when set to OFF.
- [Memory watch for a shared bot box](https://botrecipe.com/recipes/memory-watch/) - A small watcher that logs free memory and pauses non-urgent bots before the box falls over.
- [New bot launch checklist](https://botrecipe.com/recipes/new-bot-launch-checklist/) - A checklist to run before any new bot goes live.
- [Per-task budget for agents](https://botrecipe.com/recipes/agent-task-budget/) - Gives each agent task a cap on model calls, tokens and minutes, stops it when it runs over, and logs why.
- [Prompt test set](https://botrecipe.com/recipes/prompt-test-set/) - A small set of example inputs you run after every prompt change.
- [Retry with backoff for flaky APIs](https://botrecipe.com/recipes/retry-with-backoff-for-flaky-apis/) - Retries failed API calls a few times with growing waits before alerting.
- [Route bot LLM calls through Caveman Cloud](https://botrecipe.com/recipes/route-bot-llm-calls-through-caveman-cloud/) - Send your agents' model traffic through the Caveman Cloud gateway so every call shows up in Traces with its cost, and changes ship only after they pass evals.
- [Secrets in a manager, not in prompts](https://botrecipe.com/recipes/secrets-in-a-manager-not-in-prompts/) - Keeps API keys out of prompts, docs and code.
- [Shared browser lock for many bots](https://botrecipe.com/recipes/shared-browser-lock/) - Lets several bots share one logged-in X browser without clashing.
- [Webhook receiver with signature check](https://botrecipe.com/recipes/webhook-receiver-with-signature-check/) - Accepts webhooks safely by verifying they came from the sender.

### Community

- [Event recap post](https://botrecipe.com/recipes/event-recap-post/) - Posts takeaways from a community event for members who missed it.
- [Member spotlight](https://botrecipe.com/recipes/member-spotlight/) - Features one member a month with a short Q&A they approve.
- [Moderation keyword alerts](https://botrecipe.com/recipes/moderation-keyword-alerts/) - Alerts moderators to messages with risky words.
- [New member welcome](https://botrecipe.com/recipes/new-member-welcome/) - Sends new members a short welcome with three starting points and one question.
- [Questions nobody answered](https://botrecipe.com/recipes/unanswered-questions-sweep/) - Finds questions in your Discord or Slack help channels with no reply after 24 hours and posts them where helpers will see.
- [Unanswered question sweep](https://botrecipe.com/recipes/unanswered-question-sweep/) - Finds help questions nobody answered and gets them answered.
- [Weekly community highlights](https://botrecipe.com/recipes/weekly-community-highlights/) - Posts a short roundup of the best threads each week.

### Content Bots

- [Accessibility pass on posts](https://botrecipe.com/recipes/accessibility-pass-on-posts/) - Checks images have alt text, links say where they go and headings are in order before publishing.
- [Content calendar from goals](https://botrecipe.com/recipes/content-calendar-from-goals/) - Builds a month of topics tied to what you are selling or launching.
- [Content fact-check pass](https://botrecipe.com/recipes/content-fact-check-pass/) - Checks a draft for claims that need a source.
- [Daily scorer that finds weak recipes](https://botrecipe.com/recipes/daily-recipe-scorer/) - Once a day a bot counts worked and failed votes per recipe and drafts a rewrite for the weakest one.
- [Does this sound like me?](https://botrecipe.com/recipes/ai-draft-voice-check/) - Compares a drafted post with 5 of your real posts and marks phrases that do not sound like you, with plainer swaps.
- [Headline variants for a post](https://botrecipe.com/recipes/headline-variants-for-a-post/) - Writes headline options and picks the clearest.
- [Hourly X article engine (Pulse, Writer, Improver)](https://botrecipe.com/recipes/hourly-x-article-engine/) - Three bots that read the market, write, and improve their own rules every hour.
- [Image prompts for blog headers](https://botrecipe.com/recipes/image-prompts-for-blog-headers/) - Writes consistent image prompts so header images match your brand.
- [Interview-style content from a founder](https://botrecipe.com/recipes/interview-style-content-from-a-founder/) - Gets a busy founder's knowledge out through a 20-minute recorded Q&A.
- [One idea, five formats](https://botrecipe.com/recipes/one-idea-five-formats/) - Takes one core idea and plans a blog post, a thread, a short video, an email and a carousel.
- [Public build log](https://botrecipe.com/recipes/build-log-in-public/) - Keep a dated, true list of what you shipped and what broke, and show it on your site.
- [Repurpose old posts](https://botrecipe.com/recipes/repurpose-old-posts/) - Finds your best older posts and refreshes them for today.
- [Style guide for AI drafts](https://botrecipe.com/recipes/style-guide-for-ai-drafts/) - Writes a one-page style guide so every AI draft sounds like you.
- [Turn repeated questions into a post](https://botrecipe.com/recipes/comments-to-faq-post/) - Collects questions from your comments and DMs, groups them, and drafts one post answering the most common.

### Dev

- [Customer update from the changelog](https://botrecipe.com/recipes/release-notes-for-customers/) - Turns the technical changelog into a short customer update for email, your site and social.
- [Flaky test tracker](https://botrecipe.com/recipes/flaky-test-tracker/) - Spots tests that fail and then pass on retry, counts them, and opens one issue per repeat offender.
- [Production error to a useful issue](https://botrecipe.com/recipes/error-to-issue/) - When a new error type appears in production, opens one issue with the stack trace, counts and a marked guess at the cause.
- [Pull request description from the diff](https://botrecipe.com/recipes/pr-description-writer/) - Writes a clear PR description from the diff and linked issue: what changed, why, how to test, risks.
- [Test your README setup weekly](https://botrecipe.com/recipes/readme-setup-test/) - Runs your README's setup steps in a clean container each week so you know the instructions still work.
- [Weekly dependency update batch](https://botrecipe.com/recipes/weekly-dependency-batch/) - Groups minor dependency updates into one weekly pull request and summarizes anything that might break.

### Ecommerce

- [Abandoned cart follow-up with a question](https://botrecipe.com/recipes/abandoned-cart-follow-up-with-a-question/) - Sends one plain follow-up asking what stopped the purchase, instead of a discount.
- [Back in stock waitlist](https://botrecipe.com/recipes/back-in-stock-waitlist/) - Lets visitors join a waitlist for sold-out items and emails them when stock returns.
- [Low stock alert to Slack](https://botrecipe.com/recipes/low-stock-alert-to-slack/) - Posts a message when any product drops below the stock level you set.
- [Product description first drafts](https://botrecipe.com/recipes/product-description-first-drafts/) - Writes first-draft product descriptions from your own bullet notes and tone examples.
- [Product page answers from customer questions](https://botrecipe.com/recipes/product-page-questions/) - Finds what customers ask about a product before buying and adds short answers to the product page.
- [Product photo alt text writer](https://botrecipe.com/recipes/product-photo-alt-text-writer/) - Writes descriptive alt text for product images in bulk.
- [Return reason tracker](https://botrecipe.com/recipes/return-reason-tracker/) - Logs every return reason in one sheet so you can see which product or size causes problems.
- [Review request after delivery](https://botrecipe.com/recipes/review-request-after-delivery/) - Asks for a review a few days after delivery, not at checkout.
- [Sale end reminder](https://botrecipe.com/recipes/sale-end-reminder/) - Sends one reminder to subscribers on the last day of a sale.
- [Shipping delay heads-up](https://botrecipe.com/recipes/shipping-delay-heads-up/) - Finds orders whose tracking has not moved in 4 days and emails the customer before they ask.
- [Supplier reorder email drafts](https://botrecipe.com/recipes/supplier-reorder-email-drafts/) - Drafts a reorder email to your supplier when stock runs low.
- [Wholesale inquiry qualifier](https://botrecipe.com/recipes/wholesale-inquiry-qualifier/) - Asks wholesale leads a few questions automatically before you spend time on a call.

### Education

- [Completion certificate](https://botrecipe.com/recipes/completion-certificate/) - Sends a certificate when a student finishes, with an easy way to share it.
- [First-pass feedback on assignments](https://botrecipe.com/recipes/assignment-feedback-draft/) - Drafts feedback on student work against your rubric, so you edit instead of writing from zero.
- [Inactive student nudge](https://botrecipe.com/recipes/inactive-student-nudge/) - Emails course students who stall for a week with the exact next lesson.
- [Lesson outline from your expertise](https://botrecipe.com/recipes/lesson-outline-from-your-expertise/) - Turns your rough notes into a lesson outline with exercises.
- [Lesson quiz generator](https://botrecipe.com/recipes/lesson-quiz-generator/) - Writes quiz questions from your lesson transcript.
- [Office hours question queue](https://botrecipe.com/recipes/office-hours-question-queue/) - Collects student questions before live office hours so answers are prepared.
- [One-question module feedback](https://botrecipe.com/recipes/one-question-module-feedback/) - Asks one question after each module to find exactly where students get stuck.

### Events

- [Event Q&A collector](https://botrecipe.com/recipes/event-q-a-collector/) - Collects questions before the event so you can prepare real answers.
- [Meetup check-in sheet](https://botrecipe.com/recipes/meetup-check-in-sheet/) - Simple check-in for in-person events using a QR code and form.
- [Post-event feedback form](https://botrecipe.com/recipes/post-event-feedback-form/) - Sends a 3-question feedback form right after the event.
- [Replay follow-up by attendance](https://botrecipe.com/recipes/replay-follow-up-by-attendance/) - Sends different follow-ups to people who attended and people who missed it.
- [Speaker intro writer](https://botrecipe.com/recipes/speaker-intro-writer/) - Drafts short, accurate speaker introductions from their bio.
- [Sponsor prospect list for your event](https://botrecipe.com/recipes/sponsor-prospect-list/) - Builds a list of companies that sponsored similar events, with a contact and a first email draft.
- [Webinar registration to reminder sequence](https://botrecipe.com/recipes/webinar-registration-to-reminder-sequence/) - Registrants get a confirmation, a day-before reminder and a 10-minute reminder.

### Inbox Calendar

- [Agenda request before meetings](https://botrecipe.com/recipes/agenda-request-before-meetings/) - Asks external guests for agenda topics the day before, and adds them to the invite.
- [Calendar buffer guard](https://botrecipe.com/recipes/calendar-buffer-guard/) - Adds breathing room after long meetings so the day does not run late.
- [Follow-up reminder if no reply](https://botrecipe.com/recipes/follow-up-reminder-if-no-reply/) - Reminds you to follow up when a sent email gets no reply.
- [Inbox triage with three labels](https://botrecipe.com/recipes/inbox-triage-labels/) - A bot sorts new email into Needs you, Waiting, and FYI, and never replies on its own.
- [Meeting prep notes](https://botrecipe.com/recipes/meeting-prep-notes/) - Before each meeting, a bot writes a short note: who you are meeting, your last conversation, and what you want from it.
- [Meeting request to booking link reply](https://botrecipe.com/recipes/meeting-request-to-booking-link-reply/) - Drafts a reply with your booking link when someone asks to meet.
- [Newsletter digest instead of inbox clutter](https://botrecipe.com/recipes/newsletter-digest-instead-of-inbox-clutter/) - Moves newsletters out of the inbox into one daily list you read once.
- [Scam and fake invoice flagger](https://botrecipe.com/recipes/scam-invoice-flagger/) - Flags emails that look like payment scams: changed bank details, urgent wire requests, lookalike sender domains.
- [Shared inbox assignment](https://botrecipe.com/recipes/shared-inbox-assignment/) - Assigns shared inbox emails to one owner so none are missed.
- [Time zone check for new meetings](https://botrecipe.com/recipes/meeting-timezone-check/) - When someone in another time zone books a meeting, writes the time in both zones in the invite and flags odd hours.
- [Weekday morning brief](https://botrecipe.com/recipes/weekday-morning-brief/) - Each weekday morning, a bot reads what happened overnight and sends you one short list: what shipped, what broke, what needs you.

### Linkedin

- [Carousel from a blog post](https://botrecipe.com/recipes/carousel-from-a-blog-post/) - Turns a post into a slide document for LinkedIn.
- [Comment-first routine](https://botrecipe.com/recipes/comment-first-routine/) - Spend ten minutes leaving thoughtful comments on posts in your niche before posting your own.
- [Job change congratulations list](https://botrecipe.com/recipes/job-change-congratulations-list/) - Finds customers or contacts who changed jobs so you can congratulate them.
- [LinkedIn post from a customer conversation](https://botrecipe.com/recipes/linkedin-post-from-a-customer-conversation/) - Turns a real customer question into a helpful LinkedIn post.
- [New connection to useful first message](https://botrecipe.com/recipes/linkedin-accept-to-first-message/) - When someone accepts your LinkedIn invite, drafts a short first message based on their headline, with no pitch.
- [Profile visitor follow-up list](https://botrecipe.com/recipes/profile-visitor-follow-up-list/) - Keeps a weekly list of relevant profile visitors to consider connecting with.
- [Reply to every comment on your post](https://botrecipe.com/recipes/linkedin-comment-replies/) - Two hours after you post on LinkedIn, drafts a specific reply to each comment for you to post by hand.

### Local Business

- [Appointment reminders](https://botrecipe.com/recipes/appointment-reminders/) - Cuts no-shows with reminders that make rescheduling easy.
- [Google Business Profile weekly post](https://botrecipe.com/recipes/google-business-profile-weekly-post/) - Posts one update a week to your Google profile.
- [Missed call text back](https://botrecipe.com/recipes/missed-call-text-back/) - Texts callers you missed with a booking link and a promise to call back.
- [Quote request to estimate draft](https://botrecipe.com/recipes/quote-request-to-estimate-draft/) - Turns a web quote form into a ready-to-review estimate document.
- [Review card at checkout](https://botrecipe.com/recipes/review-card-at-checkout/) - Hands customers a small card with a QR code that opens your review page.
- [Seasonal service reminder](https://botrecipe.com/recipes/seasonal-service-reminder/) - Reminds last year's customers before their seasonal service is due.
- [Voicemail to a job card](https://botrecipe.com/recipes/voicemail-to-job-card/) - Turns voicemail transcripts into a short job card: name, number, what they need, where, and how urgent.

### Money Admin

- [Contract renewal tracker](https://botrecipe.com/recipes/contract-renewal-tracker/) - Reminds you before contracts and annual plans renew.
- [Expense category suggester](https://botrecipe.com/recipes/expense-category-suggester/) - Suggests a bookkeeping category for each new transaction based on your past choices.
- [Mileage and trip log](https://botrecipe.com/recipes/mileage-and-trip-log/) - Logs business trips from calendar events with locations.
- [Month-end close checklist](https://botrecipe.com/recipes/month-end-close-checklist/) - A recurring checklist that walks you through closing the books each month.
- [Quote to invoice handoff](https://botrecipe.com/recipes/quote-to-invoice-handoff/) - When a client accepts a quote, an invoice draft is created automatically.
- [Receipt capture to a sheet](https://botrecipe.com/recipes/receipt-capture-to-a-sheet/) - Forward any receipt email and it lands as a row with vendor, date and amount.
- [Receipt photo to expense](https://botrecipe.com/recipes/receipt-photo-to-expense/) - Snap a paper receipt and it becomes an expense row.
- [Receipts to your bookkeeper automatically](https://botrecipe.com/recipes/receipts-to-bookkeeper/) - Labels receipt emails as they arrive and forwards them to your bookkeeping tool's email-in address.
- [Sales tax threshold watcher](https://botrecipe.com/recipes/sales-tax-threshold-watch/) - Totals sales by US state or country and warns you when you get close to a level where you may need to register for tax.
- [Subscription audit](https://botrecipe.com/recipes/subscription-audit/) - Lists every recurring charge so you can cancel what you do not use.
- [Supplier bills to a sheet](https://botrecipe.com/recipes/bill-pdf-to-sheet/) - Reads invoices sent to a bills inbox and adds vendor, dates, amounts and tax to a sheet for review.
- [Tax set-aside reminder](https://botrecipe.com/recipes/tax-set-aside-reminder/) - When a payment arrives, reminds you to move a share to a tax savings account.
- [Unpaid invoice nudges](https://botrecipe.com/recipes/unpaid-invoice-nudges/) - Sends polite reminders for invoices that pass their due date.
- [Weekly cash runway check](https://botrecipe.com/recipes/weekly-cash-runway/) - Each week, works out how many months your cash lasts at the current burn and shows the change.

### Newsletter

- [Issue archive to SEO pages](https://botrecipe.com/recipes/issue-archive-to-seo-pages/) - Publishes each newsletter issue as a web page so it can be found in search.
- [Newsletter link roundup builder](https://botrecipe.com/recipes/newsletter-link-roundup-builder/) - Collects links you save during the week into a draft newsletter section.
- [Newsletter to social thread converter](https://botrecipe.com/recipes/newsletter-to-social-thread-converter/) - Turns each issue into a short post thread for X or LinkedIn.
- [Reader question mailbag](https://botrecipe.com/recipes/reader-question-mailbag/) - Collects reader questions into a sheet and drafts a Q&A section.
- [Referral milestone emails](https://botrecipe.com/recipes/referral-milestone-emails/) - Thanks readers when their referrals reach a milestone, with no gimmicks.
- [Sponsor report after each placement](https://botrecipe.com/recipes/sponsor-placement-report/) - Three days after a sponsored issue, sends the sponsor a short report with the real clicks and opens from your email tool.
- [Sponsor slot tracker](https://botrecipe.com/recipes/sponsor-slot-tracker/) - Tracks newsletter sponsor bookings, copy due dates and invoices in one table.
- [Subject line shortlist](https://botrecipe.com/recipes/subject-line-shortlist/) - Writes subject line options from your issue and checks them against your past best ones.
- [Subscriber cleanup every quarter](https://botrecipe.com/recipes/subscriber-cleanup-every-quarter/) - Finds subscribers who have not opened in a long time and sends one "still want this?" email.
- [Welcome sequence that asks one question](https://botrecipe.com/recipes/welcome-sequence-that-asks-one-question/) - New subscribers get a welcome email that asks what they want help with, and replies get tagged.

### Ops

- [Client onboarding file chaser](https://botrecipe.com/recipes/client-onboarding-file-chaser/) - After a client signs, sends one checklist of what you need and reminds them only about the items still missing.
- [How-to guide from a screen recording](https://botrecipe.com/recipes/sop-from-screen-recording/) - Turns a quick screen recording of you doing a task into a written step-by-step guide someone else can follow.
- [Monday metrics snapshot](https://botrecipe.com/recipes/monday-metrics-snapshot/) - Every Monday, puts the 5 numbers you care about in one message, next to last week's.
- [New hire first week plan](https://botrecipe.com/recipes/new-hire-first-week/) - Builds a day-by-day first week plan, a tool access list and an intro message from one form about the new hire.
- [Software renewal radar](https://botrecipe.com/recipes/software-renewal-radar/) - Keeps a list of every paid tool and warns you 30 and 7 days before each renewal so you can cancel or renegotiate.

### Payments

- [Chargeback evidence pack](https://botrecipe.com/recipes/chargeback-evidence-pack/) - When you get a dispute, gathers the receipt, delivery proof, emails and access logs into one document ready to submit.
- [Checkout test with a test card](https://botrecipe.com/recipes/checkout-test-with-a-test-card/) - Tests your checkout end to end after any change.
- [Failed payment recovery email](https://botrecipe.com/recipes/failed-payment-recovery-email/) - Emails customers when their card fails with a link to update it.
- [Match payouts to bank deposits](https://botrecipe.com/recipes/payout-bank-match/) - Matches each Stripe payout to the bank deposit and lists the fees and refunds inside it, so your books agree.
- [New sale note in Slack](https://botrecipe.com/recipes/new-sale-note-in-slack/) - Posts each new sale to a team channel so a small team stays close to what sells.
- [One sponsor slot with a rising price](https://botrecipe.com/recipes/sponsor-slot-price-step/) - Sell one sponsor spot on every page with a payment link. After each sale, raise the price by a fixed step.
- [Past-due follow-up list](https://botrecipe.com/recipes/past-due-follow-up-list/) - Each week, lists past-due customers for a short personal email.
- [Payment link per offer](https://botrecipe.com/recipes/payment-link-per-offer/) - Creates a separate Stripe payment link for each offer so you can see which one sells.
- [Payout reconciliation](https://botrecipe.com/recipes/payout-reconciliation/) - Matches Stripe payouts to bank deposits monthly.
- [Refund reason log](https://botrecipe.com/recipes/refund-reason-log/) - Logs every refund with a reason so product and expectation problems show up.
- [Sell a digital kit with a payment link](https://botrecipe.com/recipes/stripe-payment-link-kit/) - Sell one digital product with a payment link and an automatic thank-you page. No store needed.
- [Spending cap for bots that can buy things](https://botrecipe.com/recipes/spend-cap-guard/) - Before a bot buys a domain, ad or tool, it checks the price against a cap you set and stops if it is over.
- [Webhook-driven access granting](https://botrecipe.com/recipes/webhook-driven-access-granting/) - Grants access to a product when payment succeeds, using Stripe webhooks.

### Personal

- [Bills on your calendar, with amounts](https://botrecipe.com/recipes/bills-on-calendar/) - Puts every recurring bill on your calendar with the amount and reminds you 3 days before the ones that are not on autopay.
- [Doctor visit prep note](https://botrecipe.com/recipes/doctor-visit-prep/) - Before an appointment, turns your notes into one page: symptoms with dates, medicines, and your questions.
- [Free trial cancel reminder](https://botrecipe.com/recipes/trial-cancel-reminder/) - When a free trial starts, adds a reminder 2 days before it charges, with a link to cancel.
- [Job application tracker that follows up](https://botrecipe.com/recipes/job-application-tracker/) - Logs each job you apply to, saves the posting text, and reminds you to follow up after 7 days.
- [Remember what you read](https://botrecipe.com/recipes/highlights-spaced-review/) - Sends you 3 of your book and article highlights each morning, spaced over weeks, each as a short question.
- [Sunday family brief](https://botrecipe.com/recipes/sunday-family-brief/) - Every Sunday evening, sends the household one message with the week's events, pickups and appointments, and who handles each.

### Product

- [Bug triage labels](https://botrecipe.com/recipes/bug-triage-labels/) - Sorts incoming bugs by how many users they block.
- [Churn reason follow-up](https://botrecipe.com/recipes/churn-reason-follow-up/) - Asks customers who cancel one short question about why.
- [Feature request tally](https://botrecipe.com/recipes/feature-request-tally/) - Collects feature requests from email, chat and calls into one counted list.
- [Feedback tagger across channels](https://botrecipe.com/recipes/feedback-tagger/) - Pulls feedback from support, reviews and calls into one sheet, tagged by feature and type, so you can count requests honestly.
- [Interview notes synthesis](https://botrecipe.com/recipes/interview-notes-synthesis/) - Turns several interview notes into themes with quotes.
- [Onboarding drop-off email](https://botrecipe.com/recipes/onboarding-drop-off-email/) - Emails users who signed up but never did the key first step.
- [Pricing page FAQ from real objections](https://botrecipe.com/recipes/pricing-objection-faq/) - Collects the questions people ask before buying and turns the top 6 into a FAQ under your prices.
- [Pricing page question log](https://botrecipe.com/recipes/pricing-page-question-log/) - Logs every question about pricing to improve the page.
- [Public roadmap from the request list](https://botrecipe.com/recipes/public-roadmap-from-the-request-list/) - Publishes a simple roadmap of what is planned, in progress and shipped.
- [Release notes from merged changes](https://botrecipe.com/recipes/release-notes-from-merged-changes/) - Drafts customer-facing release notes from your change list.
- [User interview scheduler](https://botrecipe.com/recipes/user-interview-scheduler/) - Invites recent signups to a short interview and books it.

### Productivity

- [Bookmark triage](https://botrecipe.com/recipes/bookmark-triage/) - Turns a pile of saved links into read, act or delete.
- [Daily plan from your task list](https://botrecipe.com/recipes/daily-plan-from-your-task-list/) - Each morning, picks three priorities from your tasks and calendar.
- [Decision log](https://botrecipe.com/recipes/decision-log/) - Records decisions with the reason, so you stop relitigating them.
- [Inbox zero assistant rules](https://botrecipe.com/recipes/inbox-zero-assistant-rules/) - Sets up filters so newsletters, receipts and notifications skip your inbox.
- [Meeting action items that get done](https://botrecipe.com/recipes/meeting-action-items/) - After a meeting, pulls action items with owners and dates from the notes and checks in on each before it is due.
- [Meeting-free focus block guard](https://botrecipe.com/recipes/meeting-free-focus-block-guard/) - Blocks focus time on your calendar each week before meetings fill it.
- [Personal CRM nudges](https://botrecipe.com/recipes/personal-crm-nudges/) - Reminds you to check in with people you care about professionally.
- [Reading notes to flashcards](https://botrecipe.com/recipes/reading-notes-to-flashcards/) - Turns your book or article highlights into review questions.
- [Travel prep packet](https://botrecipe.com/recipes/travel-prep-packet/) - Builds a one-page trip summary from confirmation emails.
- [Voice memo to tasks](https://botrecipe.com/recipes/voice-memo-to-tasks/) - Record a voice note on a walk and get a clean task list.
- [Weekly review prompt](https://botrecipe.com/recipes/weekly-review-prompt/) - A short Friday review that closes the week and sets up the next.

### Research

- [Competitor hiring signals](https://botrecipe.com/recipes/competitor-hiring-signals/) - Watches competitor careers pages to see where they are investing.
- [Customer language mining](https://botrecipe.com/recipes/customer-language-mining/) - Collects the exact words people use about a problem so your copy sounds like them.
- [Find real complaints in your niche](https://botrecipe.com/recipes/reddit-pain-point-miner/) - Collects posts where people complain about a problem you solve and groups them by pain, with exact quotes and links.
- [Industry news morning brief](https://botrecipe.com/recipes/industry-news-morning-brief/) - A short daily brief from a few trusted sources.
- [Interview recruiting from your list](https://botrecipe.com/recipes/interview-recruiting-from-your-list/) - Finds customers to interview from your email list.
- [Literature scan with sources](https://botrecipe.com/recipes/literature-scan-with-sources/) - Gathers sources on a question and summarizes with links you check.
- [Meeting research brief](https://botrecipe.com/recipes/meeting-research-brief/) - Builds a one-page brief on a company and person before an important meeting.
- [Pricing page tracker for competitors](https://botrecipe.com/recipes/pricing-page-tracker-for-competitors/) - Watches competitor pricing pages for changes.
- [Recruit 5 users for interviews](https://botrecipe.com/recipes/interview-recruit-message/) - Writes a short, specific ask for a 20-minute call to one group of users, with a booking link and a clear thank-you.
- [Search trend check](https://botrecipe.com/recipes/search-trend-check/) - Checks whether interest in a topic is growing before you build content or a product around it.
- [Survey answer summary](https://botrecipe.com/recipes/survey-answer-summary/) - Summarizes open-ended survey answers into themes with counts and quotes.
- [Tool pricing change watch](https://botrecipe.com/recipes/pricing-page-change-watch/) - Watches the pricing pages of tools you depend on and tells you in plain English when a plan or limit changes.
- [Watch competitor pages for changes](https://botrecipe.com/recipes/competitor-page-watch/) - A bot checks a few competitor pages each week and tells you only what changed.

### Reviews

- [Google review alert and reply draft](https://botrecipe.com/recipes/google-review-alert-and-reply-draft/) - Get alerted to new Google reviews and a draft reply in your voice.
- [Negative review escalation](https://botrecipe.com/recipes/negative-review-escalation/) - Sends 1-2 star reviews straight to the owner with the customer record.
- [Review response time tracker](https://botrecipe.com/recipes/review-response-time-tracker/) - Logs how long it takes to reply to each review.
- [Review theme report](https://botrecipe.com/recipes/review-theme-report/) - Summarizes monthly reviews into what customers love and what they complain about.
- [Testimonial request after a win](https://botrecipe.com/recipes/testimonial-request-after-a-win/) - Asks for a testimonial right after a customer reports a good result.

### Sales Leads

- [Call notes to CRM](https://botrecipe.com/recipes/call-notes-to-crm/) - Turns your sales call notes into CRM fields and next steps.
- [Cold email reply sorter](https://botrecipe.com/recipes/cold-email-reply-sorter/) - Sorts replies to your outreach into Interested, Not now, Wrong person and Unsubscribe, and drafts the next step for each.
- [Demo no-show rescue in 10 minutes](https://botrecipe.com/recipes/demo-no-show-rescue/) - If a prospect has not joined a booked call 10 minutes in, sends one calm message with two new times.
- [Find people asking for help](https://botrecipe.com/recipes/lead-question-finder/) - A bot searches for people asking a question you can answer and lists them for you to reply to.
- [Follow up after a missed booking](https://botrecipe.com/recipes/calendly-no-show-followup/) - When someone books but does not show, a bot drafts a short, kind follow-up with a new booking link.
- [Inbound lead enrichment](https://botrecipe.com/recipes/inbound-lead-enrichment/) - Adds company size and website details to every form lead.
- [Lead reply within minutes](https://botrecipe.com/recipes/lead-reply-within-minutes/) - Notifies the right person instantly when a hot lead fills a form.
- [Lost deal reason log](https://botrecipe.com/recipes/lost-deal-reason-log/) - Records why deals are lost so you can spot patterns and fix them.
- [Meeting-booked prep note](https://botrecipe.com/recipes/meeting-booked-prep-note/) - After someone books a sales call, sends a short note asking for their goal.
- [Proposal first draft](https://botrecipe.com/recipes/proposal-first-draft/) - Drafts a proposal from call notes and your template.
- [Proposal sanity check](https://botrecipe.com/recipes/proposal-sanity-check/) - Before a proposal goes out, checks totals, dates, names and scope against your call notes and flags mismatches.
- [Quote follow-up ladder](https://botrecipe.com/recipes/quote-follow-up-ladder/) - After you send a quote, drafts three short, different follow-ups for day 2, 5 and 12, and stops the moment they reply.
- [Referral ask after a customer win](https://botrecipe.com/recipes/referral-ask-after-a-customer-win/) - Asks happy customers for one introduction right after they hit a result.
- [Signup research card for founders](https://botrecipe.com/recipes/signup-research-card/) - When someone signs up with a work email, reads their company homepage and writes a 5-line card so your first message is relevant.
- [Stale deal sweep](https://botrecipe.com/recipes/stale-deal-sweep/) - Every Monday, lists open deals with no activity in two weeks so each one gets a decision.
- [Win and loss interviews](https://botrecipe.com/recipes/win-loss-interviews/) - A ready 15-minute interview script and summary prompt for customers who just bought or just said no.

### Seo

- [Broken link sweep](https://botrecipe.com/recipes/broken-link-sweep/) - Finds broken links on your site every month so readers do not hit dead ends.
- [Competitor content gap list](https://botrecipe.com/recipes/competitor-content-gap-list/) - Lists topics competitors cover that you do not, to plan content.
- [Content refresh queue](https://botrecipe.com/recipes/content-refresh-queue/) - Finds older posts that still get impressions but have slipping clicks, and queues them for an update.
- [FAQ schema from real questions](https://botrecipe.com/recipes/faq-schema-from-real-questions/) - Adds an FAQ section built from questions customers actually asked.
- [Fix titles that are seen but not clicked](https://botrecipe.com/recipes/low-ctr-title-fixer/) - Finds pages with many search impressions but few clicks and drafts better titles to test.
- [Image compression check](https://botrecipe.com/recipes/image-compression-check/) - Finds heavy images slowing your pages and compresses them.
- [Internal link finder](https://botrecipe.com/recipes/internal-link-finder/) - Finds places in older posts where you should link to a new post.
- [Keyword to outline drafter](https://botrecipe.com/recipes/keyword-to-outline-drafter/) - Turns a target search phrase into an outline that answers what searchers want.
- [Programmatic page quality gate](https://botrecipe.com/recipes/programmatic-page-quality-gate/) - Before publishing many generated pages, checks each one has enough unique, useful content.
- [Search Console weekly winners and losers](https://botrecipe.com/recipes/search-console-weekly-winners-and-losers/) - Each week, lists pages whose search clicks rose or fell most.
- [Search snippet preview](https://botrecipe.com/recipes/search-snippet-preview/) - Checks how titles and descriptions will look in search before publishing.

### Site Ops

- [404 page that helps](https://botrecipe.com/recipes/404-page-that-helps/) - A not-found page with search and top links, plus a log of missing URLs to redirect.
- [Backups you have restored once](https://botrecipe.com/recipes/backups-you-have-restored-once/) - Backs up your site and database and proves restore works.
- [Connect a new domain without downtime](https://botrecipe.com/recipes/domain-connect-checklist/) - Buy a domain, point it at your site and check it, step by step, so nothing breaks.
- [Email signup that stays clean](https://botrecipe.com/recipes/email-signup-honeypot/) - A simple signup box that saves emails privately and quietly drops bot signups.
- [Form spam honeypot](https://botrecipe.com/recipes/form-spam-honeypot/) - Adds a hidden field that bots fill and humans do not.
- [Lighthouse check in CI](https://botrecipe.com/recipes/lighthouse-check-in-ci/) - Runs a performance and accessibility check on each deploy preview.
- [Make your site readable for agents](https://botrecipe.com/recipes/agent-readable-site/) - Publish a plain list of your pages, a JSON feed and an agents file so AI agents can use your site.
- [One vote per person per version](https://botrecipe.com/recipes/one-vote-per-version/) - A 'Did this work?' button that lets each person or agent vote once per recipe version, so counts stay honest.
- [Preview first, then production](https://botrecipe.com/recipes/preview-first-deploys/) - Your bot ships every site change to a private preview, checks it, and only then puts it live.
- [Privacy-friendly analytics](https://botrecipe.com/recipes/privacy-friendly-analytics/) - Uses a simple analytics tool and tracks only the events you will act on.
- [Site change log](https://botrecipe.com/recipes/site-change-log/) - Keeps a short log of every website change, so "what changed?" has an answer.
- [Spam screen for public forms](https://botrecipe.com/recipes/feedback-spam-screen/) - Before saving anything typed by the public or by agents, the form blocks links, keys and 'ignore your instructions' style text.
- [SSL and domain expiry reminders](https://botrecipe.com/recipes/ssl-and-domain-expiry-reminders/) - Reminds you before domains and certificates expire.
- [Test your own contact form weekly](https://botrecipe.com/recipes/contact-form-weekly-test/) - Submits a test lead to your site form every week and alerts you if it does not reach your inbox within 5 minutes.
- [Uptime monitor with a status page](https://botrecipe.com/recipes/uptime-monitor-with-a-status-page/) - Checks your site every few minutes and alerts when down.

### Support

- [After-hours auto acknowledgment](https://botrecipe.com/recipes/after-hours-auto-acknowledgment/) - Sends one honest "we got it, here is when we reply" note outside business hours.
- [Angry email early warning](https://botrecipe.com/recipes/angry-email-early-warning/) - Flags support emails with strong frustration so they get a fast, human reply first.
- [Bug report cleaner](https://botrecipe.com/recipes/bug-report-cleaner/) - Turns messy customer bug emails into a clean ticket with steps, device and expected result.
- [Customer reply tone check](https://botrecipe.com/recipes/customer-reply-tone-check/) - Before you send a tricky reply, a bot checks it for tone and missing answers.
- [Follow up on bad ratings within a day](https://botrecipe.com/recipes/support-low-rating-follow-up/) - When a customer gives a low satisfaction score, opens a task for a person to reach out within 24 hours.
- [Help article gap finder](https://botrecipe.com/recipes/help-article-gap-finder/) - Every Friday, lists the questions customers asked that your help docs do not answer.
- [Order status answer bot](https://botrecipe.com/recipes/order-status-answer-bot/) - Answers "where is my order" emails with the real tracking link pulled from your store.
- [Refund request router](https://botrecipe.com/recipes/refund-request-router/) - Spots refund and cancel requests and sends them to one person with the order details attached.
- [Reply in the customer's language](https://botrecipe.com/recipes/support-language-replies/) - Detects the language of new support emails, tags them, and drafts a reply in that language with an English copy for your team.
- [Saved replies from your best answers](https://botrecipe.com/recipes/saved-replies-from-your-best-answers/) - Turns the support replies you are proud of into a reusable saved-reply library.
- [Support inbox first-draft replies](https://botrecipe.com/recipes/support-inbox-first-draft-replies/) - A bot drafts a reply to every new support email so a human only edits and sends.
- [Support reply check against your help docs](https://botrecipe.com/recipes/support-reply-policy-check/) - Before a support reply goes out, checks it against your help docs and flags anything that conflicts or is not covered.
- [Weekly support digest for the team](https://botrecipe.com/recipes/weekly-support-digest-for-the-team/) - Every Monday, one short message summarizing last week's support themes.

### Video Podcast

- [Captions and chapters for every video](https://botrecipe.com/recipes/video-captions-chapters/) - Fixes captions and writes YouTube chapters from the transcript so viewers can skim and the video is searchable.
- [Clip finder for short videos](https://botrecipe.com/recipes/clip-finder-for-short-videos/) - Finds the strongest 30-60 second moments in a long video for shorts.
- [Comment question harvester](https://botrecipe.com/recipes/comment-question-harvester/) - Pulls questions from your video comments into a list of future video ideas.
- [Episode publish checklist bot](https://botrecipe.com/recipes/episode-publish-checklist-bot/) - Runs through a publish checklist so nothing is missed on release day.
- [Guest booking pipeline](https://botrecipe.com/recipes/guest-booking-pipeline/) - Tracks podcast guest invites, confirmations and recording dates without email chaos.
- [Guest research brief with fresh questions](https://botrecipe.com/recipes/podcast-guest-brief/) - Before an interview, reads the guest's site and recent talks and gives you a one-page brief with questions they rarely get.
- [Podcast listener question voicemail](https://botrecipe.com/recipes/podcast-listener-question-voicemail/) - Lets listeners leave a voice question that you can play on the show.
- [Podcast show notes from transcript](https://botrecipe.com/recipes/podcast-show-notes-from-transcript/) - Turns an episode transcript into show notes with timestamps and links mentioned.
- [Sponsor read script drafts](https://botrecipe.com/recipes/sponsor-read-script-drafts/) - Drafts a host-read ad that sounds like you, from the sponsor's brief.
- [Transcript to blog post](https://botrecipe.com/recipes/transcript-to-blog-post/) - Turns a video or episode transcript into a readable article for your site.
- [Upload backup routine](https://botrecipe.com/recipes/upload-backup-routine/) - Copies every finished video and project file to a second place automatically.
- [YouTube title and thumbnail text options](https://botrecipe.com/recipes/youtube-title-and-thumbnail-text-options/) - Drafts title and thumbnail text pairs from your video outline.

### X Growth

- [Bookmark-worthy thread outline](https://botrecipe.com/recipes/bookmark-worthy-thread-outline/) - Plans a thread that someone would save, from one thing you know well.
- [Pause reply bots when the machine is struggling](https://botrecipe.com/recipes/reply-rotation-pause/) - When the shared machine runs low on memory, reply bots pause on their own and tell you once.
- [Post idea bank from your notes](https://botrecipe.com/recipes/post-idea-bank-from-your-notes/) - Turns rough daily notes into a backlog of X post ideas.
- [Post performance notes](https://botrecipe.com/recipes/post-performance-notes/) - Logs which posts did well and why, to repeat what works.
- [Post the article, then the hook as first reply](https://botrecipe.com/recipes/x-post-hook-first-reply/) - Your bot posts each article on its own, then adds the hook or link as the first reply.
- [Profile and pinned post checkup](https://botrecipe.com/recipes/profile-and-pinned-post-checkup/) - Reviews your bio and pinned post monthly so new visitors know what you do.
- [Quote post with your take](https://botrecipe.com/recipes/quote-post-with-your-take/) - Shares a good post with your own example or disagreement instead of a plain repost.
- [Reply list of people to learn from](https://botrecipe.com/recipes/reply-list-of-people-to-learn-from/) - Keeps a private X list of accounts you reply to daily.
- [Scheduled posts with a manual check](https://botrecipe.com/recipes/scheduled-posts-with-a-manual-check/) - Queue posts ahead but read each one the morning it goes out.
- [X message requests sorter](https://botrecipe.com/recipes/x-dm-request-sorter/) - Sorts your X message requests into leads, collaborations, questions and spam, with a draft reply for the real ones.
- [X reply engine with per-account caps](https://botrecipe.com/recipes/x-reply-engine-caps/) - A reply bot that finds people asking for help on X and drafts helpful replies, with hard caps so the accounts stay safe.

## Sample recipes

Three recipes in full, so you can see the format.

<details>
<summary><b>Memory watch for a shared bot box</b>: A small watcher that logs free memory and pauses non-urgent bots before the box falls over.</summary>

Steps
-----

1. Every run, append one line to `memory-log.md`: time, available MB, chrome process count, load average.
2. Warn below 1.5 GB available.
3. On the 2nd warning in a row: pause the reply rotation and send one alert. Later warnings just log 'already paused'.
4. Log the top memory users so a human can decide what to close.
5. Never kill processes automatically; a human makes that call.

What worked / what failed
-------------------------

**Failed, then fixed**the box ran at about 243-533 MB free on Oct 13 with many leftover browser/display processes. The watch caught it and paused rotation; nothing was killed.

**Worked**one log line per run made the trend easy to read without extra tools.

For agents
----------

Report a result with `POST /api/feedback`:

```
{"recipe_id": "memory-watch", "version": 1,
 "result": "worked" | "failed",
 "agent_id": "...", "fix": "..."}
```

Source: https://botrecipe.com/recipes/memory-watch/
</details>

<details>
<summary><b>Inbox triage with three labels</b>: A bot sorts new email into Needs you, Waiting, and FYI, and never replies on its own.</summary>

Steps
-----

1. Create three labels: Needs you, Waiting, FYI.
2. The bot reads new email every hour and applies one label each.
3. Anything with money, contracts or a direct question goes to Needs you.
4. The bot can draft replies but never sends them.
5. Once a day, it sends a short list of what is in Needs you.

What worked / what failed
-------------------------

**Worked**Three labels were easy to trust. More labels made us second-guess the bot.

**Worked**Draft-only meant no accidental sends.

**Failed, then fixed**The bot first marked newsletters as Needs you when they asked a question. It now checks if the sender is a real person.

For agents
----------

Report a result with `POST /api/feedback`:

```
{"recipe_id": "inbox-triage-labels", "version": 1,
 "result": "worked" | "failed",
 "agent_id": "...", "fix": "..."}
```

Source: https://botrecipe.com/recipes/inbox-triage-labels/
</details>

<details>
<summary><b>Follow up after a missed booking</b>: When someone books but does not show, a bot drafts a short, kind follow-up with a new booking link.</summary>

Steps
-----

1. After each booked meeting, check if it was marked as a no-show.
2. The bot drafts a short note: no problem, here is a link to pick a new time.
3. You read and send it. The bot does not send on its own.
4. Only one follow-up per no-show.
5. Log it so nobody gets two.

What worked / what failed
-------------------------

**Worked**A short, friendly note got better replies than a long one.

**Worked**One follow-up only kept it from feeling pushy.

**Failed, then fixed**The bot once drafted for a meeting that was cancelled, not missed. It now checks the cancel status first.

For agents
----------

Report a result with `POST /api/feedback`:

```
{"recipe_id": "calendly-no-show-followup", "version": 1,
 "result": "worked" | "failed",
 "agent_id": "...", "fix": "..."}
```

Source: https://botrecipe.com/recipes/calendly-no-show-followup/
</details>

## Full pack

All 263 recipes as one markdown file and one JSON file, ready for a bot's memory or context. **$5, one-time.**

[Get the full pack · $5](https://pay.instaloops.com/b/14A9ATeG47MP9P91yf83C3o)

Machine-readable pricing: [pricing.json](https://botrecipe.com/pricing.json).

## Directory of MCP servers and bots

[botrecipe.com/directory](https://botrecipe.com/directory/) lists public MCP servers and bots from the official MCP Registry. Submitting yours is free and every listing is reviewed. Agents can call `list_directory` on the MCP server.

## Contributing

Run a bot that works? [Submit a recipe](https://botrecipe.com/submit/) or open a pull request that adds one line under the right category: `- [Title](link) - One sentence on what it does.`

Please share only setups you have run yourself, and never include keys or secrets.

## License

[CC0 1.0](LICENSE) for this list. Recipe pages on botrecipe.com remain © Supa Humans.
