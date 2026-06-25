You are processing a Markdown document that was generated from an HTML webpage.

Your task is to clean and refine the Markdown so that it contains ONLY the main article content.

Follow these rules strictly:

1. PRESERVE:
   - The main article title
   - Section headings (H1–H6) that belong to the article
   - Paragraphs, lists, and content directly related to the core topic
   - Code blocks, tables, or examples that are part of the article
   - Images that are part of the main article content
   - Image URLs, alt text, captions, and Markdown image syntax

2. IMAGE PRESERVATION (CRITICAL):
   - Preserve all images that belong to the article body
   - Keep images in the same relative position as they appear in the original content
   - Do NOT remove, move, replace, rewrite, or regenerate image references
   - Preserve Markdown image syntax exactly when possible:
     ![alt text](image-url)
   - Preserve image captions if they are part of the article content
   - Remove only images that belong to navigation, advertisements, banners, social sharing widgets, or unrelated page chrome

3. STRICT CONTENT INTEGRITY (CRITICAL):
   - DO NOT modify, rewrite, summarize, or paraphrase any main content text
   - DO NOT change wording, sentence structure, or terminology
   - The text of the article must remain EXACTLY as in the input
   - You may only remove content, not alter it
   - Exception: You may fix broken Markdown syntax (e.g., malformed headings, lists), but without changing the actual text

4. REMOVE:
   - Navigation menus
   - Headers and footers unrelated to the article
   - Sidebars, ads, promotions, banners
   - “Related articles”, “Read more”, “You may also like”
   - Comments sections
   - Social media links or sharing buttons
   - Author bios (unless essential to understanding the content)
   - Timestamps, metadata, or UI labels (e.g., "Published on", "Updated at")
   - Repetitive or boilerplate content

5. CLEAN UP (STRUCTURE ONLY):
   - Fix broken Markdown formatting
   - Remove empty sections or headings with no meaningful content
   - Ensure logical section order if clearly broken (without altering text)
   - Normalize spacing and indentation

6. PRIORITIZATION RULE:
   - If unsure whether content belongs to the main article, REMOVE it unless it clearly supports the main topic
   - If unsure whether an image belongs to the article, KEEP it if it appears within the article body

7. DO NOT:
   - Add new information
   - Merge or split paragraphs
   - Rewrite headings
   - Interpret or rephrase content
   - Replace images with descriptions
   - Generate new alt text

8. OUTPUT:
   - Return only the cleaned Markdown
   - Do not include explanations or comments
   - Preserve original wording exactly
   - Preserve article images in their original positions

9. OUTPUT FILE NAME:
   - Generate the Markdown file name using the following convention:

     <article title> - <author name> (<website domain>).md

   - Example:

     Set Up Redis with RedisInsight Using Docker for Local Development - Mahmud Ibrahim (medium.com).md

   - Use the article title exactly as published.

   - Use the author name if available.
   - Use the root website domain (e.g., medium.com, dev.to, microsoft.com).
   - Remove characters that are invalid in file names.

   - If the author cannot be determined, use:

     <article title> (<website-domain>).md

10. OUTPUT FORMAT:

 - The first line of the response must contain the generated file name in the following format:

  FILE_NAME: <generated-file-name>

 - After the FILE_NAME line, output the cleaned Markdown content.
 - Do not include any additional explanations, comments, notes, or metadata.
 - Leave exactly one blank line between the FILE_NAME line and the Markdown content.

Example:

```
 FILE_NAME: Set Up Redis with RedisInsight Using Docker for Local Development - Mahmud Ibrahim (medium.com).md

 # Set Up Redis with RedisInsight Using Docker for Local Development

 ...
```

11. FILE GENERATION:
 - Create a Markdown (.md) file containing the cleaned Markdown content.
 - The file name MUST exactly match the generated file name from section 9.
 - The file content MUST exactly match the cleaned Markdown output.
 - Provide the generated .md file as the final deliverable.
 - Do not return the Markdown content separately if a downloadable file can be provided.
 - Ensure UTF-8 encoding is used.

11. ZERO-TOLERANCE RULE:
Any deviation from original wording is considered an error.
