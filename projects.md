---
layout: default
title: Technical Showcase
---

## Technical Project Portfolio

Things I am working on currently:

<ul style="list-style-type: none; padding-left: 0;">
  {% for page in site.pages %}
    {% if page.category == 'project' %}
      <li style="margin-bottom: 1rem; padding: 1.1rem 1.25rem; background: var(--bg-subtle); border: 1px solid var(--border-muted); border-radius: 10px;">
        <strong style="font-size: 1rem;">
          <a href="{{ page.url | relative_url }}" style="color: var(--accent);">{{ page.title }}</a>
        </strong>
        {% if page.description %}
          <p style="margin: 0.3rem 0 0; color: var(--text-muted); font-size: 0.875rem;">{{ page.description }}</p>
        {% endif %}
      </li>
    {% endif %}
  {% endfor %}
</ul>

## GitHub Repositories

Public repositories and open-source configurations from my GitHub profile:

<div id="repo-list"><p style="color: var(--text-muted); font-size: 0.875rem;">Loading repositories…</p></div>

<script>
  const username = "jyothisthaliath";
  const container = document.getElementById("repo-list");

  fetch(`https://api.github.com/users/${username}/repos?sort=updated&per_page=30`)
    .then(r => { if (!r.ok) throw new Error("Failed to fetch."); return r.json(); })
    .then(repos => {
      const filtered = repos.filter(r => r.name !== `${username}.github.io`);
      if (!filtered.length) { container.innerHTML = "<p>No public repositories found.</p>"; return; }

      let html = '<ul style="list-style:none;padding:0;">';
      filtered.forEach(repo => {
        const topics = repo.topics && repo.topics.length
          ? `<div style="margin:0.5rem 0;display:flex;flex-wrap:wrap;gap:0.35rem;">` +
            repo.topics.map(t => `<span style="background:var(--accent-muted);color:var(--accent);font-size:0.72rem;font-weight:600;padding:0.18rem 0.55rem;border-radius:9999px;border:1px solid var(--accent-light);">${t}</span>`).join('') +
            `</div>`
          : '';
        html += `
          <li>
            <strong><a href="${repo.html_url}" target="_blank" rel="noopener noreferrer">${repo.name}</a></strong>
            <p>${repo.description || 'No description provided.'}</p>
            ${topics}
            <small>${repo.language ? `<span>● ${repo.language}</span> &nbsp;` : ''}<span>Updated: ${new Date(repo.updated_at).toLocaleDateString()}</span></small>
          </li>`;
      });
      html += '</ul>';
      container.innerHTML = html;
    })
    .catch(err => { container.innerHTML = `<p style="color:#cf222e;">Error loading repositories: ${err.message}</p>`; });
</script>
