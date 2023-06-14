# Kinesis firehose

## How Kinesis Firehose autoscales?

Regarding Firehose Limit increase: Please note that If you are already aware of the volume of data that your producer would be sending or if data world increase in near future, you may proactively increase the limits and service quotas of your firehose stream. Please refer to the link below.
[+] Amazon Kinesis Data Firehose Quota - https://docs.aws.amazon.com/firehose/latest/dev/limits.html 

Your understanding about firehose auto-scaling is correct. Please find the details I got from the service team.

1. how soon does firehose auto-scale once traffic is Hitting limits?

The auto-scaling is reactive. So it will kick-in after the traffic is throttled continuously for some time (about 5- 10 mins)

2. What are the levels the limit gets increased? Eg: 5 Mbps to 10, 10 to 20 etc

yeah its double every time.

3. Does Firehose keep scaling indefinitely depending of traffic? 

No. AWS have an upper through put limit of 640 MB/s for IAD/DUB/PDX, and 128 MB/s for rest of the regions.

Ideally customer should follow the best practice mentioned below, and get the limits increased proactively using alarms
https://docs.aws.amazon.com/firehose/latest/dev/monitoring-with-cloudwatch-metrics.html#firehose-cloudwatch-metrics-best-practices 

-------------------

"Nope. We have an upper through put limit of 640 MB/s for IAD/DUB/PDX, and 128 MB/s for rest of the regions."

Please note that the above information that I have provided is applicable to auto-scaling only. You can still further increase the Quota by raising limit increase request. 

[+] Amazon Kinesis Data Firehose Quota - https://docs.aws.amazon.com/firehose/latest/dev/limits.html 

Please note that, approval of limit increase is done by the service which depends on the availability of resources in the AWS region and your use case.

=====================

1. is this limit per region? so I am limited to 128 MB/s in eu-west-1 for example for my firehose there, and an additional 128 for another firehose in another region (e.g. paris), or is this limit is accumulated for all firehoses running? but then how it works if I have one in a 640MB region and one in 128MB region?

--> The limit I provided is per Firehose stream but it depends on the region Firehose stream belong to. For Example, if firehose belong to eu-west-1, auto-scaling can go till 128 MB/s.

2. is this a hard limit?

--> No its not hard limit. 

3. I couldn't find it in the docs, is this documented anywhere?
No. This is internal information only Service team would be knowing and these limits may subject to change (maybe due to business decision or physical resource and capacity limitations). 
