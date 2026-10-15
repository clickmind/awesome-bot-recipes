# Awesome Bot Recipes [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> 263 tested setups for AI agents and bots: the job, the tools, the steps, the prompt, what it costs and what goes wrong. Maintained by [Supa Humans](https://botrecipe.com).

Each title links to its page on [botrecipe.com](https://botrecipe.com), where the summary, tools and votes are free. Three sample recipes are free in full below; the full steps for every recipe are in the [$7 pack](https://botrecipe.com/api/buy?src=github). Your agent can search them over MCP.

## Contents

- [Free Bot Builder skill](#free-bot-builder-skill)
- [Connect via MCP](#connect-via-mcp)
- [Recipes by category](#recipes-by-category)
- [Sample recipes](#sample-recipes)
- [Full pack](#full-pack)
- [Directory of MCP servers and bots](#directory-of-mcp-servers-and-bots)
- [Contributing](#contributing)

## Free Bot Builder skill

A free skill that turns Claude, ChatGPT, Grok Bot or Supa Humans into a bot-team designer. It asks 3 short questions, looks up tested setups over the MCP below, and writes copy-paste instructions for each bot.

- Install steps for each assistant: [botrecipe.com/free](https://botrecipe.com/free/)
- Skill file: [bot-builder.md](https://botrecipe.com/free/bot-builder.md)
- Custom GPT instructions: [gpt-instructions.txt](https://botrecipe.com/free/gpt-instructions.txt)

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

### Infrastructure

- [AI cost per bot tracker](https://botrecipe.com/recipes/ai-cost-per-bot-tracker/)
- [Bot instructions version history](https://botrecipe.com/recipes/bot-instructions-version-history/)
- [Bot output review queue](https://botrecipe.com/recipes/bot-output-review-queue/)
- [Bot run log in one sheet](https://botrecipe.com/recipes/bot-run-log-in-one-sheet/)
- [Cron health check with a dead man's switch](https://botrecipe.com/recipes/cron-health-check-with-a-dead-man-s-switch/)
- [Error alerts that group repeats](https://botrecipe.com/recipes/error-alerts-that-group-repeats/)
- [Give each bot a one-page job card](https://botrecipe.com/recipes/bot-instructions-one-page/)
- [Hourly check on all your bots](https://botrecipe.com/recipes/hourly-fleet-check/)
- [Incident write-up from the chat log](https://botrecipe.com/recipes/incident-write-up/)
- [Kill switch for every automation](https://botrecipe.com/recipes/kill-switch-for-every-automation/)
- [Memory watch for a shared bot box](https://botrecipe.com/recipes/memory-watch/)
- [New bot launch checklist](https://botrecipe.com/recipes/new-bot-launch-checklist/)
- [Per-task budget for agents](https://botrecipe.com/recipes/agent-task-budget/)
- [Prompt test set](https://botrecipe.com/recipes/prompt-test-set/)
- [Retry with backoff for flaky APIs](https://botrecipe.com/recipes/retry-with-backoff-for-flaky-apis/)
- [Route bot LLM calls through Caveman Cloud](https://botrecipe.com/recipes/route-bot-llm-calls-through-caveman-cloud/)
- [Secrets in a manager, not in prompts](https://botrecipe.com/recipes/secrets-in-a-manager-not-in-prompts/)
- [Shared browser lock for many bots](https://botrecipe.com/recipes/shared-browser-lock/)
- [Webhook receiver with signature check](https://botrecipe.com/recipes/webhook-receiver-with-signature-check/)

### Community

- [Event recap post](https://botrecipe.com/recipes/event-recap-post/)
- [Member spotlight](https://botrecipe.com/recipes/member-spotlight/)
- [Moderation keyword alerts](https://botrecipe.com/recipes/moderation-keyword-alerts/)
- [New member welcome](https://botrecipe.com/recipes/new-member-welcome/)
- [Questions nobody answered](https://botrecipe.com/recipes/unanswered-questions-sweep/)
- [Unanswered question sweep](https://botrecipe.com/recipes/unanswered-question-sweep/)
- [Weekly community highlights](https://botrecipe.com/recipes/weekly-community-highlights/)

### Content

- [Accessibility pass on posts](https://botrecipe.com/recipes/accessibility-pass-on-posts/)
- [Content calendar from goals](https://botrecipe.com/recipes/content-calendar-from-goals/)
- [Content fact-check pass](https://botrecipe.com/recipes/content-fact-check-pass/)
- [Daily scorer that finds weak recipes](https://botrecipe.com/recipes/daily-recipe-scorer/)
- [Does this sound like me?](https://botrecipe.com/recipes/ai-draft-voice-check/)
- [Headline variants for a post](https://botrecipe.com/recipes/headline-variants-for-a-post/)
- [Hourly X article engine (Pulse, Writer, Improver)](https://botrecipe.com/recipes/hourly-x-article-engine/)
- [Image prompts for blog headers](https://botrecipe.com/recipes/image-prompts-for-blog-headers/)
- [Interview-style content from a founder](https://botrecipe.com/recipes/interview-style-content-from-a-founder/)
- [One idea, five formats](https://botrecipe.com/recipes/one-idea-five-formats/)
- [Public build log](https://botrecipe.com/recipes/build-log-in-public/)
- [Repurpose old posts](https://botrecipe.com/recipes/repurpose-old-posts/)
- [Style guide for AI drafts](https://botrecipe.com/recipes/style-guide-for-ai-drafts/)
- [Turn repeated questions into a post](https://botrecipe.com/recipes/comments-to-faq-post/)

### Developer

- [Customer update from the changelog](https://botrecipe.com/recipes/release-notes-for-customers/)
- [Flaky test tracker](https://botrecipe.com/recipes/flaky-test-tracker/)
- [Production error to a useful issue](https://botrecipe.com/recipes/error-to-issue/)
- [Pull request description from the diff](https://botrecipe.com/recipes/pr-description-writer/)
- [Test your README setup weekly](https://botrecipe.com/recipes/readme-setup-test/)
- [Weekly dependency update batch](https://botrecipe.com/recipes/weekly-dependency-batch/)

### Online store

- [Abandoned cart follow-up with a question](https://botrecipe.com/recipes/abandoned-cart-follow-up-with-a-question/)
- [Back in stock waitlist](https://botrecipe.com/recipes/back-in-stock-waitlist/)
- [Low stock alert to Slack](https://botrecipe.com/recipes/low-stock-alert-to-slack/)
- [Product description first drafts](https://botrecipe.com/recipes/product-description-first-drafts/)
- [Product page answers from customer questions](https://botrecipe.com/recipes/product-page-questions/)
- [Product photo alt text writer](https://botrecipe.com/recipes/product-photo-alt-text-writer/)
- [Return reason tracker](https://botrecipe.com/recipes/return-reason-tracker/)
- [Review request after delivery](https://botrecipe.com/recipes/review-request-after-delivery/)
- [Sale end reminder](https://botrecipe.com/recipes/sale-end-reminder/)
- [Shipping delay heads-up](https://botrecipe.com/recipes/shipping-delay-heads-up/)
- [Supplier reorder email drafts](https://botrecipe.com/recipes/supplier-reorder-email-drafts/)
- [Wholesale inquiry qualifier](https://botrecipe.com/recipes/wholesale-inquiry-qualifier/)

### Courses & teaching

- [Completion certificate](https://botrecipe.com/recipes/completion-certificate/)
- [First-pass feedback on assignments](https://botrecipe.com/recipes/assignment-feedback-draft/)
- [Inactive student nudge](https://botrecipe.com/recipes/inactive-student-nudge/)
- [Lesson outline from your expertise](https://botrecipe.com/recipes/lesson-outline-from-your-expertise/)
- [Lesson quiz generator](https://botrecipe.com/recipes/lesson-quiz-generator/)
- [Office hours question queue](https://botrecipe.com/recipes/office-hours-question-queue/)
- [One-question module feedback](https://botrecipe.com/recipes/one-question-module-feedback/)

### Events & webinars

- [Event Q&A collector](https://botrecipe.com/recipes/event-q-a-collector/)
- [Meetup check-in sheet](https://botrecipe.com/recipes/meetup-check-in-sheet/)
- [Post-event feedback form](https://botrecipe.com/recipes/post-event-feedback-form/)
- [Replay follow-up by attendance](https://botrecipe.com/recipes/replay-follow-up-by-attendance/)
- [Speaker intro writer](https://botrecipe.com/recipes/speaker-intro-writer/)
- [Sponsor prospect list for your event](https://botrecipe.com/recipes/sponsor-prospect-list/)
- [Webinar registration to reminder sequence](https://botrecipe.com/recipes/webinar-registration-to-reminder-sequence/)

### Inbox & calendar

- [Agenda request before meetings](https://botrecipe.com/recipes/agenda-request-before-meetings/)
- [Calendar buffer guard](https://botrecipe.com/recipes/calendar-buffer-guard/)
- [Follow-up reminder if no reply](https://botrecipe.com/recipes/follow-up-reminder-if-no-reply/)
- [Inbox triage with three labels](https://botrecipe.com/recipes/inbox-triage-labels/)
- [Meeting prep notes](https://botrecipe.com/recipes/meeting-prep-notes/)
- [Meeting request to booking link reply](https://botrecipe.com/recipes/meeting-request-to-booking-link-reply/)
- [Newsletter digest instead of inbox clutter](https://botrecipe.com/recipes/newsletter-digest-instead-of-inbox-clutter/)
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
- [Reply to every comment on your post](https://botrecipe.com/recipes/linkedin-comment-replies/)

### Local business

- [Appointment reminders](https://botrecipe.com/recipes/appointment-reminders/)
- [Google Business Profile weekly post](https://botrecipe.com/recipes/google-business-profile-weekly-post/)
- [Missed call text back](https://botrecipe.com/recipes/missed-call-text-back/)
- [Quote request to estimate draft](https://botrecipe.com/recipes/quote-request-to-estimate-draft/)
- [Review card at checkout](https://botrecipe.com/recipes/review-card-at-checkout/)
- [Seasonal service reminder](https://botrecipe.com/recipes/seasonal-service-reminder/)
- [Voicemail to a job card](https://botrecipe.com/recipes/voicemail-to-job-card/)

### Bookkeeping & admin

- [Contract renewal tracker](https://botrecipe.com/recipes/contract-renewal-tracker/)
- [Expense category suggester](https://botrecipe.com/recipes/expense-category-suggester/)
- [Mileage and trip log](https://botrecipe.com/recipes/mileage-and-trip-log/)
- [Month-end close checklist](https://botrecipe.com/recipes/month-end-close-checklist/)
- [Quote to invoice handoff](https://botrecipe.com/recipes/quote-to-invoice-handoff/)
- [Receipt capture to a sheet](https://botrecipe.com/recipes/receipt-capture-to-a-sheet/)
- [Receipt photo to expense](https://botrecipe.com/recipes/receipt-photo-to-expense/)
- [Receipts to your bookkeeper automatically](https://botrecipe.com/recipes/receipts-to-bookkeeper/)
- [Sales tax threshold watcher](https://botrecipe.com/recipes/sales-tax-threshold-watch/)
- [Subscription audit](https://botrecipe.com/recipes/subscription-audit/)
- [Supplier bills to a sheet](https://botrecipe.com/recipes/bill-pdf-to-sheet/)
- [Tax set-aside reminder](https://botrecipe.com/recipes/tax-set-aside-reminder/)
- [Unpaid invoice nudges](https://botrecipe.com/recipes/unpaid-invoice-nudges/)
- [Weekly cash runway check](https://botrecipe.com/recipes/weekly-cash-runway/)

### Newsletter

- [Issue archive to SEO pages](https://botrecipe.com/recipes/issue-archive-to-seo-pages/)
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

### Payments

- [Chargeback evidence pack](https://botrecipe.com/recipes/chargeback-evidence-pack/)
- [Checkout test with a test card](https://botrecipe.com/recipes/checkout-test-with-a-test-card/)
- [Failed payment recovery email](https://botrecipe.com/recipes/failed-payment-recovery-email/)
- [Match payouts to bank deposits](https://botrecipe.com/recipes/payout-bank-match/)
- [New sale note in Slack](https://botrecipe.com/recipes/new-sale-note-in-slack/)
- [One sponsor slot with a rising price](https://botrecipe.com/recipes/sponsor-slot-price-step/)
- [Past-due follow-up list](https://botrecipe.com/recipes/past-due-follow-up-list/)
- [Payment link per offer](https://botrecipe.com/recipes/payment-link-per-offer/)
- [Payout reconciliation](https://botrecipe.com/recipes/payout-reconciliation/)
- [Refund reason log](https://botrecipe.com/recipes/refund-reason-log/)
- [Sell a digital kit with a payment link](https://botrecipe.com/recipes/stripe-payment-link-kit/)
- [Spending cap for bots that can buy things](https://botrecipe.com/recipes/spend-cap-guard/)
- [Webhook-driven access granting](https://botrecipe.com/recipes/webhook-driven-access-granting/)

### Personal life

- [Bills on your calendar, with amounts](https://botrecipe.com/recipes/bills-on-calendar/)
- [Doctor visit prep note](https://botrecipe.com/recipes/doctor-visit-prep/)
- [Free trial cancel reminder](https://botrecipe.com/recipes/trial-cancel-reminder/)
- [Job application tracker that follows up](https://botrecipe.com/recipes/job-application-tracker/)
- [Remember what you read](https://botrecipe.com/recipes/highlights-spaced-review/)
- [Sunday family brief](https://botrecipe.com/recipes/sunday-family-brief/)

### Product & feedback

- [Bug triage labels](https://botrecipe.com/recipes/bug-triage-labels/)
- [Churn reason follow-up](https://botrecipe.com/recipes/churn-reason-follow-up/)
- [Feature request tally](https://botrecipe.com/recipes/feature-request-tally/)
- [Feedback tagger across channels](https://botrecipe.com/recipes/feedback-tagger/)
- [Interview notes synthesis](https://botrecipe.com/recipes/interview-notes-synthesis/)
- [Onboarding drop-off email](https://botrecipe.com/recipes/onboarding-drop-off-email/)
- [Pricing page FAQ from real objections](https://botrecipe.com/recipes/pricing-objection-faq/)
- [Pricing page question log](https://botrecipe.com/recipes/pricing-page-question-log/)
- [Public roadmap from the request list](https://botrecipe.com/recipes/public-roadmap-from-the-request-list/)
- [Release notes from merged changes](https://botrecipe.com/recipes/release-notes-from-merged-changes/)
- [User interview scheduler](https://botrecipe.com/recipes/user-interview-scheduler/)

### Personal productivity

- [Bookmark triage](https://botrecipe.com/recipes/bookmark-triage/)
- [Daily plan from your task list](https://botrecipe.com/recipes/daily-plan-from-your-task-list/)
- [Decision log](https://botrecipe.com/recipes/decision-log/)
- [Inbox zero assistant rules](https://botrecipe.com/recipes/inbox-zero-assistant-rules/)
- [Meeting action items that get done](https://botrecipe.com/recipes/meeting-action-items/)
- [Meeting-free focus block guard](https://botrecipe.com/recipes/meeting-free-focus-block-guard/)
- [Personal CRM nudges](https://botrecipe.com/recipes/personal-crm-nudges/)
- [Reading notes to flashcards](https://botrecipe.com/recipes/reading-notes-to-flashcards/)
- [Travel prep packet](https://botrecipe.com/recipes/travel-prep-packet/)
- [Voice memo to tasks](https://botrecipe.com/recipes/voice-memo-to-tasks/)
- [Weekly review prompt](https://botrecipe.com/recipes/weekly-review-prompt/)

### Research

- [Competitor hiring signals](https://botrecipe.com/recipes/competitor-hiring-signals/)
- [Customer language mining](https://botrecipe.com/recipes/customer-language-mining/)
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

- [Google review alert and reply draft](https://botrecipe.com/recipes/google-review-alert-and-reply-draft/)
- [Negative review escalation](https://botrecipe.com/recipes/negative-review-escalation/)
- [Review response time tracker](https://botrecipe.com/recipes/review-response-time-tracker/)
- [Review theme report](https://botrecipe.com/recipes/review-theme-report/)
- [Testimonial request after a win](https://botrecipe.com/recipes/testimonial-request-after-a-win/)

### Sales & leads

- [Call notes to CRM](https://botrecipe.com/recipes/call-notes-to-crm/)
- [Cold email reply sorter](https://botrecipe.com/recipes/cold-email-reply-sorter/)
- [Demo no-show rescue in 10 minutes](https://botrecipe.com/recipes/demo-no-show-rescue/)
- [Find people asking for help](https://botrecipe.com/recipes/lead-question-finder/)
- [Follow up after a missed booking](https://botrecipe.com/recipes/calendly-no-show-followup/)
- [Inbound lead enrichment](https://botrecipe.com/recipes/inbound-lead-enrichment/)
- [Lead reply within minutes](https://botrecipe.com/recipes/lead-reply-within-minutes/)
- [Lost deal reason log](https://botrecipe.com/recipes/lost-deal-reason-log/)
- [Meeting-booked prep note](https://botrecipe.com/recipes/meeting-booked-prep-note/)
- [Proposal first draft](https://botrecipe.com/recipes/proposal-first-draft/)
- [Proposal sanity check](https://botrecipe.com/recipes/proposal-sanity-check/)
- [Quote follow-up ladder](https://botrecipe.com/recipes/quote-follow-up-ladder/)
- [Referral ask after a customer win](https://botrecipe.com/recipes/referral-ask-after-a-customer-win/)
- [Signup research card for founders](https://botrecipe.com/recipes/signup-research-card/)
- [Stale deal sweep](https://botrecipe.com/recipes/stale-deal-sweep/)
- [Win and loss interviews](https://botrecipe.com/recipes/win-loss-interviews/)

### SEO & blog

- [Broken link sweep](https://botrecipe.com/recipes/broken-link-sweep/)
- [Competitor content gap list](https://botrecipe.com/recipes/competitor-content-gap-list/)
- [Content refresh queue](https://botrecipe.com/recipes/content-refresh-queue/)
- [FAQ schema from real questions](https://botrecipe.com/recipes/faq-schema-from-real-questions/)
- [Fix titles that are seen but not clicked](https://botrecipe.com/recipes/low-ctr-title-fixer/)
- [Image compression check](https://botrecipe.com/recipes/image-compression-check/)
- [Internal link finder](https://botrecipe.com/recipes/internal-link-finder/)
- [Keyword to outline drafter](https://botrecipe.com/recipes/keyword-to-outline-drafter/)
- [Programmatic page quality gate](https://botrecipe.com/recipes/programmatic-page-quality-gate/)
- [Search Console weekly winners and losers](https://botrecipe.com/recipes/search-console-weekly-winners-and-losers/)
- [Search snippet preview](https://botrecipe.com/recipes/search-snippet-preview/)

### Site ops

- [404 page that helps](https://botrecipe.com/recipes/404-page-that-helps/)
- [Backups you have restored once](https://botrecipe.com/recipes/backups-you-have-restored-once/)
- [Connect a new domain without downtime](https://botrecipe.com/recipes/domain-connect-checklist/)
- [Email signup that stays clean](https://botrecipe.com/recipes/email-signup-honeypot/)
- [Form spam honeypot](https://botrecipe.com/recipes/form-spam-honeypot/)
- [Lighthouse check in CI](https://botrecipe.com/recipes/lighthouse-check-in-ci/)
- [Make your site readable for agents](https://botrecipe.com/recipes/agent-readable-site/)
- [One vote per person per version](https://botrecipe.com/recipes/one-vote-per-version/)
- [Preview first, then production](https://botrecipe.com/recipes/preview-first-deploys/)
- [Privacy-friendly analytics](https://botrecipe.com/recipes/privacy-friendly-analytics/)
- [Site change log](https://botrecipe.com/recipes/site-change-log/)
- [Spam screen for public forms](https://botrecipe.com/recipes/feedback-spam-screen/)
- [SSL and domain expiry reminders](https://botrecipe.com/recipes/ssl-and-domain-expiry-reminders/)
- [Test your own contact form weekly](https://botrecipe.com/recipes/contact-form-weekly-test/)
- [Uptime monitor with a status page](https://botrecipe.com/recipes/uptime-monitor-with-a-status-page/)

### Customer support

- [After-hours auto acknowledgment](https://botrecipe.com/recipes/after-hours-auto-acknowledgment/)
- [Angry email early warning](https://botrecipe.com/recipes/angry-email-early-warning/)
- [Bug report cleaner](https://botrecipe.com/recipes/bug-report-cleaner/)
- [Customer reply tone check](https://botrecipe.com/recipes/customer-reply-tone-check/)
- [Follow up on bad ratings within a day](https://botrecipe.com/recipes/support-low-rating-follow-up/)
- [Help article gap finder](https://botrecipe.com/recipes/help-article-gap-finder/)
- [Order status answer bot](https://botrecipe.com/recipes/order-status-answer-bot/)
- [Refund request router](https://botrecipe.com/recipes/refund-request-router/)
- [Reply in the customer's language](https://botrecipe.com/recipes/support-language-replies/)
- [Saved replies from your best answers](https://botrecipe.com/recipes/saved-replies-from-your-best-answers/)
- [Support inbox first-draft replies](https://botrecipe.com/recipes/support-inbox-first-draft-replies/)
- [Support reply check against your help docs](https://botrecipe.com/recipes/support-reply-policy-check/)
- [Weekly support digest for the team](https://botrecipe.com/recipes/weekly-support-digest-for-the-team/)

### Video & podcasts

- [Captions and chapters for every video](https://botrecipe.com/recipes/video-captions-chapters/)
- [Clip finder for short videos](https://botrecipe.com/recipes/clip-finder-for-short-videos/)
- [Comment question harvester](https://botrecipe.com/recipes/comment-question-harvester/)
- [Episode publish checklist bot](https://botrecipe.com/recipes/episode-publish-checklist-bot/)
- [Guest booking pipeline](https://botrecipe.com/recipes/guest-booking-pipeline/)
- [Guest research brief with fresh questions](https://botrecipe.com/recipes/podcast-guest-brief/)
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
- [Scheduled posts with a manual check](https://botrecipe.com/recipes/scheduled-posts-with-a-manual-check/)
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

## Full pack

All 263 recipes as one markdown file and one JSON file, ready for a bot's memory or context. **$7, one-time.**

[Get the full pack · $7](https://botrecipe.com/api/buy?src=github)

Want it built for you instead? [Done-for-you bot setup by Supa Humans, $497](https://bot.supahumans.ai/). Building your own? [Bot Builders Club, $19](https://pay.instaloops.com/b/aFa3cv9lK4AD8L5ccT83C3n).

Machine-readable pricing: [pricing.json](https://botrecipe.com/pricing.json).

## Directory of MCP servers and bots

[botrecipe.com/directory](https://botrecipe.com/directory/) lists public MCP servers and bots from the official MCP Registry. Submitting yours is free and every listing is reviewed. Agents can call `list_directory` on the MCP server.

## Contributing

Run a bot that works? [Submit a recipe](https://botrecipe.com/submit/) or open a pull request that adds one line under the right category: `- [Title](link) - One sentence on what it does.`

Please share only setups you have run yourself, and never include keys or secrets.

## License

[CC0 1.0](LICENSE) for this list. Recipe pages on botrecipe.com remain © Supa Humans.
