![fedicheck](https://github.com/iftas-org/resources/assets/3419832/554fdb76-12b8-44f3-9e3f-703ed3daddc9)

# IFTAS FediCheck
*Denylist Management by IFTAS*

 - Easily compare your existing blocks with a third-party list or lists
 - Automate addition and removal of domains to your server
 - Does not change the blocks you already have

FediCheck is currently in private beta. To join, [please apply for beta access](https://cryptpad.fr/form/#/2/form/view/E2yxXhoruIVzj4EGGdDIKintwBVFYsq9Srl4GhYeXwU/).

## Overview

FediCheck is a Web service from <A href="https://about.iftas.org/">IFTAS</a> that allows service providers to review and subscribe to external sources such as the IFTAS <a href="https://github.com/iftas-org/resources/tree/main/CARIAD">CARIAD database</a> for automated updates. 

Future versions will accommodate alternative sources such as a trusted server, community of servers, a database, or flat files.

The CARIAD version of FediCheck is a pilot example of FediCheck, intended for new Mastodon administrators with few or no existing blocks in place seeking a minimum necessary denylist. CARIAD is a curated list of domains that are recommended for blocking or limiting by aggregating the actions taken by many of the largest ActivityPub services, combined with the IFTAS [DNI list](https://github.com/iftas-org/resources/tree/main/DNI).

<blockquote><img src="https://github.com/iftas-org/resources/assets/3419832/57315a9e-48d4-4320-8fcf-561de701273d" /></blockquote>

### Example Actions

 - A malicious or abusive network actor is seen to be blocked by a majority of sources, your server will automatically act on that information and block the same domain.
 - During spam waves, FediCheck will monitor if a majority of large servers ```Limit``` a domain. FediCheck can ```Limit``` it for you based on your chosen threshold, and then undo that action once spam subsides.
 - IFTAS observes a source of illegal content and adds it to the DNI list. FediCheck can automatically block that domain's content from your server.

## Permissions

FediCheck requires a Mastodon account with the relevant permissions. Mastodon API Version 4.1 or above is supported, this document will describe Mastodon implementation. Future versions may support additional platforms and versions.

 - ```read``` - to validate the access token (pending [this PR](https://github.com/mastodon/mastodon/pull/27142))
 - ```read:accounts``` - to confirm the account has the necessary permissions
 - ```admin:read:domain_blocks``` - to see what blocks are already in place
 - ```admin:write:domain_blocks``` - to create and update blocks from FediCheck

We recommend service administrators create a dedicated IFTAS role account with only the minimum necessary permissions, and use that account to sign in to FediCheck.

If creating a new account, consider removing from search, marking as unattended; and enabling multi-factor authentication. 

Multiple accounts are supported, but only one account (of your choosing) will be used for writing blocks to your server. 

While IFTAS employs standard security practices, it is not advised to use an account with full administrative permissions for this (or any other) third-party application.

## User Guide

<table border="0" style="border:0;">
<tr>
<td width="60%" valign="top">
<h3>Create Account</h3>
<ol>
<li>Enter the domain you want to manage</li>
<li>Select "Remember this server" if you want to manage one domain</li>
<li>Click "Login"</li>
</ol>
<p>FediCheck will request the necessary permissions via OAuth. Once accepted, your FediCheck account will be created.</p>
<p>FediCheck will then read the existing domain blocks on your server and store those to the FediCheck account, to ensure the FediCheck service does not overwrite your existing blocks.</p>
</td>
<td width="40%" valign="top">
<blockquote><img src="https://github.com/iftas-org/resources/assets/3419832/e2b1e72f-9628-4b76-af0d-36144655c1ac" /></blockquote>
</td>
</tr>
<tr>
<td width="60%" valign="top">
<h3>Review Denylists</h3>
<ol>
<li>Select each tab to review the various lists by threshold. Higher thresholds of agreement will block fewer domains.</li>
<li>List view will show a selection of comments from sources and/or [IFTAS labels](https://github.com/iftas-org/resources/tree/main/LABELS). Comments and labels are never copied or transmitted to your server.</li>
<li>Select any visible denylist using the "Subscribe to this list" button. This will disable any current automated updates.</li>
<li>Review which domains will be added or removed if that version were to be subscribed. (FediCheck will never remove domains already managed by you.)</li>
</ol>
</td>
<td width="40%" valign="top">
<blockquote><img src="https://github.com/iftas-org/resources/assets/3419832/d72562b5-e7bc-4d49-92ce-db8408d2838a" /></blockquote>
</td>
</tr>
<tr>
<td width="60%" valign="top">
<h3>Subscribe to Denylist</h3>
<ol>
<li>Enable Subscription to allow automated updates. This can be disabled at any time. Please note: Subscription is disabled if a new version of the list is selected.</li>
<li>Once enabled, the new blocks are added to the Mastodon server, with the private comment <code>IFTAS FediCheck updated yyyy-mm-dd hh:mm:ss UTC</code> - this will be visible in your Mastodon dashboard.</li>
<li>FediCheck does not add public comments to your server.</li>
</ol>
<p>FediCheck monitors the CARIAD database for domains being added, modified (e.g. from Suspend to Silence) or removed. Those changes are then automatically reflected on your server. In general, you should be no more than 20 minutes behind.</p>
</td>
<td width="40%" valign="top">
<blockquote><img src="https://github.com/iftas-org/resources/assets/3419832/2edbef7a-334a-4b6d-9c27-be1344c00bec" /></blockquote>
</td>
</tr>
<tr>
<td width="60%" valign="top">
<h3>Manage and Unmanage Domains</h3>
<p>You can Unmanage any domain FediCheck adds to your server, transferring control to you.</p>
</td>
<td width="40%" valign="top">
<blockquote><img src="https://github.com/iftas-org/resources/assets/3419832/71eb2544-5c9c-42c9-bf9c-7157f0550940" /></blockquote>
</td>
</tr>
</table>

### Account Management
At any time, you can specify which list is subscribed, or disable updates. 

Once a different version has been selected, you will be presented with the number of domains that will be added or removed based on the selection, and the service will cease automatically updating. You must re-enable the updates by clicking “Enable Subscription”. 


### Reset Options

Remove all Blocks - Removes all FediCheck-managed entries from your server. This removes the listings placed in the server by FediCheck and currently managed by FediCheck.

Purge All Data and Log Out - Revokes your account credentials, your server token, and purges all your data stored on FediCheck. Note: This does **not** remove any domain blocks - you may wish to run the Remove All Blocks action first.

## Help and Feedback
 - Email: fedicheck-support@iftas.org
 - Chat: https://matrix.to/#/#wg-tooling:matrix.iftas.org
 - (For CARIAD see https://github.com/iftas-org/resources/tree/main/CARIAD)

## Roadmap

### Relationship Checking
The FediCheck CARIAD version is intended for use by new administrators, and relationship checks are not enabled at this time. Future versions will enable this functionality, which will require additional API permissions.

### Multi-platform
FediCheck should be able to operate denylists for any of the major platforms that expose domain blocks via API. 

### IP Rules and Email Domains
Provide additional opt-in features to include trusted sources for malicious email domains and toxic IP addresses and ranges.

### Multi-use
While the initial version is for use by CARIAD, the intent is to allow FediCheck to operate using any of:

 - An upstream trusted server or group of servers (“I want to block what that server/group of servers blocks”),
 - A public list or collection of lists (“I want to sync with the list(s) at denylist.example/list.csv”),
 - A "shopping list" of domains by [label](https://github.com/iftas-org/resources/tree/main/LABELS),
 - A third-party data service,
 - Any mixture of the above.

Subject to interest, FediCheck could be made available for commonly used services such as broadly-adopted lists, Fediseer, The Bad Space, or a sentinel server.

### Hosted options
IFTAS may operate a multi-tenant service to allow users to specify the server or servers they want to subscribe to.

### Community / Ring of Trust
IFTAS could host a service for a given community that wishes to share their collective block activities, by allowing a specific group of servers to use a common service.

### Account Permissions
We expect Mastodon 4.3 to allow FediCheck to request finer-grained read scopes, at which point we will request ```read:me```

