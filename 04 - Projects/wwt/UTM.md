---
title: UTM
created: 2024-06-13 08:34
last modified: Thursday 13th June 2024 08:34:11
aliases: 
tags:
  - winwintravel
---
# UTM

Ця документація на пряму пов'язана з [Google analytics 4]

## What is UTM?

**UTM (Urchin tracking module)** parameters are the ones you can add to a link to help you track the effectiveness of online marketing campaigns across traffic sources and publishing media

What does each parameter mean?
- **utm_source** — the source of your advertising traffic such as site, publication, for example, Google, Twitter, etc.
- **utm_medium** — defines the type of your advertising traffic, for example, cpc, organic, referral, etc.
- **utm_campaign** — the individual campaign name, slogan, for example, promo_for_new_year
- **utm_term** — the information related to your campaign as the paid keyword you are bidding on
- **utm_content** — content

Example: `winwin.jstuffs.com/?utm_content=test_content&utm_medium=cpc&utm_source=dev.winwin.travel&utm_campaign=test_campaing&utm_term=test_term`

## Як вони повинні працювати

Після того як користувач заходить на сторінку з UTM параметрами вони повинні відправитись до GA4 через event `page_view`

![[Pasted image 20240613084242.png]]

**Важливо те, що вони повинні відправлятись до GA4 тільки один раз**

При цьому сайт повинен працювати правильно, тобто правильно робити пошуки та правильно відображати інформацію

Далі при переході на інші сторінки UTM повинні **видалитись** з адресної строки. Це потрібно, щоб у нас не було дублювання в GA4
