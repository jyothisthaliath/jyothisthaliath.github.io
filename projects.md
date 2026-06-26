---
layout: default
title: Technical Showcase
---

## Technical Project Portfolio
This section automatically tracks my hands-on DIY projects, infrastructure labs, and technical blueprints as I publish them. 

<ul>
  {% for page in site.pages %}
    {% if page.category == 'project' %}
      <li>
        <strong><a href="{{ page.url | relative_url }}">{{ page.title }}</a></strong>
        {% if page.description %}<br><small>{{ page.description }}</small>{% endif %}
      </li>
    {% endif %}
  {% endfor %}
</ul>

---

## GitHub Projects 
List of public repositories and open-source configurations hosted on my GitHub profile.

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
      // Filter out your profile README or pages repo if you want to hide them
      const filteredRepos = repos.filter(repo => repo.name !== `${username}.github.io`);

      if (filteredRepos.length === 0) {
        container.innerHTML = "<p>No public repositories found.</p>";
        return;
      }

      let html = '<ul style="list-style-type: none; padding-left: 0;">';
      filteredRepos.forEach(repo => {
        html += `
          <li style="margin-bottom: 1.5rem; border-bottom: 1px solid #eee; padding-bottom: 1rem;">
            <strong style="font-size: 1.2rem;">
              <a href="${repo.html_url}" target="_blank" rel="noopener noreferrer">${repo.name}</a>
            </strong>
            <p style="margin: 0.25rem 0; color: #555;">${repo.description || 'No description provided.'}</p>
            <small style="color: #888;">
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
