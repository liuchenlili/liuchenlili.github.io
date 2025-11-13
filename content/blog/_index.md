---
title: Blog
view: article-grid
type: landing

design:
  # Section spacing
  spacing: '5rem'

# Page sections
sections:
  - block: collection
    content:
      title: blogs
      text:  my blogs and articles.

      page_type: blog
      # Choose how many pages you would like to display (0 = all pages)
      count: 0
      # Filter on criteria
      filters:
        author: ''
        category: ''
        tag: ''
        exclude_featured: false
        exclude_future: false
        exclude_past: false
        publication_type: ''
      # Choose how many pages you would like to offset by
      offset: 0
      # Page order: descending (desc) or ascending (asc) date.
      order: desc
      design:
        # Choose a layout view
        view: card
        # Reduce spacing
        spacing:
          padding: [0, 0, 0, 0]

---
