---
title: Important upcoming changes and deprecations in Power Pages
description: Learn about the important changes, including deprecations, coming soon to Power Pages.
author: DanaMartens

ms.topic: concept-article
ms.date: 06/24/2024
ms.subservice: 
ms.author: bipuldeora
ms.reviewer: dmartens
contributors:
    - sandhangitmsft
    - dileepsinghmicrosoft
    - nageshbhat-msft
    - sampatn
ms.custom:
  - sfi-ropc-nochange
---

# Important upcoming changes and deprecations in Power Pages

The announcements for changes and deprecations described in this article apply to Power Pages. Makers, developers, and IT pros can use this information to prepare for future releases.

> [!IMPORTANT]
> *Deprecated* means that we intend to remove the feature or capability from a future major release. The feature or capability will continue to work and is fully supported until it's officially removed. This deprecation notification can span a few months or years. After it's removal, the feature or capability no longer work. This notice is to allow you sufficient time to plan and update your code before the feature or capability is removed.

## Enhanced link creation in design studio

In July 2024, we're introducing improvements to the way text, image, and button links are created in Power Pages design studio. The **Link to a URL** field will accept any type of link, including mailto and tel links. Additionally, there will be a new option to choose whether the link opens in a new window or the current one.

We'll also change the way button components are created. Previously, buttons were represented using the `<button>` HTML tag with URLs handled by the `onclick` attribute:  

`<button onclick="window.location.href='/page/subpage-1/'" type="button" value="subpage-1" class="button1">Add a call to action here</button>`

With the upcoming improvements, all new button components are created using the `<a>` anchor tag, with the href attribute responsible for URL navigation. Any `<a>` tag with the `btn` class are recognized as a button component in design studio:

`<a href="/page/subpage-1/" class="btn button1">Add a call to action here</a>`

This change only applies to new buttons. Buttons that were previously created aren't impacted and continue to work in design studio. However, you might need to adjust any custom CSS or JavaScript that uses the `<button>` tag for selection.

## Power Apps portals Studio to be retired

Effective February 26, 2024, Power Apps portals Studio will be retired. All sites open in [Power Pages design studio](configure/design-build-overview.md).

### What is Power Apps portals Studio?

Power Apps portals Studio is the legacy experience of Power Pages design studio.

### Will I lose access to all portals and websites I created in Power Apps portals Studio?

No. You can continue to access and edit all of the sites you created through Power Apps portals Studio, you'll just access them from Power Pages. More information: [Manage sites](admin/manage-sites.md) 

## Site creation from Power Apps

