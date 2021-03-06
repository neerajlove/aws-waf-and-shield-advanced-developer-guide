# How AWS WAF works<a name="how-aws-waf-works"></a>

You use AWS WAF to control how an Amazon CloudFront distribution, an Amazon API Gateway API, or an Application Load Balancer responds to web requests\. 
+ **Web ACLs** – You use a web access control list \(ACL\) to protect a set of AWS resources\. You create a web ACL and define its protection strategy by adding rules\. Rules define criteria for inspecting web requests and specify how to handle requests that match the criteria\. You set a default action for the web ACL that indicates whether to block or allow through those requests that pass the rules inspections\. 
+ **Rules** – Each rule contains a statement that defines the inspection criteria, and an action to take if a web request meets the criteria\. When a web request meets the criteria, that's a match\. You can use rules to block matching requests or to allow matching requests through\. You can also use rules just to count matching requests\. 
+ **Rules groups** – You can use rules individually or in reusable rule groups\. AWS Managed Rules and AWS Marketplace sellers provide managed rule groups for your use\. You can also define your own rule groups\.

After you create your web ACL, you can associate it with one or more AWS resources\. The resource types that you can protect using AWS WAF web ACLs are Amazon CloudFront distributions, Amazon API Gateway APIs, and Application Load Balancers\. 

AWS WAF is available in the Regions listed at [AWS Regions and Endpoints](https://docs.aws.amazon.com/general/latest/gr/rande.html#waf_region)\.
+ For an API Gateway API or an Application Load Balancer, you can use any of the Regions in the list\. 
+ For a CloudFront distribution, AWS WAF is available globally, but when you create AWS resources for use with CloudFront, you must choose the Region US East \(N\. Virginia\)\. AWS WAF resources are web ACLs, rule groups, IP sets, and regex pattern sets\.

## AWS WAF Web ACL capacity units \(WCU\)<a name="aws-waf-capacity-units"></a>

AWS WAF uses web ACL capacity units \(WCU\) to calculate and control the operating resources that are used to run your rules, rule groups, and web ACLs\. AWS WAF calculates capacity differently for each rule type, to reflect each rule's relative cost\. Simple rules that cost little to run use fewer WCUs than more complex rules that use more processing power\. 

AWS WAF manages capacity for rules, rule groups, and web ACLs:
+ **Rule capacity** – AWS WAF calculates rule capacity when you create or update a rule\. For some basic guidelines for rule capacity requirements, see the listings for the various rule statements at [AWS WAF rule statements](waf-rule-statements.md)\. You can also get an idea of the capacity required for the various rule types in the AWS WAF console by creating a web ACL or rule group and adding individual rules to it\. The console displays the capacity units used as you add the rules\. 
+ **Rule group capacity** – AWS WAF requires that each rule group is assigned an immutable capacity at creation\. This is true for managed rule groups and rule groups that you create through AWS WAF\. When you modify a rule group, your changes must keep the rule group's WCU within its max quote\. This ensures that web ACLs that are using the rule group remain within their quotas\. 
+ **Web ACL capacity** – The maximum capacity for a web ACL is 1,500, which is sufficient for most use cases\. If you need more capacity, contact the [AWS Support Center](https://console.aws.amazon.com/support/home#/)\. 

## AWS WAF pricing<a name="aws-waf-pricing"></a>

With AWS WAF, you pay only for the web ACLs and rule groups that you create, and for the number of HTTP\(S\) requests that AWS WAF inspects\. For more information, see [AWS WAF Pricing](http://aws.amazon.com/waf/pricing/)\. 