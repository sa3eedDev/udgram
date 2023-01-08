# infrastructure

## Frontend

For the Udagram frontend we use AWS s3 (bucket) to upload the static frontend files. The bucket must be publicly accessible, and configured it as a static hosting to make it work. 

**ACLs must be enabled**
must add this to the bucket policy to enable other AWS services to access the bucket:

```json

{
"Version":"2012-10-17",
"Statement":[
  {
      "Sid":"Stmt1625306057759",
      "Principal":"*",
      "Action":"s3:*",
      "Effect":"Allow",
      "Resource":"arn:aws:s3:::[bucket-name]/*"
  }
]
}
```

add this to the CORS configuration for other services to access the website:

```json 
[
 {
     "AllowedHeaders": [
         "*",
         "Content-Type",
         "Authorization",
         "Access-Control-Allow-Origin",
         "Access-Control-Allow-Headers",
         "Access-Control-Allow-Methods"
     ],
     "AllowedMethods": [
         "POST",
         "GET",
         "PUT",
         "DELETE",
         "HEAD"
     ],
     "AllowedOrigins": [
         "*"
     ],
     "ExposeHeaders": []
 }
]

```

## Backend 

For the Udagram backend we use AWS Elastic Beanstalk(EB) to run our server. EB should be Node.js 14 to run our server. 
Specify the environment variables in the Elastic Beanstalk environment >> Configuration >> Software settings >> Environment Properties section.
```
POSTGRES_USERNAME=
POSTGRES_PASSWORD=
POSTGRES_HOST=
POSTGRES_DB=
AWS_BUCKET=
AWS_REGION=
AWS_PROFILE=
JWT_SECRET=
URL=

```
then upload the backend build to the EB and should be ready to go!

## Database

For the Udagram Database we used AWS RDS database. We used Postgres 13 as our database. the database name in the server is postgres. 