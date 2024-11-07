# Frontend
This frontend repository goes over the foundation of the Cloud Resume Challenge, which is hosting a resume on a static website using a cloud software, in this case AWS S3. By deploying a file with HTML and CSS, the resume is handled through code through HTML's structure and CSS's style. This was uploaded to the S3 bucket, and using AWS CloudFront, Certificate Manager, Namecheap, and Route53, was deployed to my [website](https://www.aelikim.com). 

Some important files and directories within this repository include the index.html file that serves as the backbone of the website, the js folder containing the Javascript file, the .github/workflows directory which allows integration into the local machine, .gitignore file, and images folder from linking GitHub to S3.

### HTML and CSS

HTML (Hypertext Markup Language) is a coding language I used to create the structure of my cloud resume challenge. This serves as the backbone of websites, and dictates what will be displayed on a webpage. CSS (Cascading Style Sheets), similarly to HTML, dictates the display of a web page, but handles more of the presentation and style. In the case of my [website](https://www.aelikim.com), CSS handles the styling of the text, size, and alignment of my text, while HTML decides the actual structure. The full html file for my resume can be found within this repository, under the name index.html.

### Static S3 Website

Amazon S3 is a cloud-based storage service provided to allow a variety of different uses such as storage or referencing across different AWS applications. Most importantly for this project, however, S3 allows static website hosting and was a key part in this challenge. Below, is my current S3 bucket for aelikim.com, including the uploaded index.html file.

<img width="600" alt="Screenshot 2024-11-06 at 12 14 18 PM" src="https://github.com/user-attachments/assets/033a8813-c7f4-4201-a700-d2b931e9e016">
<br><br>
After uploading the resume to S3 and changing the access to public, the next step was to enable static website hosting. Static website hosting for this challenge entails a public accesss website where users can view static content without heavy server-side code, in this case being the cloud resume. 
<br><br>
<img width="600" alt="Screenshot 2024-11-06 at 12 14 28 PM" src="https://github.com/user-attachments/assets/07c7a9fa-97db-4a97-abaa-331006f81529">
<br><br>
By creating the bucket website endpoint, we had the endpoint in which users were to eventually reach. This by itself is not the complete endpoint, however, since the generated url does not point to a clean website like "aelikim.com," and instead points to the created s3 endpoint using HTTP. For easy access and better implementation, the website still required a custom domain, and increased security through HTTPS rather than through HTTP.

### DNS

DNS, or Domain Name System, allows for users to easily find web addresses easily through commonly used words or letters. This is much easier than using an IP address, but will require extra steps to setup and link to our current website.

In order to use a domain matching along the lines of (first_name)(last_name).com, we have to use a custom domain name. After creating this custom name, it will then need to access the CloudFront distribution to point to the correct place. We will then need to use AWS Route53 to ensure traffic gets routed correctly, including for both websites including and excluding "www."
<br><br>
<img width="600" alt="Screenshot 2024-11-06 at 12 16 09 PM" src="https://github.com/user-attachments/assets/d9d2a42b-427b-41a6-932b-63c5c43d42fd">
<br><br>
After creating the domain aelikim.com on Namecheap, we were given multiple custom DNS. Route53 is then needed to route these addresses to the correct place, being the endpoint we had created earlier in our bucket. 
<br><br>
<img width="600" alt="Screenshot 2024-11-06 at 1 05 06 PM" src="https://github.com/user-attachments/assets/4ea8d486-19ad-4d75-a250-d3286f23807d">
<br><br>
By matching the custom DNS to the correct object, the last step is to link everything together. CloudFront will act to serve content from our origin bucket to these new domains. HTTPS will cover more of AWS CloudFront, the main thing being setting up the alternative names so that our certificate will access the website through HTTPS.

### HTTPS

Utilizing HTTPS is critical for ensuring security, as we currently use the HTTP protocol. HTTPS not only encrypts data rather than transmit it using plain text in the case of HTTP, but HTTPS also uses certificate validation. SSL/TLS certificates are used by HTTPS to ensure the website is authentic, which alongside its encryption helps mitigate risk.

To go about using HTTPS, AWS CloudFront and Certificate Manager can be implemented to increase security. AWS Certificate Manager helps with SSL/TLS certificates by automatically renewing certificates and helps manage the certifications. AWS CloudFront helps with security and reliability, both enabling encryption and HTTPS support, but also uses various worldwide locations to cache the website data and deliver faster load times. 
<br><br>
<img width="600" alt="Screenshot 2024-11-06 at 12 14 51 PM" src="https://github.com/user-attachments/assets/e7a1319d-af9c-463d-81f0-8eeca0601de8">
<br><br>
The picture above shows the alternative domain names after finishing the creation of a new CloudFront distribution. By using the alternative names and SSL certificate, users seeking the website can now use HTTPS as it is enabled for the custom domain name. In order to check that this is running on HTTPS, by viewing the elements of the website and refreshing, the picture below shows that the response is coming from CloudFront. This means that it is correctly routing through HTTPS since it is responding from the created distribution.
<br><br>
<img width="600" alt="Screenshot 2024-11-06 at 12 15 16 PM" src="https://github.com/user-attachments/assets/2738fe41-7737-4064-bc6e-a4366b81c028">
<br><br>

### CI/CD (Frontend), Source Control, and Infrastructure as Code

GitHub Actions was set up within this frontend repository to automatically update S3 when new website code is pushed. This is achievable due to the workflows and .yml file.

Using VSCode, the three repositories were also created, and mirrored to match my environments. Using a variety of tools such as Terraform, GitHub, and VSCode, these three steps were completed, and the S3 was defined and deployed within Terraform.
