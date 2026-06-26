---
layout: default
title: Technical Showcase
---

## Technical Project Portfolio
Things I am working on currently:  

<ul style="list-style-type: none; padding-left: 0;">
  {% for page in site.pages %}
    {% if page.category == 'project' %}
      <li style="margin-bottom: 1.5rem; border-bottom: 1px solid #eee; padding-bottom: 1rem;">
        <strong style="font-size: 1.2rem;">
          <a href="{{ page.url | relative_url }}">{{ page.title }}</a>
        </strong>
        {% if page.description %}
          <p style="margin: 0.25rem 0; color: #555;">{{ page.description }}</p>
        {% endif %}
      </li>
    {% endif %}
  {% endfor %}
</ul>

## GitHub Projects 
List of public repositories and open-source configurations hosted on my GitHub profile:

<div id="repo-list">Loading repositories...</div>

<script>
  const username = "jyothisthaliath";
  const container = document.getElementById("repo-list");

  fetch(`https://api.github.com/users/${username}/repos?sort=updated`)
    .then(response => {
      if (!response.ok) throw new Error("Failed to fetch repositories.");
      return response.json();
    })
    .then(repos => {
      const filteredRepos = repos.filter(repo => repo.name !== `${username}.github.io`);

      if (filteredRepos.length === 0) {
        container.innerHTML = "<p>No public repositories found.</p>";
        return;
      }

      let html = '<ul style="list-style-type: none; padding-left: 0; margin-top: 0;">';
      filteredRepos.forEach(repo => {
        // Generate tag badges if topics exist
        let tagsHtml = '';
        if (repo.topics && repo.topics.length > 0) {
          tagsHtml = '<div style="margin: 0.5rem 0; display: flex; flex-wrap: wrap; gap: 0.4rem;">';
          repo.topics.forEach(topic => {
            tagsHtml += `<span style="background-color: #f1f8ff; color: #0366d6; font-size: 0.75rem; font-weight: 600; padding: 0.2rem 0.5rem; border-radius: 2px;">${topic}</span>`;
          });
          tagsHtml += '</div>';
        }

        html += `
          <li style="margin-bottom: 1.5rem; border-bottom: 1px solid #eee; padding-bottom: 1rem;">
            <strong style="font-size: 1.2rem;">
              <a href="${repo.html_url}" target="_blank" rel="noopener noreferrer">${repo.name}</a>
            </strong>
            <p style="margin: 0.25rem 0; color: #555;">${repo.description || 'No description provided.'}</p>
            ${tagsHtml}
            <small style="color: #888; display: block; margin-top: 0.4rem;">
              ${repo.language ? `<span>● ${repo.language}</span> &nbsp;&nbsp;` : ''}
              <span>Updated: ${new Date(repo.updated_at).toLocaleDateString()}</span>
            </small>
          </li>
        `;
      });
      html += '</ul>';
      container.innerHTML = html;
    })
    .catch(error => {
      container.innerHTML = `<p style="color: red;">Error loading repositories: ${error.message}</p>`;
    });
</script>
