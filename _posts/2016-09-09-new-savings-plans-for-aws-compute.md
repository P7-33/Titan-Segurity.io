---
title: 'New – Savings Plans for AWS Compute Services'
date: 2019-11-07T05:52:00+01:00
draft: false
---

I first [wrote about](https://aws.amazon.com/blogs/aws/announcing-ec2-reserved-instances/) EC2 Reserved Instances a decade ago! Since I wrote that post, our customers have saved billions of dollars by using Reserved Instances to commit to usage of a specific instance type and operating system within an AWS region.

Over the years we have enhanced the Reserved Instance model to make it easier for you to take advantage of the RI discount. This includes:

[**Regional Benefit**](https://aws.amazon.com/blogs/aws/ec2-reserved-instance-update-convertible-ris-and-regional-benefit/) – This enhancement gave you the ability to apply RIs across all Availability Zones in a region.

[**Convertible RIs**](https://aws.amazon.com/blogs/aws/ec2-reserved-instance-update-convertible-ris-and-regional-benefit/) – This enhancement allowed you to change the operating system or instance type at any time.

[**Instance Size Flexibility**](https://aws.amazon.com/blogs/aws/new-instance-size-flexibility-for-ec2-reserved-instances/) – This enhancement allowed your Regional RIs to apply to any instance size within a particular instance family.

The model, as it stands today, gives you discounts of up to 72%, but it does require you to coordinate your RI purchases and exchanges in order to ensure that you have an optimal mix that covers usage that might change over time.

**New Savings Plans**  
Today we are launching Savings Plans, a new and flexible discount model that provides you with the same discounts as Reserved Instances, in exchange for a commitment to use a specific amount (measured in dollars per hour) of compute power over a one or three year period.

Every type of compute usage has an On Demand price and a (lower) Savings Plan price. After you commit to a specific amount of compute usage per hour, all usage up to that amount will be covered by the Saving Plan, and anything past it will be billed at the On Demand rate.

If you own Reserved Instances, the Savings Plan applies to any On Demand usage that is not covered by the RIs. We will continue to sell RIs, but Savings Plans are more flexible and I think many of you will prefer them!

Savings Plans are available in two flavors:

**Compute Savings Plans** provide the most flexibility and help to reduce your costs by up to 66% (just like Convertible RIs). The plans automatically apply to any EC2 instance regardless of region, instance family, operating system, or tenancy, including those that are part of EMR, ECS, or EKS clusters, or launched by Fargate. For example, you can shift from C4 to C5 instances, move a workload from Dublin to London, or migrate from EC2 to Fargate, benefiting from Savings Plan prices along the way, without having to do anything.

**EC2 Instance Savings Plans** apply to a specific instance family within a region and provide the largest discount (up to 72%, just like Standard RIs). Just like with RIs, your savings plan covers usage of different sizes of the same instance type (such as a **c5.4xlarge** or **c5.large**) throughout a region. You can even switch switch from Windows to Linux while continuing to benefit, without having to make any changes to your savings plan.

**Purchasing a Savings Plan**  
AWS Cost Explorer will help you to choose a Savings Plan, and will guide you through the purchase process. Since my own EC2 usage is fairly low, I used a test account that had more usage. I open AWS Cost Explorer, then click **Recommendations** within **Savings Plans**:

![](https://media.amazonwebservices.com/blog/2019/spl_nav_3.png)

I choose my **Recommendation options**, and review the recommendations:

![](https://media.amazonwebservices.com/blog/2019/sp_full_mock_6.png)

Cost Explorer recommends that I purchase $2.40 of hourly Savings Plan commitment, and projects that I will save 40% (nearly $1200) per month, in comparison to On-Demand. This recommendation tries to take into account variable usage or temporary usage spikes in order to recommend the steady state capacity for which we believe you should consider a Savings Plan. In my case, the variable usage averages out to $0.04 per hour that we’re recommending I keep as On-Demand.

I can see the recommended Savings Plans at the bottom of the page, select those that I want to purchase, and **Add** them to my cart:

![](https://media.amazonwebservices.com/blog/2019/sp_side_cart_1.png)

When I am ready to proceed, I click **View cart**, review my purchases, and click **Submit order** to finalize them:

![](https://media.amazonwebservices.com/blog/2019/sp_cart_mock_2.png)

My Savings Plans become active right away. I can use the Cost Explorer’s Performance & Coverage reports to review my actual savings, and to verify that I own sufficient Savings Plans to deliver the desired amount of coverage.

**Available Now**  
As you can see, Savings Plans are easy to use! You can access compute power at discounts of up to 72%, while gaining the flexibility to change compute services, instance types, operating systems, regions, and so forth.

Savings Plans are available in all AWS regions outside of China, and you can start to purchase (and benefit) from them today!

— [Jeff](https://twitter.com/jeffbarr);

  
  
from Hacker News https://ift.tt/36Ftjzj