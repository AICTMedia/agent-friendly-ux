#Agent-Friendly UX — Replit Agent Skill
----------------------------------------

A Replit Agent skill that ensures websites are optimized for AI agent navigation and interaction. Based on Google's <a href="https://web.dev/articles/ai-agent-site-ux">Build agent-friendly websites</a> guide.

Author: Julia Logan, Head of SEO at <a href="https://aictmedia.com">AICT Media</a>


What It Does


AI agents are becoming a new class of website visitor. They navigate on behalf of humans using screenshots, raw HTML, and the accessibility tree — not a monitor. This skill ensures every site you build sends clean signals across all three channels.
Two Modes

1. Build Mode — Automatically enforces agent-friendly practices while creating websites:

    Semantic HTML for all interactive elements (<button>, <a>, not styled <div>s)
    Proper form labeling (every input linked to a <label> or aria-label)
    Stable, consistent layouts so agents can reliably find actions
    No ghost elements or transparent overlays hiding interactive content
    Appropriately sized click targets (minimum 24x24px, 44x44px recommended)
    Correct heading hierarchy and semantic page structure
    ARIA attributes for dynamic states (expanded, loading, disabled)
    Visible UI affordances for all actions (no hover-only or gesture-only interactions)
    cursor: pointer on custom interactive elements

2. Audit Mode — Analyzes any existing website and produces a scored report:

    Visual analysis from screenshots (layout stability, element sizing, ghost elements)
    Structural analysis from HTML (semantic markup, form labels, ARIA, heading hierarchy)
    Findings organized by severity: Critical, Warning, Suggestion
    Specific fix recommendations for every issue found
    Score out of 10

Installation

    Copy the agent-friendly-ux folder into your Replit project at .agents/skills/agent-friendly-ux/
    The skill is automatically available — the agent will reference it when building or auditing web pages

File Structure

.agents/skills/agent-friendly-ux/
  SKILL.md    # The skill instructions (required)
  README.md   # This file

Usage
When Building Sites

The skill activates automatically whenever you ask the agent to create or modify web pages, components, forms, buttons, navigation, or layouts. No special prompt needed — just build as usual and the agent will follow the guidelines.
When Auditing Sites

Ask the agent to review any website for AI agent friendliness:

    "Check this site for AI agent friendliness: https://example.com"
    "Audit my app for agent-friendly UX"
    "Is this website optimized for AI agents?"

The agent will produce a structured report with a score and actionable recommendations.
The 10 Rules
#	Rule	Why It Matters
1	Use semantic HTML for interactive elements	Agents recognize <button> and <a> as interactive
2	Ensure stable, consistent layouts	Screenshot-based agents get confused by shifting elements
3	Eliminate ghost elements and transparent overlays	Agents discard elements that appear covered
4	Label all form inputs	Agents need labels to understand field purposes
5	Ensure interactive elements are large enough	Elements under 8 sq px get filtered out by visual analysis
6	Use cursor: pointer for clickable elements	Strong signal for actionability in visual analysis
7	Make all actions visible in the interface	Hidden actions are invisible to agents
8	Write clean, structured HTML	Agents parse the DOM to understand element relationships
9	Provide meaningful ARIA when needed	Helps agents understand dynamic element states
10	Ensure state changes are reflected in the DOM	Agents read attributes to understand current state
Quick Checklist

    All clickable elements use <button> or <a> (or have role + tabindex)
    All form inputs have associated <label> elements or aria-label
    Interactive elements have visible area > 8 sq px (prefer 44x44px)
    No transparent overlays covering interactive elements
    Layout is stable — key actions don't shift position across similar pages
    Page uses semantic HTML structure (nav, main, section, article, footer)
    Dynamic states reflected via DOM attributes (disabled, aria-expanded, aria-busy)
    All user actions have visible UI affordances
    Custom interactive elements use cursor: pointer
    Heading hierarchy is correct and sequential

References

    Build agent-friendly websites — web.dev
    The Accessibility Tree — web.dev
    WebMCP Proposal — Chrome Developer Blog

License

This skill is freely available for use and modification.
Add GitHub README and update author link for the AI agent UX skill

create a skill which keeps track of all this https://web.dev/articles/ai-agent-site-ux while creating sites
36 minutes ago

can it also be used to check existing sites and provide recommendations for improvement?
29 minutes ago

how do I add my authorship to the skill to make it publicly available so that people could know who created the skill?
28 minutes ago
Time worked14 seconds
Work done1 action
Agent Usage
$0.08

yes please - Julia Logan, Head of SEO at AICT Media, aictmedia.com
26 minutes ago
Time worked18 seconds
Work done1 action
Code changed
+9-6
Agent Usage
$0.09

create a readme file for submitting this skill to Github
1 minute ago

Done! Here's your README, ready for GitHub:
Agent-Friendly UX — GitHub READMEText
# Agent-Friendly UX — Replit Agent Skill A Replit Agent skill that ensures websites are optimized for AI agent navigation and interaction. Based on Google's [Build agent-friendly websites](https://web...

Make, test, iterate…
