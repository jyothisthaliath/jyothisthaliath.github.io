---
layout: default
title: Contact
---

## Contact

If you would like to get in touch regarding professional inquiries, please use the form below.

---

<form action="https://formspree.io/f/xojodldd" method="POST" class="contact-form">

  <div class="form-group">
    <label for="name">Name</label>
    <input type="text" name="name" id="name" placeholder="Your full name" required>
  </div>

  <div class="form-group">
    <label for="email">Email Address</label>
    <input type="email" name="email" id="email" placeholder="you@example.com" required>
  </div>

  <div class="form-group">
    <label for="subject">Subject</label>
    <input type="text" name="subject" id="subject" placeholder="What's this about?" required>
  </div>

  <div class="form-group">
    <label for="message">Message</label>
    <textarea name="message" id="message" rows="6" placeholder="Your message…" required></textarea>
  </div>

  <!-- Honeypot anti-spam -->
  <input type="text" name="_gotcha" style="display:none">

  <div>
    <button type="submit" class="btn btn-primary" id="contact-submit">Send Message</button>
  </div>

</form>
