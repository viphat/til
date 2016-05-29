---
layout: default
title: "Chapter 4 - Measure First, Then Optimize Towards a Goal"
permalink: /:slug
tags: []
---

Công cụ hỗ trợ chẩn đoán và phân tích mạnh mẽ nhất - **Sơ đồ Waterfall**

![Waterfall](http://i.imgur.com/sp1EGDv.png)

- Line items 3,5,9 show big bodies of CSS assets. Loading too many different and large CSS files after one another will delay the rendering of the page, and specifically slow down the Start Render time.

- Several image assets are being requested in line items 16–19, and they all consist of relatively big bodies. It's best to aim for a “thin” waterfall, as this correlates to small resources (or small file sizes). Each asset or request should load quickly, that means the body of the asset should be small.

- Numerous small JavaScript files are being requested in line items 22, 24, 26 and 27. The fewer requests you make, the smaller and “steeper” the waterfall will be. A steep waterfall is a great indicator of a lean website, revealing proper sharing and parallelizing of resources.

**Resource Not Found**

![404](http://i.imgur.com/fTDaFN3.png)

Avoid red lines in your WPT waterfall. These indicate that the resource could not be found. The cause for this could be that the asset is not referenced properly in the markup (the wrong path is given, for example), or the asset doesn't exist on the server. Performance will suffer from a "not found" asset in the waterfall, because the browser is wasting precious time trying to locate the file while still having to parse the rest of the page.

--- 


