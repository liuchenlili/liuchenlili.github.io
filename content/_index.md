---
# Leave the homepage title empty to use the site title
title: ''
date: 2022-10-24
type: landing

design:
  # Default section spacing
  spacing: '6rem'

sections:
  - block: resume-biography-3
    content:
      # Choose a user profile to display (a folder name within `content/authors/`)
      username: admin
      text: ''
      # Show a call-to-action button under your biography? (optional)
      button:
        text: Download CV
        url: uploads/resume.pdf
      headings:
        about: ''
        education: ''
        interests: ''
    design:
      # Apply a gradient background
      css_class: hbx-bg-gradient
      # Avatar customization
      avatar:
        size: medium # Options: small (150px), medium (200px, default), large (320px), xl (400px), xxl (500px)
        shape: circle # Options: circle (default), square, rounded
  - block: markdown
    content:
      title: '📚 My Research'
      subtitle: ''
      text: |-
          I am currently a master’s student in Computer Technology at Zhejiang Gongshang University, specializing in knowledge graphs and artificial intelligence. I received my bachelor’s degree in Computer Science and Technology from Henan Polytechnic University, where I built a strong foundation in algorithms and engineering implementation.
          
          My research focuses on integrating large language models (LLMs) with knowledge graphs, particularly exploring multi-feature fusion techniques for knowledge representation and semantic retrieval. My first-author paper, “Multi-Feature Fusion Strategies for Enhancing Knowledge Graph Embedding,” has been accepted by IEEE Big Data 2025.
        
          In terms of engineering practice, I am skilled in backend technologies such as Spring Boot, Redis, RabbitMQ, and Docker, and I have hands-on experience with distributed systems and microservice development. I independently designed and implemented an LLM-based intelligent knowledge base system. In addition, I built a YOLO-based object detection system and contributed to developing a sign-language recognition teaching system, applying vision models to practical educational scenarios.
        
          I am passionate about combining artificial intelligence with real-world applications and aim to develop efficient and trustworthy data-intelligence systems.
    design:
      columns: '1'
---
