---
title: "Contact"
what: contact
nodisqus: true
---

<p>If you'd like to contact me, feel free to fill out the form.</p>

<form action="https://formspree.io/ksp@keishasperkins.com" method="post" id="contact-form">
	<label for="name">Your Name</label>
	<input type="text" id="name" name="name">
	<label for="email">Your Email</label>
	<input type="text" id="email" name="_replyto">
	<label for="message">Message</label>
	<textarea name="message" id="message" cols="30" rows="10"></textarea>
	<input type="hidden" name="_next" value="../page/thank-you" />
	<input type="hidden" name="_subject" value="New Form Submission from Your Website!" />
	<input type="text" name="_gotcha" style="display:none" />
	<button class="button submit button-square" type="submit" form="contact-form" value="Submit">Submit</button>
</form>
