# garie · An open source toolkit to monitor web performance

Source: Website
Status: Unprocessed
URL: https://garie.netlify.app/

![https://garie.io/img/docusaurus.png](https://garie.io/img/docusaurus.png)

---

![garie%20%C2%B7%20An%20open%20source%20toolkit%20to%20monitor%20web%20perf%20405f1d4a33a34f1f86238fbd6cfdbb15/garie-dark.png](garie%20%C2%B7%20An%20open%20source%20toolkit%20to%20monitor%20web%20perf%20405f1d4a33a34f1f86238fbd6cfdbb15/garie-dark.png)

### Keep an eye on web performance

Get started within minutes and start monitoring your application's performance. Garie uses Lighthouse, Pagespeed Insights & Browsertime to collect metrics. These metrics are visualised with premade dashboards.

[Learn more](https://garie.netlify.app/docs/using-garie/introduction)

![garie%20%C2%B7%20An%20open%20source%20toolkit%20to%20monitor%20web%20perf%20405f1d4a33a34f1f86238fbd6cfdbb15/dashboard-example-2.png](garie%20%C2%B7%20An%20open%20source%20toolkit%20to%20monitor%20web%20perf%20405f1d4a33a34f1f86238fbd6cfdbb15/dashboard-example-2.png)

![garie%20%C2%B7%20An%20open%20source%20toolkit%20to%20monitor%20web%20perf%20405f1d4a33a34f1f86238fbd6cfdbb15/report.png](garie%20%C2%B7%20An%20open%20source%20toolkit%20to%20monitor%20web%20perf%20405f1d4a33a34f1f86238fbd6cfdbb15/report.png)

### Performance Reports

Every time Garie collects performance metrics, it can store Lighthouse reports.

This data can help you visually see what is happening in your applications & also tell you where and how to improve.

[Learn more](https://garie.netlify.app/docs/contribute)

### Performance Videos

Garie also collects videos of your application, so you can visualy see what is happening thanks to the Browsertime Plugin.

[Learn more](https://garie.netlify.app/docs/browsertime/introduction)

![garie%20%C2%B7%20An%20open%20source%20toolkit%20to%20monitor%20web%20perf%20405f1d4a33a34f1f86238fbd6cfdbb15/video.gif](garie%20%C2%B7%20An%20open%20source%20toolkit%20to%20monitor%20web%20perf%20405f1d4a33a34f1f86238fbd6cfdbb15/video.gif)

![garie%20%C2%B7%20An%20open%20source%20toolkit%20to%20monitor%20web%20perf%20405f1d4a33a34f1f86238fbd6cfdbb15/919853.svg](garie%20%C2%B7%20An%20open%20source%20toolkit%20to%20monitor%20web%20perf%20405f1d4a33a34f1f86238fbd6cfdbb15/919853.svg)

### Built with Docker

Garie is built on a Docker architecture. Data is collected inside each of Garie's plugins (containers) and Garie reads the performance data collected.

All the plugins collect data and save it into InfluxDB. Garie then uses Grafana to help visualise the data.

Each plugin also has its own API - some even collect reports & videos which are all accessible.

[Learn more](https://garie.netlify.app/docs/using-garie/introduction)

Garie was built to help people get a better understanding of web performance and an easy way to start monitoring your applications.

If you would like to contribute feel free to checkout the repository.

[Learn more](https://garie.netlify.app/docs/contribute)