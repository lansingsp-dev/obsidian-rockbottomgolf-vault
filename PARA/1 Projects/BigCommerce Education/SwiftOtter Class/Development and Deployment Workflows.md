#### Workflow

It's up to you to make `stencil pull` part of your development and deployment workflow, and the availability of this tool doesn't mean that your workflow will experience no challenges in relation to preserving theme configuration.

Chief among those challenges is the reality of deployment timelines. You may well pull your store's latest theme configuration and refresh `config.json` as a final step in your code update. But in typical deployment workflows, applying your shiny new theme upgrade won't be instantaneous. Pull requests, code review, QA testing ... these steps are usually a part of the deployment cycle. Whatever such latency exists in your workflow is time in which more theme settings may be modified by admin users!

Keep this reality in mind when designing a reasonable Stencil deployment process. Perhaps your pool of admin users, or your merchant's, is small enough that it's possible to enact a "theme freeze" during the release hardening phase. Or perhaps you need to routinely perform another `stencil pull` after code review and QA, before your final deployment. Whatever workflow you choose, just make sure you're not relying on presuming that no one modified Theme Styles today!

