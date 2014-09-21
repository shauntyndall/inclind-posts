---
layout: journal
title: Washingtons Green Grocer has Relaunched!
tags: 
- integration
- amazon ses drupal integration
- amazon s3
- drupal html mail
- drupal customer balance
- drupal subscription services
- broadcast emails
- drupal messaging solutions
- send email with amazon and drupal
show_chat: true
show_contacts: false
---

Over the last couple of weeks, Inclind has been working with Ripe and the folks at Washingtons Green Grocer to implement a design overhaul of their branding and website. Major props to the Ripe team for bringing a fresh look to a cool business. But, the design wasn&#39;t all that changed! There were a number of tools and UI changes implemented for customers and staff to help manage orders more effectively, plus some new features as well. <p style="text-align: center; "><img alt="" src="/sites/default/files/wgg-2.jpg" style="width: 600px; height: 329px; " /> <h2>Customer UI</h2>One of the first things we tackled was making for a better customer experience, from the registration process to account management, system messages and more. Taking a cue from Ripe, we overhauled and rewrote the application status messages as well as the error messages so the front-facing display was more friendly and easy to understand for the user. <p style="text-align: center; "><img alt="" src="/sites/default/files/wgg-3.jpg" style="width: 600px; height: 310px; " /> <p style="text-align: center; ">&nbsp; <p style="text-align: center; "><img alt="" src="/sites/default/files/wgg-4.jpg" style="width: 600px; height: 492px; " /> <h2>HTML Mail &amp; Broadcast Emailing</h2>The underlying Drupal 6 mail framework was extended to send HTML formatted emails with templates, so every outgoing email from the application was branded with the new Green Grocer style, for a much better look and feel than standard plain text email. Along with this, we built a new interface to allow Zeke to filter down customers and email them a weekly personalized customer update. This way, he can send bulk emails to weekly customers, on demand customers, every other week customers, or customers with certain box types, for example. <h2>Amazon SES Cloud Based Email Service</h2>Going along with HTML formatted emails, we put some Amazon-muscle into Drupal by hooking it into the new <a href="http://aws.amazon.com/ses/" target="_blank">Amazon SES (Simple Email Service)</a> cloud based mail delivery service. By changing the configuration of Postfix on the server to route through Amazon, Green Grocer can now send up to 50,000 (and rising) emails per day, at the rate of 14 emails per second. This allowed Green Grocer to drop Constant Contact practically overnight. In the last week alone, they&#39;ve successfully sent around 30,000 emails, and can efficiently send 10,000 emails in 30 minutes. Every week, Zeke creates a new weekly email, selects the recipients, and off they go! <h2>Amazon S3 / Nginx / Memcache</h2>To handle the bulk of traffic Green Grocer experiences weekly, we hosted most of the theme/design assets on Amazon S3, as well as putting Nginx and Memcache on the dedicated webserver to make Drupal really fly. When 3-6k people hit the site to change their box every Monday at 9 AM, the server barely hiccups.&nbsp; The launch of the new Green Grocer website was met with very positive reactions from customers. The new branding changes also extended over into their social media campaigns, like Facebook, where they have gained almost 300 new followers in the first week. Soon, when Zeke moves his efforts into other metropolitan areas, other websites will open up branded for that city and run off the same application. We&#39;re very proud of this successful launch with another powerful example of how flexible Drupal can be! Website: <a href="http://www.washingtonsgreengrocer.com" target="_blank">Washington&#39;s Green Grocer</a>