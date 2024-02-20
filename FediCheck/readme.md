![fedicheck](https://github.com/jazmichaelking/151/assets/3419832/532cd44c-d0b2-4a03-96c7-f919812067c9)

# IFTAS FediCheck
*Denylist Management by IFTAS*

 - Easily compare your existing blocks with a trusted list
 - Automate addition and removal of domains to your Mastodon server
 - Using the IFTAS CARIAD database, quickly defederate from "the worst of the worst"
 - Does not change the blocks you already have

## Overview
FediCheck is a Web service from <A href="https://about.iftas.org/">IFTAS</a> that allows service providers to review and subscribe to the IFTAS <a href="https://github.com/iftas-org/resources/tree/main/CARIAD">CARIAD database</a> for automated updates. Future versions will accommodate alternative sources such as a trusted server, community of servers, a database, or flat file.

The CARIAD version of FediCheck is intended for new administrators with few or no existing blocks in place seeking a minimum necessary denylist. Existing services that have denylists in place may benefit from CARIAD to augment their existing federation policy by subscribing to only the new domains that appear in the CARIAD database from time to time.

In short, CARIAD is a curated list of domains that are recommended for blocking or limiting by aggregating the actions taken by many of the largest ActivityPub services, combined with the IFTAS [DNI list](https://github.com/iftas-org/resources/tree/main/DNI).

<blockquote><img src="https://github.com/jazmichaelking/151/assets/3419832/5e89260e-7280-4f99-913b-a7dc73fafdd4" /></blockquote>

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

We recommend service administrators create a dedicated IFTAS role account with only the minimum necessary permissions, and use that account to sign in to FediCheck

If creating a new account, consider removing from search, marking as unattended; and enabling multi-factor authentication. 

Multiple accounts are supported, but only one account (of your choosing) will be used for any API push activity. 

While IFTAS employs standard security practices, it is not advised to use an account with full administrative permissions for this (or any other) third-party application.

## User Guide

<table border="0" style="border:0;">
<tr>
<td width="60%" valign="top">
<h3>Create Account</h3>
<ol>
<li>Visit https://cariad.fedicheck.iftas.org</li>
<li>Enter the domain you want to manage</li>
<li>Select "Remember this server" if you want to manage one domain</li>
<li>Click "Login"</li>
</ol>
<p>FediCheck will request the necessary permissions via OAuth. Once accepted, your FediCheck account will be created.</p>
<p>FediCheck will then read the existing domain blocks on the remote server and store those to the FediCheck account, to ensure the FediCheck service does not overwrite the existing blocks.</p>
</td>
<td width="40%" valign="top">
<blockquote><img src="https://github.com/jazmichaelking/151/assets/3419832/ce5347c6-650c-4c04-a886-01ddb4ccb647" /></blockquote>
</td>
</tr>
<tr>
<td width="60%" valign="top">
<h3>Review Denylist</h3>
<ol>
<li>Select each tab to review the various lists by threshold. Higher thresholds of agreement will block fewer domains.</li>
<li>List view will show a selection of public comments from source domains, as well as <a href="https://github.com/iftas-org/resources/tree/main/LABELS">IFTAS labels</a> if IFTAS has labelled the domain e.g. <code>IFTAS:Network-Service-Abuse</code>. Public comments are never copied or transmitted to your server.</li>
<li>At any time, download the currently viewed list to obtain a CSV file for manual import.</li>
<li>Select a denylist from the dropdown and click "Save" to review which domains would be added or removed if that version were to be subscribed. FediCheck will never remove domains already managed by the server administrator.</li>
</ol>
</td>
<td width="40%" valign="top">
<blockquote><img src="https://github.com/jazmichaelking/151/assets/3419832/bbd0718c-2f69-4871-83a0-f6b582098dca" /></blockquote>
</td>
</tr>
<tr>
<td width="60%" valign="top">
<h3>Subscribe to Denylist</h3>
<ol>
<li>Enable Subscription to allow automated updates. This can be disabled at any time, and will automatically disable if a new version of the list is selected.</li>
<li>Once enabled, the new blocks are added to the Mastodon server, with the private comment <code>IFTAS FediCheck updated yyyy-mm-dd hh:mm:ss UTC</code> - this will be visible in your Mastodon dashboard.</li>
<li>FediCheck does not add public comments to your server.</li>
</ol>
<p>FediCheck monitors the CARIAD database for domains being added, modified (e.g. from Suspend to Silence) or removed, those changes are then automatically reflected on your server. The database is monitored throughout the day, and changes are queued for delivery to each subscribed server. In general, you should be no more than 20 minutes behind.</p>
</td>
<td width="40%" valign="top">
<blockquote><img src="https://github.com/jazmichaelking/151/assets/3419832/b004eff2-e008-4cf4-ab79-0d8bb4a95081" /></blockquote>
</td>
</tr>
<tr>
<td width="60%" valign="top">
<h3>Lock Domains</h3>
<p>You can lock any domain suggested by FediCheck. This transfers management of that domain from FediCheck to you, and FediCheck will no longer make changes to that domain.</p>
<p>This may include seeing a managed domain that FediCheck would remove, in which case you can unblock it and add it your Locked Domains</p>
</td>
<td width="40%" valign="top">
<blockquote><img src="https://github.com/jazmichaelking/151/assets/3419832/b0919fad-ee5d-4059-b105-a4e96bcfed54" /></blockquote>
<blockquote><img src="https://github.com/jazmichaelking/151/assets/3419832/3bb9b7ae-08da-4925-8c91-4eefe95186fb)" /></blockquote>

</td>
</tr>
<tr>
<td width="60%" valign="top">
<h3>Manage Domains</h3>
<p>You can allow FediCheck to manage any domain you added to your server. This transfers management of that domain from you to FediCheck.</p>
</td>
<td width="40%" valign="top">
<blockquote><img src="https://github.com/jazmichaelking/151/assets/3419832/ed84f71e-edeb-45e4-97f5-b94a0cc1fbc7" />

</td>
</tr>
</table>

### Account Management
At any time, you can specify which list is subscribed, or disable updates. 

Once a different version has been selected, you will be presented with the number of domains that will be added or removed based on the selection, and the service will cease automatically updating. You must re-enable the updates by clicking “Enable Subscription”. 


### Data Removal

Remove all Blocks - Removes all FediCheck-managed entries from your server server: this removes only the listings placed in the server by FediCheck, exncluding “Locked Domains”.

Purge All Data and Log Out - Revokes your account credentials, your server token, and purges all your data stored on FediCheck. Note: This does **not** remove any domain blocks - you may wish to run the Remove All Blocks action first.

## Help and Feedback
 - Email: fedicheck-support@iftas.org
 - Chat: https://matrix.to/#/#wg-tooling:matrix.iftas.org
 - (For CARIAD see https://github.com/iftas-org/resources/tree/main/CARIAD)

## Roadmap

### Relationship Checking
The FediCheck CARIAD version is intended for use by new administrators, and it is not anticipated that relationship checks are required. Future versions will enable this functionality, which will require additional API permissions.

### Multi-platform
FediCheck should be able to operate denylists for any of the major platforms that expose domain blocks via API. 

### IP Rules and Email Domains
Provide additional opt-in features to include trusted sources for malicious email domains and toxic IP addresses and ranges.

### Multi-use
While the initial version is for use by CARIAD, the intent is to allow FediCheck to operate using any of:

 - An upstream trusted server or group of servers (“I want to block what that server/group of servers blocks”)
 - A public list or collection of lists (“I want to sync with the list(s) at denylist.example/list.csv”)
 - A third-party data service
 - Any mixture of the above

Subject to interest, FediCheck could be made available for commonly used services such as broadly-adopted lists, Fediseer, The Bad Space, or a sentinel server.

### Hosted options
IFTAS may operate a multi-tenant service to allow users to specify the server or servers they want to subscribe to.

### Community / Ring of Trust
IFTAS could host a service for a given community that wishes to share their collective block activities, by allowing a specific group of servers to use a common service.

### Account Permissions
We expect Mastodon 4.3 to allow FediCheck to request finer-grained read scopes, at which point we will request ```read:me```

