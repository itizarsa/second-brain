# How to hook up a custom domain email to your free Gmail account | by Kathy Li | Build University | Medium

Source: Notes
Status: Unprocessed
URL: https://medium.com/builduniversity/how-to-hook-up-a-custom-domain-email-to-your-free-gmail-account-ead660884d11

![https://miro.medium.com/max/1200/1*M7f0F3BWt92040EAxwbUyQ.png](https://miro.medium.com/max/1200/1*M7f0F3BWt92040EAxwbUyQ.png)

---

This tutorial would ideally be helpful for people who build/manage multiple projects, while wanting a custom domain name + email address for each.

# Why not just use G Suite?

It has something to do with costs. (It always does, doesn’t it?)

Granted, a G Suite account will indeed allow you to “create business email addresses for your domain, and get 30GB of space.”

Plus, once you have signed up for a G Suite account, you will have the option to create email “aliases” — which will be useful for setting up several different identities / message filters for your brand (more on G Suite aliases in a future post, potentially).

And for the sake of full disclosure, I do use G Suite for my *main* company email addresses.

However, if you are like me and actively run a ton of standalone projects, G Suite fees will add up…

Let’s say you have 20 standalone projects that each uses its own domain. G Suite fees would come out to be:

$5.00 / user / month x 12 months x 20 projects = $1,200 per year

Versus…

Cost of this setup = $0

You will only need to pay the domain fee on an annual basis.

# The goals of my setup

What I am trying to achieve here:

- Get a **custom domain name** (wearemojis.com) for a small annual subscription fee from Google Domains — currently $12/year
- Sign up for a **free Gmail account** to use with the project (weallwearemojis@gmail.com)
- Set up a **custom domain email address for free** (crying.kitty@wearemojis.com) via Google Domains, making use of the purchased custom domain
- Have emails that are sent to the custom domain email (crying.kitty@wearemojis.com) automatically **forwarded to the Gmail account** (weallwearemojis@gmail.com)
- **Send email as** crying.kitty@wearemojis.com
- Eliminate the need to purchase a new G Suite account for every new project
- Make the most of all the free Google services that come with the Gmail account

# Now, the step-by-step guide

1. Sign up for a free Gmail account. In my case, it’s weallwearemojis@gmail.com (not a real email address).
2. Purchase a custom domain for your project from Google Domains.

USD$12.00

3. From Google Domains, set up Email Forwarding: Click on **Add email** next to the desired domain > type in the alias you want > enter the existing email you want to forward to > click the **Add** button

In my case, I’m trying to have messages sent to *crying.kitty@wearemojis.com* forwarded to my Gmail, *weallwearemojis@gmail.com.*

![How%20to%20hook%20up%20a%20custom%20domain%20email%20to%20your%20free%20%20837a6c59f9d94669ae6a5f6d5b8ffb1e/1WRQlDN6YRilMQs3tHNL6lg.png](How%20to%20hook%20up%20a%20custom%20domain%20email%20to%20your%20free%20%20837a6c59f9d94669ae6a5f6d5b8ffb1e/1WRQlDN6YRilMQs3tHNL6lg.png)

4. Confirm your existing email (check your Gmail inbox for the message).

![How%20to%20hook%20up%20a%20custom%20domain%20email%20to%20your%20free%20%20837a6c59f9d94669ae6a5f6d5b8ffb1e/1AaYW50hGYSe3hWbnhEHn2w.png](How%20to%20hook%20up%20a%20custom%20domain%20email%20to%20your%20free%20%20837a6c59f9d94669ae6a5f6d5b8ffb1e/1AaYW50hGYSe3hWbnhEHn2w.png)

Actual emails grayed out to avoid spam

## **At this point, you are pretty much good to go!**

All emails sent to *crying.ktity@wearemojis.com* can now be found in the Gmail inbox of *weallwearemojis@gmail.com.*

Simple as that!

## [Optional] But what if you want to be able to “send” or “reply to” emails from your custom email address?

You are probably aware that with this setup, you don’t actually “send” and “receive” emails with your custom email (*crying.kitty@wearemojis.com* for me).

You don’t really touch an inbox or other folders of the custom email.

But thanks to the magic of email forwarding and Gmail alias, you will be able to act as if you are doing just that.

# Additional steps to set up the “sending from” part:

**Part I.** Set up an App Password for your Gmail account to allow you to use the Gmail SMTP servers securely.

5. Go to the Gmail account. Click your username or user icon in the upper right corner to bring up the user menu.

[How%20to%20hook%20up%20a%20custom%20domain%20email%20to%20your%20free%20%20837a6c59f9d94669ae6a5f6d5b8ffb1e/0sz90MstFegA0qA7H](How%20to%20hook%20up%20a%20custom%20domain%20email%20to%20your%20free%20%20837a6c59f9d94669ae6a5f6d5b8ffb1e/0sz90MstFegA0qA7H)

For me, it’s: weallwearemojis@gmail.com

6. Click **My Account**.

7. In the Google account screen, under **Sign-in & security**, click **Signing in to Google**.

[How%20to%20hook%20up%20a%20custom%20domain%20email%20to%20your%20free%20%20837a6c59f9d94669ae6a5f6d5b8ffb1e/0jvoc6X6YcJeC25bS](How%20to%20hook%20up%20a%20custom%20domain%20email%20to%20your%20free%20%20837a6c59f9d94669ae6a5f6d5b8ffb1e/0jvoc6X6YcJeC25bS)

8. In the **Password & sign-in method** box, click **App passwords**.

[How%20to%20hook%20up%20a%20custom%20domain%20email%20to%20your%20free%20%20837a6c59f9d94669ae6a5f6d5b8ffb1e/03dWm7LikLUj0Nf_8](How%20to%20hook%20up%20a%20custom%20domain%20email%20to%20your%20free%20%20837a6c59f9d94669ae6a5f6d5b8ffb1e/03dWm7LikLUj0Nf_8)

You may be asked to re-enter your password at this point.

**Note**: You must have **2-Step Verification** enabled for the App passwords option to be available. If it is not, click **2-Step Verification** and enable 2-Step Verification. Then continue to set the App password.

9. In the App passwords box, select **Mail** for the app, select **Other** for the device.

[How%20to%20hook%20up%20a%20custom%20domain%20email%20to%20your%20free%20%20837a6c59f9d94669ae6a5f6d5b8ffb1e/0UL4UOSnRjwWkctTt](How%20to%20hook%20up%20a%20custom%20domain%20email%20to%20your%20free%20%20837a6c59f9d94669ae6a5f6d5b8ffb1e/0UL4UOSnRjwWkctTt)

10. Enter the name of your domain for the “other” device, and click Generate.

![How%20to%20hook%20up%20a%20custom%20domain%20email%20to%20your%20free%20%20837a6c59f9d94669ae6a5f6d5b8ffb1e/1LVhVuuRBxtQkimCwn5JePA.png](How%20to%20hook%20up%20a%20custom%20domain%20email%20to%20your%20free%20%20837a6c59f9d94669ae6a5f6d5b8ffb1e/1LVhVuuRBxtQkimCwn5JePA.png)

11. The Generated app password box will display a 16-character password. Copy this password. You will need it when you add your new send-as (forwarded) account.

[How%20to%20hook%20up%20a%20custom%20domain%20email%20to%20your%20free%20%20837a6c59f9d94669ae6a5f6d5b8ffb1e/0GiJ2-tZhSdhlaQFH](How%20to%20hook%20up%20a%20custom%20domain%20email%20to%20your%20free%20%20837a6c59f9d94669ae6a5f6d5b8ffb1e/0GiJ2-tZhSdhlaQFH)

12. Return to your Gmail screen.

**Part II.** Add the alias as an account to your Gmail inbox.

13. In the top right corner, click the **Settings** button.

14. Select **Settings** from the drop down menu.

15. In the **Settings** screen, click the **Accounts and Import** tab.

16. Scroll down to **Send mail as** and click **Add another email address you own**.

17. In the first **Add another email address** box, enter the name you want recipients of your email to see (such as “Support Team” or “Sales” or any other name for this contact) and the forwarded email address you are setting up.

![How%20to%20hook%20up%20a%20custom%20domain%20email%20to%20your%20free%20%20837a6c59f9d94669ae6a5f6d5b8ffb1e/1ZDlDBFZnyhw8qaepSmuSBg.png](How%20to%20hook%20up%20a%20custom%20domain%20email%20to%20your%20free%20%20837a6c59f9d94669ae6a5f6d5b8ffb1e/1ZDlDBFZnyhw8qaepSmuSBg.png)

18. Click **Next Step**.

**Part III.** Set the Gmail SMTP server as the mail server for your forwarded alias, using the generated App Password.

19. In the second **Add another email address** box, change the values in fields to enter the following:

- **SMTP Server**: `smtp.gmail.com`
- **Port**: `465`
- **Username**: Your Gmail account (the one you are logged in as)
- **Password**: The generated app password you copied in Step 11.

![How%20to%20hook%20up%20a%20custom%20domain%20email%20to%20your%20free%20%20837a6c59f9d94669ae6a5f6d5b8ffb1e/1sSU5CK8fPsLgly44F8JUbA.png](How%20to%20hook%20up%20a%20custom%20domain%20email%20to%20your%20free%20%20837a6c59f9d94669ae6a5f6d5b8ffb1e/1sSU5CK8fPsLgly44F8JUbA.png)

20. Click **Add Account**. If you see an error message, check to make sure you have entered the SMTP server, Port, Username, and Password correctly.

21. After you have successfully added the account, return to Gmail. You will see a message from **Gmail Team** with the subject **Gmail Confirmation: Send Mail As** and the address you have just added. Follow the instructions in the message to confirm the email address.

22. When you send mail from your Gmail account, click the triangle next to your **From** address to choose to send the message from the account you just added.

[How%20to%20hook%20up%20a%20custom%20domain%20email%20to%20your%20free%20%20837a6c59f9d94669ae6a5f6d5b8ffb1e/0uTvy8I2Ji-g4igkK](How%20to%20hook%20up%20a%20custom%20domain%20email%20to%20your%20free%20%20837a6c59f9d94669ae6a5f6d5b8ffb1e/0uTvy8I2Ji-g4igkK)

## That’s it!

# Final notes:

1. [wearemojis.com](https://www.teepublic.com/user/wearemojis) is indeed one of my domains. Have a look at the site if you want — and maybe buy a t-shirt or two while you’re there ;)
2. All other email accounts in this tutorial are completely made up and won’t actually work — so there is no need to waste time spamming those 👐
3. This discovery was made during my “[Building 3 Products in 30 Days](https://medium.com/@kathyli/building-3-products-in-30-days-day-1-2a01e6e074f6)” journey.