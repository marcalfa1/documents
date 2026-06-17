Right.
And you can set your variables.
Ask like,
or to give like,
not been permissions in,
in,
uh,
the lieutenant.
Okay.
Okay.
And so would I be able to create my own workspace?
I know I'm going to ask her to do it the first time,
but I also would like to see the processes that as well.
So if I can,
yeah,
you can create a non-prod in the part in it.
He won't be able to do it right there.
You can do it.
Yeah.
Yeah.
And set your own variables and everything.
Okay.
Yeah.
For now she can,
she can,
she can show you.
Okay.
and the very first thing is basically because that's how you learn right with this why you
give it a very simple task right yeah i get that workspace where like you know service accounts on
the role management is created and later on you can delete that make sure the same service account
role management gets added for that project okay okay yeah and also i reach out to someone to see
if I can get the GCP client installed on my laptop.
So I can do the login directly.
Even the G Cloud?
Yeah, the G Cloud.
Because it's approved by the bank,
but for some reason it's not on the software.
It's not working.
The service is not working.
I tried to do it.
It's not working for some reason.
So I think what happened is if you point into the TCP proxy,
it might be an issue, but I think on the CNJ proxy,
but I just got to figure out how to point it to the CNJ proxy
it that way but i need to talk to somebody in mac no i didn't because i know i had similar issue
with another with the aws cli client um and i know that's how i was able to get it to work but um
and i know i had a i was working with marcel a networking team and also i was also working with
with this guy from the um for the proxy team as well so i think it's it's been you know there is
a gcloud ui somebody created apparently it's available self-serviceman i don't know how
Okay.
Like, you can request through our software center, right?
Somehow it gets deployed into your self-service where you can, you know, trigger to, like, install in your, like, you know, in your Mac, right?
So I created that through software center, but in self-service, it's not appearing, GCloud.
So they said it is delegated to Mac.
So if you happen to solve that, let me know.
Okay.
I have a same problem.
Okay, so then I pretty much just request it to Software Center, and they'll just give me a link to, I guess, to install it, right?
Yeah, yeah.
So while I'm gone, right, one is, you know, the main thing is that AI Hub, right?
Through a cloud code, actual service account, you can run whatever it is, right?
Yes.
The other thing is understanding the, two more things.
The other thing is basically one is understanding the GCP design document, remember?
Yes.
understanding that core base yes okay so there was there was two design document if if there's one
that you um you want me to completely focus on if you can resend that to me that'll be great because
i know i have it and i've been i've looking at both of them because i said there was a different
versions of the design document so i know there was a version two um or you know if there's if
there's one that's you know you think well version 12 or whatever it is right 12 i think
version 12 i think the one i sent it version 12 i think the latest one in the ptb version 12 is
the latest one whichever it is let me just give you yeah if you can you send that to i just want
to make sure i have the correct one because i know we've been talking about that a lot and i know i've
been looking at the one from confluence i know there's a version 012 okay 012 okay got it
all right
okay i think i yeah i think it's part of the same document so there's two versions on there
version 01 yeah yeah
i'm trying to
I'll clear from the device.
so the version so this is basically it's uh
this this ptv document is a simplified version of okay are you sharing are you sharing something
or you can or you can just send me the link and i'll take a look at it i'm sending you the link
okay right same thing i i just sent you okay okay this is the one i shared is simplified version of
what um what i google design yeah i think yeah that's i have that one but that's the one that
i think i've so that's more detail i like that right like now i know that is changing right um
gcp design dog so i i like this one or the other one right but whichever it is once you understand
that you can read through it this one um so the one thing is you go over whichever is familiar
understand how the some of the design principles are like how it is what are the like some of the
design thought went through and how it is right initial one right not everything is perfect right
yeah i know the one we discussed in the morning with timothy was going to look into it some of
there are like a lot of gaps actually that guy left abruptly okay um overworked on it so just
read through this or the other one get your the understanding of it right now it's like shared
vpc there's azure sorry gcp you know spoke gcp hub from there and connects to like you know um
so this is the organization right it's still self-readable yeah with the folders yeah i did
see all those are yeah uh this is bny dev i saw the bny prod organization has uh various folders
level OUs, right? Fraud, pre-prod and fraud and management account. Management account is for
logging and billing purpose. Okay. Just purpose, high level. Yeah. And the fraud, every account has
multiple folders. Okay. There's a DMZ folder, there's a shared folder, services folder,
there's a landings on this where all the application workloads go into go. Okay. Okay.
Okay. And in the shared services, there is a core services which is owned by our team. Core means hub and spoke and everything. Okay. And shared services is artifactory, DNS hub and whatnot. Okay. So within hub, this is where Ravi and team, remember the guy the other day we were talking? Ravi is from network. Ravi, Joaquin and Chris Fahir. They own this area mostly.
this is where they basically deploy all these A-matrix components, deploy the network connectivity
center, deploy the like crowd routers, which basically all this A-matrix which connects
to eventually to on-prem. This is where we deploy our like shared VPC with like a multiple
subnet center and E-subnets, right? This is where like new generation firewall, all there's a VPC
perimeter, defined this, and basically all these landing zones leverage the VPC boundary
from this shared network scope.
Okay.
And there's a DNS hub, right, obviously, which also go into network scope, like all this
from the landing zone from the high-level perspective.
This is also artifact.
This is because these two are not deployed yet.
This is for the future.
Okay.
Okay.
Networks, this is hub is basically to deploy anything, you know, in the on-prem there's something called info blocks, you may have heard, right?
Correct?
Yep.
All DNS resolution.
In cloud also we have info blocks running.
Okay.
So we're saying it's going to run in the DNS hub.
So we're going to have a DNS hub project.
Eventually it's not there.
It's info blocks eventually.
Similarly, Artifactory for all the image repo and whatnot for container repositories.
I build anything in containers, like DKE.
But right now, they're going to connect to on-prem,
but eventually it's going to be Artifactory running in the cloud.
This is for the future.
The landing zone, so any landing zone the other day,
the landing zone that you created here, this one, basically.
It basically shades the same VPC boundary.
Any landing zone which is running here, anything here basically visible from here, not visible from here.
Or any other landing zone.
Okay.
And any landing zone deployed in C or any resource, they need to be able to talk to each other.
And this should be able to talk to, this is the hierarchy.
Let me just go.
Yeah.
Sorry.
And.
And.
i have a simplified version so you can just go overall
it's very detailed okay yeah so i have that i mean i went to actually i went to the a lot of
the stuff and get some of the you know key components and names just so you know yeah
so this is what i was looking at to try if you see this right so the landing zones so this is
slightly wrong okay landing zone basically always connects to both okay so this is how like i i made
some changes to here yesterday because i was going to talk to google today but i asked disability to
cancel that meeting
are you in office today you're going to meet there tom no no we're gonna you're gonna be on the um
over the phone i'm not i'm in the office um tomorrow but i was in the office yesterday
i'll be in the office tomorrow and thursday okay okay and i um i heard you mention you get
are you gonna are you gonna be out of um out of office for today or for a couple of days
and i don't know if i over starting thursday starting thursday for two weeks that's why i was
Okay. So, yeah, so I know we have something scheduled for tomorrow.
So what I'm going to do, I'm just going to give you a list of action items that I've been putting together.
I'll share that with you and then you can probably let me know, hey, you know, for the next, you know, you know, I guess when you're out.
So at least, you know, there is some progress.
and also who can I look up to or look into if it's if it's tomo um if I have any you know if I want to
you know it's like tomo is the first point of contact of any help right from the engineering
perspective and operations perspective any of the guys okay okay yeah or is available you should be
able to use it there's more than three persons right there's also more here there are like a
bunch of people there are like five people here like close to 10 people in india but these are
three contacts these are right i mean but there is also more guy here okay like no this guy
this guy is also got matrani okay
him and uh probably more closely together okay
yeah i think i'm gonna pick everyone's brain you know by this week yeah you don't know but i think
the end of the day one is the other gcp project the other one is just understanding end-to-end
this one right oh yeah this is this is very simple this one here extremely right so basically um
we have four swim lanes right one is del tenant right there's a one swim lane running in there
seven and there's like three other swim lanes running in g and bny broad tenant the product
organization okay so how does the swim lane look like this is how one swim lane look like
okay there's an on-frame component within that there is an on-frame core infrastructure tpc cnj
this is where you are before yeah and there is a network hub component where which is basically
is like a host project in google they call it as host project it's a bunch of projects bunch of
like a little resources running here including a vpc in eastern vpc in central and they are paired
together globally it's all connected through ncc i i think it has its own i didn't put all this this
is this i just spent some time yesterday i was going to say let's meet with google to explain it
okay and it has other components too as you read through it you will understand that code base
because i remember that cloud engine and git lab core base yeah you'll understand this yeah
similarly spoke is there's a shared vpc okay and two subnets so shared whereas this one is not
shared vpc because there's a bgp or lan session like obviously uh there's i think bunch of vpcs
uh like a dedicated vpcs aligned each right and the way it is supposed to work um for a way it
takes is ended up having I think we should talk to Ravi by right they end up creating two different
VPCs but which let's not worry too much on this right this is how it is created okay and shared
VPC obviously the way Google network is work I'm not sure I learned last few months okay that it's
like I think they they have the I think their thought process is really good right that one
it's a flat network, right? But within that they have pods. Okay. So when you create in our
application, you can create this network boundary pods within that network, like a global boundary,
this global shared VPC. Okay. Okay. So that you won't be able, you won't lose or you won't waste
any set of range. I really like, I hope I think you figured out our like landing zone or any other
like in azure today where there's a dedicated vpn sorry vnets connected to each right landing
zone comes to two vnets did like no shibar somebody went over with you yes right with two
minutes and vnet comes with multiple subnets right so if you don't use it any of some of this like
say you are literally wasting a lot of this resources right ip ranges because private ip
is the more expensive resources correct yeah final range yeah so you're going to lose it here
you can have like n number of landing zones this is basically uh landing zone n right
landing zone one and landing zone you can end number of landing zones each landing zone connects
to both subnets within landing zone you can have like you know database workloads like level balance
or workloads and all right this is how the last swimming look like if you do further deep right
what happens what we have how does the like a workload look like so you may have a landing zone
it's very simple like traditional workloads of your balance or a gke and oracle vm okay
and each landing zone they have a gke and the compute on the east and complete on the central
okay these are stateless correct so there's no stator with lingual basically copying
whereas working when we create a vertical medium this is what i was talking to uh who are own
arun and martin is working on the low like golden image if you remember remember right yeah yeah
yep they've mentioned so once the golden image is available it's going to that image is available
in some project in google okay some project okay whatever that project is yeah
and based on the project we create a working VM through storefront right and when you set up
one key cluster there'll be two VMs here one VM here there's a synchronous replication between
within the region but of course asynchronous replication across the AC okay
what
want to do and undo. Muir is a little bit sensitive at times.
Async replication, right? This is how it is. But whereas some cases they have GKE, Snowflake,
a lot of PaaS services, okay? PaaS or SaaS services.
So they may have some pass service, like, you know.
So where does the AI hub stuff fit into this?
I can tell you.
So, like, this is a pass, right?
This is a SaaS.
no the best one is basically we should use big cori okay
okay so you can have like a project with like traditional workloads
and pass and chas and verticals whatever you can think of okay and there's like a landing zone
without any of these workloads they just need google access that's where the ai hub is okay
ai have also google quality some of the if you see legacy ai hub right so the one you created is
the one you created is this right yeah the core yes okay uh access to this
space is blocked by whatever it is right okay this is not the
okay this one right but there is also like existing this one is
in the non-prod there is also an existing one it has a lot of other workloads
probably
BigQuery
I hate this query man
they are so powerful creating this one
but their UI really sucks
okay but they do have a lot of other resources right i'm just saying it right for the sake of
that we do have projects without any proper without any vnet resources vcp like shared
services vcp vpc resources okay just that google access only right so mostly ai hub is with with
the model enablement and some of the ai related ai related workloads that's what i'm trying to say
yeah okay so we have like so various type of landing zones okay one is people say this is
a cloud standard landing zone the other one is cloud maybe flexible you can say it that's what
workloads running in six other regions right because ai for ai hub we will grab wherever
we have the capacity right whereas this one when we enable the workload here um see all the standard
landing zone we automate workloads to storefront so somebody will go to the storefront and create
aks which gets deployed to your case here right gk somebody will go to like what a like a storefront
create a vm or virtual vm it will get deployed here right but oracle ai and another ai services
are existing in the in the in the storefront today okay those are flexible so we created our own ai
resources or for 250 because they have is so demanding they have so many things right so
marcy and timothy and other resource who was let go last year he was not let go but he was a really
good guy for some like organizational issue he was he left the firm it was very good he was like a
bad swiping right he just came in and yeah yeah that's definitely not a good thing yeah he was
bad i think he just somebody caught him like he was so good i just got in and he just left him
at leaving and then somebody caught him wow yeah yeah he was that but he was so good very good my
very close friend of mine was there anyway i'll post that right so he was so he helped then i took
over the whole ai and everything right and rap used to manage and rat left and then i manage the whole
team right now okay um so we have two types of workloads one is the cloud standard landing zone
and cloud flexible cloud standard is basically everything is automated everything is basically
where we have vpcrv net running resources and basically position through start standard process
right cloud flexible is where you have resources outside of like east and central for example if
you have open a model running like an auto west or north central or other regions you still you
want to use it you should be able to use it yeah we don't need to wait for any because you don't
need any cloud resources here vnet resources or vcp vpc resources right so so yeah i have model was
created like that okay okay um not not to cut you off short but i um i have a call in two minutes
with tomo yeah yeah yeah yeah so go ahead right you should go ahead we will continue tomorrow
yeah okay yeah those are the two tasks right the other one is basically i want you to understand
this that whole identity right how gc identity works today okay okay um the amst i'm going to
ask tomo to start looking into it right i don't know if you like unless you understand it well
maybe it will take time right maybe you might not be able to but i lost to what will just drive that
project okay yeah yeah i mean i can you know i can probably work with him on that as well if you
can add me at secondary so you know at least i know everything yeah yeah yeah but meanwhile understand
from uh like no shiba knows how the identity works for the existing workspace from the cloud
support why it was done she's because she's not engineering right yeah she doesn't have the right
i just asked like subhu and like oh the mad guy who left before they they did something like four
five years ago i didn't join them we know no one has any clarity okay yeah yeah yeah try to
understand as much as possible don't like worry i know there are a lot of meetings a lot of things
right don't worry too much okay just focus i want you to just start working on one thing so that you
can deliver end to end right yeah you see how it is done yeah yep all right no problem eventually
and do it.
Okay, so we'll
catch up again tomorrow.
Thanks for putting
this call together.
All right,
take care, man.
No problem.
See you soon.
Okay, bye-bye.
.
