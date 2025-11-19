Step 1 — Define Scope and Objectives
1.1 define_goal()
Action: choose primary goal (educational/research/industry).
Example: "educational — course module + reference for students"
Deliverable: one-line mission statement saved as meta/goal.txt.
1.2 set_target_audience()
Input: skill-level options {novice, intermediate, advanced}
Example: audience = "intermediate (CS undergrads / junior ML engineers)"
Deliverable: meta/audience.txt
1.3 draft_core_topics()
Output: canonical list (save as meta/topics.md) — copy your list, e.g.:
Intro to AI & ML
What is Generative AI?
Types: GANs / VAEs / Diffusion Models
LLM Introduction & Architectures (Transformer, GPT, BERT)
Training, Datasets, Compute & Scaling
Applications & Case Studies
Ethics, Risks, Limitations
Future Trends, Conclusion, References
Acceptance criteria: goal, audience, and topic list exist and are approved (or set for self-approval).

Step 2 — Create Report Skeleton/Structure
2.1 — 2.7 build_skeleton() (automated folder + template creation)
Create folders: drafts/, figures/, references/, slides/, appendix/.
Generate files:
drafts/title_page.md (Title, Author, Date, Affiliation)
drafts/abstract.md (one-paragraph summary)
drafts/toc.md (auto-generated from headings)
drafts/introduction.md
drafts/sections/01_intro_AI_ml.md, … , drafts/conclusion.md, drafts/references.md
Pseudocode
function build_skeleton(topics):
    create_directories([...])
    for each topic in topics:
        create file drafts/sections/{index}_{slug(topic)}.md
    create title_page.md, abstract.md, toc.md, conclusion.md, references.md
Deliverable: a filled skeleton with section placeholders and brief 2–3 line notes per section describing what to write there.

Step 3 — Research and Data Collection
3.1 collect_sources()
Tasks:
Search for 10–15 primary sources: seminal papers (e.g., Transformer 2017), prominent reviews, official docs (OpenAI, Google), reputable blog posts, recent survey papers.
Save metadata (title, authors, year, url, short summary) into references/sources.csv and refs.bib.
3.2 extract_key_points()
For each source, write a 3–5 sentence summary and extract useful figures/diagrams. Save as references/summaries/{id}.md.
3.3 organize_materials()
Tag sources by section (e.g., “Architectures”, “Training”, “Applications”) to speed later writing.
Output example row (sources.csv):
id,pub_year,authors,title,url,tags,one_line_summary
arxiv2017,2017,Vaswani et al.,Attention Is All You Need,https://...,architecture;transformer,Introduced the Transformer architecture using self-attention...
Acceptance criteria: at least 12 high-quality sources with summaries and bib entries.

Step 4 — Content Development
4.1 write_section(section_file, references)
Use a standardized subsection template:
short intro (2–3 sentences)
definitions/keywords (highlighted)
detailed explanation (1–2 pages)
example(s) or analogy
key references (3–5)
4.2 add_figures_and_tables()
For architectural sections: include diagrams (Transformer block, encoder/decoder, attention flow).
For comparisons: make a table tables/model_compare.md (columns: Model, Year, Type, Parameters, Strengths, Weaknesses).
4.3 highlight_terms()
Maintain a glossary appendix/glossary.md with short definitions.
4.4 use_examples_and_analogies()
E.g., explain attention as “a soft spotlight on previous words” and show a worked example.
Pseudocode for writing loop
for file in draft_sections:
    content = render_template(section_template, data_for_section)
    write file content
Acceptance criteria: all main sections drafted as complete first-pass markdown files.

Step 5 — Visual and Technical Enhancement
5.1 create_tables_and_charts()
Example chart: “Scaling effects” sketch: rows = model (GPT-2/3/3.5/4), columns = parameters, token budget, sample tasks accuracy. (If exact numbers unavailable, use ranges and clearly label estimates.)
5.2 format_report(format)
Choose LaTeX if academic/print-quality; else Google Docs + export PDF.
Apply consistent styles: header levels, captioned figures, numbered equations.
5.3 add_code_snippets()
Provide short, safe pseudocode for:
forward pass of Transformer block
training loop skeleton (data loader, optimizer step, checkpointing)
Example pseudocode (transformer block)
def transformer_block(x):
    attn = multi_head_attention(x, x, x)
    x = layer_norm(x + attn)
    mlp = feed_forward(x)
    x = layer_norm(x + mlp)
    return x
Acceptance criteria: at least 6 good-quality figures; tables comparing popular LLMs; code snippets in appendix.

Step 6 — Review and Edit
6.1 proofread_and_edit()
Run mechanical checks (spellcheck), then technical validation:
Verify facts against sources (citations inline).
Recalculate any numbers shown in tables.
6.2 consistency_checks()
Ensure consistent terminology (e.g., LLM vs large language model) and citation style (APA / IEEE / ACM).
6.3 peer_review()
Get feedback from 1–2 colleagues or simulate review by using an external tool (e.g., Grammarly or review checklist). Record reviewer comments in reviews/.
6.4 apply_changes()
Triage comments into critical / medium / minor; implement.
Acceptance criteria: no major factual errors, grammar/spelling < 2 minor issues, at least one external review comment addressed.

Step 7 — Finalize and Export
7.1 final_format_and_export()
Build production-quality PDF:
If using LaTeX: compile main.tex → report.pdf
If using Docx: export as report.pdf
7.2 prepare_presentation()
Summarize report into slides.pptx (8–10 slides) with: Title, Key findings, Visuals, Use cases, Ethics, Future trends, Conclusion.
7.3 package_deliverables()
Put report.pdf, slides.pptx, refs.bib, appendix_code.md, and figures/ into deliverables.zip.

Acceptance criteria: download-ready artifacts exist in deliverables/ and pass a quick sanity check (openable PDF, slides, bib).
