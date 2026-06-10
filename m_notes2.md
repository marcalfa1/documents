No, if what we want to do for additional APIs, right, is for the ops to just go and keep
adding it to the project configuration, sort of, you know, in the console, right?
So that's why I think Marsing had a few options of how we can potentially approach this.
Okay.
Basically, the landings provisioning, the landings and provisioning for the GCP is a
bit different from what I see from Azure because on Azure you have basically the variables and
settings, you had the version control and you were pointing to a specific repo and specific branch and
you could basically change it. For GCP landing zone which is being ordered by the storefront,
the provisioning is triggered by storefront API and as you see here basically there is no version
control and from what storefront team told me basically they are pushing the zip package somehow
to this terraform yeah and this this part of the the mechanics you know it's something that we can
look to change if we decide that vcs integration is something that we want to do right this is kind
of done like native sort of natively in storefront which we didn't do for the agile landing zone
right so we don't really i mean we don't really have you know we cannot use that the workspace
as kind of a ui to upgrade things anymore right but also the problem right now is that uh you know
the the list of projects for all of the landing zones that gets created is now in the in that
in in the code and in a package so only way to update that right is by upgrading the you know
making a new release of the you know landing zone which is really cumbersome right so and also in
gcp we haven't thought about having a landing zone configuration that is outside of this you know the
landing on module right like in the azure we tend to use those zone configuration yaml file
right to customize landing zone we don't have that in gcp right so this is really about just
you know so we can do something about the initial set of you know you know apis maybe we should
you know externalize this right rather than hard coding this into the roundings or module we can
do that in godox we can do as a zone config right and you know we can do it in different ways but we
need to decide what to do with additional projects right so we're going to do so tomorrow two use
cases right one is the static list of apis that every landing zone needs it those are like basic
basic like google apis that everyone needs access to but that's one correct the other one is for
project basis for example mainstream like mainframe api modernization needs address validation api
only that project alone will have access to that project right that google api access or or if
somebody wants like you know the vortex api we enable the vortex api for eliza whatnot like the
project which like you know we need to work for co-work right that means are we trying to externalize
both use cases tomo like so those so those two are different right okay well even though you know
upgrading a landing zone updating the list can solve the second you know problem right but i
don't know if that's what we want to do so enabling apis by default some subset of apis by default in
landing them to me is more of an optimization right we should just figure out where we should
configure right projects fine i think so i think so how you guys did it for using the godox whatever
is that you can put all those things right so that solves the first problem right if how do we
efficiently you know properly manage the default set of you know the apis right i don't think
hard coding into the code is the right way to do it and we can move it out right but still we still
need to be able to do ad hoc right we definitely need our hook yes right so the question so i think
that's why we have these options right so what are the options is somebody sharing okay okay
right i think masi is sharing okay yeah yeah i'm sharing so basically the first option is manual so
basically we can ask ops to enable the apis which i don't think we want to do
second that's a storefront driven it's saying that's the store hold on
that's here really storefront driven right really one option is really console right access yes
yes so that's that's what they did for for the gitbot so uh the ops were enabling some
apis for me which i needed and second option yeah so this is basically storefront driven so let's
say we will be provisioning the GKE using the storefront so we can instruct the storefront.
So let's say if you are provisioning the GKE or Google bucket, first you need to enable these
APIs and then you can provision it. So it's storefront driven, but this does not
address the issue that we will be developing the products by the client.
That's an interesting one. If some deployment of some resources in the landing zone requires some
APIs to be enabled, what do we do about that? And that's probably a third use case. That's an
interesting one. Yeah, second use case is here that basically we can pivot a bit into the Azure,
so we can maintain some kind of the YAML configuration,
which the landing zone will be reading.
But here we had the problem that the workspace is zip package,
so it's not connected to the code.
So we cannot easily rerun it after post-landing zone provisioning.
So we can do it during the landing zone provisioning,
if you know what API needs to be enabled.
That's not necessarily true.
if we have access to the workspace right we can refresh it right plan and apply it yeah you will
need to go to the workspace then you will need to connect it to the version control well we don't
necessarily have to connect it to the version control if the landing zone code is able to read
from the zone is he talking about something like zone can become yes if it's like zone
config what we can do is that as a part of this workspace creation we can add a variable right
that points to a particular zone config file right that's fine that's it i think that's the easiest
yeah but we cannot rerun the workflow the workspace uh what do you mean we can't rerun
well because it's not connected to any code right you push the code as a part of the api request no
no no no no that food has to right be able to read some config based on the location
that's no no no i'm talking about a terraform i'm talking about a terraform code
so right now the workspace is not connected to any terraform code so now if you go ahead
no no it is connected under under the cover it's it loads the bundled terraform code it's just not
using a vcs you know integration so if you just go ahead and click like rerun or run again it's
should plan right now again yeah yes okay all right and where the code is
right now like stored as a part of the workspace definition
yeah this this is sort of the native you know storefront right thing right so underneath the
cover somehow store you know storefront has wired in such a way that they will go to
to Artifactory and actually load our, you know, unpack, you know,
okay, so we rerunning from the storefront not from the
Terraform?
Well, storefront creates the Terraform workspace.
Yeah, but now it's created already, right? So when it is
created already, if I need to rerun it, it will trigger the
rerun. Right. Is it gonna be storefront?
No, we can do that from here. As long as we have the right
access, we can do it from here.
So we can now go to run and just trigger another run.
Right.
And it will run the same version of the code.
There is a way to.
Are you sure about that?
Yeah.
Okay.
I've never seen Terraform Enterprise work like this.
So that's why I'm asking.
Yeah.
So this is not a sort of a native Terraform, you know, you know, so what we do for Azure
is that even though we have this on our side our service is going to create our workspace that do
that vcs integration so that we have full control of that that you know the workspace
natively doesn't let you do that so tomo today if you create any landing going in azure
and the next time if they want to run it they have to go through that workspace and read on it
They never use Storefront to rerun it, correct?
No, because what we do is that even though Storefront kind of is creating this workspace,
behind the scene, we create our own workspace and connect to our code using VCS integration.
My Storefront team doesn't like that we do that, right?
But we think that that gives our engineer slightly and helps better user experience, right?
I think this gives the flexibility.
Yeah.
I think that makes sense.
I think this is the easiest option, maybe,
what of three, not four.
Right.
But for now, when the storefront integration was done for GCP,
storefront team did this.
Right?
So we don't have that kind of customization that we did for Azure
to allow us to use VCS integration and use branch changes
to you know you know upgrade the module and things like that it's very very you know it's tricky to
do something like that with the you know storefront it can be done it can you know we can do upgrade
and they do support you know a separate ui to do upgrade but it's not a you know it's not a terraform
ui it's going to be a storefront ui right ops is you know generally ops you know team is familiar
with that process but we are not right but just going back to the zone config part as long as
our code is aware of the zone config and able to read it from the variable we can create these
storefront workspaces and make sure that those are set in the variable right so if the zone config
changes all we have to do is we plan and apply this workspace yeah i think that's fine
but right so if we are going to do a zone config then we have to figure out where that goes
how that gets created as a part of the landing zone provision you know provisioning process
and we have to make sure that our landing zone code changes right and also we have to agree on
the format of that you know zone config you know zone config is not just for a project
right it's for the folder right so we have to come up with that the right structure right
to do you know to you know to start with so there's going to be some work to do
and if you know down the road if the team decides that this storefront you know that the ui is you
know way of you know doing using terraform is not right for us then you know uh i think we need to
do something more similar to Azure.
It's done with a PC yesterday.
Garth's process actually creates
the workspace for us behind the scene.
And static list extending,
I don't know if we want to do this on a per.
So I'm curious, is there any harm in
enabling same APIs on all projects or are there any downsides to that?
No, I think the anything common project makes sense to enable it on those things
because when you talk about APIs, we don't know kind of like thresholds and like
how frequently we don't need all these projects to be enabled on everything.
No, but is there any downside that the easiest solution is right? I think that's a number three,
update the central list and then just plan and apply right i just don't know eventually eventually
we want to customize this really for per project or landing i mean what worst case is we can create
a separate product which can give you a set of right that's the another option right yeah that's
we create an additional but yeah possible yeah project you know the but is it really worth
creating a separate product from on koro api adding this for what is that you know
If the use case and the users basically are actively
requesting it all the time.
This is definitely a repeated use case, Gato, right?
Customized.
Then maybe, maybe.
Right, but the thing is we can create a store
from product, right, where you can order a API
to be enabled in a particular project.
We can do that, right?
The question becomes though, we are not capturing
the requirement in some configuration file, right?
It's a one-off thing, right?
We're just replacing the console manual change
with automation.
No, there's a far APA specific controls
that we have to not really that, right Tomo?
It's API to API.
For example, if you're enabling vertex API
is different from address validation API
is different from something else.
Because the API threshold is different.
If you need to buy anything around it,
if you're just enabling, it's not going to help them.
tomorrow if you want to, let's say,
add additional services around that API flavor, right?
Well, but the thing is that I think
this discussion is simply about enabling APIs, right?
Whatever that has to happen after that or before that.
Yeah, so just
Right, I don't think we all need that.
Landing zone workspace, YAML,
that's the easiest option, right? Isn't it?
Well, it's not the easiest
because we still have to develop that, right?
Then I leave it to you basically, right?
I don't, as long as we don't like squish all this in one place,
because we need to have a generic list, we need to have a special customizer list.
So the easiest is really, really have a single place, right?
Where everybody shares a single list.
So is that a baseline config or is that a shared list for everyone?
So the question is that, is there any downside to enabling all the APIs for everyone?
No, I don't think so. It depends because if you give people some rules, I mean
it's a there's no downside right because enabling the API doesn't force you to
use it. The problem could be, could arise if we use some kind of a let's say
predefined IAM roles and things like that that give a little bit more
permissions outside of the intended API, right? And then people can use API because it's enabled,
right? But the roles are different from API enablement, right? The enabling of API does
not give you that role by default. No, yeah, I totally get it. But like, let's say we give
somebody a like cluster Kubernetes developer, right? Or something like this. It could give you
permissions to do stuff on GKE, but additionally it can also give you some permissions on some
additional APIs, right? That because when they are not enabled you just cannot use it, but if we
enable everything then you now potentially can use them. That's the only kind of like area.
I think so, I think this will go with the least privilege always.
Yeah, least privilege always better. Yeah, so go with what is needed every project, right?
Timothy? This standard list, right? I understand, but that means that we're going to have to craft
potentially a lot of custom roles, which is not a downside, just additional work.
No, so one is a generic list that you are showing here that every project should contain,
right? And depends on who are requesting new project, right? They're looking for a or two APIs,
part of that, whatever the new implementation, right? Either through YAML or some other like
product which Gauru is going to create if they get access to those APIs. Then obviously the
third one is the one which I think the mass incentive, there is a VPC service control
where saying if these are the load for this for this lieutenant whatever it is.
I think that needs to be enhanced as well. But that's anyway one time.
So this is a list of APIs that are allowed to be used in our organization. So the goal of point
three or the idea behind point three is if we are enabling it that on the to be used in organization
we can also allow it in all projects by default can you show me the list yeah yeah so it's here
allowed gcp service i'm curious keep going now just how big is the list
but what why do we even have the allowed apis and how does it get updated
So this is basically organization policy. So if the API is not on that list, you cannot
even enable it because it's...
Right, I understand. What was the intentions behind that? Like, why would we restrict it
at that BNY, like, work level? And what is the process to get that added?
Yeah, so the process is, you know, you just add it here and you rerun.
Oh, no, no, no. But the thing is somebody has to be approving that, right? I'm not
talking about a mechanical process.
Okay.
Right?
So I think part of the one, if I remember, right, you added Radis and a couple of other
things, right?
I don't know, to be frank, right, what exactly the reasoning behind adding part of the VPC
service control, if it is already enabled through that static list?
Is this a VPC service control?
No, no, it's something different.
It's our policy?
What is this?
Yes, of course.
This is our policy, right?
Yes.
So this is some kind of like check, right?
Checks and balances that we have it in place.
What is this?
Do we have a similar role on the project level?
Why do we need this?
This is different from enabling project with an API.
Right.
So enabling project is just allow you to access it,
but it doesn't really check whether you are allowed to access this or not.
But I think at that point, the org policy will kick in and block it if this list doesn't
contain that API that you're trying to enable at the project level.
So correct.
So basically, if that doesn't exist, so we're going to have all APIs in one place in the
org policy, one per day, one per crowd.
Which is kind of weird.
I'm really curious to know why this policy even exists.
I don't know.
So we were trying to enable for Firebase from project level it got enabled but when we were
trying to create a Firebase project so there is a different console.firebase.oogle.com
it was throwing error that this particular API is not whitelisted in the VPC.
So we face this issue today itself.
Yeah.
This is what this was VPC service control that you faced.
Yes.
Right.
What are we doing with the API at the VPC service control?
Hold on. We have third control.
Where is the VPC?
Can you show me the VPC control where the API has access?
Marcin, can you go to a VPC service control one?
Yeah.
Sometimes we add some policies around the API
vpc service control but i'm not sure if that's always required
so it should be in 100 workspace
i think we're kind of so it's here yeah i think we're drifting away from the
the topic of the conversation yeah maybe yeah yeah but if this is
sure because i think that is a fundamental problem that we need to tackle and this is the the
deployment of the landing zones right right now it's done through the storefront which creates
the workspace in terraform with a zip package and then runs but the question is uh do you
intend to use this workspace later to upgrade the landing zones
we cannot okay so this workspace cannot be used to upgrade the landing zone code
right so we cannot use tfe as a as a way to do this so so if that is not upgrading lending zones
then right so if we feel that right as we start to you know on you know start to have more and
more use case around this if the you know we collectively feel that we should be using
right terraform to actually upgrade rather than using storefront upgrade we can do something
similar to azure right but that requires you know us to you know do some additional work you know on
on the PCS side. The only thing is that Storefront team discourages us from doing that. They always
keep saying that, "Hey, you will see some problem with the stability of the VCS integration."
They always said, "Hey, Terraform or even HashiCorp kind of discourage us from using VCS integration."
Sorry, FASIC Corp discourages.
Yeah, they keep saying that there's some kind of scalability issues that we're going to experience at some point, and we haven't hit that yet.
I don't even know what that scalability issue is because they haven't really articulated that.
I know what it is.
If you remember, it's the limitation of the number of webhooks.
Yeah, webhook, yes.
Webhook limitation, we can address at one point.
Why would there be?
So I think we are three minutes away right now.
So we definitely need access to these APIs.
I don't think it's wise to enable every API to every project, Tomo.
I think let's maintain that list right somewhere, whether it is static or...
Okay, so we have a sort of a central list of APIs that are default,
configured by default, and we want to move that out of the...
at least our code, right? That's one.
Yes, yes.
Two is that then we need to be able to customize
per landing zone, per project,
while additional APIs that need to be configured.
So we'll figure out how to do that.
In some ways, yeah, well, me and Gaurav and Amo
can discuss this and decide what to do.
In the meantime, I think ops needs to do this manually.
Yeah, that's fine.
that's known thing right for cloud co-work that is very simple AP it's what I need from this is
basically it's nothing to cloud co-work it's just a fancy name they have any you know use case where
from cloud co-work they're trying to enable for 100 plus users eventually to the entire like the
our business community which is owned by Swartak's team and they want to do a cloud co-work poc which
they did with the first party mode but it turned out to be very expensive first party in the sense
directly calling the anthropic model, right. Expensive one, they are not that safe, right.
Calling that, I think they're not, so they want to call through Google, right, via Eliza. So,
like cloud cover talk to Eliza, Eliza talks to this, this sub, you know, the existing,
the, you know, the GCP project, right, similar to 14AI, right. So, we're going to create a new
project with this new API enablement and they are all the required roles we enable it
and are there any additional configurations that we need to do beyond like projects
I think it's right now it's APIs it's right now it is for this so for now the current use care
for ELISA is just for this only but eventually this project can be used for any other workload
for ELISA because we want to I'm going to ask them to start moving eventually because they are
on GCP 1.0 that project has a lot of vulnerabilities right yeah but I want to understand what that is
right for example right for now we cannot use vertex ai through tomorrow if they need a GKE
right or any other database this is the project is going to be used for them going forward yeah
okay i think one last thing uh timothy i think we should figure out that file for landing zone
uh yeah we should do yeah i i just don't know what what we need to do from that landing zone
perspective so let's come up with a design so that we can schedule uh some implementation
or testing yeah okay yeah i wanna i wanna just add that there's like a central place where you
can basically define it by the folder and project name apis that's enabled and it actually is a
forepoint on that list that is shared here so basically it's already about the policy
list yes so it's basically enable of apis per you see there's like a oh no but that's for the
i think it's for our foundation projects yeah but we can enable an api we need yeah but i i don't
keep adding here or create like a separate workspace with similar use case but it may not
scale well for 100 plus projects yeah i mean yes it's possible to just keep adding right to you
were saying that we can accommodate the spoke project right configuration here i don't know if
you want to be doing that in the foundation though yeah i think that they need to be separate um
right first of all why foundation maybe google foundation is needed because you see that right
this project list is totally different from the one you know but i think the foundation works
projects would require these api to do what it needs to do yeah yeah right that's all right but
i don't from the change management perspective i don't think that we should be using foundation
works places for you know spoke related things yeah and let's keep it separate i think um
Marcin, I think we agreed those two approaches, right? And for now, until we have this API ready,
we'll continue to use the approach that we were doing it, right? And we have to also look into
that Firebase issue and other things, right? So, Timothy, I know we have the right forum, right,
Timothy? You are making progress on the private service connect, okay? We agreed yesterday,
there's no back and forth that for option b for right whatever the 4b is the right way to go right
can you come back on the email close that because we don't want any disagreement again right we
reviewed with gcp like a couple of weeks ago we reviewed with like the dns guys right option b is
basically having like now they are authorized you know the domain where we register all these
a point in a records and cnames whatnot then you create the private service connect in the shared
vpc okay yeah i'm currently battling the uh the workspace that is not willing to authenticate to
google for some reason yeah i'm working with cloud ops to to fix that okay hopefully today we can
deploy and and it should work but the problem is that this is only for the new gcp the old gcp the
workspace for the vpc service control is completely broken so i don't even know how to how to fix
this with the gcp 1.0 yeah yeah the old one because it's still on terraform 0.12 and then
now it has a bunch of issues with it unable to use the provider version either uses that
yeah eliza is still on the old one so this is the new eliza is going to be on this okay
Okay. And also when you talk to like I know Arun said he's going to work with Steve right
on the DNS domains we want to see that list like all the Google API's list before we make this
change enable this change in dev tenant. Okay. Well yeah but like what what's the list that
we're looking for besides the address validation is there anything else? There is one more API
there is a Firebase, there is all this like the ELISA 1.0, like all the anything, right,
that we're going to ask this, you know, the vertex AI, they should start communicating through the
interconnector instead of going through public internet. ELISA need to talk about this. Okay.
Okay. So everything in ELISA plus Firebase and plus the address. So right now address validation
is one, address validation is not, we test with that. Okay. One thing, so from the forwarding
perspective i know we are digressing but from the dns forwarding perspective right we don't
are we just using the wild card we don't do any forwarding uh we resolve directly oh sorry yeah
we create a records right like that i think that has to be done for every explicit uh url or the
yes so yes okay so we just have to do it for every every well no no not exactly it has to be done
for every uh endpoint in every region yes yes but what about the service what about service we can
wildcard can we work okay all right cool so we we have a fixed set that we have to create and that's
it right per yeah i think we can wild card but i don't know i hope so yeah otherwise we have to
create so many records right every time yeah okay okay cool i think we're making good progress
and martin you had another point that you wanted to discuss
now we have subus kt so we know there's one oh my god yeah okay that's cool okay all right cool
thanks martin if there's anything just ping us in the chat i have a cold schedule for tomorrow
Okay.
You did?
Okay.
Cool.
Yeah.
Hey, Noshiba?
Yes.
Hey, so I want you to start setting up the project, okay?
Noshiba?
Yeah.
Is that fixed today with StorePoint?
Yeah, that is fixed.
Yesterday only we deployed it and it is ready.
Okay.
Ready and just enable it along with Mark, right?
if you need any help take timothy right timothy is working on other foundation thing um timothy
just add mark on song that right he will learn along with us yeah uh to what to any of this like
you know any of the charts right the uh private service connecting other things that we are working
on it yeah yeah yeah okay okay thank you okay uh manor can you add a comment to the jira like what
i did right how many i added a bunch of comments can you open it share me oh okay let me share give
me one second i have not caught the update let me probably i need to open this one give me one second
i'm just waiting for also uh one more thing manohan with respect to the api enablement right so
we face the issue i'll show you that one also quickly because that is also open um no
i i had the comments you don't see that yeah i just posted something on the chat that might
that had some of the last comments on which is the mai dash 4552 i'm not sure if that's the same one
okay probably okay you added the comments here go down yeah
yeah oh okay okay okay okay i got it okay guys let's enable tomorrow all right make you ping my
finger who is that the nikon's right in terms of apis um and mark just trying to understand it i
know it's like a lot of still a lot of greek and latin right now for you yeah very easy one
two is basically to follow is that ptp document that i shared you i hope i think you went over
that document right let's talk tomorrow okay okay and and it's very important and also the
the code base i know you can i think i shared you the code base also right
yeah cloud engineer one start reading the the one two different things so one is the
how the foundation is set up and how the landing zone is set up right read through that
code base and also when you talk to nosibar try to understand which one is eliza so nosibar we are
not responsible for anything else except eliza i'll allow anything that we created in gcp2.1
okay anything that nadim creating we are not responsible don't pull him anyway sure okay
and just give him a walkthrough like how ams amst is created and all i hope you are familiar with
some of the AD sync and all those things right so i want you to just understand the mark right
the whole identity how the uh federation works between gcp and azure today okay right how the how
the user management access is done right when noshiba is our one of our production sources very
very familiar okay she's expert in this okay she will talk to you right so just spend some time
with her tomorrow it's already late i guess yeah we'll do we did spend some time yesterday and
learn some stuff but it will definitely make sure but the important thing is that ptp design document
and start digesting the telephone code okay i want you to start focusing on some of the work okay
okay and i'm now on the service account and ad group i think we can create a resource workspace
as we have for cnph 14 ai dev uh which have the code like timothy did it via code they were two
ad group see assigned role to them and service accounts were created as part of the resource
workspace so maybe we can leverage him for these two parts ad group we already have we can and
where is that service account in new google yeah that is a this one one second
yeah as part of this workspace actually uh we created a resource workspace so he uh created
the service account and assigned the roles and the ad groups are already there where
in the kunj and everyone are there where is that where is that create that's my question
it's in azure or where is that created no no it's it's in gcp assigned to cnvh14 ai
yeah so either we can leverage we can leverage the same ad group because it's in dev tenant and
same users are there but service account we can have uh tied to this project so we can have this
resource workspace created and then probably timofi can help to update the code and we can deploy
the service account and mark can do that too mark mark should be able to do that too if you need to
yeah sure yeah yeah maybe we can have uh timofi to go over this particular part so if you see
the service account assignment there two service accounts will be created one is this one and one
is restricted and there is a set of uh permissions for vertex ai and some of the air services that
will be assigned and give it to mark right you will learn it right yes sure sure yeah i'll send
here the code as well uh so yeah and tomorrow workspace yeah make sure mark has access to
everything and he will learn it okay okay sure sure and one last thing whenever quick one so this is
the vpc uh service where we are whitelisting the apis so even though the apis are added to the uh
like project second thing we have to whitelist them here because uh firebase we are trying to
create a new service under the project but it is feeling that martin bring the mars right start it
start another chart for firebase by martin can you take a look this okay okay i don't
want to put everything in mark okay martin okay sure sure yeah start on that add him to that right
martin can you take a look what's going on with this yes sure okay definitely i'll check with them
Okay, thank you.
Thank you, Manoha.
Thank you, Maan.
No problem.
We'll talk a little bit, Nishima.
Sure.
Definitely.
Thank you, Maan.
ご視聴ありがとうございました
