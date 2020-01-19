---
layout: post
title:  "What happened when my project got on top of Hacker News"
date:   2017-07-18 11:38:57 +0100
categories: Google Analytics hacker news
---

This is analysis how much traffic I got from being on front page of hacker news, how it spreaded accross other social media. From which countries people came and what operating system and browser they use.

Few days ago, I have noticed, that people are posting about unix timestamp approaching 1.5B. Websites that they have linked were displaying either just current timestamp or time remaining in seconds. So, I was thinking, that this could be opportunity for my website [Timestamp Converter Online](http://timestamp.online/). So, I put together simple page, which is showing [timestamp countdown](http://timestamp.online/countdown/1600000000) in more human readable form.

I have submitted it to [hacker news](https://news.ycombinator.com/item?id=14765198) at around 23:00 my local time and I had very low expectations about getting any upvotes so I went to bed. However, when I have checked Google Analytics, I was shocked. There was 49 people on my website. This website have 5 users per day – which were mostly unrecognized bots.

# Timeline #
These are random snapshots when I have checked what is going on hacker news and on my website.

* 2017-07-13 23:11:39 – 49 users – big surprise:
![Screenshot 2017-07-13 23:11:39 - 49 users](/assets/2017-07-18-Screenshot_20170713-231139-1.png)
* 2017-07-13 23:14:36 – 5th position and I was surprised by their ranking algorithm:
![Screenshot 2017-07-13 23:14:36 - Position 5](/assets/2017-07-18-Screenshot_20170713-231436.png)
* 2017-07-13 23:51:27 – 345 users is maximum that I have seen:
![Screenshot 2017-07-13 23:51:27 - Realtime users](/assets/2017-07-18-Screenshot_20170713-235127.png)
* 2017-07-13 23:53:35 – 2nd position, this was the best that I have seen:
![Screenshot 2017-07-13 23:53:35 - Position 2](/assets/2017-07-18-Screenshot_20170713-235335.png)
* 2017-07-14 00:08:13 – Number of current users was slowly decreasing:
![Screenshot 2017-07-14 00:08:13 - Realtime Users](/assets/2017-07-18-Screenshot_20170714-000813.png)
* 2017-07-14 00:08:39 – And source of traffic moved to other social networks:
![Screenshot 2017-07-14 00:08:39 - Sources](/assets/2017-07-18-Screenshot_20170714-000839.png)
* Screenshot 2017-07-14 00:09:06 – Since it was midnight in Europe, it was kind of expected, that US will dominate active users:
![Screenshot 2017-07-14 00:09:06 - Countries](/assets/2017-07-18-Screenshot_20170714-000906.png)
* 2017-07-14 00:17:48 – Link is gone from HP. Based on discussion in following [thread](https://news.ycombinator.com/item?id=13857086) it made sense that this link is not as valuable as announcement of Go 2 or research from Google about deep learning and therefore mods took it down.:
![Screenshot 2017-07-14 00:17:48 - Link is gone from HP of hacker news](/assets/2017-07-18-Screenshot_20170714-001748.png)

It never occurred to me, that I should scroll down to check if it’s somewhere lower. So I fall asleep. When I woke up, I have checked stats. There was still around 40 people there!!! It didn’t make any sense to me, how it’s possible that there are still people from hacker news, when I was taken down. I have checked [Twitter Search](https://twitter.com/search?f=tweets&vertical=default&q=timestamp.online&src=typd) and I have discovered, that there are many bots that will tweet the post when it reaches cerating rank or number of points. This is where I have discovered, that there is [@hn_bot_top1](https://twitter.com/hn_bot_top1) which tweets all stories, that reach [first position](https://twitter.com/hn_bot_top1/status/885622123921854468). When I was looking for some other evidence, that the post was indeed first I have discovered [HN Rankinings](http://hnrankings.info/14765198/). This is where I have found out that I am still on first page.

![Rank for timestamp.online on hacker news.](/assets/2017-07-18-hacker-news-rank-number-1.png)

# Analysis #

And now some analysis how many people visited timestamp.online, from where, and what is their equipment. Google Analytics is using PST, so there is 9 hours difference between times reported here and screenshots above.

In it’s peak there was 2,276 people during one hour and then it was slowly decreasing. Second spike happened, when it got shared on [wykop.pl](https://www.wykop.pl/link/3827993/zostaly-4-godziny-do-unix-timestamp-1500000000/) and after that 3k people from Poland visited it.

![Google Analytics - timestamp.online Main Dashboard](/assets/2017-07-18-timestamp.online-main-dashboard.png)

## Location: 18,436 ##
1. USA: 38.69%
2. Poland: 16.96%
3. UK: 5.78%
4. Australia: 4.53%
5. Canada: 3.90%
6. Germany: 3.55%
7. Japan: 2.78%
8. India: 2.78%
9. Netherlands: 1.71%
10. Argentina: 1.30%

## Browser: 18,436 ##
1. Chrome: 61.14%
2. Safari: 16.77%
3. Firefox: 8.84%
4. Android Webview: 7.08%
5. Safari (in-app): 3.55%
6. Edge: 0.77%

## OS: 18,436  ##

1. Macintosh: 27.31%
2. Windows: 23.92%
3. Android: 22.48%
4. iOS: 17.47%
5. Linux: 8.31%
6. Windows Phone: 0.20%

When I compare [browser](http://gs.statcounter.com/browser-market-share) or [OS](http://gs.statcounter.com/os-market-share) with general population, I can see big differences. Even when compared with more developer focused websites, statistics for [browser](https://www.w3schools.com/browsers/default.asp) and [OS](https://www.w3schools.com/browsers/browsers_os.asp) looks differently. There is way more Macintosh users than there should be.

## Referrers ##
![GA - Referrers - timestamp.online](/assets/2017-07-18-timestamp.online-referrers-all.png)

### By Date ###
* 2017-07-12: 7
* 2017-07-13: 10,947
* 2017-07-14: 6,696
* 2017-07-15: 536

### By Sources: ###

1. None: 46.72%
2. news.ycombinator.com: 33.40%
3. wykop.pl: 6.72%
4. t.co: 5.18%
5. m.facebook: 2.26%

First, I was confused, why there is so many people with referrer Direct / None, but then I have learned, that it [means](https://support.google.com/analytics/answer/6205762?hl=en#flowchart), that there was no referrer nor cookie, so it’s most likely in-app browsers.

#### Source None (1): 8,613  ####

1. USA: 36.47%
2. Poland: 22.20%
3. Australia: 5.02%
4. UK: 4.78%
5. Germany: 3.25%

#### Source news.ycombinator.co (2): 6,157 ####

How it was shared [there](https://news.ycombinator.com/item?id=14765198).

1. USA: 51.10%
2. UK: 8.04%
3. Canada: 5.23%
4. Australia: 4.48%
5. Germany: 3.85%

#### Source wykop.pl (3): 1,239 ####

How it was shared [there](https://www.wykop.pl/link/3827993/zostaly-4-godziny-do-unix-timestamp-1500000000/).

1. Poland: 87.49%
2. UK: 3.79%
3. Germany: 2.58%

#### Source t.co (4): 955 ####

How it was shared [there](https://twitter.com/search?f=tweets&vertical=default&q=timestamp.online&src=typd).

1. USA: 33.61%
2. Japan: 28.90%
3. UK: 5.03%
4. Canada: 3.98

#### Source Reddit (6): 368 ####

How it was shared [there](https://www.reddit.com/domain/timestamp.online/). It was very interesting to see, how the number of votes is going up and down all the time.

1. USA: 27.45%
2. Germany: 11.14%
3. UK: 10.60%
4. Netherlands: 5.16%
5. Poland: 3.53%

## Behavior ##

From 18k people at least 2k people clicked on something. I would expect this number to be lower.

![timestamp.online - Flow](/assets/2017-07-18-timestamp.online-flow.png)

There are also links to my other sites where each of them got around 200 visits.

# Hosting #
I have my websites on [Savana](http://www.savana.cz/?aid=1905c689) with the cheapest plan [Savana 500](https://www.savana.cz/multihosting/). Load on my VM increased from 0.4 to 20 in that moment. In GA I can see, that average page load time was increased to 18s. However, when I check different sections I can see only 4s as average time. It would be better to know p95 than average.

![timestamp.online - Average Page Load Time](/assets/2017-07-18-timestamp.online-page-load-time.png)

# Further Analysis #
If you want to check raw data you can check either [raw logs](https://goo.gl/2YYmGF) or [awstats](http://stats.martinmajlis.savana-hosting.cz/timestamp.online/2017-07/cz/) with user public and password public. It may be interesting to look more closely how was the number of icomming people correlated with rank on hacker news or number of tweets. It’s also interesting, that awstats are showing completely different numbers than Google Analytics.

