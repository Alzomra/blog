---
layout: page
title: Contact
permalink: /contact/
---

<form id="contact-form" action="https://blog-form.alzomra.workers.dev/" method="POST" onsubmit="handleFormSubmit(event)">
  <div>
    <label for="name">Name:</label>
    <input type="text" id="name" name="name" required>
  </div>
  <div>
    <label for="email">Email:</label>
    <input type="email" id="email" name="email" required>
  </div>
  <div>
    <label for="message">Message:</label>
    <textarea id="message" name="message" required></textarea>
  </div>
    <div
    class="cf-turnstile"
    data-sitekey="0x4AAAAAAAkr18nCdMwyNyrb"
    data-callback="javascriptCallback"
    ></div>
  <button type="submit">Send</button>
  <div id="form-status"></div>
</form>

<script
  src="https://challenges.cloudflare.com/turnstile/v0/api.js?onload=onloadTurnstileCallback"
  defer>
</script>

<script>
  async function handleFormSubmit(event) {
    event.preventDefault();

    const form = document.getElementById('contact-form');
    const statusDiv = document.getElementById('form-status');

    const formData = new FormData(form);

    try {
      const response = await fetch(form.action, {
        method: 'POST',
        headers: {
          'Accept': 'application/json',
        },
        body: formData
      });

      if (response.ok) {
        form.reset();
        statusDiv.innerHTML = '<p style="color:green;">Your message has been sent successfully!</p>';
      } else {
        statusDiv.innerHTML = '<p style="color:red;">Oops! Something went wrong. Please try again.</p>';
      }
    } catch (error) {
      statusDiv.innerHTML = `<p style="color:red;">Error: ${error.message}. Please try again later.</p>`;
    }
  }
</script>


<style>

form {
  background-color: #333;
  padding: 20px;
  border-radius: 5px;
  max-width: 600px; 
  margin: 0 auto; 
  box-sizing: border-box; 
}

input, textarea {
  width: 100%;
  max-width: 100%; 
  padding: 10px;
  margin-bottom: 10px;
  background-color: #222;
  color: #fff;
  border: 1px solid #444;
  box-sizing: border-box;
  border-radius: 4px;
}

textarea {
  height: 150px; 
  resize: vertical; 
}

button {
  background-color: #555;
  color: #fff;
  padding: 10px 15px;
  border: none;
  cursor: pointer;
  border-radius: 4px;
}

button:hover {
  background-color: #666;
}

</style>