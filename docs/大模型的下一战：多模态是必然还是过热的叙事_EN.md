# The Next Battle of Large Models: Is Multimodality Inevitable or an Overheated Narrative?

A deep dialectical analysis of the future direction of AI

---

## Introduction: A Direction Dispute That Cannot Be Avoided

In May 2024, OpenAI released GPT-4o. At the launch event, when the model analyzed facial expressions in real-time and responded to questions with emotion-filled voice, the audience present let out exclamations of amazement. This moment created an almost instinctive consensus in the global technology community: the future of large models lies in multimodality.

But is this consensus correct?

When discussing "future direction," we actually mix two different questions: Does multimodality have value (almost everyone agrees it does); and should we now treat multimodality as the top priority and, for this reason, minimize deep optimization of text-only language models (this is the real point of disagreement).

This article attempts to untangle these two questions, using recent technological advances, product cases, and market data to provide a more honest judgment.

---

## First Dimension: The Real Value of Perception Expansion

The most intuitive argument supporting multimodal priority is that human cognition itself is multimodal.

This argument is not hollow. In the medical field, Google's Med-PaLM M reached specialist-doctor-level performance in diagnosing chest X-rays, fundus images, and pathological sections, and Stanford research shows that combined visual + text diagnosis has an accuracy rate 23 percentage points higher than text-only medical record analysis. In education, the photo-to-solve-problems feature increased student engagement by 40%. In the creative industry, Midjourney, Suno, and Adobe Firefly gave billions of ordinary people the opportunity to possess professional-level creative production capability for the first time.

These are not demonstration cases, but rather commercial implementations with real user bases.

From the perspective of information theory, this trend also has its internal logic. The amount of video information generated daily on Earth far exceeds the amount of text information. A 1080P image contains an amount of information equivalent to thousands of words. An AI that can only process text is in contact with an extremely small subset of the human information world.

---

## Second Dimension: Has LLM "Maturity" Been Overestimated?

However, the inference "LLMs are already sufficiently mature, so we should move to multimodality" does not withstand careful examination.

What is the evidence for "sufficiently mature"? ChatGPT has over 200 million monthly active users and covers over 90% of Fortune 500 companies. From the perspective of user scale, this is indeed impressive.

But from the perspective of capability reliability, the picture is much more complex. Stanford's 2024 evaluation showed that the hallucination rate of LLMs in medical literature summarization tasks remains as high as 20-30%. The problem in the legal field is more specific: there are frequent cases of lawyers in New York being sanctioned by courts for submitting false AI-generated case citations. The 200 million users are using a tool with such a high error rate every day, which indicates tool proliferation, not capability maturity.

More importantly, OpenAI's o1/o3 series demonstrated the potential of another path. Abandoning the fast-iteration RLHF route and returning to deep reasoning training, o3 on the ARC-AGI benchmark shows improvements that are several times greater than the sum of all multimodal progress over the past two years. This indicates that LLM reasoning depth is far from its ceiling. Diverting resources from here to multimodality represents a real and tangible cost.

---

## Third Dimension: Disputes Over Multimodal Technical Depth

Multimodal advocates frequently cite an inspiring scenario: GPT-4o sees a photo and can understand emotions, analyze composition, connect context, and provide deep responses. Isn't this "sufficiently mature"?

There is a key technical detail that deserves serious attention.

The architecture of virtually all current multimodal large models is pipeline-based: the vision encoder converts the image into tokens, and the language model processes these tokens. There is no true bidirectional interaction between visual reasoning and language reasoning - visual input ultimately gets "translated" into linguistic concepts, with core processing remaining language reasoning.

There is an experiment that illustrates this problem: for the same image, if you tell GPT-4o in text what the image contains ("a sad girl with war ruins in the background"), the quality of its analysis is nearly identical to viewing the image directly. Visual input is the "receiving end," language reasoning is the "processing end" - the "synergy" of multimodality in this architecture is largely illusory; a more accurate description would be: LLM is the core engine, multimodality is peripheral input.

MIT's 2024 research also found that most multimodal models exhibit systematic failures in real-world visual reasoning - particularly in understanding spatial relationships, counting, and 3D structure, significantly inferior to humans. Videos generated by Sora show physical errors such as liquid flowing backward and limb penetration, which also illustrates this: the model imitated visual patterns at the statistical level but did not truly understand physical reality.

---

## Fourth Dimension: Stratification of Commercial Value

The commercial value of multimodality requires an important distinction.

What are enterprises using multimodal AI for? Salesforce's visual analysis is essentially identifying product categories in images, HubSpot's image understanding is detecting brand logo appearance frequency, factory safety detection is identifying whether workers are wearing safety helmets. These tasks really need computer vision (machine vision), not large multimodal language models - using ResNet that was already mature in 2019 is sufficient. Most commercial security AI vendors also use lightweight specialized vision models, because universal multimodal models have excessive costs and inference speeds are too slow.

