# Drupal at Extreme Scale: Verified Examples with Specific Numbers

Research compiled March 2026. Each entry includes source links for verification.

---

## 1. NBC Sports Digital: Olympics, Super Bowl, World Cup

NBC Sports Digital runs on Drupal (hosted on Acquia Cloud), covering **30,000+ sporting events per year**.

**Super Bowl LII (2018):**
- Peaked at **3.1 million concurrent streams** — the largest domestic streaming sports event in history at that time
- Delivered **546 million live streaming minutes**
- Total audience delivery averaged **106 million viewers**
- Source: [Next TV](https://www.nexttv.com/news/nbc-s-stream-super-bowl-lii-peaks-31m-concurrent-streams-417953), [Comcast Corporate](https://corporate.comcast.com/stories/nbc-sports-playmaker-media-powers-437-billion-live-streaming-minutes-across-super-bowl-lii-pyeongchang-winter-olympics-and-2018-fifa-world-cup)

**Rio 2016 Olympics:**
- **3.3 billion total streaming minutes**
- **2.71 billion live streaming minutes**
- **100 million unique visitors**
- Source: [Dries Buytaert blog](https://dri.es/drupal-goes-to-rio)

**PyeongChang 2018 Winter Olympics:**
- **1.86 billion live streaming minutes**
- Consumed across **32.8 million unique devices**
- Source: [NBC Sports press release](https://www.nbcsports.com/pressbox/press-releases/nbc-sports-playmaker-media-powers-4-37-billion-live-streaming-minutes-across-super-bowl-lii-pyeongchang-winter-olympics-and-2018-fifa-world-cup)

**2018 FIFA World Cup:**
- Combined with Super Bowl LII and PyeongChang: **4.37 billion live streaming minutes** total, **93 million unique users**
- Source: [Acquia blog](https://www.acquia.com/blog/how-nbc-sports-supports-biggest-media-events-online)

---

## 2. NASA: 2017 Total Solar Eclipse

NASA.gov runs on headless Drupal in an AWS cloud environment.

- **2,000,000+ concurrent users** at peak
- **40+ million page views in a single day** (other sources cite 90 million page views across nasa.gov and eclipse2017.nasa.gov)
- The largest web-traffic event in US government history at that time
- NASA.gov supports over **1 billion visits annually**
- Source: [Drupal.org case study](https://new.drupal.org/case-study/nasagov), [Deadline](https://deadline.com/2017/08/nasa-claims-40-million-watched-its-live-broadcast-of-the-great-american-eclipse-1202156753/), [Space.com](https://www.space.com/37939-great-american-solar-eclipse-nasa-web-record.html)

---

## 3. The Weather Channel (weather.com): Hurricane Sandy

Weather.com migrated entirely to Drupal on Acquia Cloud.

- **1 billion+ page requests in the week Hurricane Sandy hit**
- One of the highest-trafficked websites in the world to launch on an open-source CMS
- Experiences multiple massive traffic days every year during severe weather events
- Source: [Drupal.org case study](https://www.drupal.org/case-study/the-weather-channel-weathercom), [Dries Buytaert blog](https://dri.es/weather-com-using-drupal)

---

## 4. European Commission: 770 Sites, 2.2 Billion Page Views

The European Commission standardized on Drupal across its digital estate.

- **770 live websites**
- **700 million visits per year**
- **2.2 billion page views per year**
- Operated by **44 different services** across the Commission
- Transition took 4 years, involved analysis of 160 websites and 500+ stakeholder meetings
- Source: [Drunomics / Drupal4Gov EU 2026](https://drunomics.com/en/blog/drupal4gov-eu-2026-how-drupal-powers-european-governments-247), [Drupal.org](https://www.drupal.org/european-commission-and-european-union-institutions-agencies-and-bodies)

---

## 5. Australian Government (GovCMS): 320+ Government Sites

Australia's Federal Government chose Drupal as its preferred CMS through the GovCMS platform.

- **320+ government websites** on the GovCMS Drupal platform (as of 2020)
- Serves millions of Australian citizens yearly
- Includes large high-profile federal departments
- Launched in 2015, managed by the Department of Finance
- Source: [GovCMS](https://www.govcms.gov.au/content-management-and-web-hosting-government), [Drupal.org](https://www.drupal.org/govcms-australian-government-department-of-finance)

---

## 6. Grammy Awards (Grammy.com): Live Event Night Traffic

Grammy.com is built on Drupal, hosted on Acquia.

- **~5 million unique visitors** requesting **~20 million pages** on Grammy night and the day after
- Won the Best Media Website Built with Drupal award (Blue Drop Awards)
- Site receives the majority of its **entire lifetime traffic over the course of a single night**
- Acquia provided "white glove service" to handle the spike
- Source: [Dries Buytaert blog](https://dri.es/when-traffic-skyrockets-your-site-shouldnt-go-down), [Grammy.com](https://www.grammy.com/news/grammycom-wins-award-for-drupal-excellence)

---

## 7. Al Jazeera: Arab Spring (2011)

Al Jazeera ran its live blog on Drupal, hosted on Acquia Cloud.

- **1,000% traffic increase** to Al Jazeera's main site during Egyptian revolution
- **2,000% traffic increase** to Al Jazeera Live blog
- Transferred to Acquia Cloud to handle the surge with redundant caching, memcache, load balancing, and clustered servers
- Site stayed online throughout the crisis
- Source: [Memeburn](https://memeburn.com/2011/03/al-jazeera-handling-traffic-spikes-with-cloud-services-and-drupal/)

---

## 8. WhiteHouse.gov (2009-2017)

The White House website ran on Drupal throughout the Obama administration.

- Served as the digital front door to the US Presidency for 8 years
- Part of a broader adoption: **150+ federal government sites** using Drupal
- Includes Department of Defense, Department of Homeland Security, Department of Energy, Department of Education, Department of Transportation, Department of Agriculture, and Department of Health
- Source: [Dries Buytaert blog](https://dri.es/whitehouse-gov-using-drupal), [Metal Toad](https://www.metaltoad.com/blog/whitehousegov-re-launches-drupal)

---

## 9. UNICEF: Global Knowledge Platform

UNICEF uses Drupal for multiple websites and technology products.

- Powers UNICEF's Knowledge Management platform (Clearing House + Knowledge at UNICEF)
- Integrates with SharePoint, syncing metadata every 2-3 minutes
- Chosen for budget-friendliness, scalability, and quick launch across UNICEF's multisite estate
- Source: [Drupal.org case study](https://www.drupal.org/case-study/unicefs-knowledge-management-platform-powered-by-drupal), [QED42 case study](https://www.qed42.com/work/building-drupal-powered-knowledge-management-platform-for-unicef)

---

## 10. The News Minute (India): Breaking News Scaling

The News Minute, a major Indian news publisher, runs on Drupal.

- **8 million users/month** average
- Previously crashed at 500 concurrent users
- After Drupal optimization: handled **9,543 concurrent users** (19x improvement)
- Later hit **15,000+ concurrent visitors** during breaking news without downtime
- Source: [Drupal.org case study](https://www.drupal.org/case-study/drupal-performance-optimization-helps-the-news-minute-bring-in-more-traffic)

---

## 11. UK Local Government (LocalGov Drupal)

LocalGov Drupal is an open-source Drupal distribution for councils.

- **58+ councils** live on the platform across the UK and Ireland
- **50-80% cost savings** compared to custom council websites
- Built collaboratively as shared infrastructure
- Source: [Drupal4Gov EU 2026](https://drunomics.com/en/blog/drupal4gov-eu-2026-how-drupal-powers-european-governments-247)

---

## 12. Pfizer: Global Pharmaceutical Digital Estate

Pfizer uses Drupal across its web properties.

- Developed a "Drupal Cookbook" to standardize architecture across multiple vendors
- Drupal powers ongoing site development and deployment at scale
- Listed as an organizational member on Drupal.org with issue credits
- Source: [Appnovation case study](https://www.appnovation.com/our-work/pfizer-business-transformation-to-deliver-consistency-quality-efficiency), [Drupal.org](https://www.drupal.org/pfizer-inc)

---

## Summary: The Most Vivid Numbers

| Event/Organization | Key Metric | Context |
|---|---|---|
| NASA Eclipse 2017 | 2M+ concurrent users, 40M+ page views/day | Largest US gov web event ever |
| NBC Super Bowl LII | 3.1M concurrent streams | Largest domestic streaming sports event |
| NBC Rio Olympics | 3.3B streaming minutes, 100M unique visitors | Summer Olympics digital coverage |
| Weather.com Hurricane Sandy | 1B+ page requests in one week | Severe weather emergency |
| European Commission | 770 sites, 2.2B page views/year | EU institutional web estate |
| Grammy.com | ~20M page views on a single night | Live awards show |
| Al Jazeera Arab Spring | 2,000% traffic spike | Revolution/crisis coverage |
| Australian GovCMS | 320+ government websites | National gov platform |
| NBC 2018 total | 4.37B live minutes, 93M unique users | Super Bowl + Olympics + World Cup |
