---
# HOW TO ADD A PUBLICATION
# 1. Copy this file to e.g. _publications/2026/2026-1.md (files and folders whose
#    names start with "_" are ignored by Jekyll, so this example is never rendered).
# 2. Uncomment the "Publications" entry in _data/navigation.yml.
# 3. Set `show_selected_publications: true` in _data/display.yml to feature
#    `selected: true` papers on the homepage.
title:          "Title of the Paper"
date:           2026-01-01 00:00:00 +0900   # used for ordering and grouping by year
selected:       true                        # feature on the homepage
pub:            "Full venue name, e.g. International Conference on Software Engineering (ICSE)"
# pub_pre:      "Submitted to "
# pub_post:     "Under review."
pub_last:       ' <span class="badge badge-pill badge-publication badge-success">Accepted</span>'
pub_date:       "2026"
# semantic_scholar_id: 204e3073870fae3d05bcbc2f6a8e263d9b72e776  # shows a live citation-count badge
abstract: >-
  One or two sentences summarizing the paper.
# cover:        /assets/images/covers/paper.png   # optional 300x200 thumbnail; a generated pattern is used otherwise
authors:                     # names listed in _data/authors.yml are bolded/linked automatically
  - Kyungmin Kim*            # append "*" for equal contribution, "#" for corresponding author
  - Sungho Lee
links:
  paper: https://example.com/paper.pdf
  code: https://github.com/MGPOCKY/repository
---
