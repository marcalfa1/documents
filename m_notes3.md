okay
okay well let me share my screen again so yeah then you have to just search for
GCP landing zone and a form will be populated and this form you
just have to open.
And we have to update the requested details. I'll add your
name.
and then here in watch list I can put my name and Manoha's name
yeah and then because mnemonic in the other chat Manoha confirmed so it is easy one so we'll just
search for easy one second thing is idip functional group name so how to get this name so basically
there is a url um i did okay let me try to copy from that yes i did that bny.net or i don't know
if it should take you to idip too okay i'll just i just uh search that in the other one
I'll show you how it shows.
So once we search the mnemonic in here,
it will show this particular mnemonic is part of which neighborhood.
So for the platform, so that same platform number we have to fill in.
And this remains the same for GCT and Azure projects.
We have to follow that process to ensure like we are creating in the right platform.
Okay, let it load.
So it is mapped to CHP1.
Once it is loaded, I will show you again.
So for now, we can search CHP1.
And then we can select this.
Then swim lane, because Manohar asked for dev tenant, so it means lab.
So we'll select lab.
Same way, like going forward, they want to test in non-prod, pre-prod, or prod.
We have to select the swim lanes accordingly.
Okay?
Okay.
So for now we can do lab and we can leave this as it is for now.
We don't have to select anything.
Then in the landing zone suffix, actually we have to append something.
So there are two things.
One top folder is created.
Okay.
It's loaded now.
So if you see neighborhood is CHP1.
So for Eliza, easy one, this one is CHP1.
So just copy this one.
Okay, so usually there are two things for the GCP console.
One is project and one is folder.
So whatever we are giving here, it will give folder level name.
So usually we'll give whatever the mnemonic is there, same we'll copy here.
And project also, we can have something like related to mnemonic.
If there is one-on-one mapping, for example, there is one folder
where we just need to create only one project.
But since EasyOne is a shared ELISA platform,
which is growing,
so there could be different sort of projects.
So we cannot keep EasyOne as the project name also
because we need to have multiple other projects
under the EasyOne umbrella.
So for now, because this is for Cloud Cowork,
I'll just mention Cowork.
Okay.
So that is relevant to projects.
So under the easy one folder, we'll have a project naming non-prod CHP one something and with the suffix core.
So once this is done, I will just order this.
So any reason we didn't pick a VPC or this is going to be a completely new VPC for this?
No, also this particular one, like usually we are not selecting VPCs in case like we are not having a proper on-prem to Azure connectivity or some default setup is required.
Because currently we don't have a private DNS zone setup, how the like endpoints for the different AI services deployed will be connecting.
So all are connecting over the internet.
So basically that's the reason we are not following that VPC path.
So by default it will be attached to whatever VPC is there.
Until NLS we are mentioning explicitly.
Okay, got it.
So we have this request and I'll go and see in the service now.
So, there is this portal where we can go ahead and search for the request.
So, basically for all the Azure requests, it will go for Manohar's approval or
whosoever is the requester, their manager's approval.
So, if you are requesting, it will go to Manohar.
Then second landing zone automation team, that is Tomo and Goram,
they have to do the second approval.
Then after the processing of the initial checks, it will create an SC task that will be closed by someone from the cloud operations team.
Either it's me, Praveen, Lalit, any of us.
And once that is closed, it will be like apply will be initiated on the background.
So that's the flow on the Azure side.
But in the GCP, the flow is it will directly create a SC task.
I'll just see if nothing new changes are there.
So it will directly go to the SC task.
And then once we close the SC task,
it will create the workspace
and it will proceed with the project deployment,
folder and project deployment.
Okay.
So I'll just see, search this one here.
Okay.
It shows up now.
So if you see here in the activities, you can see what sort of approval it's waiting
on. So it is waiting for approval for public cloud support. So I'm part of it, Jay and
all the other folks are part of it. So here is the approval one. If we just click here,
and approve
okay approve it's approved now the status is changed and also we can go to the
data form to see if it has started the workspace creation.
One second.
If you don't mind, can you paste those, I guess, those URLs as well on the chat?
Sure, definitely.
Yeah.
Yeah, yeah.
Thank you.
Okay, I think it is, I'll just share another screen.
It's taking some time to load here.
So what's triggering the Terraform workflow here?
Is there something, I guess, in GitLab that's tied into service now and that's triggering this?
Yes, yes, that's right.
So basically, we have, like in GitLab, we have different modules for landing zone build for Azure and GCP.
That has definition of all the underlying resources that needs to be created either in Azure or GCP.
So that code is in GitLab.
And all of that is put behind Storefront.
And on front of Storefront, there is ServiceNow.
So once we request, send a request in service now, it will call the storefront API and behind the scene, a storefront will call Terraform.
And there a workspace will be created and then plan apply action.
So that are the stages, how this complete workflow works.
Okay.
Okay.
So now there are two, Terraform is there, right?
So now if you see, there are different sort of organizations here.
So, like, we usually work on public cloud PT.
That is for prod tenants.
So, any of the non-prod, pre-prod, and prod projects will be created here.
And anything in the lab will be created under public cloud dev PD.
Okay.
And as we speak, this particular workspace is created.
This is StoredFront, EasyOne, Lab, EasyOne, PC, Google.
So, let's see this one.
This is for the project we just requested.
And
reference to one declared input variable.
Probably
secret got expired or some provider issue
seems like. Okay.
Let me see. Who can check this?
from engineer
it
Let me see the access on this workspace.
Okay, so this is a group where all public cloud engineering folks are there.
So I'll just give access to that.
So public cloud engineering is able to view this workspace.
And then let me check with Gaurav from Cloud Landing Zone Automation Team.
Just give me a second.
I've also added you in the chat.
Hi.
E aí
Okay.
And whenever we are providing someone the details for the errors, we also have to provide
the RITM number
so they are able to see
where exactly it's stuck.
Okay.
Okay.
And
Okay.
So I've added you
in the chat
and I've tagged Gaurav and Yon to investigate the issue.
Also, I'll just share you from where we can open
the storefront URL to see that particular API.
Just one second.
So once you search for the request,
this will be created a request ID in the storefront.
And once you click for the details,
it will navigate to this particular page.
Then you just have to give your LDEF credentials,
the one you use for Windows login.
And then...
So, yeah, and once the landing zone, like we have to work on the fix with the Gaurav and
others, and once the landing zone is ready, we have to work on the IAM part, like how the
service account and AD groups will be created for this particular landing zone, and also
on the enablement of Cloud APIs, what all different sort of models they require, like
like Gemini, Claude, and we have to enable them as well.
Okay.
Yeah.
Good night.
Thank you.
Okay.
So this is the storefront UI,
and it will also show the workspace name,
and then once you click on it, you can see the error details, like why it is failed.
And also if you don't have workspace name handy, that you don't know what workspace was created
or something like that, you can directly click from here and it will give you that particular
Terraform workspace link and then you can log in and look for the details. So even though it failed,
so it still created the LinkedIn page, right? The page for? Yeah, the workspace will be created. It
failed at the planning level itself. I think so. There are some outdated provider issue or something,
But I'm not very sure on the GCP side.
This one is still new and evolving, the landing zone product.
So, yeah, probably Gaurav or team can review this and suggest like what changes are required.
And based on that, we can make the changes or they can make the changes to the Terraform module library code.
And then we can plan and apply this workspace.
But once it is fixed, it will show, just it created the workspace.
And now I'll just show you.
Once this is fixed, it will show what all resources project folder will be created as part of this plan.
So, yeah, let's wait for them to provide an update on the issue.
And once they get back, maybe we can connect again for the next steps.
And once we have project ready, we have to work with Manohar on the authentication part,
like what service account, AD group, and then what APIs are required for enablement of this one.
So, yeah.
Okay.
No problem.
So, yeah, definitely.
Yeah, ping me, I guess, if you want to jump back on the call, just let me know.
Sure, definitely.
Yeah.
Also, you please review this process and let me know in case you have any questions.
No problem.
And thank you, and thank you for your help and showing me this.
Anytime, yeah.
Thank you so much.
Have a nice day.
Okay, bye-bye.
Bye.
Bye.
Bye.
