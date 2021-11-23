---
layout: default
title: Consents FAQ
parent: Help Center
nav_order: 4
permalink: /consents-faq/
--- 

_This FAQ will go through the most often asked questions regarding all things consent._

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
- TOC
{:toc}
</details>

## How long is the consent that visitors give valid for?

How long users consent is valid for depends on what choices they make in regards to their consent to cookies. If a visitor accepts all cookies, then their consent will be valid for 12 months. 

If a visitor declines one or more cookie categories, then their consent will be valid for 2 weeks (14 days). 

In both cases, at the end of these time periods, they will be prompted with the Consent Pop-up again.

## Can I change the length of time consent is valid for?

If you would like to change the length of time your visitors consent is valid for, you can do so by adding the following script above the uc.js (pop-up) script:

```js
<script type="text/javascript">
window.cookieInformationCustomConfig = {
acceptFrequency: 100,
declineFrequency: 20
};
</script>
```

The number you provide for the accept and decline frequency must be in days.

## If I have made changes, is there a way to make all visitors give their consent again the next time they visit my site?

Yes. If you have changed the length of consent validity, it is a good idea to push for consent so that all your visitors are prompted with the Consent Pop-up the next time they visit your website.

It's also useful and advised if you have added third party services to your website that you know also set cookies (that your previous visitors will not have consented to yet).

If you would like to push for consent, please have a look at our article on how to do so: [How to push for consent]().

## How does it work when a visitor decides to update their consent?

If a visitor decides to update their consent via the Re-open consent pop-up icon (pictured below), then the adjustments they make will be recorded as a new consent.

![re-open consent icon](../assets/consents-faq/reopen-icon.png)

However, this does not mean that the cookies they have declined are suddenly removed. Cookie Information (or you as a website owner) do not have the ability to add or remove cookies from a users browser at will.

If the visitor would like to ensure that they have removed cookies they do not wish to accept then they should clear their browser cookies.

## Why do I see a different number of consents in the Compliance Dashboard vs our own traffic and Analytics numbers?

If you are looking at the consent rate data for past consents and find that the numbers between the Compliance Dashboard and your own traffic and Analytics reporting do not match, then it's likely that it is due to archived data.

We regularly archive consent data to ensure that the user experience of our platform is not negatively impacted. If we were to show all consent rate data in the compliance dashboard the loading time would be unreasonably long.

If you have the Basic Dashboard as part of your subscription, this data is limited to the past 7 days.

## How can I tell how many visitors accepted a certain category?

You'll be able to see this information as part of the Premium Compliance Dashboard under the Consent Insights tab.

## Can I tell if individual visitors have accepted a certain category?

No - the only information available on acceptance for certain cookie categories can be found in the Compliance Dashboard for the total number of consents to a category (like above). Individual users cannot be identified in these statistics.

## Can I pre-tick category toggles so that visitors accept all cookies by default?

Although it is possible to do - doing so would not be compliant with GDPR and DPA guidelines as a visitors' choice regarding cookies must be opt-in rather than opt-out.

## Can I see how many visitors didn't take any action on the pop-up?

It is not possible to see how many visitors did not take any action on the pop-up before browsing away from the site.

## Can I see what visitors spent the most time on when looking at the pop-up?

It is not possible to see what part or parts of the pop-up a visitor spent the most time looking at before they made their consent choice.

Still unsure or didn't find the answer you were looking for? Contact us at [support@cookieinformation.com]()
