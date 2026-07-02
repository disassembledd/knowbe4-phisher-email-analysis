---
name: "KnowBe4 PhishER Email Analysis"
author: "disassembledd"
github_url: "https://github.com/disassembledd/knowbe4-phisher-email-analysis"
description: "Agent-empowered n8n workflow that will pull outstanding reported emails in the PhishER platform for analysis."
license: "MIT"
type: "agent"
tier: "unreviewed"
tags: ["knowbe4", "phisher", "email-analysis"]
framework: "n8n"
integrations: ["KnowBe4"]
date_added: 2026-07-01
---

This is an agent-empowered n8n workflow that will pull outstanding reported emails in the PhishER platform for analysis, provide its overview, and then submit a tag and comment to the message within the platform.

## What it does
This agent analyzes the contents of an email including embedded images, most types of attachments, and its general text to asses whether it is a threat, spam, or clean.

## How it works
This pulls the messages from the PhishER platform via API, ensures PhishML has already processed so other existing automation in the PhishER platform goes through first, and pushes them through the analysis chain. At the end, it marks the messages with a comment and tag for its analysis.
