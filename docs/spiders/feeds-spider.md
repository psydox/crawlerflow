# Feeds Spider


Create a manifest.yml and run the spider.


```yaml
cti_id: news.ycombinator.com
init_spider:
  spider_id: default
  start_urls:
    - https://news.ycombinator.com/rss
spiders:
- spider_id: default
  allowed_domains:
  - news.ycombinator.com
  iterator: xml
  itertag: item
  extractors:
  - extractor_id: stories
    extractor_type: CustomContentExtractor
    data_selectors:
    - selector_id: title
      selector: title
      selector_type: xpath
      selector_attribute: text()
      data_type: StringField
    - selector_id: link
      selector: link
      selector_type: xpath
      selector_attribute: text()
      data_type: StringField
    - selector_id: published_date
      selector: pubDate
      selector_type: xpath
      selector_attribute: text()
      data_type: StringField
settings:
  allowed_domains:
  - "news.ycombinator.com"
  download_delay: 0
context:
  author: https://github.com/rrmerugu
  description: Crawler that scrapes ycombinator news


```



## Running the Spider

```bash
invana-bot --type=rss
```