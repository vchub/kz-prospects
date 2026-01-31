# Structural and Technical Obstacles to Cost-Per-Action Influencer Platform Dominance in the Kazakhstani Digital Economy

The digital marketing ecosystem in Kazakhstan is currently defined by a profound contradiction: while the country exhibits some of the highest digital literacy and internet penetration rates in Central Asia, the sophisticated "Cost-Per-Action" (CPA) influencer marketing models that have dominated Russia and Western markets remain conspicuously underdeveloped. Between 2024 and 2025, Kazakhstan witnessed a 51.3% increase in average mobile internet download speeds, providing the technical foundation for a surge in digital advertising that reached 14 billion KZT in the first half of 2025 alone [1]. However, the anticipated transition from traditional flat-fee influencer collaborations to performance-based CPA models has been stifled. An investigation into the market reveals that this stagnation is not the result of a single factor but rather a convergence of the overwhelming dominance of the Kaspi.kz ecosystem, technical barriers in attribution, a tightening regulatory and fiscal framework, and a cultural preference for guaranteed compensation over performance risk.

## The Hegemony of the Walled Garden: Kaspi.kz as a Structural Blocker

The most significant structural barrier to the scaling of independent CPA platforms like Perfluence or LTK in Kazakhstan is the absolute dominance of the Kaspi.kz ecosystem. Unlike fragmented markets where consumers move fluidly between social media, independent web browsers, and various e-commerce sites, the Kazakhstani consumer journey is increasingly circular and contained within a single super-app. As of 2024, marketplaces accounted for an extraordinary 84.9% of all online purchases in Kazakhstan, with Kaspi.kz leading the sector [1].

### The Integrated Ecosystem and the Death of the Tracking Link

The core mechanism of a CPA platform relies on the "tracking link"—a unique URL that follows a user from an influencer’s social media post to a completed purchase on a merchant's website. In Kazakhstan, this mechanism is fundamentally broken by the "Kaspi Flywheel." Kaspi.kz has successfully integrated QR payments, e-commerce, and fintech lending (notably Kaspi Red and Kaspi installments) into a seamless interface used by over 13.5 million monthly active users [3]. When an influencer promotes a product, the typical Kazakhstani consumer does not click a link to an external website; instead, they open the Kaspi.kz app to search for the item, verify its availability for Kaspi delivery, and utilize their existing credit lines or saved payment methods [1].

This behavior creates a technical "attribution wall." Standard cookie-based tracking or browser-level redirects cannot penetrate the closed environment of the Kaspi app. While merchants can utilize APIs to track orders, these integrations are designed for internal fulfillment and CRM management rather than external marketing attribution. The data suggests that as users enter these all-encompassing ecosystems—which now include banking, travel, groceries, and even government services—they become highly unlikely to seek alternative purchasing paths that would allow for third-party tracking [2].

### Retail Media and the Displacement of Influencer Budgets

The growth of "Retail Media"—advertising placed directly within marketplaces—is a secondary effect of this ecosystem dominance that directly competes with influencer CPA models. Retail media in Kazakhstan is growing at record speeds because it offers brands high relevance and immediate conversion within the very platform where the purchase is made [1]. For a brand, the unit economics of a Retail Media ad within Kaspi.kz are often more transparent and easier to manage than an influencer campaign where attribution is fuzzy. This shift is reflected in the 29% growth in internet advertising, where automation and measurability are becoming the primary drivers of brand investment [1].

**E-commerce and Digital Metrics (2024-2025)**

| Metric | Value / Percentage |
| :--- | :--- |
| Total Advertising Market Growth (H1 2025) | 17% [1] |
| Internet Advertising Revenue (H1 2025) | 14 billion KZT [1] |
| Marketplace Share of Total Online Purchases | 84.9% [1] |
| Mobile Internet Speed Growth (Y-o-Y) | 51.3% [1] |
| Internet Penetration Rate | 96% [2] |
| Digital Literacy of Population | 92% [2] |

