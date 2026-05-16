---
layout: default
title: Home
description: Academic personal website of Haeyun Choi
---

# Haeyun Choi

<section class="intro">
  <div class="intro-text">
    <p>
      I am an incoming Ph.D. student in the <a href="https://datascience.virginia.edu/" target="_blank" rel="noopener noreferrer">School of Data Science at the University of Virginia</a>, advised by <a href="https://craigleili.github.io/" target="_blank" rel="noopener noreferrer">Prof. Lei Li</a> and <a href="https://sites.google.com/view/cheng-peng/" target="_blank" rel="noopener noreferrer">Prof. Cheng Peng</a>. Before beginning my Ph.D., I am working as a Research Scientist at <a href="https://corp.kt.com/eng/" target="_blank" rel="noopener noreferrer">KT R&amp;D Center</a> on vision-language-action (VLA) model development. I received my M.S. in Artificial Intelligence from <a href="https://www.postech.ac.kr/eng/index.do" target="_blank" rel="noopener noreferrer">POSTECH</a>, where I was a member of the <a href="https://cg.postech.ac.kr/" target="_blank" rel="noopener noreferrer">Computer Graphics Lab</a> advised by <a href="https://www.scho.pe.kr/" target="_blank" rel="noopener noreferrer">Prof. Sunghyun Cho</a>.
    </p>
    <p>
      My research interests lie broadly in <strong>computer vision</strong> and <strong>computer graphics</strong>, with a focus on building visual systems for real-world scenarios. I am currently interested in 3D scene representation and neural rendering under challenging conditions such as blur, noise, and sparse observations. More broadly, I aim to develop reliable visual intelligence systems at the intersection of vision, graphics, multimodality, and generative models.
    </p>
  </div>
  <img class="profile-image" src="{{ '/assets/images/profile/avatar.jpg' | relative_url }}" alt="Portrait of Haeyun Choi">
</section>

<section aria-labelledby="news">
  <h2 id="news">News</h2>
  <div class="news-list">
    {% for item in site.data.news limit:4 %}
      <div class="news-item">
        <span class="news-date">{{ item.date }}</span>
        <span>
          {% if item.url and item.link_text %}
            {{ item.text_before }}<a href="{{ item.url }}" target="_blank" rel="noopener noreferrer">{{ item.link_text }}</a>{{ item.text_after }}
          {% else %}
            {{ item.text }}
          {% endif %}
        </span>
      </div>
    {% endfor %}
  </div>
</section>

<section aria-labelledby="publications">
  <h2 id="publications">Publications</h2>
  <div class="publication-list">
    {% for pub in site.data.publications %}
      <article class="publication">
        <div class="publication-media">
          <div class="publication-thumb{% if pub.hover_thumbnail %} has-hover{% endif %}">
            <img class="thumb-default" src="{{ pub.thumbnail | relative_url }}" alt="{{ pub.alt }}">
            {% if pub.hover_thumbnail %}
              <img class="thumb-hover" src="{{ pub.hover_thumbnail | relative_url }}" alt="">
            {% endif %}
          </div>
          {% if pub.hover_thumbnail %}
            <div class="hover-hint">✓ hover to compare</div>
          {% endif %}
        </div>
        <div class="publication-body">
          <h3>{{ pub.title }}</h3>
          <p class="authors">{{ pub.authors }}</p>
          <p class="venue">
            {% if pub.location and pub.location != "" %}
              <span class="venue-name">{{ pub.venue }},</span>
              <span class="venue-meta">{{ pub.location }}{% if pub.year and pub.year != "" %}, {{ pub.year }}{% endif %}</span>
            {% elsif pub.year and pub.year != "" %}
              <span class="venue-single">{{ pub.venue }}, {{ pub.year }}</span>
            {% else %}
              <span class="venue-single">{{ pub.venue }}</span>
            {% endif %}
          </p>
          {% if pub.award and pub.award != "" %}
            <p class="award">{{ pub.award }}</p>
          {% endif %}
          <p class="pub-links">
            {% for link in pub.links %}
              <a href="{{ link.url | relative_url }}" target="_blank" rel="noopener noreferrer">{{ link.label }}</a>
            {% endfor %}
          </p>
        </div>
      </article>
    {% endfor %}
  </div>
</section>
