---
title: "Prompting Is a Skill, Not a Trick. Here's the Experiment That Proved It."
date: 2026-04-07
categories: [Trained to Build, AI Engineering]
tags: [Prompting, ChatGPT, Amazon PPC, AI Tools, Prompt Engineering]
image:
  path: /assets/img/posts/prompting-is-a-skill-section2/post2-hero-analyst-reviewing-data.jpg
---

Everyone tells you to use AI when you're learning to code. Open ChatGPT. Ask it your questions. Let it explain the errors. It will speed everything up.

Nobody tells you that using AI badly is just as slow as not using it at all.

That's the thing I didn't expect from Section 2 of Louis-François Bouchard's Python for AI Engineering course.

On the surface, the section is a comparison of the top AI tools like ChatGPT, Claude and Gemini. How they were built, what makes each one different, when you might use one over another.

But the lesson that actually stuck wasn't about the tools at all.

It was about communication. Specifically, how the way you talk to AI determines everything about what you get back.

This post is about that lesson. And about the experiment that proved it.

---

## A Quick Note on the Tools

I use ChatGPT Plus as my main tool. The experiment in this post ran entirely on it.

Claude and Gemini are part of the course material and I have free accounts on both. But this isn't a three-way comparison. It's a prompting experiment on one tool with one dataset.

The course gives each tool its own lane. ChatGPT for versatility and general tasks. Claude for structured content and nuanced reasoning. Gemini for scale, with a context window large enough to process entire codebases in a single pass.

I found that last detail genuinely surprising. I'd been thinking of these tools as roughly interchangeable. They're not. Though with how fast these models are evolving, that might not be true for long.

The smarter question isn't which model is best. It's which one fits the task. You can't figure that out until you know how to talk to them.

---

## Prompting 101

Section 2 covers five techniques:

1. Zero-shot is asking directly with no setup.
2. Role prompting assigns the model a persona before the task.
3. Few-shot means showing it examples of what good output looks like.
4. Chain-of-thought asks it to reason step by step.
5. Iterative prompting refines the output through follow-up.

Role prompting clicked for me right away. In PPC I never audit an account as a generalist. I step into a specific role depending on what the data needs.

Sometimes that's a bid strategist. Sometimes it's a listing analyst. The role shapes what you notice first. Role prompting works exactly the same way.

I wanted to test all five against a dataset I knew well enough to separate better reasoning from just better-sounding answers.

---

## The Experiment: Five Techniques, One Dataset

I took an anonymized Amazon PPC search term report and ran it through five prompting techniques in ChatGPT Plus. Same dataset. Same tool. The only variable was the prompt.

Steps one through four each ran in separate chats. Step five continued in the same chat as Step four, with two follow-up prompts building on the previous output.

One note on the data. I replaced campaign names, ad group names, and ASINs with neutral identifiers. I replaced the original search terms with unrelated product keywords.

I left all performance metrics untouched. Spend, clicks, orders, sales, conversion rate. Everything that matters for analysis remained exactly as it was.

The substitution wasn't perfect. Some search terms ended up as odd combinations that wouldn't appear in a real account. The AI analyzed all of them with equal confidence. It never flagged a single one as unusual.

A real analyst would have. I noted it and kept going.

### Before the Results

A few things worth stating plainly.

Each step builds on the previous one. These techniques rarely appear in isolation in real work, and the experiment reflects that.

The goal of the experiment was never keyword realism. It was to test how prompting changes analytical reasoning.

I evaluated each output the way I would evaluate a junior analyst's work. Was the reasoning accurate? Was it grounded in the data? Did the logic follow from the report?

Here is what happened.

---

## Step 1: Zero-Shot

```
Analyze this Amazon PPC search term report.
```

The output looked thorough. Headers, tables, generic benchmark comparisons, percentage breakdowns. A beginner would have trusted it immediately.

I didn't.

It was reciting the PPC playbook. Add negative keywords. Move winners to exact match. Lower bids on high-spend terms. Not wrong. Just not derived from the data. The same recommendations you'd give any account in any category without looking at a single row.

The most telling moment came in a section the AI titled "The Hidden Insight."

