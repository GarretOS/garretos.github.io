---
title: "Section 1 Complete: Building My AI Engineering Foundation (Properly)"
date: 2026-02-26
categories: [AI Engineering, Learning Journey]
tags: [AI Engineering Transition, Python Foundations, Build in Public]
---

# Section 1 Complete: Building My AI Engineering Foundation

I finished Section 1 of my AI Engineering curriculum this week. There's nothing to demo, nothing to deploy, no output that looks impressive at a glance. Just a couple of GitHub repositories, a local development environment, and a set of notes that probably only make sense to me right now.

I've been sitting with that a little. There's something strange about spending real time on something and having so little to show for it visually. It made me realize how conditioned I am, coming from marketing, to measure progress by outputs. Campaigns have dashboards. Learning doesn't, at least not early on. That discomfort is something I'm getting used to.

## What I Built and Why It Mattered More Than I Expected

The work itself was straightforward on paper. I set up two repositories: `python-ai-foundations` for learning fundamentals and `ai-research-assistant-v1` for the application I'll eventually build. I also configured a virtual environment and installed only the packages I actually have a use for right now.

That last part is where I found myself pausing and thinking. I deliberately didn't install `requests` or `gradio`, even though they appear on plenty of beginner setup guides. My reasoning was simple: I'm not calling any APIs yet, and I'm not building any UI yet. Installing things speculatively felt like a small way of lying to myself about where I actually am in the process. I'd rather my environment reflect reality.

I did create a `.env` template file, which felt slightly contradictory given that logic. I don't need it yet either. But there's a difference between setting up a placeholder for a good habit and installing tools you're not equipped to use. Keeping API keys out of source code is the kind of practice that should feel automatic, and the only way to make it automatic is to start early.

The piece of Section 1 that surprised me most was going back through CS fundamentals: syntax, interpreters, data types, data structures, control flow, and functions. I thought this would feel tedious, like reviewing things I already knew. Instead, it felt clarifying. There's a difference between having used something and actually understanding it, and I'm noticing more gaps in my understanding than I expected. That's uncomfortable, but I think it's useful discomfort.

## The Shift I'm Actually Going Through

I keep coming back to something that's harder to articulate than the technical tasks: the way I need to think is fundamentally different here.

In performance marketing, you're working with a system that already exists. Your job is to tune it. Adjust the variables, read the signals, optimize. The system has guardrails. There's always a campaign structure, a platform, a framework someone else designed.

In engineering, you are designing the system. The decisions you make about structure, naming, dependencies, and documentation are not cosmetic. They compound. A messy foundation doesn't stay contained to the foundation.

I don't think I fully believed that before starting this. I believed it intellectually, the way you believe something you've read but haven't experienced. I'm starting to feel it now in small ways. Noticing why a clean repo matters, why documentation written now is easier than documentation written later, why the `.env` habit is worth ingraining before it's strictly necessary.

Section 1 was quiet work. But I think it was the right work to start with.

## What's Next

Section 2 shifts into territory I'm genuinely curious about: learning to use LLMs as engineering tools rather than just as assistants.

I'll be running structured experiments: comparing how outputs change between a basic prompt and a role-based prompt, testing few-shot examples, and documenting where models are reliable and where they're not. I'll also be building a reusable `llm_request()` function, something I can use as a consistent interface as the projects get more complex, and making a decision about which LLM provider to use for my capstone.

What I'm most interested in is developing a more honest mental model of how these systems actually behave. Not the hype version, not the dismissive version. Something grounded in actual observation. That feels like the right foundation before building anything on top of it.

More to come.