## Technical Barriers and the Limitations of Attribution Infrastructure

The technical architecture of the Kazakhstani e-commerce market further complicates the implementation of CPA models. For a platform like Perfluence to function, it needs real-time data from the merchant regarding which influencer-driven clicks resulted in a "successful" (paid and delivered) action. In Kazakhstan, the most critical data is locked behind the APIs of Kaspi.kz and Halyk Bank [4].

### API Gaps and Integration Complexity

Analysis of the available API integrations, such as those provided by ApiMonster, shows a robust set of fields for order management, including `attributes.totalPrice`, `attributes.paymentMode`, and detailed customer info like `attributes.customer.cellPhone` [5]. However, there is a notable absence of standard "Affiliate IDs" or "Click IDs" within the core marketplace order structures. Merchants can set up webhooks for new orders, but connecting these orders back to a specific influencer's post requires a manual or semi-automated process using promo codes [5].

Promo codes, while functional, are a "leaky" attribution method. They are frequently shared on coupon-scraping sites, leading to brands paying commissions for sales that were not actually driven by the influencer. Furthermore, the integration of these systems into local CRMs like amoCRM or Bitrix24 remains a complex task for the average small-to-medium enterprise (SMB) in Kazakhstan, despite the availability of "turnkey" solutions [5]. This technical friction increases the "cost of entry" for brands wanting to move beyond simple flat-fee payments.

### The Shift Toward Zero-Click Search and AI Erosion

The broader technical environment is also moving away from the "click-out" model. The rise of AI tools like Gemini and Copilot, which provide answers directly on the search results page, has led to a 60% increase in "zero-click" searches [1]. This trend, combined with a 34.5% drop in click-through rates (CTR) for top search positions, means that influencers are finding it harder to drive traffic to external landing pages [1]. In a CPA model where "actions" are the only currency, this erosion of the traffic funnel makes the model less attractive to influencers who see their effort resulting in fewer trackable conversions, even as their influence on the "brand discovery" phase remains high.

## Regulatory and Fiscal Blockers: The Blogger Tax and Compliance Pressure

Perhaps the most daunting barrier to the scaling of CPA platforms is the rapidly evolving legal and fiscal landscape in Kazakhstan. The government has introduced a series of laws and tax code changes specifically designed to bring the "shadow" influencer economy into the formal sector.

### The 2023 Law on Online Platforms and Fines for Influencers

In September 2023, the Law "On Online Platforms and Online Advertising" came into force, officially defining an "influencer (blogger)" as a user who publishes information for entrepreneurial purposes [6]. This legislation mandates that influencers must register as individual entrepreneurs (IP) and pay taxes on their income [6]. For a CPA platform to operate legally at scale, every micro-influencer in its network must be a registered business entity.

The penalties for non-compliance are significant and scaled by the type of entity. Influencers face fines of up to 30 MCI (Monthly Calculation Index) for distributing false information and 15 MCI for failing to register their entrepreneurial activity [6]. These fines create a "compliance barrier" that is particularly burdensome for nano-influencers (1K-5K followers), who are the primary engine of high-volume CPA networks [8]. If a nano-influencer only expects to earn 10,000 KZT from a CPA campaign but faces a 55,380 KZT fine for improper registration, the economic logic of the model collapses [7].

**Penalty for Distribution of False Information (2024)**

| Entity | Fine in MCI (Monthly Calculation Index) |
| :--- | :--- |
| Individuals (General Users) | 20 MCI [6] |
| Influencers (Bloggers) | 30 MCI [6] |
| Small Businesses / Non-profits | 30-40 MCI [6] |
| Medium Businesses | 50-80 MCI [6] |
| Large Businesses | 100 MCI [6] |

### The 2026 Tax Code and the 16% VAT Wall

