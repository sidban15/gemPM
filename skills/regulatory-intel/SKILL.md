---
name: regulatory-intel
description: Performs regulatory research for the US and Canada for a given topic.
---
# Instructions
1.  **Input**: The skill receives a research topic (e.g., "crypto travel rule").
2.  **Research (US)**: Use Google Search to find relevant regulatory documents, news, and official guidance from US government agencies (e.g., Treasury, SEC, FinCEN) or reputable legal sources. Focus on `.gov` domains.
3.  **Research (Canada)**: Use Google Search to find relevant regulatory documents, news, and official guidance from Canadian government agencies (e.g., Department of Finance, OSFI, IIROC) or reputable legal sources. Focus on `.gc.ca` domains.
4.  **Summarize Findings**: For each country, synthesize the key regulatory requirements, upcoming changes, and important considerations related to the given topic.
5.  **Output**: Save the combined summary into a new Markdown file in the `RawNotes/` folder. The filename should be descriptive, like `RawNotes/regulatory_research_[topic_slug].md`. The content should clearly separate findings for the US and Canada.
