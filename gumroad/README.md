# Hacking Gumroad

Gumroad was the very first audit we did at Hacktron — and the results blew us away.

We ran it using Gemini 2.5 Pro, backed by our swarm of hundreds of specialized agents — some pure LLM-based, some AST-based, some CodeQL-based, and others built for niche vulnerability classes, including many cutting-edge source code review agents, each laser-focused on a different weakness.

You can view the full pentest report here —— and we're proud to be the first to publicly release an AI-driven security audit on a live production system:

 👉 [Gumroad Pentest Report](/reports/Gumroad_01.pdf)


### Findings
For anyone in the security industry, these findings speak for themselves. These weren't theoretical bugs or generic checklist items. They were exploitable, high-impact vulnerabilities. The SQL injection alone posed a serious risk, and Gumroad moved quickly to remediate it.

| Issue ID        | Severity | Title/Description                                                      |
| --------------- | -------- | ---------------------------------------------------------------------- |
| GUM-01-001 WP1  | High     | DOM XSS via Unsafe `innerHTML` Assignment in Tiptap Raw Node           |
| GUM-01-003 WP1  | High     | DOM-based XSS via iframe.ly Embed Handling in `MediaEmbed.tsx`         |
| GUM-01-004 WP1  | High     | Stored XSS via Product Description Rendering                           |
| GUM-01-005 WP1  | High     | Stored XSS via Seller Display Name in Receipt Generation               |
| GUM-01-007 WP1  | Critical | SQL Injection in `ORDER BY` Clause via Unvalidated `sort_direction`    |
| GUM-01-008 WP1  | Low      | IDOR in Email Unsubscribe Functionality                                |
| GUM-01-009 WP1  | Low      | IDOR/BOLA in Affiliate Request Approval                                |
| GUM-01-010 WP1  | Low      | IDOR in Mobile Preorder Attributes API with Hardcoded Mobile Token     |
| _Miscellaneous_ |          |                                                                        |
| GUM-01-002 WP1  | Info     | Weak Host Validation in `isValidHost` Function                         |
| GUM-01-006 WP1  | Info     | Stored XSS via Unsanitized Third-Party Analytics Snippets              |
| GUM-01-011 WP1  | Low      | Unauthenticated Purchase Unsubscribe via IDOR in `PurchasesController` |
| GUM-01-012 WP1  | Low      | Potential XSS via Arbitrary HTML Upload to `files.gum`                 |


You can find all the vulnerabilities it reported here:  
👉 [Issues](https://github.com/HacktronAI/hacktivity/issues?q=is%3Aissue%20state%3Aopen%20label%3Agumroad). 


The crazy part is the false positive rate is very low, since we have multiple filtering agents removing any hallucinations. You can watch the symbiosis of Hacktron and our co-founder @msrkp working together on bugs. Also, all of these tickets came straight from Hacktron’s create_finding tool.


### Contact us

If you want to secure your apps and get an audit or be a design partner in building the future, reach out here: https://app.hacktron.ai/contact
