---
layout: post
title:  "Spoofing MS Office comments"
date:   2023-02-06 18:44:17 +0200
author: PfiatDe
excerpt_separator: <!--more-->
---

# Spoofing comments in MS Office

## TL;DR;

MS Office does not verify the integrity of the comment section. This allows an attacker to spoof comments or the author in the same tenant / AD or even crosstenant.
<!--more-->


## Preamble
Last year, there was an interesting article on medium.

[https://mearegtu.medium.com/insecure-comments-73399193f804](https://mearegtu.medium.com/insecure-comments-73399193f804)

The post describes, how to spoof comments by intercepting the POST request to the O365 API. As this was quite interesting I wanted to have a closer look at this.

Microsoft has a "huge" Warning for this in the documentation.
[https://support.microsoft.com/en-us/office/insert-or-delete-a-comment-8d3f868a-867e-4df2-8c68-bf96671641e2](https://support.microsoft.com/en-us/office/insert-or-delete-a-comment-8d3f868a-867e-4df2-8c68-bf96671641e2)

![MS Documentation](/assets/media/Spoof_Office/MS_Doku.png){:width="100%"}
*Documentation by Microsoft*

```Note: Keep in mind that it's possible for others to edit your comments. Comments in an Office document are stored in the file, so anyone with edit access to your file can edit your comment.```

However as also stated in the other blogpost, this does not direct implicate that this will also work completly without target user interaction.
If you think about it, it totally makes sense, what is happening, but I did not expect it to be like that and I guess this is an awareness topic, as I would expect most of the O365 users are completly unaware of this possibility.
 

## Action
Lets have a look what is happening on a file based approach.


### Create a Document & Analyse

We just create an office document. For the example a `.pptx` will be used, as the file formats differ a little bit and the `.pptx` is quit easy.
![Initial document](/assets/media/Spoof_Office/InitDocument.png){:width="100%"}
*Initial document*

Remember that the new office files are just zip compressed, so we can rename the file or open it with 7-zip directly.
Under the `Presentation.pptx\ppt\` path we find a folder named `comments` and an `authors.xml`.

![Initial document](/assets/media/Spoof_Office/7zip.png){:width="100%"}
*File structur*

If we look at the `authors.xml` we see an `author id` and an `userID`. 

![Initial document](/assets/media/Spoof_Office/Attack_2.png){:width="100%"}
*Content author.xml*

The author id is just a random hash, used to make the connection to the comments, what we will see in a second.
`userID` is the e-mail and the objectID of an Azure user.
So we need to get the objectID somewhere. If we have an email and the tenant does allow to use Teams we can check it by the search function.

### Using Teams to get the objectID
We can use the external search feature of MS Teams to get the objectID, if the tenant allows external communication.

![Initial document](/assets/media/Spoof_Office/Attack_3.png){:width="100%"}
*External Search*

The search is quering the following API:
`https://teams.microsoft.com/api/mt/part/emea-03/beta/users/searchV2?includeDLs=true&includeBots=true&enableGuest=true&source=allTrue&skypeTeamsInfo=true`

So we can just edit and resend the request with other data to get our neccessary responses. Note: This is only necessary, if you want the objectID from the same tenant, otherwise you can just lookup the original request.

Lets query for the CFO of our target.

![Initial document](/assets/media/Spoof_Office/Attack_4.png){:width="100%"}
*Query the Teams Endpoint directly*

In the reply we can see the objectID of the user. This might not be the only way to get this information.

### Tamper the document

With the gathered information, we can add another author.
![Initial document](/assets/media/Spoof_Office/Attack_5.png){:width="100%"}
*Add a new author with the collected data*

The `author id` can get incremented, just avoid collisions.

Next step is to relink our comment to the new author by editing the comment file. We just change the `author id` to our new value.

![Initial document](/assets/media/Spoof_Office/Attack_6.png){:width="100%"}
*Relink the comment to the new author*

Save and update the (zip-)file and we are done.

### Open the file

If we open the file, we can clearly see our spoofed comment as approval. 

![Initial document](/assets/media/Spoof_Office/Attack_7.png){:width="100%"}
*Initial document*

As office trusts itself and the data is valid, it will even show profile pictures and Teams status for the spoofed users, the same way as for other users in the tenant.

## Conclusion

A really simple way to spoof some comments. You can directly do this via intercepting the POST request as stated in the origin Blogpost, but generating the file offline, might bring less indicators of tampering.


## IOCs & Mitigation

There are no real mitigation, beside signing the documents. But even signing, will just stop attackers from editing existing documents. Attackers can simply just create a new unsigned document and do the spoofing there.

The best chance is to build some awareness on the user side and generally not to trust comments in Office documents.