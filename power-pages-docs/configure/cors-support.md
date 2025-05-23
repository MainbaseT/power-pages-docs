---
title: Set up HTTP headers in Power Pages
description: Learn how to set up HTTP headers in Power Pages.
author: DanaMartens

ms.topic: conceptual
ms.custom: 
ms.date: 4/10/2023
ms.subservice: 
ms.author: bipuldeora
ms.reviewer: dmartens
contributors:
    - sandhangitmsft
    - nageshbhat-msft
---

# Set up HTTP headers in Power Pages

The [cross-origin resource sharing (CORS)](https://www.w3.org/TR/cors/) protocol consists of a set of headers that indicates whether a response can be shared with another domain. You can configure CORS support in Power Pages using the [Portal Management app](portal-management-app.md) by adding and configuring the [site settings](configure-site-settings.md).

The following site settings are used to configure CORS:

| Site Setting | Request Header | Description |
|-|-|-|
| HTTP/Access-Control-Allow-Credentials | Access-Control-Allow-Credentials | The only valid value for this header is true (case-sensitive). If you don't need credentials, omit this header entirely (rather than setting its value to false). 
| HTTP/Access-Control-Allow-Headers | Access-Control-Allow-Headers | A comma-delimited list of the supported HTTP request headers.
| HTTP/Access-Control-Allow-Methods | Access-Control-Allow-Methods | A comma-delimited list of the allowed HTTP request methods such as GET, POST, OPTIONS.
| HTTP/Access-Control-Allow-Origin | Access-Control-Allow-Origin | URL of the Microsoft Dataverse instance, such as https://contoso.crm.dynamics.com. To allow any URI to access your resources, use \*.                 |
|  HTTP/Access-Control-Expose-Headers | Access-Control-Expose-Headers | A comma-delimited list of HTTP header names other than the simple response headers that the resource might use and can be exposed.
| HTTP/Access-Control-Max-Age | Access-Control-Max-Age |  Maximum number of seconds the results can be cached.
| HTTP/Content-Security-Policy | Content-Security-Policy | Controls resources the user agent is allowed to load for a given page.
| HTTP/Content-Security-Policy-Report-Only | Content-Security-Policy-Report-Only | Allows web developers to experiment with policies by monitoring, but not enforcing, their effects. These violation reports consist of JSON documents sent via an HTTP POST request to the specified URI.
| HTTP/X-Frame-Options | X-Frame-Options | Indicates whether a browser should be allowed to render a page in a *\<frame\>*, *\<iframe\>*, *\<embed\>* or *\<object\>*.
| HTTP/X-Content-Type-Options | X-Content-Type-Options | Disables MIME sniffing and forces browser to use the type given in *Content-Type*.

## Frequently asked questions

### Is it possible to add a **Cache-Control** in http response header?

Cache-Control in http response header is added in all requests to the site, none of the Cache-Control directives are configurable. Cache-Control for anonymously accessible static files set to public. The **max-age** value is defaulted to 1 hour.

For more information about how to configure site settings in Power Pages, go to [Manage site settings](configure-site-settings.md#manage-site-settings).