The fiscal environment will become even more restrictive on January 1, 2026, when a new Tax Code takes effect. The standard VAT rate is set to increase from 12% to 16% [9]. More importantly for global CPA platforms, foreign internet companies will be required to register in a special register of the State Revenue Committee and pay VAT on their Kazakhstani turnover [9]. Non-compliance can result in the blocking of the company's internet resources within the country [9].

This "fiscal wall" discourages foreign CPA platforms from entering the market unless they can guarantee high volumes. The administrative burden of navigating the "Digital Tenge" pilot project—which aims to automate VAT refunds but requires funds to be "marked" for specific purposes—adds another layer of complexity that typical affiliate networks are not equipped to handle [10].

## Competitive Landscape and the Failure of Traditional Adtech Models

The history of adtech in Kazakhstan is littered with failed attempts to transplant foreign models without sufficient localization. The "Fail Up Night" series at Astana Hub has documented numerous instances where entrepreneurs invested heavily in digital platforms only to struggle with the specificities of the local market [13].

### The Perfluence Niche and the Rise of Internal Ecosystem Platforms

While Russia's Perfluence has successfully run campaigns for brands like Megamarket, delivering 50,000 leads in a year, its success in Kazakhstan has been more localized and limited to brands with a strong cross-border presence [14]. In contrast, the most successful performance-based influencer initiatives are currently those that are built within existing marketplaces. Wildberries, for example, launched "Wibes" in 2025—a video shopping platform where influencers post 90-second reviews with direct purchase links [15]. Wibes has already exceeded 14 million users and 267 million content views [15].

This "internal CPA" model avoids all the technical attribution walls and fiscal registration hurdles that plague third-party platforms. Because Wildberries controls the platform, the payments, and the delivery, they can offer influencers a seamless way to earn commissions without the need for complex external tracking links. This has essentially "pre-empted" the market for independent CPA platforms.

### Ozon’s Hyper-Localized Entry Strategy

Ozon's expansion into Kazakhstan also highlights the necessity of deep integration. Sellers on Ozon Kazakhstan are advised to use local payment gateways like Kaspi.kz and Halyk Bank and to prioritize language localization [4]. Ozon’s affiliate program, while offering lower payouts (often around 0.90% to 5.18% per sale), is growing because it is part of a larger, trusted logistics and payment network [4].

**Marketplace Affiliate Comparison (2025/2026)**

| Platform | Typical Payout Range | Key Feature |
| :--- | :--- | :--- |
| Ozon Kazakhstan | 0.90% - 5.18% [16] | Deep local bank integration [4] |
| Wildberries (Wibes) | Variable / Social Commerce | AI-driven video shopping [15] |
| AliExpress | High / Global | Multilingual, established [18] |
| Perfluence (Third-party) | Action-based (CPA) | Multi-brand lead generation [14] |

## Cultural Maturity: The Persistence of the Flat-Fee Model

Cultural attitudes toward compensation and risk constitute a significant, albeit less tangible, barrier to CPA dominance. The influencer market in Kazakhstan remains heavily skewed toward a "prestige" economy rather than a "performance" economy.

### The "Brandformance" Compromise

Market reports indicate that 71% of brands still prefer fixed-fee models for influencer collaborations [19]. This is driven by the fact that many large players in the Kazakhstani market are still focused on building brand awareness rather than immediate conversion, a strategy now being termed "Brandformance" [2]. In this model, metrics like reach and engagement are prioritized over actual sales, which are often difficult to attribute accurately anyway due to the aforementioned ecosystem silos.

Influencers also prefer the stability of a flat fee. For a Macro-influencer (100K–1M followers), a single post can earn up to $600 [8]. Under a CPA model with a 5% commission, that same influencer would need to drive $12,000 in sales to match their flat-fee income—a risky proposition in a market where consumers often wait for "Kaspi Zhuma" (sales events) to make large purchases.

### The Micro-Influencer Demographics and Categories

