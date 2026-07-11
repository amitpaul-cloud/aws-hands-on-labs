# Day 5 – Amazon S3 Hands-on Lab (Part 2)

## Objective

The objective of this hands-on lab was to practise advanced Amazon S3 features used for data replication, storage lifecycle management, access logging, batch operations, and event-driven notifications.

In this lab, I configured S3 replication between two buckets, replicated existing objects using S3 Batch Operations, created a lifecycle rule for automatic storage-class transitions, enabled server access logging, and integrated Amazon S3 with Amazon SNS to receive email notifications for object-level events.

---

## AWS Services Used

- Amazon Simple Storage Service (Amazon S3)
- Amazon Simple Notification Service (Amazon SNS)
- AWS Identity and Access Management (IAM)

---

## Features Practised

- S3 Replication Rules
- S3 Object Replication
- S3 Batch Operations
- S3 Batch Replication
- S3 Lifecycle Rules
- S3 Storage-Class Transitions
- S3 Server Access Logging
- Amazon SNS Topics
- SNS Email Subscriptions
- S3 Event Notifications
- Event-Driven Email Notifications

---

## Lab Architecture


                     Amazon S3 Source Bucket
                              |
          +-------------------+-------------------+
          |                   |                   |
          v                   v                   v
 
   Replication Rule     Lifecycle Rule     Server Access Logs
   
          |                   |                   |
          v                   v                   v

 Destination Bucket     Standard-IA        Logging Destination
                       after 30 days             Bucket
                       
                              |
                              v
                    Glacier Deep Archive
                       after 60 days


Amazon S3 Object Event
          |
          v
    Amazon SNS Topic
          |
          v
 Confirmed Email Subscription
          |
          v
 Email Notification Received


## Task 1: Configure an S3 Replication Rule

I created and enabled an S3 replication rule to automatically replicate objects from a source S3 bucket to a destination S3 bucket.

## Configuration

Replication status: Enabled
Replication scope: Entire bucket
Source Region: Asia Pacific (Mumbai) – ap-south-1
Destination Region: Asia Pacific (Mumbai) – ap-south-1
Destination storage class: S3 Standard-IA

## Result
The replication rule was successfully enabled.
---

## Task 2: Verify Object Replication

After configuring the replication rule, I verified that the object was successfully copied from the source S3 bucket to the destination S3 bucket.

## Result

The replicated object was available in the destination bucket with the configured S3 Standard-IA storage class.
---

## Task 3: Perform S3 Batch Replication

I used Amazon S3 Batch Operations to replicate an existing object.

S3 replication rules generally replicate new objects uploaded after the replication configuration is enabled. S3 Batch Replication can be used to replicate eligible existing objects.

## Result

Operation: Replicate
Job status: Completed
Completion: 100%
Failed objects: 0
---

## Task 4: Configure an S3 Lifecycle Rule

I created an S3 lifecycle rule to automatically transition objects between storage classes according to their age.

## Lifecycle Transition

Object Age	Storage Class
Day 0	S3 Standard
After 30 days	S3 Standard-IA
After 60 days	S3 Glacier Deep Archive
---

## Lifecycle Flow

                  Object Uploaded
                       |
                       v
                   S3 Standard
                       |
                       | After 30 days
                       v
                S3 Standard-IA
                       |
                       | After 60 days
                       v
              S3 Glacier Deep Archive

## Result

The lifecycle rule was successfully created and enabled.
---

## Task 5: Enable S3 Server Access Logging

I enabled S3 Server Access Logging on the source bucket and configured another S3 bucket as the destination for the generated access logs.

Server access logs provide detailed records of requests made to an S3 bucket and can be useful for:

Security auditing
Access analysis
Troubleshooting
Operational monitoring
---

## Task 6: Verify Access-Log Delivery

After generating activity in the source bucket, I verified that S3 access-log objects were delivered to the configured destination bucket.

The log objects were organised using the AWS account, Region, source bucket, year, month, and day prefixes.

## Result

S3 server access logs were successfully generated and delivered to the destination bucket.
---

## Task 7: Create an Amazon SNS Topic and Subscription

I created an Amazon SNS Standard topic and added an email subscription.

I confirmed the subscription using the confirmation link received by email.

## Result
SNS topic type: Standard
Subscription protocol: Email
Subscription status: Confirmed
---

## Task 8: Configure an S3 Event Notification

I configured an S3 event notification and selected the Amazon SNS topic as the notification destination.

## Events Configured

All object-created events
All object-removed events

## Event Workflow
                  
                  Object Uploaded or Deleted
                             |
                             v
                       Amazon S3 Event
                             |
                             v
                      Amazon SNS Topic
                             |
                             v
                     Email Subscription
                             |
                             v
                    Notification Received
  ---

## Task 9: Verify the SNS Email Notification

I uploaded objects to the source S3 bucket and successfully received Amazon S3 event notifications through Amazon SNS.

The notification included event information such as:

Event name
AWS Region
S3 bucket name
Object key
Object size
Event timestamp

## Result

The complete event-driven notification workflow operated successfully.
---

## Key Learnings

S3 replication can automatically copy new objects between source and destination buckets.
S3 Batch Replication can replicate eligible existing objects.
S3 lifecycle rules help optimise storage costs by automatically transitioning objects between storage classes.
Lifecycle transitions occur asynchronously and do not happen immediately.
S3 Server Access Logging records requests made to an S3 bucket.
Server access logs are delivered asynchronously on a best-effort basis.
Amazon SNS uses a publish-and-subscribe messaging model.
Email subscriptions must be confirmed before receiving normal SNS notifications.
S3 event notifications can publish object-level events to an SNS topic.
S3 and SNS can be integrated to create an event-driven email-notification workflow.
---

## Lab Outcome

Successfully implemented and verified:

S3 Replication Rule
S3 Object Replication
S3 Batch Replication
S3 Lifecycle Management
Storage-Class Transitions
S3 Server Access Logging
Access-Log Delivery
Amazon SNS Topic
Confirmed Email Subscription
S3 Event Notifications
Email Notification Delivery
