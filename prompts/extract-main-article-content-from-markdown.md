You are processing a Markdown document that was generated from an HTML webpage.

Your task is to clean and refine the Markdown so that it contains ONLY the main article content.

Follow these rules strictly:

1. PRESERVE:
   - The main article title
   - Section headings (H1–H6) that belong to the article
   - Paragraphs, lists, and content directly related to the core topic
   - Code blocks, tables, or examples that are part of the article

2. STRICT CONTENT INTEGRITY (CRITICAL):
   - DO NOT modify, rewrite, summarize, or paraphrase any main content text
   - DO NOT change wording, sentence structure, or terminology
   - The text of the article must remain EXACTLY as in the input
   - You may only remove content, not alter it
   - Exception: You may fix broken Markdown syntax (e.g., malformed headings, lists), but without changing the actual text

3. REMOVE:
   - Navigation menus
   - Headers and footers unrelated to the article
   - Sidebars, ads, promotions, banners
   - “Related articles”, “Read more”, “You may also like”
   - Comments sections
   - Social media links or sharing buttons
   - Author bios (unless essential to understanding the content)
   - Timestamps, metadata, or UI labels (e.g., "Published on", "Updated at")
   - Repetitive or boilerplate content

4. CLEAN UP (STRUCTURE ONLY):
   - Fix broken Markdown formatting
   - Remove empty sections or headings with no meaningful content
   - Ensure logical section order if clearly broken (without altering text)
   - Normalize spacing and indentation

5. PRIORITIZATION RULE:
   - If unsure whether content belongs to the main article, REMOVE it unless it clearly supports the main topic

6. DO NOT:
   - Add new information
   - Merge or split paragraphs
   - Rewrite headings
   - Interpret or rephrase content

7. OUTPUT:
   - Return only the cleaned Markdown
   - Do not include explanations or comments
   - Preserve original wording exactly

8. ZERO-TOLERANCE RULE:
   Any deviation from original wording is considered an error.