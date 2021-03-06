---
layout: journal
title: How to: Collecting Custom Dates in Drupal
tags: 
- drupal
- custom web development
- development
- drupal 7 development
- programming
- form-api
show_chat: true
show_contacts: false
---

The FormAPI, first introduced in Drupal 4, is a very powerful API that allows you to create forms effortlessly. Every major release of Drupal, the FormAPI has become more mature and flexible, allowing you to create full forms with fields, and provide ways of altering them on output with #after_build, or hook_form_alter, for example. In Drupal 7, the FormAPI has a 'date' type form element. This field generally is used to collect data such as a birthdate, or a date in the future. By default, it provides a month, day, and year option as 3 inline select drop downs. What if we need to be more specific, like collecting a credit card expiration date(s)? There are two requirements to that where Drupal has no way to set default formatting properties: we do not need to collect a day, and the years cannot be in the past. Let's start by defining our form element: $form['credit_card_expiration'] = array( '#type' =&gt; 'date', '#title' =&gt; 'Expiration Date',); Woohoo, we're on our way. Our date form field is now a part of our form: So, how can we get rid of the day part, and adjust our year options? With the #after_build property, we can set a callback on that form element. $form['credit_card_expiration'] = array( '#type' =&gt; 'date', '#title' =&gt; 'Expiration Date', '#after_build' =&gt; array('mymodule_expiration_date_alter'),);function mymodule_expiration_date_alter(&amp;$field) { unset($field['day']); unset($field['year']['#options']); for ($y = date('Y'); $y &lt; date('Y') + 10; $y++) { $options[$y] = $y; } $field['year']['#options'] = $options; return $field;} The result is now a Date field with two inline select drop downs for month and year, with year being from 2012-2021! As an added bonus, if you have <a href="http://drupal.org/project/date" target="_blank">Date</a> and <a href="http://drupal.org/project/date" target="_blank">Date Popup</a> modules enabled, you get more form field types: date_text and date_popup, both of which can have a couple of additional properties assigned, such as date_format. With the date_popup type, you get access to a jQuery style date picker which is extremely useful if you are collecting data, like a meeting or scheduling date. Our code is not that different: $form['schedule_date'] = array( '#type' =&gt; 'date_popup', '#title' =&gt; 'Schedule Date',); Hot damn! Another great reason to use date or date_popup is that you know the data you get will be consistent. Leaving date fields as text fields opens up a lot of room for user error and complicated validation logic. Keep it simple! The possibilities are endless.