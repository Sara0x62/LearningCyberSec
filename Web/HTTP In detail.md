# What is HTTP(S)?
**HTTP (HyperText Transfer Protocol)**: HTTP is the standard protocol for transmitting webpage data, including HTML, images, and videos. Developed by Tim Berners-Lee and his team between 1989-1991, it's used whenever you view a website.

**HTTPS (HyperText Transfer Protocol Secure)**: HTTPS is the secure version of HTTP. It encrypts data transmission, preventing unauthorized access. This encryption ensures data integrity and authenticity, verifying that you're communicating with the correct web server.
# Requests and Responses
## What is a URL?

![](../attachments/859794625d4b69dff96ea0a1c6ea6641.png)

**Scheme**: what protocol to use, such as HTTP, HTTPS, FTP.
**User**: (not shown in image) some services require authentication, you can put a username:password in the URL to log in. Example; `http://user:password@example.com:80`
**Host**: The domain or IP of the server
**Port**: The port the service is on, usually 80 for HTTP, 443 for HTTPS - can be anywhere from 1 to 65535.
**Path**: Filename or location of the page/resource you're trying to access.
**Query String**: extra values for parameters using a `key=value` system, (e.g. YouTube has `v=dQw4w9WgXcQ` so it knows what video you want)
**Fragment**: Reference to a location on an actual page.

## Making a Request

Example request:
```http
GET / HTTP/1.1
Host: tryhackme.com
User-Agent: Mozilla/5.0 Firefox/87.0
Referer: https://tryhackme.com/

```

Breaking down the lines:
1. Sending the GET method, requesting the homepage ( `/` ) and telling the server we're using HTTP version 1.1
2. Telling the server what website we want
3. Telling the server our browser
4. Telling the server where we got referred from
5. HTTP requests always end with a blank line

Example response:
```http
HTTP/1.1 200 OK
Server: nginx/1.15.8
Date: Fri, 09 Apr 2021 13:34:03 GMT
Content-Type: text/html
Content-Length: 98

<html>
<head>
    <title>TryHackMe</title>
</head>
<body>
    Welcome To TryHackMe.com
</body>
</html>
```

Line breakdown:
1. HTTP 1.1, the HTTP version from the server `200 OK` is the HTTP Status Code.
2. The server software and version number
3. current date/time of the web server
4. `Content-Type` is to inform the client what kind of data is being sent such as HTML, images, videos, pdf, XML, etc.
5. `Content-Length` - the amount of data is in the response.
6. Blank line to confirm the end of the HTTP Response.
7. - 14 : the requested information, here it's the homepage.
# HTTP Methods
HTTP Methods show the intended action when making a request the most common ones are **GET** and **POST**

**GET Request** - used for getting information of a web server.
**POST Request** - used for submitting data to the web server
**PUT Request** - used for submitting to a web server to update information.
**DELETE Request** - used for deleting information/records from a web servers.

# HTTP Status Codes
## HTTP Status code ranges:

| **Status-code range**              | **Range description**                                                                                                                                                                  |
| ---------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **100-199 - Information Response** | These are sent to tell the client the first part of their request has been accepted and they should continue sending the rest of their request. These codes are no longer very common. |
| **200-299 - Success**              | This range of status codes is used to tell the client their request was successful.                                                                                                    |
| **300-399 - Redirection**          | These are used to redirect the client's request to another resource. This can be either to a different webpage or a different website altogether.                                      |
| **400-499 - Client Errors**        | Used to inform the client that there was an error with their request.                                                                                                                  |
| **500-599 - Server Errors**        | This is reserved for errors happening on the server-side and usually indicate quite a major problem with the server handling the request.                                              |
## Common HTTP Status Codes:
| **Status code**                  | **Description**                                                                                                                                                                                                               |
| -------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **200 - OK**                     | The request was completed successfully.                                                                                                                                                                                       |
| **201 - Created**                | A resource has been created (for example a new user or new blog post).                                                                                                                                                        |
| **301 - Moved Permanently**      | This redirects the client's browser to a new webpage or tells search engines that the page has moved somewhere else and to look there instead.                                                                                |
| **302 - Found**                  | Similar to the above permanent redirect, but as the name suggests, this is only a temporary change and it may change again in the near future.                                                                                |
| **400 - Bad Request**            | This tells the browser that something was either wrong or missing in their request. This could sometimes be used if the web server resource that is being requested expected a certain parameter that the client didn't send. |
| **401 - Not Authorised**         | You are not currently allowed to view this resource until you have authorised with the web application, most commonly with a username and password.                                                                           |
| **403 - Forbidden**              | You do not have permission to view this resource whether you are logged in or not.                                                                                                                                            |
| **404 - Page Not Found**         | The page/resource you requested does not exist.                                                                                                                                                                               |
| **405 - Method Not Allowed**     | The resource does not allow this method request, for example, you send a GET request to the resource /create-account when it was expecting a POST request instead.                                                            |
| **500 - Internal Service Error** | The server has encountered some kind of error with your request that it doesn't know how to handle properly.                                                                                                                  |
| **503 - Service Unavailable**    | This server cannot handle your request as it's either overloaded or down for maintenance.                                                                                                                                     |
# Headers
## Common Request Headers
﻿These are headers that are sent from the client (usually your browser) to the server.  

**Host:** Some web servers host multiple websites so by providing the host headers you can tell it which one you require, otherwise you'll just receive the default website for the server.  

**User-Agent:** This is your browser software and version number, telling the web server your browser software helps it format the website properly for your browser and also some elements of HTML, JavaScript and CSS are only available in certain browsers.  

**Content-Length:** When sending data to a web server such as in a form, the content length tells the web server how much data to expect in the web request. This way the server can ensure it isn't missing any data.

**Accept-Encoding:** Tells the web server what types of compression methods the browser supports so the data can be made smaller for transmitting over the internet.

**Cookie:** Data sent to the server to help remember your information (see cookies task for more information).  
## Common Response Headers
These are the headers that are returned to the client from the server after a request.

**Set-Cookie:** Information to store which gets sent back to the web server on each request (see cookies task for more information).  

**Cache-Control:** How long to store the content of the response in the browser's cache before it requests it again.  

**Content-Type:** This tells the client what type of data is being returned, i.e., HTML, CSS, JavaScript, Images, PDF, Video, etc. Using the content-type header the browser then knows how to process the data.  

**Content-Encoding:** What method has been used to compress the data to make it smaller when sending it over the internet.
# Cookies
![](../attachments/7cfabfe57a5ed04e9133b05054056e69.png)
**Cookies** are commonly used for website authentication, storing tokens instead of clear-text passwords. You can view the cookies your browser sends to a website by accessing developer tools and navigating to the "Network" tab. This tab displays all requested resources, and you can find cookies in the "Cookies" tab of each request's detailed breakdown.