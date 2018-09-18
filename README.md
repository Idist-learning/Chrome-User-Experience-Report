
[Source](https://developers.google.com/web/tools/chrome-user-experience-report/ "Permalink to Chrome User Experience Report  |  Tools for Web Developers  |  Google Developers")

# Chrome User Experience Report  |  Tools for Web Developers  |  Google Developers
# Báo cáo về trải nghiệm người dùng | Các công cụ cho các web developer | Google Developer
![][1]

The Chrome User Experience Report provides user experience metrics for how real-world Chrome users experience popular destinations on the web.
Chrome User Experience Report cung cấp các số liệu từ trải nghiệm người dùng đến cách mà người dùng Chrome trải nghiệm trong thế giới thực với các địa điểm cụ thể.

## Methodology
## Các phương pháp luận

The Chrome User Experience Report is powered by real user measurement of key user experience metrics across the public web, aggregated from users who have opted-in to syncing their browsing history, have not set up a Sync passphrase, and have [usage statistic reporting][2] enabled. The resulting data is made available via:
Chrome User Experience Report được hỗ trợ đo đạc các chỉ số về trải nghiệm người dùng trên chính các web công cộng, được tổng hợp từ những người dùng được chọn tham gia đồng bộ hoá lịch sử trình duyệt của họ, không thiết lập mật khẩu cho đồng bộ hoá, và bật tính năng [báo cáo thống kê sử dụng][2]. Dữ liệu về kết quả được thông qua:

1. [PageSpeed Insights][3], which provides URL-level user experience metrics for popular URLs that are known by Google's web crawlers.
1. [PageSpeed Insights][3] cung cấp các chỉ số về trải nghiệm người dùng của mỗi mức URL đối với các URL phổ phiến mà công cụ crawler các web của Google biết.
2. [Public Google BigQuery project][4], which aggregates user experience metrics by origin, for all origins that are known by Google's web crawlers, and split across multiple dimensions outlined below.
2. [Dự án cộng đồng Google BigQuery][4] tổng hợp các chỉ số về trải nghiệm của người dùng theo nguồn gốc, áp dụng với mọi nguồn gốc mà trình thu thập dữ liệu của Google biết được và chia nhỏ dữ liệu theo những mục được nêu dưới đây:

### Metrics
### Các chỉ số

Metrics provided by the public Chrome User Experience Report hosted on Google BigQuery are powered by standard web platform APIs exposed by modern browsers and aggregated to origin-resolution. Site owners that want more detailed (URL level resolution) analysis and insight into their site performance and can use the same APIs to gather detailed real user measurement (RUM) data for their own origins.
Các chỉ số được cung cấp bởi Chrome User Experience Report một cách công khai, lưu trữ trên Google BigQuery được cung cấp dựa trên các nền tảng web thông qua API được hiển thị trên các trình duyệt hiện đại, và tổng hợp theo các phân bố ban đầu. Chủ sở hữu trang wbe muốn phân tích chi tiết hơn (phân tích theo URL) và hiểu rõ hơn về hiệu suất trang web của họ và có thể sử dụng cùng 1 API để thu thập dữ liệu phục vụ việc đo lường chi tiết trong thực tế (RUM) về dữ liệu 

**Note:** Currently the Chrome User Experience Report is focused on loading performance. With time, we hope to add more metrics and dimensions, both to provide more insight into loading and other [critical factors that most affect user experience][5].

For guidance on which metrics to track and optimize for, and best practices on how to interpret real user measurement data, refer to our [user centric performance][5] documentation.

#### First Paint

Defined by the [Paint Timing API][6] and [available in Chrome M60+][7]:

> "First Paint reports the time when the browser first rendered after navigation. This excludes the default background paint, but includes non-default background paint. This is the first key moment developers care about in page load – when the browser has started to render the page."

#### First Contentful Paint

Defined by the [Paint Timing API][8] and [available in Chrome M60+][7]:

> "First Contentful Paint reports the time when the browser first rendered any text, image (including background images), non-white canvas or SVG. This includes text with pending webfonts. This is the first time users could start consuming page content."

#### DOMContentLoaded

Defined by the [HTML specification][9]:

> "The DOMContentLoaded reports the time when the initial HTML document has been completely loaded and parsed, without waiting for stylesheets, images, and subframes to finish loading." - [MDN][10].

#### onload

Defined by the [HTML specification][11]:

> "The load event is fired when the page and its dependent resources have finished loading." - [MDN][12].

### Dimensions

Performance of web content can vary significantly based on device type, properties of the network, and other variables. To help segment and understand user experience across such key segments, the Chrome User Experience Report provides the following dimensions.

#### Effective Connection Type

Defined by the [Network Information API][13] and [available in Chrome M62+][14]:

> "Provides the effective connection type ("slow-2g", "2g", "3g", "4g", or "offline") as determined by round-trip and bandwidth values based on real user measurement observations."

#### Device Type

Coarse device classification ("phone", "tablet", or "desktop"), as [communicated via User-Agent][15].

#### Country

Geographic location of users at the country-level, inferred by their IP address. Countries are identified by their respective [ISO 3166-1 alpha-2 codes][16].

### Data format

The report is provided via [Google BigQuery][17] as a collection of datasets containing user experience metrics aggregated to origin-resolution. Each dataset represents a single country, `country_rs` captures user experience data for users in Serbia (`rs` is the [ISO 31611-1][16] code for Serbia). Additionally, there is a globally aggregated dataset (`all`) that captures the world-wide experience. Each row in the dataset contains a nested record of user experience for a particular origin, split by key dimensions.

| ----- |
| Dimension |  
| `origin` |  "https://example.com" |  
| `effective_connection_type.name` |  4G |  
| `form_factor.name` |  "phone" |  
| `first_paint.histogram.start` |  1000 |  
| `first_paint.histogram.end` |  1200 |  
| `first_paint.histogram.density` |  0.123 | 

For example, the above shows a sample record from the Chrome User Experience Report, which indicates that 12.3% of page loads had a "first paint time" measurement in the range of 1000-1200 milliseconds when loading "http://example.com" on a "phone" device over a "4G"-like connection. To obtain a cumulative value of users experiencing a first paint time below 1200 milliseconds, you can add up all records whose histogram's "end" value is less than or equal to 1200. 

**Note:** The Chrome User Experience Report does not provide quantile values (e.g. median). Such values can be approximated from the provided data, but are not exposed directly by the report.

## Getting started

The Chrome User Experience Report is provided as a public project on [Google BigQuery][17]. To access the project, you'll need a Google account and a Google Cloud Project: [refer to our step by step guide][18] and [the guided tour of how to query the project][19].

## Analysis tips & best practices

### Consider population differences across origins

The metrics provided by the Chrome User Experience Report are powered by real user measurement data. As a result, the data reflects how real users experienced the visited origin and, unlike synthetic or local testing where the test is performed under fixed and simulated conditions, captures the full range of external factors that shape and contribute to the final user experience.

For example, differences in population of users accessing a particular origin can contribute meaningful differences to the user experience. If the site is frequented by more visitors with more modern devices or via a faster network, the results may appear "fast" even if the site is not well optimized. Conversely, a well optimized site that attracts a wider population of users, or a population with larger fraction of users on slower devices or networks, may appear "slow".

When performing head-to-head comparisons across origins, it is important to account and control for the population differences: segment by provided dimensions, such as device type and connection type, and consider external factors such as size of the population, countries from which the origin is accessed, and so on.

### Consider population size differences across origins

The Chrome User Experience Report aggregates data for each origin, with the "density" values across all dimension-metric histograms summing to a value of "1.0". This provides insight into the distribution of experiences across the key dimensions for a single origin.

However, when aggregating data from multiple origins, for example within an industry vertical or geographic regions, be careful with the types of conclusions being drawn: adding up densities for the same metric across multiple origins does not account for relative population differences across origins. 

For example, site A may have ten million visitors, while site B has ten thousand. In both cases, the histogram densities for each origin sum to "1.0", and the dataset does not provide any absolute metrics about the population size of individual origins, or relative population size differences across origins. As a result, if you add together the densities from A and B, and average the results, you will treat them as equals even though A has three orders of magnitude more traffic.

### Consider Chrome population differences

The Chrome User Experience report is powered by real user measurement aggregated from Chrome users who have opted-in to syncing their browsing history, have not set up a Sync passphrase, and have usage statistic reporting enabled. This population may not be representative of the broader user base for a particular origin and many origins may have population differences among each other. Further, this data does not account for users with different browsers and differences in browser adoption in different geographic regions.

As a result, be careful with the types of conclusions being drawn when looking at a cross-section of origins, and when comparing individual origins: avoid using absolute comparisons and consider other population factors outlined in the sections above.

## Feedback and suggestions

We would love to hear your feedback, questions, and suggestions to help us improve the Chrome User Experience Report. Please join the conversation on our [public Google Group][20].

## License

"Chrome User Experience Report" datasets by Google are licensed under a [Creative Commons Attribution 4.0 International License][21].

[1]: https://developers.google.com/web/tools/chrome-user-experience-report/images/dataset.png
[2]: https://www.google.com/chrome/browser/privacy/whitepaper.html#usagestats
[3]: https://developers.google.com/speed/pagespeed/insights/
[4]: https://bigquery.cloud.google.com/dataset/chrome-ux-report:all
[5]: https://developers.google.com/web/updates/2017/06/user-centric-performance-metrics
[6]: https://w3c.github.io/paint-timing/#first-paint
[7]: https://www.chromestatus.com/feature/5688621814251520
[8]: https://w3c.github.io/paint-timing/#first-contentful-paint
[9]: https://html.spec.whatwg.org/#event-domcontentloaded
[10]: https://developer.mozilla.org/en-US/docs/Web/Events/DOMContentLoaded
[11]: https://html.spec.whatwg.org/#event-load
[12]: https://developer.mozilla.org/en-US/docs/Web/Events/load
[13]: https://wicg.github.io/netinfo/#dfn-effective-connection-types
[14]: https://www.chromestatus.com/feature/5108786398232576
[15]: https://developer.chrome.com/multidevice/user-agent
[16]: https://en.wikipedia.org/wiki/ISO_3166-1#Officially_assigned_code_elements
[17]: https://cloud.google.com/bigquery/
[18]: https://developers.google.com/web/tools/chrome-user-experience-report/getting-started#access-dataset
[19]: https://developers.google.com/web/tools/chrome-user-experience-report/getting-started#example-queries
[20]: https://groups.google.com/a/chromium.org/forum/#!forum/chrome-ux-report
[21]: https://creativecommons.org/licenses/by/4.0/

  