---
layout: post
title: "Wikipedia page traffic"
date: 2020-10-04
---

<h3><strong> Goal of this project </strong></h3>
<p>The goal of this project is to construct, analyze, and publish a dataset of monthly traffic on English Wikipedia from January 1 2008 through August 30 2020.
We combine the data from two different API endpoints, the Legacy Pagecounts API and the Pageviews API and perform analysis of the combined data by plotting a time series plot.</p>


<h3><strong>License of the source data </strong></h3>
<p>Unless otherwise specified in the endpoint documentation below, content accessed via the 2 APIS is licensed under the CC-BY-SA 3.0 and GFDL licenses, and you irrevocably agree to release modifications or additions made through this API under these licenses. More details are available in the link to the Wikimedia Foundation REST API terms of use: </p>
<a href="https://www.mediawiki.org/wiki/REST_API#Terms_and_conditions">Mediawiki Terms_and_conditions</a> 

<h3><strong>Links to all relevant API documentation:</strong></h3>
<p>In order to measure Wikipedia traffic from 2008-2020, you will need to collect data from two different API endpoints, the Legacy Pagecounts API and the Pageviews API.</p>

<ul><li>The Legacy Pagecounts API (documentation and endpoint links below) provides access to desktop and mobile traffic data from December 2007 through July 2016.
"https://wikitech.wikimedia.org/wiki/Analytics/AQS/Legacy_Pagecounts https://wikimedia.org/api/rest_v1/#/Pagecounts_data_(legacy)/get_metrics_legacy_pagecounts_aggregate_project_access_site_granularity_start_end </li>

 <li>The Pageviews API (documentation and endpoint links below) provides access to desktop, mobile web, and mobile app traffic data from July 2015 through last month. 
https://wikitech.wikimedia.org/wiki/Analytics/AQS/Pageviews https://wikimedia.org/api/rest_v1/#/Pageviews_data/get_metrics_pageviews_aggregate_project_access_agent_granularity_start_end </li></ul>


<h3><strong>Description of fields in the data file en-wikipedia_traffic_200712-202008.csv</strong></h3>
<ul>
<li>year	  - year in the format YYYY </li>
<li>month	  - month in the format MM</li>
<li>pagecount_all_views	- number of views from pagecount API that has combined traffic from mobile and desktop </li>
<li>pagecount_desktop_views	- number of views from pagecount API that has combined traffic from desktop only</li>
<li>pagecount_mobile_views	- number of views from pagecount API that has combined traffic from mobile only </li>
<li>pageview_all_views	- number of views from pageview API that has combined traffic from mobile and desktop </li>
<li>pageview_desktop_views - number of views from pageview API that has combined traffic from desktop only</li>
<li>pageview_mobile_views - number of views from pageview API that has combined traffic from mobile only </ul>


<h3><strong>Known issues/considerations</strong></h3>
<p>Data from the Pageview API excludes spiders/crawlers, while data from the Pagecounts API does not</p>

<h5><strong>Links to artifacts</strong></h5>
<a href="">Code link</a>
<a href="">Time series plot</a>