The demographics of the influencer market also play a role. The core Instagram audience and creator base in Kazakhstan are women aged 18 to 34, with the "Beauty" category being the most dominant (12.65% of all influencers) [8]. Beauty products often have lower price points, meaning a CPA model requires massive volumes to be profitable for the influencer. Furthermore, the average engagement of Kazakhstani influencers is reported to be lower than the worldwide average, making performance-based models even less attractive to the creators themselves [8].

**Influencer Tier in Kazakhstan**

| Influencer Tier | Follower Count | Market Share (%) |
| :--- | :--- | :--- |
| Mega-influencers / Celebrities | > 1 Million | Limited [8] |
| Macro-influencers | 100K - 1 Million | Growing / Selective [8] |
| Mid-tier influencers | 20K - 100K | Moderate [8] |
| Micro-influencers | 5K - 20K | 54.5% (Dominant) [8] |
| Nano-influencers | 1K - 5K | High volume / High risk [8] |

### The Hyper-Localization Trend: Language as a Competitive Advantage

A critical factor that global CPA platforms often miss is the rapid shift toward Kazakh-language content. The preference for Kazakh-language media has reached 60–65% among younger users, and it is now considered a "must-have" for any brand wanting to communicate effectively with the local audience [2].

Global CPA platforms often operate with a "one-size-fits-all" interface, typically in English or Russian. This creates a cultural distance between the platform and the local influencers who are increasingly building their personal brands around the Kazakh language and culture. Platforms that fail to offer localized dashboards, Kazakh-language AI creative tools, and local customer support are finding themselves at a disadvantage compared to domestic startups or localized versions of Russian giants like Wildberries and Ozon [2].

## Financial Infrastructure and the Mass Payout Problem

The technical logistics of paying out commissions to thousands of influencers is a final, significant hurdle. In more developed CPA markets, services like Qiwi or Yandex Money provided a low-friction way to distribute funds. In Kazakhstan, the "mass payout" market is more complex.

### Payout Fragmentation and E-Wallet Trends

While Qiwi had a strong presence in Kazakhstan through its extensive terminal network, its online capabilities were always secondary to its cash-in terminals [20]. Local players like Wooppay have stepped in to provide financial services, but they are still in the process of scaling the integrated tax-automation features that are standard in more mature markets [22].

The introduction of the "Digital Tenge" and the requirement for electronic invoicing (e-Tamga) starting in 2026 means that a CPA platform must not only handle the payment but also ensure that the VAT is paid at the transactional level before the invoice is issued [10]. If a company does not have sufficient funds to cover the VAT, the system will block the invoice issuance, creating a potential liquidity crisis for a platform managing thousands of micro-payments [10].

## Future Trajectories and Strategic Conclusions

The failure of a large-scale, independent CPA influencer platform to achieve dominance in Kazakhstan is not a sign of a lagging market, but rather an indicator of a highly evolved, ecosystem-centric digital economy. The combination of the Kaspi.kz "walled garden," the technical friction of third-party attribution, and the aggressive formalization of the tax regime has created an environment where internal, marketplace-driven social commerce is the path of least resistance.

For a CPA model to scale in the future, it would need to overcome three primary challenges:

1.  **Attribution Innovation:** Moving beyond tracking links and promo codes toward deeper integrations with banking APIs that can track "offline" or "in-app" purchases driven by digital influence.
2.  **Compliance-as-a-Service:** The platform must act as more than just a marketplace for talent; it must provide a full-service legal and tax-automation layer that allows influencers to remain compliant with the 2023 Blogger Law and the 2026 Tax Code without administrative burden.
3.  **Hyper-Localization:** Dominance will require a "Kazakh-first" approach, focusing on the cultural nuances and language preferences of the dominant micro-influencer segment.

The current landscape suggests that the dominant "CPA platform" in Kazakhstan may not be a standalone entity like Perfluence at all, but rather the social commerce wings of the major marketplaces (Kaspi, Wildberries, Ozon) that have already built the necessary "flywheels" to bypass the structural and technical walls that currently inhibit independent players. The transition toward "Brandformance" and the growth of Retail Media indicate a market that values certain results but is currently forced to find them within the confines of established ecosystems. Moving forward, the players that can offer the measurability of CPA with the stability of the super-app environment will define the next era of Kazakhstani digital marketing.

