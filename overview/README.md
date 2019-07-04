# AWS Regions
- Region is separate geographic area.
- Resources are tied to a specific regions (**except for IAM, S3, Route 53**)
- e.g. us-east-1
- 21 Regions

# AWS Availability Zones
- Phyiscal data centres in the region
- Separated from one another to isolate from disasters
- e.g. us-east-1a (**letter a marks an AZ in us-east-1 region**)
- 66 AZ(s)

# Edge locations
- Located in most of the major cities around the world and are specifically used by CloudFront (CDN-Content delivery network)
- Used to avoid network latency
- Have cached content.
- 44 Edge locations

![alt text](https://github.com/ajiks143/aws-solution-architect-associate-2019-notes/blob/master/overview/aws_regions.png "AWS-Regions-AZs")

**Reference**: https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-regions-availability-zones.html
