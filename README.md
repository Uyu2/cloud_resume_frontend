# Frontend
This frontend repository goes over the foundation of the Cloud Resume Challenge, which is hosting a resume on a static website using a cloud software, in this case AWS S3. By deploying a file with HTML and CSS, the resume is handled through code through HTML's structure and CSS's style. This was uploaded to the S3 bucket, and using AWS CloudFront, Certificate Manager, Namecheap, and Route53, was deployed to my [website](https://www.aelikim.com). 

### HTML and CSS

HTML (Hypertext Markup Language) is a coding language I used to create the structure of my cloud resume challenge. This serves as the backbone of websites, and dictates what will be displayed on a webpage. CSS (Cascading Style Sheets), similarly to HTML, dictates the display of a web page, but handles more of the presentation and style. In the case of my [website](https://www.aelikim.com), CSS handles the styling of the text, size, and alignment of my text, while HTML decides the actual structure. The full html file for my resume can be found within this repository, under the name [index.html](https://github.com/Uyu2/Frontend/blob/8109766f7f4d52137aa295cc66cd6d56ee88240b/index.html).

### Static S3 Website

Amazon S3 is a cloud-based storage service provided to allow a variety of different uses such as storage or referencing across different AWS applications. Most importantly for this project, however, S3 allows static website hosting and was a key part in this challenge. Below, is my current S3 bucket for aelikim.com, including the uploaded index.html file.

<img width="600" alt="Screenshot 2024-11-06 at 12 14 18 PM" src="https://github.com/user-attachments/assets/033a8813-c7f4-4201-a700-d2b931e9e016">
<br><br>
After uploading the resume to S3 and changing the access to public, the next step was to enable static website hosting. Static website hosting for this challenge entails a public accesss website where users can view static content without heavy server-side code, in this case being the cloud resume. 
<br><br>
<img width="600" alt="Screenshot 2024-11-06 at 12 14 28 PM" src="https://github.com/user-attachments/assets/07c7a9fa-97db-4a97-abaa-331006f81529">
<br><br>
By creating the bucket website endpoint, we had the endpoint in which users were to eventually reach. This by itself is not the complete endpoint, however, since the generated url does not point to a clean website like "aelikim.com," and instead points to the created s3 endpoint using HTTP. For easy access and better implementation, the website still required a custom domain, and increased security through HTTPS rather than through HTTP.