### Works cited

1.  What Awaits Digital Marketing in Kazakhstan in 2025 - BYYD, accessed January 31, 2026, [https://www.byyd.me/en/blog/2025/07/what-awaits-digital-marketing-in-kazakhstan-in-2025/](https://www.byyd.me/en/blog/2025/07/what-awaits-digital-marketing-in-kazakhstan-in-2025/)
2.  What Awaits Digital Marketing in Kazakhstan in 2025 - Astana Hub, accessed January 31, 2026, [https://astanahub.com/en/blog/chto-zhdet-digital-marketing-v-kazakhstane-v-2025-godu](https://astanahub.com/en/blog/chto-zhdet-digital-marketing-v-kazakhstane-v-2025-godu)
3.  How Does Kaspi.kz JSC Company Work? – PortersFiveForce.com, accessed January 31, 2026, [https://portersfiveforce.com/blogs/how-it-works/kaspi](https://portersfiveforce.com/blogs/how-it-works/kaspi)
4.  Ozon Kazakhstan Site Setup Guide 2025 - SmartBuy, accessed January 31, 2026, [https://smartbuy.alibaba.com/tips/ozon-kazakhstan-guide](https://smartbuy.alibaba.com/tips/ozon-kazakhstan-guide)
5.  Integration with Kaspi.kz API (Kaspi (marketplace)) - Api Monster, accessed January 31, 2026, [https://apimonster.io/connector/service/kaspiKz/](https://apimonster.io/connector/service/kaspiKz/)
6.  Налоги и штрафы для блогеров Казахстана в 2024 году - Uchet.kz, accessed January 31, 2026, [https://uchet.kz/news/blogery-kazakhstana-pod-kontrolem-nalogi-i-shtrafy/index.php?MID=](https://uchet.kz/news/blogery-kazakhstana-pod-kontrolem-nalogi-i-shtrafy/index.php?MID=)
7.  Статус блогера в казахстанском законодательстве в 2024 г - MyBuh.kz, accessed January 31, 2026, [https://mybuh.kz/news/status-blogera-ofitsialno-zakrepili-v-kazakhstanskom-zakonodatelstve/](https://mybuh.kz/news/status-blogera-ofitsialno-zakrepili-v-kazakhstanskom-zakonodatelstve/)
8.  State of Instagram Influencer Marketing in Kazakhstan - HypeAuditor, accessed January 31, 2026, [https://hypeauditor.com/blog/state-of-instagram-influencer-marketing-in-kazakhstan/](https://hypeauditor.com/blog/state-of-instagram-influencer-marketing-in-kazakhstan/)
9.  Kazakhstan: New VAT rules for foreign internet companies effective January 1, 2026, accessed January 31, 2026, [https://kpmg.com/us/en/taxnewsflash/news/2025/11/kazakhstan-new-vat-rules-foreign-internet-companies-2026.html](https://kpmg.com/us/en/taxnewsflash/news/2025/11/kazakhstan-new-vat-rules-foreign-internet-companies-2026.html)
10. Kazakhstan | E-invoicing compliance | Thomson Reuters - Pagero, accessed January 31, 2026, [https://www.pagero.com/compliance/regulatory-updates/kazakhstan](https://www.pagero.com/compliance/regulatory-updates/kazakhstan)
11. Tax legislation updates in the Republic of Kazakhstan effective from 1 January 2026 | B1 Analytics, accessed January 31, 2026, [https://b1.ru/en/insights/tax-messenger/kazakhstan-tax-legislation-changes-30-october-2025/](https://b1.ru/en/insights/tax-messenger/kazakhstan-tax-legislation-changes-30-october-2025/)
12. Important Changes in Tax Law of Republic Kazakhstan - SCHNEIDER GROUP, accessed January 31, 2026, [https://schneider-group.com/en/news/countries/important-changes-in-tax-law-of-republic-kazakhstan-2026/](https://schneider-group.com/en/news/countries/important-changes-in-tax-law-of-republic-kazakhstan-2026/)
13. FAIL UP NIGHT: "MISTAKES ON THE WAY TO LAUNCHING A SUCCESSFUL STARTUP", accessed January 31, 2026, [https://astanahub.com/en/event/fail-up-night-oshibki-na-puti-k-zapusku-uspeshnogo-startapa/](https://astanahub.com/en/event/fail-up-night-oshibki-na-puti-k-zapusku-uspeshnogo-startapa/)
14. Cases | Perfluence Blog, page 2 out of 4, accessed January 31, 2026, [https://perfluence.net/en/blog/category/cases/page/2](https://perfluence.net/en/blog/category/cases/page/2)
15. Wildberries is betting on AI and robots to boost e‑commerce across Eurasia - EU Reporter, accessed January 31, 2026, [https://www.eureporter.co/internet-2/artificial-intelligence/2025/12/20/wildberries-is-betting-on-ai-and-robots-to-boost-e-commerce-across-eurasia/](https://www.eureporter.co/internet-2/artificial-intelligence/2025/12/20/wildberries-is-betting-on-ai-and-robots-to-boost-e-commerce-across-eurasia/)
16. Wildberries Affiliate Program with Payout 0.90% Per Sale | January 2026 - Cuelinks, accessed January 31, 2026, [https://www.cuelinks.com/campaigns/wildberries-affiliate-program](https://www.cuelinks.com/campaigns/wildberries-affiliate-program)
17. Ozon.ru. Онлайн-мегамаркет Affiliate Program with Payout 0.90% Per Sale - Cuelinks, accessed January 31, 2026, [https://www.cuelinks.com/campaigns/ozonru-affiliate-program](https://www.cuelinks.com/campaigns/ozonru-affiliate-program)
18. TOP 10 best affiliate programs for beginners in Russia - - Indoleads.com, accessed January 31, 2026, [https://indoleads.com/blog/earnings-on-affiliate-programs-top-10-best-affiliate-programs-for-beginners-in-russia/](https://indoleads.com/blog/earnings-on-affiliate-programs-top-10-best-affiliate-programs-for-beginners-in-russia/)
19. 71% of brands pay influencers on fixed fee model; 29% based on performance-linked model: Report - Buzzincontent, accessed January 31, 2026, [https://www.buzzincontent.com/influencer-marketing/71-of-brands-pay-influencers-on-fixed-fee-model-29-based-on-performance-linked-model-report-4448039](https://www.buzzincontent.com/influencer-marketing/71-of-brands-pay-influencers-on-fixed-fee-model-29-based-on-performance-linked-model-report-4448039)
20. QIWI PLC - NanduQ, accessed January 31, 2026, [https://nanduq.com/wp-content/uploads/2024/12/Qiwi-2019-Annual-Report-on-Form-20-F.pdf](https://nanduq.com/wp-content/uploads/2024/12/Qiwi-2019-Annual-Report-on-Form-20-F.pdf)
21. Which is a better payment solution for the Russian and CIS market - Qiwi or Yandex Money?, accessed January 31, 2026, [https://www.quora.com/Which-is-a-better-payment-solution-for-the-Russian-and-CIS-market-Qiwi-or-Yandex-Money](https://www.quora.com/Which-is-a-better-payment-solution-for-the-Russian-and-CIS-market-Qiwi-or-Yandex-Money)
22. Top Trending iPhone Finance Apps in Kazakhstan [December 9] | Similarweb, accessed January 31, 2026, [https://www.similarweb.com/top-apps/apple/kazakhstan/finance/trending/](https://www.similarweb.com/top-apps/apple/kazakhstan/finance/trending/)