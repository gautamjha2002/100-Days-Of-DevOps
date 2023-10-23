# Simple Storage Service (S3)

**What is S3 ?**  
S3 stands for simple Storage Service, and essentially It's Object storage in the cloud. 
- It provides secure, durable, and highly-scalable obect storage. 
- S3 allows us to store and retrieve any amount of data from anywhere on the web at very low cost. So it's extreamly Scalable. 
- It's really, realy simple to use. It comes with really easy-to-use web interface, 

**S3 is object based storage**  
S3 manages data as objects rather than in file systems or data blocks. basically it means S3 is a place where we can store our files. 
- We can upload any type of file in S3 
- Example include photos, videos, code, documents, and text files. 
- We can't install Operating System on S3 or cant run a database on S3. 
- S3 is ust a place to store our static files. the files that do not change. 

**S3 Basics** 
- Unlimited Storage :- The total volume of data and the number of obects we can store is unlimited. 
- Objects up to 5 Tb in size :- objects in S3 can be start with 0 bytes and go all the way up to 5 terabytes. 
- S3 Buckets :- We store our files in a thing called Bucket. It's basically a folder inside S3. So We might have bucket for our Test and Dev. Basically everywhere we store out files is in these things called Buckets. 

**Working With S3 Buckets**  
1. Universal Namespace :- All AWS accounts share the S3 namespace and for that reason, our S3 Bucket name has to be globally unique. 
2. Example S3 URLs :- ``https://bucket-name.s3.Region.amazonaws.com/key-name``
3. Uploading Files :- When we upload a file to S3, If that upload is successful, our browser will receive a HTTP 200 code.  

**Key-Value Store**  
1. Key :- Key is simply the name of the object, do if we were to upload a photo of AWS logo, The key would be *logo.jpg* 
2. Value :- Vale is the data itself, It is made up of a sequence of bytes.
3. Version Id :- This is whe we have versioning enabled on the bucket. This is imporant for storing multiple versions of the same object. 
4. Metadata :- Metadata is simply data about data. in S3 case the data about the data that we are storing could be content type, laste time the file modified, etc., etc. 

**S3 a safe place** 

S3 is a safe place to store our files. The data is always spread across multiple devices and facilities to ensure availability and durability. So it's is not on single data center in a single server, it is always spread across multiple devices an multiple facilities. 

**Highly Available and Highly Durable** 

- Built for availability :- It's built for 99.95% to 99.99% service availability depending on the S3 tier. 
- Designed for Durability :- Durability just means is our files going to be lost at some point? S3 is designed for what's called 11 9's (99.99999999%) durability for data stored in S3. 


