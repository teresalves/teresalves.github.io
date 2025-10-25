---
title: "Oh no! I clicked a malicious link!"
description: "Will my computer explode?"
summary: "What happens when we enter a website we should not have clicked?"
date: 2025-10-24T22:00:00+02:00
lastmod: 2025-10-24T22:22:22+02:00
draft: false
images: []
weight: 9999
categories: ["techteresa", "cybersecurity"]
tags: []
contributors: []
pinned: false
homepage: false
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---

I remember panicking when I was younger whenever I opened a malicious website or clicked those big green buttons that said "CLICK ME". And then I closed it right away, in panic.

Now that I have a bit more context I started looking into what exactly happens when you click them.

Common misconceptions:

- it will steal all your passwords ❌
- it will capture what you're doing in other tabs ❌
- it will inject a virus into your computer ❌

Just by opening this website, it won't steal your passwords. You can be tricked into inserting them somewhere - for example, if it looks like an exact replica of a website you usually use.

Each tab has its own isolated environment, so the browser will not let this website access your other tabs. It might however ask you for camera or microfone access, or even screen access. But if you do not alllow it, it can't see anything.

What it might do:

- automatically download a malicious file ✅
- track every single thing you type in that website, even if you don't submit it ✅
- trick you into giving it camera, microphone or screen access ✅

Even if it downloads a file, it will stay dorment until you actually open it. Without opening it, it can't really do anything. If you open it, you now have a computer virus! It can do absolutely anything - delete important files, crash you laptop, access important information, change permissions for camera/microfone usage, amongst other things. Note that whenever a file is downloaded you see the downloads executed in your browser. If you did not intend to download it, go ahead and delete it.

Note however, that some browser extensions can be explotaitable and might allow downloading things without the download notification. This is rare and you'd need to have some sketchy extension installed (which is probably filtered from the allowed extensions), but still be aware.

Sometimes malicious sites trick you into thinking you're in a particular store, like a bank home page, and ask you to input your credentials. In this case they can and will save your password. But that's the only one they will have access to, not any other (unless you input them here ofc). You don't need to submit the login for the data to be captured - if you wrote it or pasted it there, it is now compromised.

So what should I do?

- Don't panic! Just opening the website probably didn't even do anything. Close it and move on.
- Never trust an email that redirects you directly to where you need to insert your password. If you are unsure (and please be very skeptical), search for the website in question instead of accessing that link.
- Make sure you have an antivirus set up in your computer  - Windows Defender comes by default and should detect malicious files.
- If a website automatically downloaded a file you did not want, delete it immediately.
