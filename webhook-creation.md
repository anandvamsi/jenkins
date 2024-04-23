# Webhook

A webhook is a method for web applications to communicate with each other in real-time. 
It's a way for one application to notify another application or service about events that have occurred.

Webhooks are commonly used in various scenarios such as integrating different services, automating processes, 
and triggering actions based on specific events, like new data being available or a status update occurring

### How to create a webhook in Jenkins.

```Jenkins Part```
Imagine jenkins is installed in public cloud server 18.188.30.125
1.Create a free style project/Maven  and Add the github repo where in SCM
2.In the "BUILD TRIGGER" Section select the ```Gitub hook for GitSCM polling```
3.Save the project

Note:: Make sure port no 8080 is open to public.

### At the Github page.

1. Go the GitHub repo
2. Choose the options "setting" right top and select the "Webhooks" in right side bar.
3. Click "Add Webhooks" 
Fill the the following details
	 Payload URL http://18.188.30.125:8080/github-webhook/
	 content type :- application-json
4. click "Add Webhook" to finish it


Notes:
when ever commits are pushed to this repo, It send notification to Jenkins .Under Jenkins there can be mulitple project who use the same project.
Only those project who has enabled with Github hook for GitSCM polling will only get triggred the job.