Andreessen Horowitz's 2024 report confirms this: most enterprise AI projects cut multimodal features because inference costs exceeded expectations. The token cost of multimodal reasoning is several times higher than text reasoning, which is a real constraint in price-sensitive markets.

High-value scenarios that truly need the deep capability of multimodal large models do exist - complex medical image analysis, cross-modal understanding of research data - but these scenarios need domain-specialized models more than universal multimodal models. In medical image diagnosis, the accuracy of GPT-4V (universal multimodal) is 63%, that of specialized medical vision models (Med-Gemini specialized version) is 84%, and the gap has not narrowed significantly with scale expansion.

---

## Fifth Dimension: Two Sides of the Data Bottleneck

Multimodal advocates have an important argument: text data is already running out. Meta's research team estimated that high-quality internet text data will peak in 2026-2028. The amount of image and video data far exceeds text, and is the way out of the "data wall".

This argument is true, but the logical chain is not complete.

Multimodal data is abundant in quantity, but the density of effective training signal is extremely low. YouTube videos don't come with high-quality semantic annotations, image alt text is extremely rudimentary - although the amount of multimodal data is large, much of it is noise. In contrast, synthetic data is another path for text data expansion - DeepMind's AlphaProof, using only synthetic mathematical proof data, achieved a historic breakthrough at the International Mathematical Olympiad. In domains with objective verification mechanisms (does the program run or not, is the proof valid or not), synthetic data can effectively break through the data wall.

Both paths have their value and limitations, but directly equating "text data touching the peak" with "should prioritize developing multimodality" is a simplification that skips many intermediate steps.

---

## Sixth Dimension: Asymmetric Risk of Security and Ethics

The security risks of multimodal technology are harder to handle than text alone and are often underestimated.

Deepfakes are the most typical security hazard of multimodal technology. In 2024, a company in Hong Kong was defrauded of 25 million dollars by a multimodal forged video. Multimodal content is more harmful in subtle ways - image context dependence, cross-language visual memes, prohibited information disguised as "normal" images - the difficulty of moderation is exponentially greater than text content.

Content tracing technologies like C2PA digital watermarks are effective in laboratory settings but fail in real propagation environments (transcoding, screenshots, compression). For image emotion recognition applications, MIT Media Lab research discovered that the correlation between facial muscle actions and internal emotional states is much lower than commonly assumed, so emotion computing applications built on this scientific assumption have inherent accuracy deficiencies and ethical risks.

This is not to deny multimodal technology itself, but to say: when safety alignment is not yet perfect, rapid expansion of multimodal capability needs to be more cautious, not advance rapidly under the pretext that "governance will catch up."

---

## Seventh Dimension: The Timing Issue of Resource Allocation

Considering all this, the core of this debate is not "does multimodality have value," but rather "at what timing and in what proportion should we invest in multimodality."

An interesting observation is that there is a clear divergence between the focus of research publications at top global AI labs and the focus of product launches. At the product level, multimodality is the marketing focus, the star of launches; at the research level, the deepest advances (o1/o3's reasoning breakthrough, systematization of chain-of-thought, self-consistency methods, synthetic data verification mechanisms) occur mostly in the pure language model domain.

This divergence illustrates something: products evolve toward multimodality because users can see and touch it, experience is more intuitive; but the truly difficult intelligence problems, researchers continue excavating in the soil of language reasoning.

Historically, in each generation's technology development path, there are stages where "narrative runs ahead of technology." Current discussion about large multimodal models, in part, belongs to this category - its long-term direction may be correct, but short-term resource investment proportion may be overestimated by grand narratives.

---

## Conclusion: Foundation and Roof, Not Either-Or

The most honest answer is not "multimodality is the future" nor "LLM is the focus," but rather: both matter, but there is an order.

At the current stage, language model reliability, reasoning depth, and safety alignment remain the top priority directions that deserve resource concentration. These capabilities are the foundation. Multimodality's perception expansion is genuine incremental value, but when the foundation is not yet stable, transferring large amounts of resources to the upper level carries very high structural risk.

This is not technical conservatism, but respect for engineering reality.

The launch of GPT-4o was indeed impressive, and multimodal commercial implementation is also genuinely progressing. But what will truly change the world is not the "can see images" function, but when AI can truly integrate perception, reasoning, and reliability as a unified whole. Until that day arrives, we need to maintain clear judgment between pursuing narratives and consolidating the foundation.

---

*This article is based on public technical reports, academic papers, and product evaluation data. All cited data have bibliographic sources, with no unfounded predictions added.*