![Zero-shot hidden insight screenshot](/assets/img/posts/prompting-is-a-skill-section2/zero-shot-hidden-insight.png)
*The AI named it "The Hidden Insight." It was confident. It was also unearned. Full response [here](https://chatgpt.com/share/69b20716-0154-8006-a7cc-d16f312653d8).*

It concluded that some PPC problems are actually listing problems, but the reasoning was inferred from general patterns rather than demonstrated from the data.

That conclusion isn't wrong in principle. A real expert would look for it too. But only after identifying specific high-intent terms with strong clicks and weak conversions. That pattern is what justifies the conclusion.

The AI skipped that step.

It also concluded that discovery and performance campaigns were mixed together.

A search term report can’t confirm that. It shows what shoppers typed, not how your campaigns are structured.

The AI didn't make that distinction.

A junior analyst might act on that. An experienced one would keep reading. That's when the role prompting instinct kicked in.

---

## Step 2: Role Prompting

```
You are an expert Amazon PPC analyst. Analyze this Amazon PPC search term report.
```

One change. That's all it took.

The output didn't overhaul completely. But something shifted.

Zero-shot gave me playbook advice. Role prompting moved to row-level identification. Instead of flagging terms for looking broad, it named specific terms with actual dollar amounts and zero sales.

That's a real difference. Playbook advice tells you what to do in general. Row-level identification tells you where to act first.

The confident unsupported assumptions stayed though. The campaign structure claim came back. The AI concluded that ASIN targeting was leaking into keyword campaigns.

A search term report can hint at structure from the targeting column, but it can't prove campaign separation or leakage on its own.

![Role prompt ASIN leakage screenshot](/assets/img/posts/prompting-is-a-skill-section2/role-prompt-asin-leakage.png)
*The AI was confident about campaign leakage. The data didn't support it. Full response [here](https://chatgpt.com/share/69b22012-5a08-8006-b1b3-d34710b3fd06).*

Every row shown for B00TEST001 comes from ASIN, category, or auto targeting. None of these are keyword targeting types, and there's no evidence here that keyword campaigns triggered this traffic.

![Step 2 targeting column screenshot](/assets/img/posts/prompting-is-a-skill-section2/step2-targeting-column.png)
*B00TEST001's targeting breakdown. The leakage conclusion isn't in here.*

The AI recognized a familiar pattern and treated it like proof, instead of checking whether the report actually supported it.

Giving it a role made it sharper. It didn't make it more skeptical.

That gap mattered. So I showed it what good reasoning looks like.

---

## Step 3: Role Plus Few-Shot

```
You are an expert Amazon PPC analyst. Here are two examples of the kind of insight I am looking for:

Example 1: Search term: electric can opener for seniors | Spend: $45.20 | Orders: 8 | ACOS: 28%. 
Diagnosis: High intent specific query converting well below target ACOS. Isolate into exact match and increase bid by 15 to 20% to capture more volume.

Example 2: Search term: kitchen tool | Spend: $515.00 | Orders: 9 | ACOS: 75%. 
Diagnosis: Generic head term bleeding budget. CTR is acceptable but conversion rate is low, suggesting shoppers are not finding what they need. Reduce bid aggressively or move to a low budget discovery campaign.

Now analyze this search term report the same way. Go term by term on the highest spend search terms and give me the same level of specific, data driven diagnosis for each one.
```

The output didn't just improve. It changed character.

Steps 1 and 2 gave me narrative advice. Step 3 gave me a diagnostic audit. Term by term. Metrics cited. Actions tied to specific numbers.

It read like something a senior analyst would hand to a client.

The clearest illustration was "kitchen tool."

I used it as a negative example in the prompt. Generic head term. The kind of term you'd cut or deprioritize.

Zero-shot flagged it as a problem for the same reason. High spend, broad match, risky.

But the AI looked at the actual numbers and reached a different conclusion. ACOS of 9.2%. CVR of 27.5%. CPC of CAD 1.17.

"Kitchen tool" came back as the strongest term among the high-spend terms analyzed. The AI recommended scaling the exact match version and keeping the broad match from dragging it down.

It didn't copy the example. It used the reasoning framework and let the data lead.

![Step 3 kitchen tool diagnosis screenshot](/assets/img/posts/prompting-is-a-skill-section2/step3-kitchen-tool-diagnosis.png)
*The AI saw a different story in the same term. Full response [here](https://chatgpt.com/share/69b22027-f084-8006-83c1-e907ece5aa22).*

The jump from Step 2 to Step 3 was bigger than the jump from Step 1 to Step 2. Role prompting changed the focus. Few-shot examples changed the entire output structure. Those are two different things.

But the overconfident assumptions didn't disappear. The model said it was analyzing where spend was coming from across match types. That's possible from the raw report. But it never showed that breakdown.

It jumped straight to conclusions like "broad is weak" and "phrase is carrying performance." The match type data to support either wasn't there.

Better prompting improved the output. But it didn't stop the AI from making claims it couldn't support. That ceiling stayed the same regardless of how well I prompted.

The next prompt addressed that directly.

---

## Step 4: Role Plus Chain-of-Thought (Structured Reasoning)

```
You are an expert Amazon PPC analyst. Analyze this Amazon PPC search term report step by step in the following order: 

1. Spend efficiency (identify where most of the ad spend is going) 
2. Conversion patterns (which search terms convert well vs poorly) 
3. Keyword intent (high-intent vs broad or irrelevant traffic) 
4. Optimization recommendations (specific actions: scale, reduce bids, negate, isolate exact match) 

Base your conclusions strictly on the data in the report. Flag any conclusions you are not certain about based on the data alone.
```

One extra instruction: don't guess.

Step 3 showed the AI what good output looked like. Step 4 added a chain-of-thought structure by forcing the analysis through a fixed sequence.

The output followed the structure exactly. It built account benchmarks. It separated strong converters from weak ones. It organized recommendations into four buckets: scale, reduce bids, negate, isolate exact match.

It read like a first-pass audit. Not a summary. Not a playbook recap.

But the most important moment wasn't the structure. It was a single note buried in the recommendations section.

For B00TEST001, it stopped short of a strong recommendation. Without product context, it wouldn't commit. Scale aggressively or pull back cautiously? It couldn't say.

![Step 4 B00TEST001 uncertainty screenshot](/assets/img/posts/prompting-is-a-skill-section2/step4-b00test001-uncertainty.png)
*Step 4 response (partial). The first time in the experiment the AI admitted it didn't know enough to make a call. Full response [here](https://chatgpt.com/share/69b22054-1c0c-8006-b98a-867b149bd371).*

The AI analyzed B00TEST001 confidently in Steps 1 through 3, even though the report shows the code, not the product behind it. It worked only from the data in the report. The moment I asked it to flag uncertainty, it did.

I didn't make it smarter. I gave it permission to be honest about what the data couldn't tell it.

That's the most useful thing prompting did in this entire experiment.

The biggest improvement wasn't in structure or depth. It was in honesty. One sentence at the end of the prompt caused it.

Step 3 and Step 4 aren't on the same scale though. Step 3 is punchier, term by term, sharp calls. Step 4 is more disciplined. It showed its methodology more clearly and admitted some things it couldn't prove.

A junior analyst might trust Step 3 more because it sounds confident. An experienced one would rely on Step 4 because it shows where its conclusions end.

The structured prompt got close to what a real first-pass audit looks like. But overconfidence didn't disappear entirely. Some match type inferences crept back in, stated as fact without showing the supporting breakdown.

Step 5 kept the same chat open and asked harder questions.

---

## Step 5: Iterative Prompting

Steps 1 through 4 each ran in a fresh chat. Step 5 stayed in the same conversation and kept going.

Two follow-up prompts. Both built directly on the Step 4 output. The first follow-up asked for priorities.

```
Based on your analysis, what are the top 5 highest priority actions I should take this week, ranked by expected impact on ACOS? 
Be specific about which search terms, what bid changes, and why.
```

The output shifted character completely. No more audit structure. No more section headers and pattern summaries.

It gave me a ranked action list. Five items. Each one tied to a specific search term, a specific bid adjustment, and a clear expected impact on ACOS.

It read like something you'd hand to a client on Monday morning.

![Step 5 follow-up 1 action plan screenshot](/assets/img/posts/prompting-is-a-skill-section2/step5-followup1-action-plan.png)
*The output stopped being analysis and became a to-do list. Full response [here](https://chatgpt.com/share/69b22054-1c0c-8006-b98a-867b149bd371).*

That's not a small difference. Steps 1 through 4 told me what was wrong. Step 5 told me what to do about it first.

The second challenged the recommendation directly.

```
You recommended cutting bids aggressively on "can opener manual" because of the 91% ACOS. 
However, that term still generated 12 orders and meaningful revenue. 
Could there be a case for keeping bids stable and improving conversion instead? 
Walk through both sides of that decision using the data from the report.
```

This was the most interesting prompt in the experiment.

I wasn't asking for more analysis. I was challenging a recommendation the AI had already made.

It didn't fold.

It held its position and argued both sides using the actual numbers. Then it landed on a hybrid recommendation. Reduce bids moderately. Audit listing competitiveness. Review search term variants inside the cluster.

![Step 5 follow-up 2 hybrid recommendation screenshot](/assets/img/posts/prompting-is-a-skill-section2/step5-followup2-hybrid-recommendation.png)
*The prompt challenged the recommendation. The AI framed the decision like a real analyst. Full response [here](https://chatgpt.com/share/69b22054-1c0c-8006-b98a-867b149bd371).*

The reasoning it used to get there was the sharpest in the entire experiment. "The decision comes down to whether the problem is traffic cost or conversion efficiency." That's how a real analyst frames a gray area decision.

That level of reasoning didn't appear in any earlier step. It took a direct challenge to surface it.

The match type assumptions didn't disappear entirely. They never did across any step. But by this point the AI was doing something the earlier prompts couldn't produce. It was refining its own conclusions through pushback instead of just generating new ones.

That's the real difference iterative prompting makes. The first prompt starts the analysis. The conversation improves it.

---

## What the Experiment Proved

The most honest conclusion isn't the progression. It's what stayed the same.

Overconfident assumptions never fully disappeared. The AI inferred campaign structure from a report that can't confirm it. It made match type claims without showing the supporting breakdown. It stayed confident about B00TEST001 until I explicitly asked it to flag uncertainty.

Better prompting reduced the overconfidence. It didn't eliminate it.

The anonymization test made something else clear. I replaced real search terms with unrelated product keywords. The AI analyzed every substituted term with full confidence. It never flagged a single one as unusual. A real analyst would have noticed something was off within the first few rows.

That gap matters. Prompting skill gets you closer to expert-level output. It doesn't replace the expert. The model still needs someone in the chair who knows when the reasoning is sound and when it's just convincing.

---

## What to Do Differently Now

This experiment started as a course exercise. It ended as something more useful.

I went in thinking prompting was about finding the right words. I came out knowing it's about controlling how the AI reasons. That's a different skill entirely.

The technique matters less than the intention behind it. Role prompting works because you're telling the AI what lens to use. Few-shot works because you're showing it what good looks like. Chain-of-thought works because you're forcing it to slow down. Iterative prompting works because you're willing to push back.

None of that is magic. It's just deliberate communication.

I've been doing PPC for five years. I already knew how to read a search term report. What the experiment showed me is that the AI gets closer to useful when I bring that knowledge into the prompt, not just into the evaluation.

That's the part nobody tells you. The domain expertise doesn't become less important when you use AI. It becomes the thing that makes AI actually work.

And honestly, that surprised me. I expected the techniques to be the main lesson. They were. But they only worked because I knew enough to evaluate what came back. Prompting is the skill. Domain knowledge is what sharpens it.

---

## What's Next

This experiment came from Section 2 of Louis-François Bouchard's Python for AI Engineering course. The theory section. The part where you learn how the tools work before you touch any code.

Section 3 is where the building starts.

Five beginner projects. Each one introducing a new Python concept. Each one built with an LLM alongside.

I'm not just building the course projects though. Post 3 will be something different. I'm going to build a custom Python tool for Amazon PPC analysis. Something I'd actually use at work.

That's the point of this whole thing. Learn the skill. Apply it somewhere real.
