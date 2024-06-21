# Outlook Simple Add-in

## To support the latest version of `yo office` you need node version of node 18

1. To install yo and office-generator
   1. make sure you are in the folder you want to generate the files or it will generate in the default folder you are in

`npm install -g yo generator-office`

`yo office`

2. This will bring you to a setup in terminal:

* _**Office Add-in Task Pane project**_&#x20;
* _**Office Add-in Task Pane project using React framework**_&#x20;
* _**Excel Custom Functions using a Shared Runtime**_&#x20;
* _**Excel Custom Functions using a JavaScript-only Runtime**_&#x20;
* _**Office Add-in Task Pane project supporting single sign-on**_&#x20;
* _**Outlook Add-in with unified manifest for Microsoft 365 (preview)**_&#x20;
* _**Office Add-in project containing the manifest only**_

I selected the _**Office Add-in Task Pane project**_ it is a basic project with HTML CSS and JavaScript

3. It will ask if you want to generate the template in vanilla js or typescript
4. Next name the project
5. Next it will ask you what type of Add-in you want to create:

* _**Excel**_&#x20;
* _**Onenote**_&#x20;
* _**Outlook**_&#x20;
* _**Powerpoint**_&#x20;
* _**Project**_&#x20;
* _**Word**_

6. After you selected what app you are making the Add-in for it will generate the template

## There are two ways to run the project to test

* Local host side loading&#x20;
  * spins up a webpage for testing to view HTML, no attachment to outlook&#x20;
* Installing to outlook add-in
  * this is more for production but can work for testing, you have to keep uploading after each change

## How to install Add-in into outlook

{% embed url="https://support.microsoft.com/en-us/office/use-add-ins-in-outlook-1ee261f9-49bf-4ba6-b3e2-2ba7bcab64c8" %}

