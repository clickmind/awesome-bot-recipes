# Awesome Bot Recipes [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> 579 setups for AI agents and bots: the job, the tools, the steps, the prompt and what goes wrong. Maintained by [Supa Humans](https://botrecipe.com).

Each title links to its page on [botrecipe.com](https://botrecipe.com). Every recipe is free: the title, summary and first step are open, and the full steps need only an email address. Three sample recipes are in full below, and the list by category is a selection; [all 579 are on botrecipe.com](https://botrecipe.com/recipes/). Your agent can search them over MCP.

## Contents

- [Free Bot Builder skill](#free-bot-builder-skill)
- [Connect via MCP](#connect-via-mcp)
- [Recipes by category](#recipes-by-category)
- [Sample recipes](#sample-recipes)
- [Every recipe, free](#every-recipe-free)
- [Directory of MCP servers and bots](#directory-of-mcp-servers-and-bots)
- [Contributing](#contributing)

## Free Bot Builder skill

A free skill that turns Claude, ChatGPT, Grok Bot or Supa Humans into a bot-team designer. It asks 3 short questions, looks up tested setups over the MCP below, and writes copy-paste instructions for each bot.

- Install steps for each assistant: [botrecipe.com/free](https://botrecipe.com/free/)
- Skill file: [bot-builder.md](https://botrecipe.com/free/bot-builder.md)
- Custom GPT instructions: [gpt-instructions.txt](https://botrecipe.com/free/gpt-instructions.txt)

## Connect via MCP

Remote server, Streamable HTTP, no key needed: `https://botrecipe.com/api/mcp`

Tools: `search_recipes`, `get_recipe` (pass an `email`), `list_directory`. Listed in the [official MCP Registry](https://registry.modelcontextprotocol.io) as `com.botrecipe/recipes`.

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

### Infrastructure

- [AI cost per bot tracker](https://botrecipe.com/recipes/ai-cost-per-bot-tracker/)
- [Bot handoff note between runs](https://botrecipe.com/recipes/bot-handoff-note-between-runs/)
- [Bot inbox rules so codes go to the right bot](https://botrecipe.com/recipes/bot-inbox-rules-so-codes-go-to-the-right-bot/)
- [Bot instructions version history](https://botrecipe.com/recipes/bot-instructions-version-history/)
- [Bot output review queue](https://botrecipe.com/recipes/bot-output-review-queue/)
- [Bot run log in one sheet](https://botrecipe.com/recipes/bot-run-log-in-one-sheet/)
- [Bot task that asks before spending](https://botrecipe.com/recipes/bot-task-that-asks-before-spending/)
- [Cron health check with a dead man's switch](https://botrecipe.com/recipes/cron-health-check-with-a-dead-man-s-switch/)
- [Error alerts that group repeats](https://botrecipe.com/recipes/error-alerts-that-group-repeats/)
- [Give each bot a one-page job card](https://botrecipe.com/recipes/bot-instructions-one-page/)
- [Hourly check on all your bots](https://botrecipe.com/recipes/hourly-fleet-check/)
- [Incident write-up from the chat log](https://botrecipe.com/recipes/incident-write-up/)
- [Kill switch for every automation](https://botrecipe.com/recipes/kill-switch-for-every-automation/)
- [Lock a shared browser before a bot uses it](https://botrecipe.com/recipes/lock-a-shared-browser-before-a-bot-uses-it/)
- [Memory watch for a shared bot box](https://botrecipe.com/recipes/memory-watch/)
- [New bot launch checklist](https://botrecipe.com/recipes/new-bot-launch-checklist/)
- [Night slot for your heaviest bot job](https://botrecipe.com/recipes/night-slot-for-your-heaviest-bot-job/)
- [One login per bot](https://botrecipe.com/recipes/one-login-per-bot/)
- [Per-task budget for agents](https://botrecipe.com/recipes/agent-task-budget/)
- [Prompt test set](https://botrecipe.com/recipes/prompt-test-set/)
- [Retry with backoff for flaky APIs](https://botrecipe.com/recipes/retry-with-backoff-for-flaky-apis/)
- [Route bot LLM calls through Caveman Cloud](https://botrecipe.com/recipes/route-bot-llm-calls-through-caveman-cloud/)
- [Secrets in a manager, not in prompts](https://botrecipe.com/recipes/secrets-in-a-manager-not-in-prompts/)
- [Shared browser lock for many bots](https://botrecipe.com/recipes/shared-browser-lock/)
- [Webhook receiver with signature check](https://botrecipe.com/recipes/webhook-receiver-with-signature-check/)

### Community

- [Event recap post](https://botrecipe.com/recipes/event-recap-post/)
- [Handle a heated thread in your community](https://botrecipe.com/recipes/handle-a-heated-thread-in-your-community/)
- [Member spotlight](https://botrecipe.com/recipes/member-spotlight/)
- [Moderation keyword alerts](https://botrecipe.com/recipes/moderation-keyword-alerts/)
- [Monthly community call agenda](https://botrecipe.com/recipes/monthly-community-call-agenda/)
- [New member welcome](https://botrecipe.com/recipes/new-member-welcome/)
- [Questions nobody answered](https://botrecipe.com/recipes/unanswered-questions-sweep/)
- [Unanswered question sweep](https://botrecipe.com/recipes/unanswered-question-sweep/)
- [Weekly community highlights](https://botrecipe.com/recipes/weekly-community-highlights/)

### Content

- [Accessibility pass on posts](https://botrecipe.com/recipes/accessibility-pass-on-posts/)
- [Content audit of your last 20 posts](https://botrecipe.com/recipes/content-audit-of-your-last-20-posts/)
- [Content calendar from goals](https://botrecipe.com/recipes/content-calendar-from-goals/)
- [Content fact-check pass](https://botrecipe.com/recipes/content-fact-check-pass/)
- [Daily scorer that finds weak recipes](https://botrecipe.com/recipes/daily-recipe-scorer/)
- [Does this sound like me?](https://botrecipe.com/recipes/ai-draft-voice-check/)
- [Headline variants for a post](https://botrecipe.com/recipes/headline-variants-for-a-post/)
- [Hourly X article engine (Pulse, Writer, Improver)](https://botrecipe.com/recipes/hourly-x-article-engine/)
- [Image prompts for blog headers](https://botrecipe.com/recipes/image-prompts-for-blog-headers/)
- [Interview-style content from a founder](https://botrecipe.com/recipes/interview-style-content-from-a-founder/)
- [One idea, five formats](https://botrecipe.com/recipes/one-idea-five-formats/)
- [Paste-ready prompt instead of a long guide](https://botrecipe.com/recipes/paste-ready-prompt-instead-of-a-long-guide/)
- [Public build log](https://botrecipe.com/recipes/build-log-in-public/)
- [Repurpose old posts](https://botrecipe.com/recipes/repurpose-old-posts/)
- [Rewrite jargon into plain words](https://botrecipe.com/recipes/rewrite-jargon-into-plain-words/)
- [Style guide for AI drafts](https://botrecipe.com/recipes/style-guide-for-ai-drafts/)
- [Turn a webinar into a written guide](https://botrecipe.com/recipes/turn-a-webinar-into-a-written-guide/)
- [Turn repeated questions into a post](https://botrecipe.com/recipes/comments-to-faq-post/)
- [Weekly post from customer questions](https://botrecipe.com/recipes/weekly-post-from-customer-questions/)

### Developer

- [Customer update from the changelog](https://botrecipe.com/recipes/release-notes-for-customers/)
- [Explain an error log in plain words](https://botrecipe.com/recipes/explain-an-error-log-in-plain-words/)
- [Flaky test tracker](https://botrecipe.com/recipes/flaky-test-tracker/)
- [Preview check before an agent deploys](https://botrecipe.com/recipes/preview-check-before-an-agent-deploys/)
- [Production error to a useful issue](https://botrecipe.com/recipes/error-to-issue/)
- [Pull request description from the diff](https://botrecipe.com/recipes/pr-description-writer/)
- [Review what an AI coding agent changed](https://botrecipe.com/recipes/review-what-an-ai-coding-agent-changed/)
- [Test your README setup weekly](https://botrecipe.com/recipes/readme-setup-test/)
- [Weekly dependency update batch](https://botrecipe.com/recipes/weekly-dependency-batch/)
- [Write a task spec a coding agent can finish](https://botrecipe.com/recipes/write-a-task-spec-a-coding-agent-can-finish/)

### Online store

- [Abandoned cart follow-up with a question](https://botrecipe.com/recipes/abandoned-cart-follow-up-with-a-question/)
- [Back in stock waitlist](https://botrecipe.com/recipes/back-in-stock-waitlist/)
- [Gift guide from your own products](https://botrecipe.com/recipes/gift-guide-from-your-own-products/)
- [Low stock alert to Slack](https://botrecipe.com/recipes/low-stock-alert-to-slack/)
- [Product description first drafts](https://botrecipe.com/recipes/product-description-first-drafts/)
- [Product launch email to your list](https://botrecipe.com/recipes/product-launch-email-to-your-list/)
- [Product page answers from customer questions](https://botrecipe.com/recipes/product-page-questions/)
- [Product photo alt text writer](https://botrecipe.com/recipes/product-photo-alt-text-writer/)
- [Respond to a shipping damage claim](https://botrecipe.com/recipes/respond-to-a-shipping-damage-claim/)
- [Restock email to past buyers of one product](https://botrecipe.com/recipes/restock-email-to-past-buyers-of-one-product/)
- [Return reason tracker](https://botrecipe.com/recipes/return-reason-tracker/)
- [Review request after delivery](https://botrecipe.com/recipes/review-request-after-delivery/)
- [Sale end reminder](https://botrecipe.com/recipes/sale-end-reminder/)
- [Shipping delay heads-up](https://botrecipe.com/recipes/shipping-delay-heads-up/)
- [Supplier reorder email drafts](https://botrecipe.com/recipes/supplier-reorder-email-drafts/)
- [Wholesale inquiry qualifier](https://botrecipe.com/recipes/wholesale-inquiry-qualifier/)
- [Write size and fit notes from returns](https://botrecipe.com/recipes/write-size-and-fit-notes-from-returns/)

### Courses & teaching

- [Completion certificate](https://botrecipe.com/recipes/completion-certificate/)
- [Course announcement email that students read](https://botrecipe.com/recipes/course-announcement-email-that-students-read/)
- [Explain a topic three ways](https://botrecipe.com/recipes/explain-a-topic-three-ways/)
- [First-pass feedback on assignments](https://botrecipe.com/recipes/assignment-feedback-draft/)
- [Inactive student nudge](https://botrecipe.com/recipes/inactive-student-nudge/)
- [Lesson outline from your expertise](https://botrecipe.com/recipes/lesson-outline-from-your-expertise/)
- [Lesson quiz generator](https://botrecipe.com/recipes/lesson-quiz-generator/)
- [Office hours question queue](https://botrecipe.com/recipes/office-hours-question-queue/)
- [One-question module feedback](https://botrecipe.com/recipes/one-question-module-feedback/)
- [Practice test from your study notes](https://botrecipe.com/recipes/practice-test-from-your-study-notes/)

### Events & webinars

- [Event follow-up email within a day](https://botrecipe.com/recipes/event-follow-up-email-within-a-day/)
- [Event Q&A collector](https://botrecipe.com/recipes/event-q-a-collector/)
- [Meetup check-in sheet](https://botrecipe.com/recipes/meetup-check-in-sheet/)
- [Post-event feedback form](https://botrecipe.com/recipes/post-event-feedback-form/)
- [Replay follow-up by attendance](https://botrecipe.com/recipes/replay-follow-up-by-attendance/)
- [Speaker intro writer](https://botrecipe.com/recipes/speaker-intro-writer/)
- [Sponsor prospect list for your event](https://botrecipe.com/recipes/sponsor-prospect-list/)
- [Volunteer schedule for an event](https://botrecipe.com/recipes/volunteer-schedule-for-an-event/)
- [Webinar registration to reminder sequence](https://botrecipe.com/recipes/webinar-registration-to-reminder-sequence/)

### Inbox & calendar

- [Agenda request before meetings](https://botrecipe.com/recipes/agenda-request-before-meetings/)
- [Calendar buffer guard](https://botrecipe.com/recipes/calendar-buffer-guard/)
- [Find a meeting time for five people](https://botrecipe.com/recipes/find-a-meeting-time-for-five-people/)
- [Follow-up reminder if no reply](https://botrecipe.com/recipes/follow-up-reminder-if-no-reply/)
- [Inbox triage with three labels](https://botrecipe.com/recipes/inbox-triage-labels/)
- [Meeting prep notes](https://botrecipe.com/recipes/meeting-prep-notes/)
- [Meeting request to booking link reply](https://botrecipe.com/recipes/meeting-request-to-booking-link-reply/)
- [Newsletter digest instead of inbox clutter](https://botrecipe.com/recipes/newsletter-digest-instead-of-inbox-clutter/)
- [Out-of-office message that actually helps](https://botrecipe.com/recipes/out-of-office-message-that-actually-helps/)
- [Scam and fake invoice flagger](https://botrecipe.com/recipes/scam-invoice-flagger/)
- [Shared inbox assignment](https://botrecipe.com/recipes/shared-inbox-assignment/)
- [Time zone check for new meetings](https://botrecipe.com/recipes/meeting-timezone-check/)
- [Weekday morning brief](https://botrecipe.com/recipes/weekday-morning-brief/)

### LinkedIn

- [Carousel from a blog post](https://botrecipe.com/recipes/carousel-from-a-blog-post/)
- [Comment-first routine](https://botrecipe.com/recipes/comment-first-routine/)
- [Job change congratulations list](https://botrecipe.com/recipes/job-change-congratulations-list/)
- [LinkedIn post from a customer conversation](https://botrecipe.com/recipes/linkedin-post-from-a-customer-conversation/)
- [New connection to useful first message](https://botrecipe.com/recipes/linkedin-accept-to-first-message/)
- [Profile visitor follow-up list](https://botrecipe.com/recipes/profile-visitor-follow-up-list/)
- [Reconnect with old colleagues on LinkedIn](https://botrecipe.com/recipes/reconnect-with-old-colleagues-on-linkedin/)
- [Reply to every comment on your post](https://botrecipe.com/recipes/linkedin-comment-replies/)

### Local business

- [Answer common phone questions on your website](https://botrecipe.com/recipes/answer-common-phone-questions-on-your-website/)
- [Appointment reminders](https://botrecipe.com/recipes/appointment-reminders/)
- [Fill last-minute cancellations from a waitlist](https://botrecipe.com/recipes/fill-last-minute-cancellations-from-a-waitlist/)
- [Google Business Profile weekly post](https://botrecipe.com/recipes/google-business-profile-weekly-post/)
- [Missed call text back](https://botrecipe.com/recipes/missed-call-text-back/)
- [Quote request to estimate draft](https://botrecipe.com/recipes/quote-request-to-estimate-draft/)
- [Reply to every new review in your voice](https://botrecipe.com/recipes/reply-to-every-new-review-in-your-voice/)
- [Review card at checkout](https://botrecipe.com/recipes/review-card-at-checkout/)
- [Seasonal service reminder](https://botrecipe.com/recipes/seasonal-service-reminder/)
- [Voicemail to a job card](https://botrecipe.com/recipes/voicemail-to-job-card/)
- [Write a seasonal promotion for a local shop](https://botrecipe.com/recipes/write-a-seasonal-promotion-for-a-local-shop/)

### Bookkeeping & admin

- [Check a loan offer before you sign](https://botrecipe.com/recipes/check-a-loan-offer-before-you-sign/)
- [Contract renewal tracker](https://botrecipe.com/recipes/contract-renewal-tracker/)
- [Expense category suggester](https://botrecipe.com/recipes/expense-category-suggester/)
- [Find money you are owed by companies](https://botrecipe.com/recipes/find-money-you-are-owed-by-companies/)
- [Mileage and trip log](https://botrecipe.com/recipes/mileage-and-trip-log/)
- [Month-end close checklist](https://botrecipe.com/recipes/month-end-close-checklist/)
- [Prepare documents for your accountant](https://botrecipe.com/recipes/prepare-documents-for-your-accountant/)
- [Quote to invoice handoff](https://botrecipe.com/recipes/quote-to-invoice-handoff/)
- [Receipt capture to a sheet](https://botrecipe.com/recipes/receipt-capture-to-a-sheet/)
- [Receipt photo to expense](https://botrecipe.com/recipes/receipt-photo-to-expense/)
- [Receipts to your bookkeeper automatically](https://botrecipe.com/recipes/receipts-to-bookkeeper/)
- [Sales tax threshold watcher](https://botrecipe.com/recipes/sales-tax-threshold-watch/)
- [Split shared bills fairly with housemates](https://botrecipe.com/recipes/split-shared-bills-fairly-with-housemates/)
- [Subscription audit](https://botrecipe.com/recipes/subscription-audit/)
- [Supplier bills to a sheet](https://botrecipe.com/recipes/bill-pdf-to-sheet/)
- [Tax set-aside reminder](https://botrecipe.com/recipes/tax-set-aside-reminder/)
- [Track freelance income and expenses monthly](https://botrecipe.com/recipes/track-freelance-income-and-expenses-monthly/)
- [Unpaid invoice nudges](https://botrecipe.com/recipes/unpaid-invoice-nudges/)
- [Weekly cash runway check](https://botrecipe.com/recipes/weekly-cash-runway/)
- [Write a request to waive a late fee](https://botrecipe.com/recipes/write-a-request-to-waive-a-late-fee/)

### Newsletter

- [Issue archive to SEO pages](https://botrecipe.com/recipes/issue-archive-to-seo-pages/)
- [Newsletter issue from your best replies](https://botrecipe.com/recipes/newsletter-issue-from-your-best-replies/)
- [Newsletter link roundup builder](https://botrecipe.com/recipes/newsletter-link-roundup-builder/)
- [Newsletter to social thread converter](https://botrecipe.com/recipes/newsletter-to-social-thread-converter/)
- [Reader question mailbag](https://botrecipe.com/recipes/reader-question-mailbag/)
- [Referral milestone emails](https://botrecipe.com/recipes/referral-milestone-emails/)
- [Sponsor report after each placement](https://botrecipe.com/recipes/sponsor-placement-report/)
- [Sponsor slot tracker](https://botrecipe.com/recipes/sponsor-slot-tracker/)
- [Subject line shortlist](https://botrecipe.com/recipes/subject-line-shortlist/)
- [Subscriber cleanup every quarter](https://botrecipe.com/recipes/subscriber-cleanup-every-quarter/)
- [Welcome sequence that asks one question](https://botrecipe.com/recipes/welcome-sequence-that-asks-one-question/)

### Operations

- [Client onboarding file chaser](https://botrecipe.com/recipes/client-onboarding-file-chaser/)
- [How-to guide from a screen recording](https://botrecipe.com/recipes/sop-from-screen-recording/)
- [Monday metrics snapshot](https://botrecipe.com/recipes/monday-metrics-snapshot/)
- [New hire first week plan](https://botrecipe.com/recipes/new-hire-first-week/)
- [Software renewal radar](https://botrecipe.com/recipes/software-renewal-radar/)
- [Weekly team update in one message](https://botrecipe.com/recipes/weekly-team-update-in-one-message/)

### Payments

- [Chargeback evidence pack](https://botrecipe.com/recipes/chargeback-evidence-pack/)
- [Checkout test with a test card](https://botrecipe.com/recipes/checkout-test-with-a-test-card/)
- [Failed payment recovery email](https://botrecipe.com/recipes/failed-payment-recovery-email/)
- [Match payouts to bank deposits](https://botrecipe.com/recipes/payout-bank-match/)
- [Monthly revenue snapshot from Stripe](https://botrecipe.com/recipes/monthly-revenue-snapshot-from-stripe/)
- [New sale note in Slack](https://botrecipe.com/recipes/new-sale-note-in-slack/)
- [One sponsor slot with a rising price](https://botrecipe.com/recipes/sponsor-slot-price-step/)
- [Past-due follow-up list](https://botrecipe.com/recipes/past-due-follow-up-list/)
- [Payment link per offer](https://botrecipe.com/recipes/payment-link-per-offer/)
- [Payment reminder schedule that stays polite](https://botrecipe.com/recipes/payment-reminder-schedule-that-stays-polite/)
- [Payout reconciliation](https://botrecipe.com/recipes/payout-reconciliation/)
- [Refund reason log](https://botrecipe.com/recipes/refund-reason-log/)
- [Refund request reply drafts](https://botrecipe.com/recipes/refund-request-reply-drafts/)
- [Sell a digital kit with a payment link](https://botrecipe.com/recipes/stripe-payment-link-kit/)
- [Spending cap for bots that can buy things](https://botrecipe.com/recipes/spend-cap-guard/)
- [Take a deposit before starting work](https://botrecipe.com/recipes/take-a-deposit-before-starting-work/)
- [Webhook-driven access granting](https://botrecipe.com/recipes/webhook-driven-access-granting/)

### Personal life

- [Bills on your calendar, with amounts](https://botrecipe.com/recipes/bills-on-calendar/)
- [Doctor visit prep note](https://botrecipe.com/recipes/doctor-visit-prep/)
- [Free trial cancel reminder](https://botrecipe.com/recipes/trial-cancel-reminder/)
- [Get a car repair quote explained](https://botrecipe.com/recipes/get-a-car-repair-quote-explained/)
- [Job application tracker that follows up](https://botrecipe.com/recipes/job-application-tracker/)
- [Learn to cook five meals this month](https://botrecipe.com/recipes/learn-to-cook-five-meals-this-month/)
- [Make a study schedule for an exam](https://botrecipe.com/recipes/make-a-study-schedule-for-an-exam/)
- [Organize important family documents](https://botrecipe.com/recipes/organize-important-family-documents/)
- [Plan a birthday party on a small budget](https://botrecipe.com/recipes/plan-a-birthday-party-on-a-small-budget/)
- [Plan a garden for your space and season](https://botrecipe.com/recipes/plan-a-garden-for-your-space-and-season/)
- [Plan a road trip with stops](https://botrecipe.com/recipes/plan-a-road-trip-with-stops/)
- [Plan a week of school lunches tonight](https://botrecipe.com/recipes/plan-a-week-of-school-lunches-tonight/)
- [Prepare for a vet visit](https://botrecipe.com/recipes/prepare-for-a-vet-visit/)
- [Remember what you read](https://botrecipe.com/recipes/highlights-spaced-review/)
- [Sort out a medical bill you do not understand](https://botrecipe.com/recipes/sort-out-a-medical-bill-you-do-not-understand/)
- [Sunday family brief](https://botrecipe.com/recipes/sunday-family-brief/)
- [Write a complaint to an airline](https://botrecipe.com/recipes/write-a-complaint-to-an-airline/)
- [Write a letter to contest a parking ticket](https://botrecipe.com/recipes/write-a-letter-to-contest-a-parking-ticket/)
- [Write a message to a neighbor about a problem](https://botrecipe.com/recipes/write-a-message-to-a-neighbor-about-a-problem/)
- [Write a message to end a service politely](https://botrecipe.com/recipes/write-a-message-to-end-a-service-politely/)
- [Write a thank-you note that sounds real](https://botrecipe.com/recipes/write-a-thank-you-note-that-sounds-real/)
- [Write a toast for a wedding in one evening](https://botrecipe.com/recipes/write-a-toast-for-a-wedding-in-one-evening/)

### Product & feedback

- [Bug triage labels](https://botrecipe.com/recipes/bug-triage-labels/)
- [Changelog post users will read](https://botrecipe.com/recipes/changelog-post-users-will-read/)
- [Churn reason follow-up](https://botrecipe.com/recipes/churn-reason-follow-up/)
- [Customer call to product decision note](https://botrecipe.com/recipes/customer-call-to-product-decision-note/)
- [Feature request tally](https://botrecipe.com/recipes/feature-request-tally/)
- [Feedback tagger across channels](https://botrecipe.com/recipes/feedback-tagger/)
- [Interview notes synthesis](https://botrecipe.com/recipes/interview-notes-synthesis/)
- [Onboarding drop-off email](https://botrecipe.com/recipes/onboarding-drop-off-email/)
- [Pricing page FAQ from real objections](https://botrecipe.com/recipes/pricing-objection-faq/)
- [Pricing page question log](https://botrecipe.com/recipes/pricing-page-question-log/)
- [Public roadmap from the request list](https://botrecipe.com/recipes/public-roadmap-from-the-request-list/)
- [Release notes from merged changes](https://botrecipe.com/recipes/release-notes-from-merged-changes/)
- [User interview scheduler](https://botrecipe.com/recipes/user-interview-scheduler/)
- [What only the founder should still do](https://botrecipe.com/recipes/what-only-the-founder-should-still-do/)

### Personal productivity

- [Bookmark triage](https://botrecipe.com/recipes/bookmark-triage/)
- [Daily plan from your task list](https://botrecipe.com/recipes/daily-plan-from-your-task-list/)
- [Daily standup note from yesterday's work](https://botrecipe.com/recipes/daily-standup-note-from-yesterday-s-work/)
- [Decide between two options with a simple table](https://botrecipe.com/recipes/decide-between-two-options-with-a-simple-table/)
- [Decision log](https://botrecipe.com/recipes/decision-log/)
- [Inbox zero assistant rules](https://botrecipe.com/recipes/inbox-zero-assistant-rules/)
- [Meeting action items that get done](https://botrecipe.com/recipes/meeting-action-items/)
- [Meeting-free focus block guard](https://botrecipe.com/recipes/meeting-free-focus-block-guard/)
- [Personal CRM nudges](https://botrecipe.com/recipes/personal-crm-nudges/)
- [Plan your week around three outcomes](https://botrecipe.com/recipes/plan-your-week-around-three-outcomes/)
- [Reading notes to flashcards](https://botrecipe.com/recipes/reading-notes-to-flashcards/)
- [Reply to a long email thread in five minutes](https://botrecipe.com/recipes/reply-to-a-long-email-thread-in-five-minutes/)
- [Travel prep packet](https://botrecipe.com/recipes/travel-prep-packet/)
- [Turn a long video into notes](https://botrecipe.com/recipes/turn-a-long-video-into-notes/)
- [Turn a messy notes file into a clean doc](https://botrecipe.com/recipes/turn-a-messy-notes-file-into-a-clean-doc/)
- [Voice memo to tasks](https://botrecipe.com/recipes/voice-memo-to-tasks/)
- [Weekly email cleanup in fifteen minutes](https://botrecipe.com/recipes/weekly-email-cleanup-in-fifteen-minutes/)
- [Weekly review prompt](https://botrecipe.com/recipes/weekly-review-prompt/)

### Research

- [Compare two vendors from their own docs](https://botrecipe.com/recipes/compare-two-vendors-from-their-own-docs/)
- [Competitor hiring signals](https://botrecipe.com/recipes/competitor-hiring-signals/)
- [Customer language mining](https://botrecipe.com/recipes/customer-language-mining/)
- [Customer review mining for your product](https://botrecipe.com/recipes/customer-review-mining-for-your-product/)
- [Find real complaints in your niche](https://botrecipe.com/recipes/reddit-pain-point-miner/)
- [Industry news morning brief](https://botrecipe.com/recipes/industry-news-morning-brief/)
- [Interview recruiting from your list](https://botrecipe.com/recipes/interview-recruiting-from-your-list/)
- [Literature scan with sources](https://botrecipe.com/recipes/literature-scan-with-sources/)
- [Meeting research brief](https://botrecipe.com/recipes/meeting-research-brief/)
- [Pricing page tracker for competitors](https://botrecipe.com/recipes/pricing-page-tracker-for-competitors/)
- [Recruit 5 users for interviews](https://botrecipe.com/recipes/interview-recruit-message/)
- [Search trend check](https://botrecipe.com/recipes/search-trend-check/)
- [Survey answer summary](https://botrecipe.com/recipes/survey-answer-summary/)
- [Tool pricing change watch](https://botrecipe.com/recipes/pricing-page-change-watch/)
- [Watch competitor pages for changes](https://botrecipe.com/recipes/competitor-page-watch/)

### Reviews & reputation

- [Ask for reviews in the right moment](https://botrecipe.com/recipes/ask-for-reviews-in-the-right-moment/)
- [Google review alert and reply draft](https://botrecipe.com/recipes/google-review-alert-and-reply-draft/)
- [Negative review escalation](https://botrecipe.com/recipes/negative-review-escalation/)
- [Review response time tracker](https://botrecipe.com/recipes/review-response-time-tracker/)
- [Review theme report](https://botrecipe.com/recipes/review-theme-report/)
- [Testimonial request after a win](https://botrecipe.com/recipes/testimonial-request-after-a-win/)

### Sales & leads

- [Call notes to CRM](https://botrecipe.com/recipes/call-notes-to-crm/)
- [Cold email reply sorter](https://botrecipe.com/recipes/cold-email-reply-sorter/)
- [Demo no-show rescue in 10 minutes](https://botrecipe.com/recipes/demo-no-show-rescue/)
- [Find five businesses that need your setup offer](https://botrecipe.com/recipes/find-five-businesses-that-need-your-setup-offer/)
- [Find people asking for help](https://botrecipe.com/recipes/lead-question-finder/)
- [First paying client checklist](https://botrecipe.com/recipes/first-paying-client-checklist/)
- [Follow up after a missed booking](https://botrecipe.com/recipes/calendly-no-show-followup/)
- [Follow up after sending a proposal](https://botrecipe.com/recipes/follow-up-after-sending-a-proposal/)
- [Inbound lead enrichment](https://botrecipe.com/recipes/inbound-lead-enrichment/)
- [Lead list from a niche directory](https://botrecipe.com/recipes/lead-list-from-a-niche-directory/)
- [Lead reply within minutes](https://botrecipe.com/recipes/lead-reply-within-minutes/)
- [Lost deal reason log](https://botrecipe.com/recipes/lost-deal-reason-log/)
- [Meeting-booked prep note](https://botrecipe.com/recipes/meeting-booked-prep-note/)
- [Price a done-for-you setup](https://botrecipe.com/recipes/price-a-done-for-you-setup/)
- [Proposal first draft](https://botrecipe.com/recipes/proposal-first-draft/)
- [Proposal sanity check](https://botrecipe.com/recipes/proposal-sanity-check/)
- [Quote follow-up ladder](https://botrecipe.com/recipes/quote-follow-up-ladder/)
- [Referral ask after a customer win](https://botrecipe.com/recipes/referral-ask-after-a-customer-win/)
- [Reply to a lead who asks for a discount](https://botrecipe.com/recipes/reply-to-a-lead-who-asks-for-a-discount/)
- [Sell a setup service before you build anything](https://botrecipe.com/recipes/sell-a-setup-service-before-you-build-anything/)
- [Signup research card for founders](https://botrecipe.com/recipes/signup-research-card/)
- [Stale deal sweep](https://botrecipe.com/recipes/stale-deal-sweep/)
- [Turn a finished job into a case study](https://botrecipe.com/recipes/turn-a-finished-job-into-a-case-study/)
- [Weekly pipeline review in ten minutes](https://botrecipe.com/recipes/weekly-pipeline-review-in-ten-minutes/)
- [Win and loss interviews](https://botrecipe.com/recipes/win-loss-interviews/)

### SEO & blog

- [Answer page for one buyer question](https://botrecipe.com/recipes/answer-page-for-one-buyer-question/)
- [Broken link sweep](https://botrecipe.com/recipes/broken-link-sweep/)
- [Business facts page for AI assistants](https://botrecipe.com/recipes/business-facts-page-for-ai-assistants/)
- [Check if AI assistants recommend you](https://botrecipe.com/recipes/check-if-ai-assistants-recommend-you/)
- [Comparison page that stays fair](https://botrecipe.com/recipes/comparison-page-that-stays-fair/)
- [Competitor content gap list](https://botrecipe.com/recipes/competitor-content-gap-list/)
- [Content refresh queue](https://botrecipe.com/recipes/content-refresh-queue/)
- [FAQ from what buyers ask assistants](https://botrecipe.com/recipes/faq-from-what-buyers-ask-assistants/)
- [FAQ schema from real questions](https://botrecipe.com/recipes/faq-schema-from-real-questions/)
- [Fix pages AI assistants misquote](https://botrecipe.com/recipes/fix-pages-ai-assistants-misquote/)
- [Fix titles that are seen but not clicked](https://botrecipe.com/recipes/low-ctr-title-fixer/)
- [Image compression check](https://botrecipe.com/recipes/image-compression-check/)
- [Internal link finder](https://botrecipe.com/recipes/internal-link-finder/)
- [Keyword to outline drafter](https://botrecipe.com/recipes/keyword-to-outline-drafter/)
- [Product feed check for AI shopping answers](https://botrecipe.com/recipes/product-feed-check-for-ai-shopping-answers/)
- [Programmatic page quality gate](https://botrecipe.com/recipes/programmatic-page-quality-gate/)
- [Schema check for your key pages](https://botrecipe.com/recipes/schema-check-for-your-key-pages/)
- [Search Console weekly winners and losers](https://botrecipe.com/recipes/search-console-weekly-winners-and-losers/)
- [Search snippet preview](https://botrecipe.com/recipes/search-snippet-preview/)
- [Update an old post that lost traffic](https://botrecipe.com/recipes/update-an-old-post-that-lost-traffic/)

### Site ops

- [404 page that helps](https://botrecipe.com/recipes/404-page-that-helps/)
- [Backups you have restored once](https://botrecipe.com/recipes/backups-you-have-restored-once/)
- [Connect a new domain without downtime](https://botrecipe.com/recipes/domain-connect-checklist/)
- [Cookie banner and privacy check](https://botrecipe.com/recipes/cookie-banner-and-privacy-check/)
- [Domain and email settings check](https://botrecipe.com/recipes/domain-and-email-settings-check/)
- [Email signup that stays clean](https://botrecipe.com/recipes/email-signup-honeypot/)
- [Form spam honeypot](https://botrecipe.com/recipes/form-spam-honeypot/)
- [Lighthouse check in CI](https://botrecipe.com/recipes/lighthouse-check-in-ci/)
- [Make your contact page easy for bots](https://botrecipe.com/recipes/make-your-contact-page-easy-for-bots/)
- [Make your site readable for agents](https://botrecipe.com/recipes/agent-readable-site/)
- [One vote per person per version](https://botrecipe.com/recipes/one-vote-per-version/)
- [Plain text version of your pricing page](https://botrecipe.com/recipes/plain-text-version-of-your-pricing-page/)
- [Preview first, then production](https://botrecipe.com/recipes/preview-first-deploys/)
- [Privacy-friendly analytics](https://botrecipe.com/recipes/privacy-friendly-analytics/)
- [Robots rules check for AI crawlers](https://botrecipe.com/recipes/robots-rules-check-for-ai-crawlers/)
- [Site change log](https://botrecipe.com/recipes/site-change-log/)
- [Spam screen for public forms](https://botrecipe.com/recipes/feedback-spam-screen/)
- [SSL and domain expiry reminders](https://botrecipe.com/recipes/ssl-and-domain-expiry-reminders/)
- [Test your own contact form weekly](https://botrecipe.com/recipes/contact-form-weekly-test/)
- [Uptime monitor with a status page](https://botrecipe.com/recipes/uptime-monitor-with-a-status-page/)
- [Weekly check that your site is reachable by agents](https://botrecipe.com/recipes/weekly-check-that-your-site-is-reachable-by-agents/)

### Customer support

- [After-hours auto acknowledgment](https://botrecipe.com/recipes/after-hours-auto-acknowledgment/)
- [Angry email early warning](https://botrecipe.com/recipes/angry-email-early-warning/)
- [Bug report cleaner](https://botrecipe.com/recipes/bug-report-cleaner/)
- [Customer reply tone check](https://botrecipe.com/recipes/customer-reply-tone-check/)
- [Explain a delay to a customer honestly](https://botrecipe.com/recipes/explain-a-delay-to-a-customer-honestly/)
- [Follow up on bad ratings within a day](https://botrecipe.com/recipes/support-low-rating-follow-up/)
- [Help article gap finder](https://botrecipe.com/recipes/help-article-gap-finder/)
- [Order status answer bot](https://botrecipe.com/recipes/order-status-answer-bot/)
- [Refund request router](https://botrecipe.com/recipes/refund-request-router/)
- [Reply in the customer's language](https://botrecipe.com/recipes/support-language-replies/)
- [Saved replies from your best answers](https://botrecipe.com/recipes/saved-replies-from-your-best-answers/)
- [Support inbox first-draft replies](https://botrecipe.com/recipes/support-inbox-first-draft-replies/)
- [Support reply check against your help docs](https://botrecipe.com/recipes/support-reply-policy-check/)
- [Support reply from a voice note](https://botrecipe.com/recipes/support-reply-from-a-voice-note/)
- [Turn a help article into a short video script](https://botrecipe.com/recipes/turn-a-help-article-into-a-short-video-script/)
- [Weekly list of customers waiting on you](https://botrecipe.com/recipes/weekly-list-of-customers-waiting-on-you/)
- [Weekly support digest for the team](https://botrecipe.com/recipes/weekly-support-digest-for-the-team/)

### Video & podcasts

- [Captions and chapters for every video](https://botrecipe.com/recipes/video-captions-chapters/)
- [Clip finder for short videos](https://botrecipe.com/recipes/clip-finder-for-short-videos/)
- [Comment question harvester](https://botrecipe.com/recipes/comment-question-harvester/)
- [Episode publish checklist bot](https://botrecipe.com/recipes/episode-publish-checklist-bot/)
- [Guest booking pipeline](https://botrecipe.com/recipes/guest-booking-pipeline/)
- [Guest research brief with fresh questions](https://botrecipe.com/recipes/podcast-guest-brief/)
- [Podcast episode outline from a guest's work](https://botrecipe.com/recipes/podcast-episode-outline-from-a-guest-s-work/)
- [Podcast listener question voicemail](https://botrecipe.com/recipes/podcast-listener-question-voicemail/)
- [Podcast show notes from transcript](https://botrecipe.com/recipes/podcast-show-notes-from-transcript/)
- [Sponsor read script drafts](https://botrecipe.com/recipes/sponsor-read-script-drafts/)
- [Transcript to blog post](https://botrecipe.com/recipes/transcript-to-blog-post/)
- [Upload backup routine](https://botrecipe.com/recipes/upload-backup-routine/)
- [YouTube title and thumbnail text options](https://botrecipe.com/recipes/youtube-title-and-thumbnail-text-options/)

### X growth

- [Bookmark-worthy thread outline](https://botrecipe.com/recipes/bookmark-worthy-thread-outline/)
- [Pause reply bots when the machine is struggling](https://botrecipe.com/recipes/reply-rotation-pause/)
- [Post idea bank from your notes](https://botrecipe.com/recipes/post-idea-bank-from-your-notes/)
- [Post performance notes](https://botrecipe.com/recipes/post-performance-notes/)
- [Post the article, then the hook as first reply](https://botrecipe.com/recipes/x-post-hook-first-reply/)
- [Profile and pinned post checkup](https://botrecipe.com/recipes/profile-and-pinned-post-checkup/)
- [Quote post with your take](https://botrecipe.com/recipes/quote-post-with-your-take/)
- [Reply list of people to learn from](https://botrecipe.com/recipes/reply-list-of-people-to-learn-from/)
- [Reply to a big account with something useful](https://botrecipe.com/recipes/reply-to-a-big-account-with-something-useful/)
- [Scheduled posts with a manual check](https://botrecipe.com/recipes/scheduled-posts-with-a-manual-check/)
- [Turn a customer win into a short X post](https://botrecipe.com/recipes/turn-a-customer-win-into-a-short-x-post/)
- [X message requests sorter](https://botrecipe.com/recipes/x-dm-request-sorter/)
- [X reply engine with per-account caps](https://botrecipe.com/recipes/x-reply-engine-caps/)

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

## Every recipe, free

All 579 recipes are free. Agents can list them with `GET https://botrecipe.com/recipes.json?email=you@example.com` and read one with `GET https://botrecipe.com/api/recipe?id=ID&email=you@example.com`. People enter an email once on any recipe page.

Want it built for you instead? [Done-for-you bot setup by Supa Humans, $497](https://bot.supahumans.ai/). Building your own? [Bot Builders Club, $19](https://pay.instaloops.com/b/aFa3cv9lK4AD8L5ccT83C3n).

Machine-readable pricing: [pricing.json](https://botrecipe.com/pricing.json).

## Directory of MCP servers and bots

[botrecipe.com/directory](https://botrecipe.com/directory/) lists public MCP servers and bots from the official MCP Registry. Submitting yours is free and every listing is reviewed. Agents can call `list_directory` on the MCP server.

### Agent tools by Supa Humans

- [Agent Access Check](https://accesscheck.cloudforbots.com) - Checks if a website will block your AI agent and finds its llms.txt, MCP or OpenAPI door. MCP: `https://accesscheck.cloudforbots.com/mcp`
- [Agent Wake](https://wake.cloudforbots.com) - Schedules wake-ups that hand your agent its saved notes and next step, so a new session picks up where the last one stopped. MCP: `https://wake.cloudforbots.com/mcp`
- [Run Budget Guard](https://budget.cloudforbots.com) - Puts hard dollar, token, call and time caps on one agent run, shared by every sub-agent. MCP: `https://budget.cloudforbots.com/mcp`
- [Signal Leads](https://leads.cloudforbots.com) - Finds 25 sales leads, each with a public funding, hiring or tech signal, a source link and a draft message. MCP: `https://leads.cloudforbots.com/mcp`

## Contributing

Run a bot that works? [Submit a recipe](https://botrecipe.com/submit/) or open a pull request that adds one line under the right category: `- [Title](link) - One sentence on what it does.`

Please share only setups you have run yourself, and never include keys or secrets.

## License

[CC0 1.0](LICENSE) for this list. Recipe pages on botrecipe.com remain © Supa Humans.
