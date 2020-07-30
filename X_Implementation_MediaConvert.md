# Implementation with AWS MediaConvert

1. Create S3 buckets to store input files.
    1. Docs: https://docs.aws.amazon.com/mediaconvert/latest/ug/set-up-file-locations.html
2. Set up IAM permissions
    1. To run transcoding jobs with AWS Elemental MediaConvert, 
       first set up an AWS Identity and Access Management (IAM) role 
       to allow MediaConvert access to your input files 
       and the locations where your output files are stored.
    2. Docs: https://docs.aws.amazon.com/mediaconvert/latest/ug/iam-role.html   
3. Create MediaConvert Job
    0. Should we use CloudFormation to create pipeline for this flow?
    1. Docs: https://docs.aws.amazon.com/mediaconvert/latest/ug/create-a-job.html
    2. How to Convert to WebM? (start investigation with https://aws.amazon.com/about-aws/whats-new/2020/06/webm-outputs-with-vp8-and-vp9-video-now-available-with-aws-elemental-mediaconvert/)
    3. Looks that WebM/HLS and WebP will cover all our needs: https://caniuse.com/#search=video%20format
    4. Supported inputs: https://docs.aws.amazon.com/mediaconvert/latest/ug/reference-codecs-containers-input.html
    5. Supported outputs: https://docs.aws.amazon.com/mediaconvert/latest/ug/reference-codecs-containers.html
    6. Looks that all information about video which used for crawling is on FE side, but probably we should add smth to 
    video container during conversion. Check this: https://support.google.com/webmasters/answer/156442?hl=en#file-types
    7. Auto play policy is on FE side, looks we can't impact on this during conversion: https://developers.google.com/web/updates/2017/09/autoplay-policy-changes
    8. Read more about video compression formats: this can be useful 
    for deciding which settings should we use during conversion: https://developers.google.com/media/vp9
4. Provide access to S3 bucket files
    1. Docs: https://aws.amazon.com/premiumsupport/knowledge-center/read-access-objects-s3-bucket/
5. We can create microservice to store S3 links, and API to give all links for specified car.
Frontend should build video tag with all links listed in source sub-tag.
6. Serverless watchfolder workflow
   https://aws.amazon.com/blogs/media/vod-automation-part-1-create-a-serverless-watchfolder-workflow-using-aws-elemental-mediaconvert/
    
**NOTES:**
Workflow for MediaConvert looks a little similar to DMS (Database Migration System)
At least we can think about repeating this approach. It is not handy, but it works.