**S3 Standard**  
standarad S3 is default version of S3, when we store our objects. 
- High Availability and Durability :- Data is sstored redundantly across multiple devices in multiple facilities ( >=3 AZs ):  
    * 99.99% availability
    * 99.999999999% durability (11 9's)  
- Designed for frequent access :- If we are frequently accessing our data may be reading or writing to it every second or even every hour or every day, that's what S3 is built for. 
- Suitable for most workloads :-
    *  S3 is default storage class 
    * it's use cases include things like websites, content distribution, mobile and gaming applications, big data analytics etc., etc. 

**Characteristics** 
- Tiered Storage :- S3 offers a range of storage classes designed for different use cases. So S3 Standrd fits most use cases, but it doesn't fit all use cases. 
- Lifecycle Management :- This is where we difine rules to automatically transistion our objects or files to a cheaper storage tier or to delete the objects that are no longer required after a set period of time. 
- Versioning :- With Versioning all versions of an object are stored in S3 and they can be retrieved, including deleted objects. 

**Securing Our Data**  
In terms of securing our data, we can secure our data in number of different ways. 
1. Server-Side Encryption :- Here we can set default encryption on a Bucket to encrypt all new objects when they are stored in the Bucket. So as soon as we upload an object to ur bucket that object will be encrypted. So if somebody breaks into AWS data center and starts stealing Hard drives, which is higly unlikely, that means they will not be able to access our objects because it would be encrypted. 
2. Access Control Lists (ACLs) :- This defines which AWS accounts or groups are granted access and the type of access that they are granted. We can attach S3 access control lists to individual objects to individual files within a Bucket. It gives us that much of a fine-grained approach. 
3. Bucket Poicies :- These are policies that are specific to what actions are allowed or denied for that particular Bucket. So we could allow Alice to put but not delete objects into a bucket. Bucket policies are bucket wide. It is simply JSOn policies, and we attach them to buckets and they will apply across the Bucket as a whole. 

**Strong Read-After-Write Consistency**  
- After a successful write :- A new object (PUT) or an overwrite of an existing object, any subsequent read request immediately receives the latest version of the object. 
- Strong consistency :- after a write, we can immediately perform a listing of the objects in a bucket with all changes reflected. 

| Access Control List  | Bucket Policy |
| ------------- | ------------- |
| Object ACLs work on an individual object level  | Bucket policies work on an entire bucket level  |


## Create a bucket
Step 1 :-
![Create Bucket](Assets/01.png)

Step 2 :- Give name to bucket (name should be universally unique)
![Unique Name](Assets/02.png)

Step 3 :- Hit on create button 

![Hit Create](Assets/03.png) 

Step 4 :- S3 bucket List 

![Bucket List](Assets/04.png) 

## Upload objects to bucket 

Step 1 :- Click on Bucket to upload object
![Bucket List](Assets/04.png) 

Step 2 :- Click on Upload 
![Click Upload](Assets/05.png) 

Step 3 :- Click on add files
![Click Add fies](Assets/06.png) 

Step 4 :- Select files 
![Select fies](Assets/07.png) 

Step 5 :- Select Upload 
![Select Upload](Assets/08.png) 

Step 6 :- Check for status if upload succeded
![Status Check](Assets/09.png) 

## Make object publically accessible 

Step 1 :- In bucket, click on permissions 
![click permission](Assets/10.png) 

Step 2 :- in block public access section, click on edit
![click edit](Assets/11.png) 

Step 3 :- Uncheck block public access 
![click edit](Assets/12.png) 

Step 4 :- Click on save changes and then type confirm then click confirm
![type confirm](Assets/13.png) 

Step 5 :- Again go to bucket permission and click on Edit Object ownership 
![Edit object Ownership](Assets/14.png)

Step 6 :- Click on ACL enabled and click on checklist (I acknowledge that ACL will be restored) 

![Enable ACL](Assets/15.png)

Step 7 :- Save Changes 
![Save Changes](Assets/16.png)

Step 8 :- Go to bucket and click the checklist of object that you want to make public 
![Click checklist](Assets/17.png)

Step 9 :- Go to action and click make public using ACL
![Click make public using ACL](Assets/18.png)

Step 10 :- Click Make Public 
![Click make public](Assets/19.png)


## Access the public file of S3
``https://bucket-name.s3.Region.amazonaws.com/key-name``  


``https://gautam-bucket.s3.ap-south-1.amazonaws.com/My_Linked_In.png``  
![Access file](Assets/20.png)


## Host Static Website using S3

We can use S3 to host Static Websites, wuch as .html sites. 

Dynamic websites, such as those that require database connections cannot be hosted on S3. 

**S3 Scales Automatically**  
To meet demand S3 scales automatically, many enterprises will put static websites on S3 when they think there is going to be a large number of requests (e.g., for a moview preview). 


**Let's Create a new bucket for Hosting Static Content.**

Step 1 :- Create a bucket with allowing public access
![Public access bucket](Assets/21.png)

Step 2 :- Go to properties of bucket and scroll down to static website hosting and click on Edit
![Edit static website hosting](Assets/22.png)

Step 3 :- Enable Static website hosting 
![Enable static website hosting](Assets/23.png)

Step 3 :- below that enter index.html file name and error.html file name and click save changes
![Specify index.html and error.html](Assets/24.png)

Step 4 :- Upload the static files
![Upload files](Assets/25.png)

Step 5 :- Make entire bucket public using Bucket policy, Go to permissions of bucket.
![Bucket Permission](Assets/26.png)

Step 6 :- Go to edit Bucket policy and copy this json and paste it there 
```json 
{
    "Version": "2012-10-17",
    "Statement" : [
        {
            "Sid": "PublicReadGetObject",
            "Effect": "Allow",
            "Principal": "*",
            "Action": [
                "s3:GetObject"
            ],
            "Resource": [
                "arn:aws:s3:::BUCKET_NAME/*"
            ]
        }
    ]
}
```
![Bucket Policy Update](Assets/27.png)

**[NOTE]** Do not foget to update the resource arn.

Step 7 :- Click on save changes  
![Bucket Policy save changes](Assets/28.png)

To access the website go to properties of bucket and in static website hosting section click on the URL to access the website. 
![Website URl](Assets/29.png)

Here is the website 

![Website](Assets/30.png)

## Versioning Objects in S3 

**What is versioning?**  
We can enable versioning in S3 so that we have multiple versions of an object within S3 bucket. It is a way of doing versio control with your object or files. 

**Advantages Of versioning**
- All Versions :- All versions of an object are stored in S3. This includes all writes and even if you delete an object.
- Backup :- Can be a great backup tool
- Cannot be Disbled :- Once enabled, versioning cannot be disabled only suspended. 
- Lifecycle Rules :- Can be integrated with lifecycle rules.
- Supports MFA :- Can Support multi-factor Authentication. 

**Steps to enable Versioning**  
Step 1 :- Go to Bucket and click properties  
Step 2 :- In bucket versioning Section, click Edit  
Step 3 :- Click on enable and save changes.  

Now when we will add a object in file with same name it will be versioned. 


**What happen When We delete the latest version of Object**  
When latest version is deleted It will not be shown directly in the bucket, but when we click on List version (toggle button) We will see the every version even deleted one.

There will be a delete marker in the object which is deleted. When we delete that delete marker the object will be restored. 

## S3 Storage Classes 

1. S3 Standard 
- High Availability and Durability
    * Data is stoored redundantly across multiple devices in multiple facilities (>=3 AZs)
    * 99.99% Availability 
    * 99.999999999% durability (11 9's)
- Designed for Frequent Access
    * Perfect for frequently accessed data. 
- Suitable for Most Workloads
    * The default storae class.
    * Use cases include websites, content distribution, mobile and gaming applications, and big data analytics. 

2. S3 Standard-Infrequent Access (S3 Standard-IA)
- Designed for Infrequently Accessed Data
- Rapid Access :- Used for data that is accessed less frequently but requires rapid access when needed. 
- We Pay to access the Data :- There is low per-GB storage price and a per-GB retrieval fee. 
- Use cases :- Great for long-term storage, backups, and as a data store for disaster recovery files.
- Comes with :  
    * 99.9% Availability 
    * 99.999999999% (11 9's) Durability

3. S3 One Zone-Infrequent Access  
- It is like S3 standard-IA, but data is sstored redundantly within a single AZ.  
- Costs 20% less than regular S3 Staandard-IA 
- Great for long-lived, infrequently accessed, non-critical data. 
- 99.9% Availability
- 99.999999999% (11 9's) Durability

4. S3 Intelligent-Tiering
- 2 Tiers - Frequent and Infrequent Access :- Automatically moves our data to most cost-effective tier based on how frequently we access each object. 
- 99.99% Availability
- 99.999999999% (11 9's) Durability
- Optimizes cost :- montly fee of $0.0025 per 1,000 objects

5. Glacier and Glacier Deep Archive
- We pay each time we access our data.
- Use only for archiving data
- Glacier is cheap storage
- Optimize for data that is very infrequently accssed. 
- 3 Glaier Options :-  
    * Glacier Instant Retrieval :- Provides long-term data archiving with instant retrieval time for your data.  
    * Glacier Flexible Retrival :- Ideal storage class for archieve data that does not require immediate access but needs the flexibility to retrieve large sets of data at no cost, such as backup or disaster recovery use cases. Can be minutes or up to 12 hours. 
    * Glacier Deep Archive :- Cheapest storage class and designed for customers that retain data sets for 7-10 years or longer to meet customer needs and regulatory compliance requirements. The standard retrieval time is 12 hours, and the bulk retrival time is 48 hours. 
- 99.99% Availability 
- 99.999999999% (11 9's) Durability

**S3 Storage class cost High to low**  
S3 Standard  
S3 Intelligent-Tiering  
S3 Standard-infrequent Access  
S3 One Zone-Infrequent Access  

## Lifecycle Management with S3 
Lifecycle management automates moving your objects between the different storage tiers, thereby maximizing cost effectiveness.  

**Combining Lifecycle management with versioning**   
We can use lifecycle management to move different versions of objects to different storage tiers.  

**Steps to enable Lifecycle management**    
Step 1 :- Enable versioning   
Step 2 :- Go to management section of Bucket   
Step 3 :- Click on create Lifecycle rules.   
Step 4 :- Give Lifecycle rule name, choose rule scope, Select Lifecycle rule actions.   
Step 5 :- To move between storage clsses, select "move current versions of objects between storage classes"   
Step 6 :- Add transistion rules   
Step 7 :- Click create rule.   

