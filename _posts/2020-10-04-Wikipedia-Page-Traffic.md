---
layout: post
title: "Wikipedia Page Traffic"
date: 2020-10-04
---

<h2><strong> Goal of this project </strong></h2>
<p>The goal of this project is to construct, analyze, and publish a dataset of monthly traffic on English Wikipedia from January 1 2008 through August 30 2020.
We combine the data from two different API endpoints, the Legacy Pagecounts API and the Pageviews API and perform analysis of the combined data by plotting a time series plot.</p>

![Wikipedia Time Series plot](/assets/WikiTraffic/wikipedia_traffic_plot.jpg)

<h2><strong>License of the source data </strong></h2>
<p>Unless otherwise specified in the endpoint documentation below, content accessed via the 2 APIS is licensed under the CC-BY-SA 3.0 and GFDL licenses, and you irrevocably agree to release modifications or additions made through this API under these licenses. More details are available in the link to the Wikimedia Foundation REST API terms of use: </p>
<a href="https://www.mediawiki.org/wiki/REST_API#Terms_and_conditions">Mediawiki Terms_and_conditions</a> 

<h2><strong>Links to all relevant API documentation:</strong></h2>
<p>In order to measure Wikipedia traffic from 2008-2020, you will need to collect data from two different API endpoints, the Legacy Pagecounts API and the Pageviews API.</p>

<ul><li>The Legacy Pagecounts API (documentation and endpoint links below) provides access to desktop and mobile traffic data from December 2007 through July 2016.
 <a href="https://wikitech.wikimedia.org/wiki/Analytics/AQS/Legacy_Pagecounts">Pagecounts API documentation</a>
 <a href="https://wikimedia.org/api/rest_v1/#/Pagecounts_data_(legacy)/get_metrics_legacy_pagecounts_aggregate_project_access_site_granularity_start_end">End point</a></li>

 <li>The Pageviews API (documentation and endpoint links below) provides access to desktop, mobile web, and mobile app traffic data from July 2015 through last month. 
 <a href="https://wikitech.wikimedia.org/wiki/Analytics/AQS/Pageviews">Pageviews API documentation</a>
 <a href="https://wikimedia.org/api/rest_v1/#/Pageviews_data/get_metrics_pageviews_aggregate_project_access_agent_granularity_start_end">Endpoint</a></li></ul>


<h2><strong>Description of fields in the data file en-wikipedia_traffic_200712-202008.csv</strong></h2>
<ul>
<li>year	  - year in the format YYYY </li>
<li>month	  - month in the format MM</li>
<li>pagecount_all_views	- number of views from pagecount API that has combined traffic from mobile and desktop </li>
<li>pagecount_desktop_views	- number of views from pagecount API that has combined traffic from desktop only</li>
<li>pagecount_mobile_views	- number of views from pagecount API that has combined traffic from mobile only </li>
<li>pageview_all_views	- number of views from pageview API that has combined traffic from mobile and desktop </li>
<li>pageview_desktop_views - number of views from pageview API that has combined traffic from desktop only</li>
<li>pageview_mobile_views - number of views from pageview API that has combined traffic from mobile only</li> </ul>


<h2><strong>Known issues/considerations</strong></h2>
<p>Data from the Pageview API excludes spiders/crawlers, while data from the Pagecounts API does not</p>

<h2><strong>Links to artifacts</strong></h2>
<ul>
 <li><a href="/assets/WikiTraffic/Analysis/Wikipedia_traffic_analysis.ipynb">Source Code</a></li>
 <li><a href="/assets/WikiTraffic/Raw Data/">Raw data files</a></li>
 <li><a href="/assets/WikiTraffic/Clean Data/clean_data_en-wikipedia_traffic_200712-202009.xlsx">Clean data</a></li> 
 <li><a href="/assets/WikiTraffic/LICENSE">License</a></li> 
</ul>
