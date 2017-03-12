---
layout: page
title: Contact
---

<p>Yes, this contact form actually works. If you really want to test it, please write something in it. I do receive these submissions ;-)</p>

<form action="//formspree.io/{{ site.author.email }}"
      method="POST">
    <input type="email" name="_replyto" placeholder="{{ site.var_your_email }}">
    <input type="hidden" name="_next" value="{{ site.baseurl }}/thanks" />
    <input type="hidden" name="_subject" value="New submission from {{ site.url }}{{ site.baseurl }}" />
    <input type="text" name="_gotcha" style="display:none" />
    <textarea type="text" name="content" rows="8" placeholder="{{ site.var_your_message }}"></textarea>
    <input type="submit" value="Send">
</form>