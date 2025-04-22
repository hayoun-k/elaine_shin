---
layout: blog
title: hey sample
pubDate: 2025-04-21T22:53:00.000Z
HeroImage: src/assets/images/sample.png
description: Wrold is changing
---



I’ve always been a marinator who needs time to organize thoughts. I lean heavily on planning, not on spontaneity. 

But there are low-stakes situations where I could see that it’s better to immediately hash out steps to keep making progress.

One way that I’ve evolved as an operator was speeding up a train of thought and decisively marking what findings are conclusive or needing further research.

This wasn’t something I intentionally worked on.

So, it came as a sudden realization that I improved when a teammate needed support on a task one day.

Here’s how I played out an investigative outline on the spot to help my teammate keep moving things along instead of pausing their progress so that I can marinate later.

It’s very much a string of consciousness that I’ve tried to organize to show how independent troubleshooting might look like.

—-

Today at work, my teammate asked me to confirm whether or not a filter that they set up for a customer relationship management tool (CRM) and Mailchimp (MC) integration “looked good.”

It’s a one-way sync to automatically transfer CRM contacts into MC. They were in charge of the initial setup to see what info will successfully transfer into MC.

We had debriefed on some issues we found on MC’s side earlier that day, but this is the first time I’ve ever seen our CRM’s interface.

My gut reaction to their question is “How am I supposed to know if this looks good without being familiar with the software?” I think about exploring the CRM on my own first and then scheduling time with them later.

As risk averse as I am, it just feels safer that way. Less room for mistakes in my mind.

But then a sudden switch turns on and I conduct a 15ish minute investigation that moves my teammate along with new information and next steps.

## Exploration

My teammate asked me if the filter they chose for a CRM and MC integration was “good.”

To define what “good” means, let’s circle back to the problems we identified earlier that day:

1. We have only ten contacts in MC when there should be a thousand.
2. Contacts that did go through are missing the information we expected (state, school name, etc).

So I define an ideal “good” as resolving these two issues.

### Problem one

*We have only ten contacts in MC when there should be a thousand.*

Sometimes, the outcome is wrong because we overlooked something simple. Let’s see if it’s that easy this time. 

#### Start

I look at the filter and recount what contacts we expected to see in MC:

* Contacts located in the states we operate in.
* Contacts with a field called “Open Deal.”

At a glance, I can see that the filter is set with the correct states and fields. There seems to be no obvious issue with filter logic, so the problem might lie elsewhere.

Where? I’m not sure yet. 🛑

#### End - Needs further investigation

Let’s explore a different part of the CRM while moving on to problem two.

### Problem two

*MC contacts are missing info that they supposedly have in the CRM.*

How the integration is set seems pretty intuitive. You tell the CRM which MC audience you want to send contacts to, and the integration pulls up all possible audience fields you can associate CRM fields with. 

For example, I can select the MC field “Job” and correspond it with the CRM field “Job Title.” The integration knows exactly where CRM info should go in MC even if the field names are different.

#### Start

Since I need to learn how CRM fields work on the go, I pull up a separate window to feature a couple different CRM contacts as I look at the integration window.

I guess reasons why we might be encountering problem two:

* Did we connect to the right MC audience?
* Are we pulling info from the correct CRM fields?
* Is the integration product functioning as intended?

##### Part I

The first question is easy to verify since the integration explicitly states the name of the MC audience we’re connected to. ✅

* Did we connect to the right MC audience? 

  **Yes**
* Are we pulling info from the correct CRM fields?
* Is the integration product functioning as my prior assumption?

##### Part II

The second question requires a bit more digging, because I notice that the CRM fields feature three lines of info. The first line says “People,” the second says the field name, and the third says the content type like “Text.” 

I’m not sure why the first line would be there, because all of the fields just say “People.” I’m unable to find a field that doesn’t say this.

Maybe looking at the fields in a different context will help my understanding.

Let’s review a CRM contact.

Okay, so there are actually two separate categories of info: People and Organization. I look at the possible fields for each category and I find duplicates.

The duplicates are the potential answer to question number two! 

If we only looked at the field names, then the correlations make sense. But our BD teammates don’t actually fill this section out. Instead, they input the info we need in a differently named field.

Looks like we have to use the People category. 

I want to verify this, so I compare the info of the MC contacts we got with how their profile looks like in the CRM.

To verify, I’ll review the following CRM profiles.

* Contact 1 which has California written only in People.
* Contact 2 which has New Jersey only written in Org.

MC’s contact 1 was the only one with state info. Contact 2’s state field was blank. This verifies that our sync can only pull info from People but not in Org. Which would explain why none of our MC contacts were populated with more info. ✅

* Did we connect to the right MC audience? 

  **Yes**
* Are we pulling info from the correct CRM fields?

   

  **No, but we can fix this by requesting BD to fill out our required fields.**
* Is the integration product functioning as my prior assumption?

We’ve solved question two and verified the answer. **This also ends up being the answer to problem one, because the one-way sync was looking for “Open Deal” under People, but it was often a selected field under Org instead.**

##### Part III

It’s now time for the final question. I generally ask this because I have experienced my fair share of faulty products.

To do a brief sweep, I double-check that all of the fields we chose in the integration are listed in People. It means I look up a target CRM profile that is already in MC to verify what information actually transfers over if they’re all under People.

Every field except for one ended up populating in MC: an owner field.

* Did we connect to the right MC audience?

   

  **Yes**
* Are we pulling info from the correct CRM fields? 

  **No, but we can fix this by requesting BD to fill out our required fields.**
* Is the integration product functioning as my prior assumption? 

  **No, the owner is not populating in MC despite it being filled correctly in the CRM.**

   

I have my own work to do so I only devote a few minutes to uncover the issue, which I don’t. At this point, I’ve reached the 15ish minute mark, so it’s time to wrap this up.

## Summary

Let’s summarize what we were trying to solve in order to determine whether or not the CRM and MC integration was “good.”

1. Q: Why did we only have ten contacts in MC when there should be a thousand?
2. Q: Why were contacts that went through to MC missing the information we expected (state, school name, etc.)?

I give my teammate a few action items:

1. Let BD know that they must use the People categories to ensure that marketing receives necessary info to distinguish contacts.
2. Spend up to 30 minutes investigating the owner issue.
3. If there is no answer after 30 minutes, then submit a support ticket to the CRM.

And that’s the end!

Investigative sessions like these help me to ensure that I’ve progressed as much as I can independently before contacting others for help.

Normally, I’d type the problems, questions, and steps I’m taking throughout the whole process. 

But this time, I cycled through the whole process and only noted my teammate to take notes every time I made a mini discovery.

I suspect that I wrote my outline so many times that it now lives imprinted on my brain somewhere, ready to play out on command. (Ofc, it’s not going to play out perfectly every time and not going to stop me from continuing to write everything out!
