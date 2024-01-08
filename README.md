# aws-event-bridge-schedule
This project is related to create a scheduler to start the stop the ec2 machine in night and restart at morning 

# Plan: 
Lets plan before enter into the aws console, lets create two schedules. 
- 1) sc_start_ec2
  2) sc_stop_ec2

# Step: 
## open your console search the service  <Amazon EventBridge>
## Navigate to service Amazon eventBridge > scheduler > schedules > create schedule 
## specify all detail :
  - schedule name and description : 
    - schedule name :sc_start_ec2
    - description (optional) :
    - schedule group : < default > 
  - schedule pattern:
    - Occurence : two type occurence a) One-time schedule b) recurring schedule. we need to choose <Recurring schedule>
    - schedule type : two type a) crone-based schedule b) Rate-based schedule . we need to choose <Crone-based schedule>
  - crone expression : 30 7 * * ? *
    -  formate ( [minute] [hours] [day of month] [month] [day of week] [year] )
  - Flexible time window : off
  - TimeFrame : empty
  - Next
## select Target: 
  - Target Api : there are two option [templated targets] and [all apis] . select All api 
  - All Aws Service >  Amazon EC2 > just search [start] > StartInstances >
  - startInstances > input
    ```git
    {
      "InstanceIds": [
        "i-07de2eb70b1c287c9"  ## provide your instance id 
      ]
    }
    ```
  - Next
 ## schedule state 
  - enable 
    

AWS Account :  536984075386
Objective : To save the cost 

Task 1  : Stop the instance ( passbolt ) at  23:30  ( Night)
Task 2 : Start the Instance ( passbolt) at 7:30 ( next day morning ) 


Detail : 
—---------------------------





















If  you are doing 1st time may be no role there, in this case you need to create new role by click on “Go to IAM Console” 

And create the Role 



{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Principal": {
                "Service": "scheduler.amazonaws.com"
            },
            "Action": "sts:AssumeRole"
        }
    ]
}





In same way create another scheduler to start the machine 