Starting September 2023, blank app portal creation from Power Apps will be redirected to [Power Pages](https://make.powerpages.microsoft.com). 

### Why can't I create a portal from Power Apps?

As part of providing a streamlined and improved experience for makers to create a website, all the site creation experience is now provided through [Power Pages](https://make.powerpages.microsoft.com). You can create secure, enterprise-grade, low-code business websites with Power Pages. More information: [Create a site with Power Pages](getting-started/create-manage.md)

### Why don't I see Dynamics 365 portal templates in Power Apps?

You can create websites using the Dynamics 365 templates from [Power Pages](https://make.powerpages.microsoft.com). More information: [Dynamics 365 templates](templates/dynamics-365-apps/overview.md)

### Why don't I see Dynamics 365 portal templates in Power Pages? 

If you're using [Power Pages](https://make.powerpages.microsoft.com) for the first time, you won't see Dynamics 365 portals in your first site creation. You'll see them in subsequent sites created, if the environment has any of the Dynamics 365 applications installed in it.   

### Why don't I see my Portals created in Power Apps under the **Apps** list in Portals Studio? 

Starting October 2023, portals created in Power Apps portals will show in [Power Pages](https://make.powerpages.microsoft.com), More information: [Manage sites created in Power Apps](/power-apps/maker/portals/manage-existing-portals)

## Power Apps portals admin center

The Power Apps portals admin center is now deprecated and no longer available as of June 2023. Use the new [Power Pages admin hub](/power-pages/admin/admin-overview) in the Power Platform admin center. 

## Controlling site visibility changes in Power Pages

Starting October 2022 with website version 9.4.9.xx, any new site created in Power Pages or Power Apps portals will be private by default. Only makers or people in the organization granted permission by makers will have website access, making Power Pages sites secure. This feature provides another layer of security using Microsoft Entra authentication to prevent accidental leaks of partially developed website data and design. When a website is ready to go-live, the site visibility can be changed to public making it accessible to everyone over the internet anonymously or secured with identity providers.  

At launch, users with the system administrator role along with [service admins](/power-platform/admin/use-service-admin-role-manage-tenant) will by default have privilege to change site visibility status (private to public or vice versa). 

> [!NOTE]
> After October 1, 2023 system administrators will not be able to change site visibility when the tenant-level setting is null.  To prevent this, set the value for the tenant level setting to either TRUE or FALSE. More information: [Change tenant-level setting](security/site-visibility.md#change-the-tenant-level-setting)

## OAuth 2.0 implicit grant flow within your portal 

The [authorize endpoint](/power-apps/maker/portals/oauth-implicit-grant-flow#authorize-endpoint-details), [token endpoint](/power-apps/maker/portals/oauth-implicit-grant-flow#authorize-endpoint-details) using GET request, and using the default certificate for OAuth 2.0 implicit grant flow is deprecated. No action is needed for newly created portals or for existing portals that don't use this feature. If you're already using this feature, you need to use the token endpoint POST request to get a secure access token to authorize the external APIs.

> [!NOTE]
> - All existing customers who are using this deprecated feature need to migrate to the supported method by October 2022.
> - For more information on using a custom certificate, go to [Using a custom certificate](/power-apps/maker/portals/oauth-implicit-grant-flow#custom-certificates).
> - For sample code on using POST calls on the Token endpoint, go to [Token endpoint sample](/power-apps/maker/portals/oauth-implicit-grant-flow#token-endpoint-sample).

## List OData feed 

Starting June 2022, using [OData feeds](/power-apps/maker/portals/configure/list-odata-feeds) to interact with data via RESTful web services will be deprecated. We recommend that you migrate to the Power Pages [Web API](configure/web-api-overview.md). 

> [!NOTE] 
> - Starting October 2022, newly provisioned websites won't able to use list OData features. 
> - The OData feeds list feature will be removed April 1, 2024.

## Portal content editor

Starting June 2022, the portal content editor tool to design your website is deprecated. We recommend using Power Apps portals Studio to edit the portal.

> [!NOTE]
> This feature will be removed by October 1, 2023.

## Portals search using Lucene.NET search 

Starting with website version 9.4.4.xx, portal search uses Dataverse search as a default search provider for all new portals. Lucene.NET search is deprecated; however, existing portals that use Lucene.NET search won't be affected. We recommend that users migrate to Dataverse search. Enable Dataverse search for existing portal by setting the Search/EnableDataverseSearch site setting to true.

> [!NOTE]
> All existing customers who use Lucene.NET search must migrate to Dataverse search by October 1, 2024.

## Content Delivery Network for US Government

Starting January 2022, Power Apps portals for US Government will begin using [Azure Content Delivery Network](/azure/cdn/cdn-overview) for default JavaScript and CSS files. Depending on the US Government deployment, configure the allowlist for the following Content Delivery Network URLs as follows.

| Power Pages version | Content Delivery Network URL |
| - | - |
| Government Community Cloud (GCC) | `https://gov.content.powerapps.us` |
| GCC High | `https://high.content.powerapps.us` |
| Power Apps Department of Defense | `https://content.appsplatform.us` |

## Table permission changes for forms and lists on new websites

Starting with release [9.3.7.x](/power-platform/released-versions/portals/portalupdate1), newly created websites will have table permissions enforced for all [forms](/power-apps/maker/portals/configure/entity-forms#secure-your-forms) and [lists](/power-apps/maker/portals/configure/securing-lists), irrespective of the **Enable Table Permissions** setting.

Also, with the same release, lists on all websites (new or existing) that have [list OData feeds](/power-apps/maker/portals/configure/list-odata-feeds) enabled will require that the appropriate [table permissions](security/table-permissions.md) be set up for the feed on these lists to work.

> [!NOTE]
> The changes described above also apply to websites [converted](/power-apps/maker/portals/admin/convert-portal) from trial to production.

To configure anonymous access explicitly, use proper [table permissions](security/table-permissions.md) and web role set up instead.

## SameSite mode changes

Starting with Power Pages version [9.3.6.x](/power-apps/maker/portals/versions/version-9.3.6.x), makers can mark **SameSite** mode as **Strict** for all portal cookies where applicable.  

With this change, we're adding a new website setting to control the **SameSite** mode for all cookies, configurable to the level of specific cookies.

| Site setting name | Scope | Possible value |
| - | - | - |
| HTTP/SameSite/Default | Global, for all cookies. | None <br /> Lax <br /> Strict |
| HTTP/SameSite/{CookieName} | Specific cookie. | None <br /> Lax <br /> Strict |

The default value for all existing and newly provisioned websites is **None**.

To learn how to configure site settings for websites, go to [Configure site settings for portals](/power-apps/maker/portals/configure/configure-site-settings).

## Tracking for webpage, and web file

Starting with portals version [9.3.4.x](/power-apps/maker/portals/versions/version-9.3.4.x), the following functionality has been retired:

- [Webpage tracking](/power-apps/maker/portals/admin/portal-checker-performance#webpage-tracking-enabled)
- [Web file tracking](/power-apps/maker/portals/admin/portal-checker-performance#web-file-tracking-enabled)

### See also

[Important changes (deprecations) coming in Power Apps, Power Automate, and customer engagement apps](/power-platform/important-changes-coming)
