---
{"dg-publish":true,"permalink":"/technology/linux/coolify-and-cloudflared/","tags":["linux"],"created":"2024-06-02 7:18:44 pm","updated":"2024-06-02 7:18:55 pm"}
---



[[TECHNOLOGY/LINUX/Portainer -- alphapi\|Portainer -- alphapi]] on alphapi

[[TECHNOLOGY/DEV/HEDGEDOC on Coolify\|HEDGEDOC on Coolify]]


Instructions:
https://www.youtube.com/watch?v=ZvIdFs3M5ic
https://www.youtube.com/watch?v=ey4u7OUAF3c

DIRECTIONS: https://coolify.io/docs/knowledge-base/cloudflare/tunnels
# Coolify.io

```
curl -fsSL https://cdn.coollabs.io/coolify/install.sh | bash
```
# Cloudflared tunnel for Bookworm
https://github.com/cloudflare/cloudflared/issues/576

https://rasmusgodske.com/posts/securely-expose-your-coolify-apps-with-the-magic-of-cloudflare-tunnels/

useful commands: https://developers.cloudflare.com/cloudflare-one/connections/connect-networks/configure-tunnels/local-management/tunnel-useful-commands/

if tunnel is down, check
```
sudo systemctl status cloudflared.service
```

try
```
sudo systemctl enable cloudflared.service
```

if doesn't work, uninstall...
```
sudo cloudflared service uninstall
```



check status
https://one.dash.cloudflare.com/85c72c7e3c5d0360367307dada3d35f8/networks/tunnels?search=

more info:
https://omar2cloud.github.io/cloudflare/cloudflared/cloudflare/


## Update cloudflared

https://developers.cloudflare.com/cloudflare-one/connections/connect-networks/downloads/update-cloudflared/

```
sudo apt-get upgrade cloudflared
```

```
sudo systemctl restart cloudflared.service
```

```
curl --location --output cloudflared.deb https://github.com/cloudflare/cloudflared/releases/latest/download/cloudflared-linux-arm64.deb && sudo dpkg -i cloudflared.deb
```

```
sudo systemctl restart cloudflared.service
```



(https://github.com/cloudflare/cloudflared/releases/latest/download/cloudflared-linux-arm64.deb) && sudo dpkg -i cloudflared.deb && sudo systemctl restart cloudflared


### Check architecture
```
apt-config dump | grep -F "APT::Architectures" -
```


fix architectures if error:

```
sudo dpkg --add-architecture armhf
```

```
sudo dpkg --remove-architecture armhf
```

```
apt-config dump | grep -F "APT::Architectures" -
```

---

[[TECHNOLOGY/LINUX/Secure VPS - Self-host\|Secure VPS - Self-host]]

Install NPM, NVM, NODE, PNPM, etc. [[REFERENCE/Useful Linux Commands\|Useful Linux Commands]]

## Install coolify.io
https://coolify.io/self-hosted

### create root password
https://idroot.us/change-root-password-ubuntu-24-04/


```
sudo curl -fsSL https://cdn.coollabs.io/coolify/install.sh | bash
```



https://medium.com/@vcoder/pi-hosted-on-premise-a-simple-guide-for-a-secured-budget-and-efficient-home-hosting-83c98027771a

https://github.com/coollabsio/coolify/blob/main/README.md


https://rasmusgodske.com/posts/securely-expose-your-coolify-apps-with-the-magic-of-cloudflare-tunnels/
# [Self-hosting Your Website with Coolify v4: A Step-by-Step Guide](https://billyle.dev/posts/self-hosting-your-website-with-coolify-v4-a-step-by-step-guide)

## Creating your SSH key

[[TECHNOLOGY/LINUX/Lock down raspberry pi\|Lock down raspberry pi]]

[[TECHNOLOGY/DEV/Git & Github Useful Commands\|Git & Github Useful Commands]]

If you want to use your password for SSH’ing remotely onto your server, you will have to perform this step. Otherwise, you can just skip to the next section since Hetzner will email you the root password if you omit it. You can also skip this step if you already have an existing SSH key you want to use.

In your terminal, follow these commands:

Have your domain ready for the next step. You’ll be renting a private server.

Hetzner is a great choice for me compared to other companies that charge quite a lot for the same offerings. Hetzner is cheap and seems like a popular choice among the Coolify crowd.

When picking a server, there are some details you want to pay attention to:

-   the location where you think most of your traffic will come from (I chose Germany since it’s a nice in-between Continental US and Asia)

![hHetzner server location options](https://billyle.dev/_astro/hetzner-location-selection.Co179Ww5_SKzDN.webp)

-   the image you want to use on the server (Ubuntu is a great choice)

![Hetzner images options](https://billyle.dev/_astro/hetzner-image-selection.BeMLhoLM_Zbrkpo.webp)

-   whether you will need shared or dedicated vCPU (shared is the best price/performance)

![Hetzner CPU options](https://billyle.dev/_astro/hetzner-server-type-selection.CABaESdi_Z1fnGjp.webp)

-   the server resources like how many CPUs, RAM, and storage your sites and apps will consume. To run Coolify, these are the **minimum requirements**
    -   **2 CPUs**
    -   **2 GB memory**
    -   **30+ GB of storage for the docker images**

![Hetzner review order](https://billyle.dev/_astro/hetzner-server-selection.0RNWiYvd_kCrGW.webp)

-   lastly, your monthly budget

### Add your SSH key

After your selection, you may want to include your SSH key. Skip this if you want Hetzner to email the password to you.

Under the section titled “SSH keys”, click on “Add SSH Key” and a modal will pop up.

Back to the terminal now, we’re going to copy our SSH key and paste it into the modal.

```
cat ~/.ssh/id_rsa.pub
```

The `.pub` signifies that this is the public key and the output will look something like this:

```
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAACAQDbQj5IxxXslqfOl4Qv5Ux0RNbofCVy5EWbkosc2AnDj6XAFZSdLNwlPG1qnckhuWCeHveWmJAU80G9d4eTvV/W4bKOE8jj0iqVCFHLXdgOlbO+WQgpVDKjhAnRlaJfPNiLvAn0yNr/Sj1ESbMzBwNK4bjTBCMOalvq/NUqz+3bcewdlc3gDunvdmGf4RbfUydZ73rhO0Bg/r+u7NWT1pghcFW/E/E9f6OavBzyHRSSP0MJQYx3bnmgpFcmZlz/3O0gUaxLGXAmFAsaYxAZ7iZXz8AWw2DmcaNlf+lyAYOQ2TGVaZ4VAUwDQE/8u4zFaX+HooUScgTY3oUztIHFDFgyu6Q4N6ILj/aujnSiuv5fW9PiQ70Jce78IMTAlRSqVeBxRgK8Di5eHECFOH+chNp9UhThw+ZO4dHBwxngdZcbd7xmX3hczS1DnYgtOKUIWzx6rUGrN1wsMsdJS4GAWHvhtWMZITqvg4XXEsMdFtKZ8pJj8O8qjNyPEmfYg1upVmoGufcCCbIRY0CKzBeer3hpqD74EcGyB0TJmeHQezCMsmdBW9DJNPDtCfL/zMMXyqtyjsddkl8AbloZmlkgHDLtSscfWeLtMMX1DkT13LoekjL11ZCOMU5vAWvKiJGxU0NRFRStHU/AIpRqDBtD+VFPRWa0javzgXZTr3ALQun5jQ== [email protected]
```

Highlight all the output and then paste it into the modal and then click save.

After that, you will want to review your Hetzner configuration before you complete the transaction.

If all looks okay, go ahead and create it. It will take less than a minute to spin up your new server.

If you mess up, you can always delete the server and start a new one since they charge by the hour.

## Installing Coolify

Once your server is created, you will see an IP address for your remote server. You will connect to it and configure your server to use Coolify.

In your terminal, type in these commands:

```
ssh root@<server_ip_address>
```

Where `<server_ip_address>` is the one provided to you by Hetzner.

The next prompt will ask you to add the IP to your known hosts list.

Type in “yes” here.

Then you will enter the passphrase that you used to create the SSH key or the password that Hetzner sent to you by email.

```
The authenticity of host '162.55.37.168' can't be established.
ED25519 key fingerprint is SHA256:L1WGqdh9jEOSIrQ/eNcDOtgyYNDWCbTIlEtMcp8rs10.
This key is not known by any other names.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '162.55.37.168' (ED25519) to the list of known hosts.
Enter passphrase for key '/Users/billyle/.ssh/id_rsa':
```

You should now have remote access to your server and execute commands.

```
Welcome to Ubuntu 22.04.3 LTS (GNU/Linux 5.15.0-91-generic x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

  System information as of Sun Mar  3 03:54:34 AM UTC 2024

  System load:  0.0               Processes:             100
  Usage of /:   5.1% of 37.23GB   Users logged in:       0
  Memory usage: 5%                IPv4 address for eth0: 162.55.37.168
  Swap usage:   0%                IPv6 address for eth0: 2a01:4f8:c012:7c82::1


Expanded Security Maintenance for Applications is not enabled.

0 updates can be applied immediately.

Enable ESM Apps to receive additional future security updates.
See https://ubuntu.com/esm or run: sudo pro status


The list of available updates is more than a week old.
To check for new updates run: sudo apt update

root@ubuntu-4gb-fsn1-1:~#
```

If you go to [Coolify.io docs](https://coolify.io/docs/installation) and search for installation, you should see the installation script which looks like this:

```
curl -fsSL https://cdn.coollabs.io/coolify/install.sh | bash
```

Enter the command and let the installation script do its thing. Once that’s complete, you will see an output with an IP address where you can access the Coolify instance on your server, in my case it was `http://162.55.37.168:8000`.

![Coolify installing in the terminal gif](https://billyle.dev/images/coolify-installation.gif)

Copy the IP address along with the port and enter that in your browser’s URL. You will be directed to the registration screen for Coolify.

## Coolify Onboarding Experience

When you follow the IP address from the Coolify installation, you will be taken to a registration page.

Sign up to log in to the Coolify instance where we will host it on your domain.

Be sure to use a strong, unique password since this is how you will interface with Coolify on your custom domain.

![Coolify onboarding registration form](https://billyle.dev/_astro/coolify-registration.DVuBZX2F_1zCgh3.webp)

You will be prompted with a series of onboarding questions. Just keep clicking next until you see the page, “Server”.

![Welcome to the Coolify page](https://billyle.dev/_astro/coolify-welcome.BqMKuoWY_11yCzL.webp)

You will select “localhost” as that’s where this instance of Coolify is installed.

![Coolify onboarding - server-type options](https://billyle.dev/_astro/coolify-server-selection.CzYg1JZv_JOlX2.webp)

Then you will create your first project. These projects are a way to organize your resources under one umbrella. Here you will be adding your first project so click on “Let’s create a new one”. This will create a project called, “My first project” for you.

![Coolify onboarding - project selection](https://billyle.dev/_astro/coolify-project-selection.B4YUg5SQ_27WYM0.webp)

After that, the next page says something about adding resources. Resources are things that your app or website needs such as databases, servers, etc. Click on the “Let’s do it!” button.

If you’re deploying a static site, chances are, you only have one resource to deploy. Select the “Public Repository” resource.

![Coolify - create a resource page](https://billyle.dev/_astro/coolify-resource-add.Dy3_OK0k_Z2lN1zD.webp)

When you click that, you will be asked which server you like to use. There should be only one and that’s “localhost” from before.

![Coolify resource select server option](https://billyle.dev/_astro/coolify-resource-add-server.iF0wPhJu_ZiqSnx.webp)

Then it will ask you to select a Destination. Just choose the only option which should be a Standalone Docker instance called “localhost-coolify”.

![Coolify resource select destination option](https://billyle.dev/_astro/coolify-resource-destination.CcJEVCoh_Z3TIF4.webp)

And lastly, it will ask you for the URL for the public repository. Paste the URL of your public repo into the field.

It will get the metadata from the Git repo and should populate all the necessary details.

The important part here is the **Publish Directory** where the build output will be.

Also, toggle the “Is it a static site” toggle if it applies to you.

![Coolify - creating a new application page](https://billyle.dev/_astro/coolify-source-repo.CGjlYuI2_Z1M2yjS.webp)

You should now see a configuration page for the resource you just created.

There’s a lot on this screen but we’re going to focus solely on deploying to see if we can get Coolify to build our application.

On the top right corner, click “Deploy”

![Coolify&#x27;s application configuration page](https://billyle.dev/_astro/coolify-resource-config.-8BvsAX-_1WIiTL.webp)

You will be taken to the Deployment page and your build logs will start appearing.

Hopefully, there won’t be any errors and you will see a “New container started” as the last log entry and your deployment says “Finished”.

![Coolify&#x27;s deployment page](https://billyle.dev/_astro/coolify-app-deploy.D52UTq9V_ZR2s5.webp)

To test to see if Coolify can serve the website, click on the “Open Application” button and select the auto-generated link to view your site.

![opening deployment application on Coolify](https://billyle.dev/_astro/coolify-app-open.ucG3SqMt_ZvF5Uz.webp)

You should see your site being served by Coolify.

![my website live on URL that Coolify provided](https://billyle.dev/_astro/coolify-app-website.D0yye6Me_2i2RTY.webp)

Keep your Coolify page open for the next part as we still need to tinker with it later.

## Proxy domain from Cloudflare to Coolify

Now all we need to do is some configuration between Cloudflare and Coolify. We need to point our domain in Cloudflare to our Hetzner server and Coolify will serve our applications.

It took me a long time to figure this out so there might be some trial and error on your part, but I hope this next set of instructions just works for you.

### Enforce Strict SSL/TSL Mode

This next part is important! Navigate to the SSL/TLS page in Cloudflare.

![navigation menu showing how to get to Cloudflare&#x27;s SSL overview](https://billyle.dev/_astro/cloudflare-ssl.k4NkRZce_Z6x8kw.webp)

We want to turn on SSL Full (strict) mode to allow Coolify to serve HTTPS for us.

By default, SSL will be on Flexible mode and if you had this on, both Coolify and Cloudflare will be stuck in a redirect loop causing the page to throw a “Too many redirects” error.

![selecting the Full Strict option in Cloudflare SSL/TLS page](https://billyle.dev/_astro/cloudflare-ssl-full-strict.DDobnh-M_Z2h6LrQ.webp)

### Access Coolify from our domain

In your Cloudflare dashboard, go to the DNS Records Management page for your domain. We want to add a subdomain for our Coolify instance.

![navigation menu showing how to get to Cloudflare&#x27;s DNS records management](https://billyle.dev/_astro/cloudflare-dns-management.Cu9wI8OU_ZYkgls.webp)

Add a new “**A**” record, with the hostname “**coolify\*\***”, and the value is the IP address of your remote server, and click save.

![creating Coolify instance DNS record](https://billyle.dev/_astro/cloudflare-dns-coolify.S0VNt0vW_ZbjD8i.webp)

Go back to Coolify, and go to the Settings page.

![navigation menu showing how to get to Coolify&#x27;s settings page](https://billyle.dev/_astro/coolify-settings.DXvv3RlG_Z2rwbEo.webp)

In the “**Instance’s Domain**” field, type out `https://coolify.<your_domain>`.

Notice that we added HTTPS here. Coolify will automatically generate an SSL cert when it sees this configuration. Be sure to hit save.

![configuring Coolify&#x27;s setting to point to the domain](https://billyle.dev/_astro/coolify-instance-url.Dk-vZacE_1lqA9W.webp)

Let’s see if we can now access our Coolify instance from our domain instead of the Hetzner server IP address.

Head over to `https://coolify.<your_domain>` and check out your new Coolify on your domain!

If it doesn’t load yet, wait a few moments until the DNS propagates.

![Custom domain website hosting Coolify](https://billyle.dev/_astro/coolify-domain.DlIME1sK_Znbj21.webp)

Now login with the credentials you used to register in the initial Coolify setup, and you should now be at the Coolify dashboard.

### Link the Coolify app to your domain

From the Coolify dashboard, navigate back to your project configuration dashboard.

We’re going to change the auto-generated domain that Coolify created to use our domain.

Type in your domain and then click save. After you save, make sure to click “Redeploy” or else this won’t work.

![configuring custom domain in Coolify&#x27;s application configuration page](https://billyle.dev/_astro/coolify-custom-domain.C1GmZV8t_wjzE0.webp)

Back to Cloudflare, we need to create more DNS records to make sure our domain is pointed to our server.

So head on back to the Cloudflare DNS Management and enter a new “**A**” record, with the hostname ”**@**”, and the value should be the Hetzner server IP address.

![entering DNS record for custom domain](https://billyle.dev/_astro/cloudflare-dns-domain.qWXg6Up__1VnDyu.webp)

Now give it a couple of minutes and visit your domain. You should see live! How cool is that?

![Custom domain running off Cloudflare and Coolify](https://billyle.dev/_astro/custom-domain.2cqOA67F_Z23Nj52.webp)

## Redirect www to non-www

We’re almost done with the long tutorial. I was excited when I got this far and I hope you are too.

This last part is the final section and what we’re going to do is redirect our `www.<domain>` to just `<domain>`.

All of this will happen in Cloudflare so we don’t need to mess around with Coolify.

In Cloudflare, back in our DNS management, we’re going to add two records.

The first one is an “**A**” record, with the name of “**www**”, and the value of `192.0.2.1`.

This is saying we are creating an ALIAS record that uses the `www` subdomain, and we are pointing to a dummy IPv4 address.

The dummy IPv4 address is insignificant since Cloudflare will redirect all traffic before reaching the IP address.

![entering DNS record for ipv4](https://billyle.dev/_astro/cloudflare-redirect-ipv4.DUgFc3TM_2c2O8d.webp)

Now we’ll create the IPv6 version with another “**AAAA**” with the name same name but this time the IPv6 address is `100::`

![entering DNS record for ipv6](https://billyle.dev/_astro/cloudflare-redirect-ipv6.Bp5L-Fpr_Z1b0Xpx.webp)

While that’s being propagated, we need to set up the actual redirect rules in Cloudflare.

Head over to the Rules Redirect page

![navigation menu showing how to get to Cloudflare&#x27;s redirect rules](https://billyle.dev/_astro/cloudflare-redirect-rules.BKH3Cnp4_yub4e.webp)

Once there, click on ”+ Create rule” where you’ll be taken to a form.

Add the name of your Redirect Rule. I named mine “www to apex”.

![enter the redirect rule name](https://billyle.dev/_astro/cloudflare-redirect-name.SmAfUcDV_ZMjfiR.webp)

Then click on “Edit expression” where you’ll type in the rule expression. Replace `billyle.dev` with your actual domain.

![arrow showing how to edit expressions](https://billyle.dev/_astro/cloudflare-redirect-edit-expression.BOYyCJdj_Z1kiBwX.webp)

```
(http.request.full_uri contains "www.billyle.dev")
```

![condition criteria inside edit expressions](https://billyle.dev/_astro/cloudflare-redirect-expression.DVZ9F81L_red0h.webp)

The last input field is where Cloudflare does something when it matches the condition above.

We want a “Dynamic”, with a “301” permanent redirect and our expression will be:

![dynamic redirect expression with status code 301](https://billyle.dev/_astro/cloudflare-redirect-dynamic.Bul0g9mn_Z142P0k.webp)

```
concat("https://","billyle.dev",http.request.uri.path)
```

Again, replace `billyle.dev` with your actual domain and make sure the “Preserve query string” is checked.

Now test it out after a few minutes to see if it works. Visit `www.<your_domain>` and see if it redirects you to the root domain.

## That’s it! You’re done!

Wow, that was a lot! I’m glad you made it all the way through. I hope you’re proud of what you did here.

This is our new journey down self-hosting PaaS. The days of paying for a droplet and managed DB are over for me.

You’ve learned how to create a remote server with Hetzner, SSH into it, and install Coolify. Then you managed to link your domain to Coolify and deploy your website!

If you have any questions, feel free to email me or contact me through my social media links.

And thank you for reading! Hope you have a great rest of your day wherever you are.

[RSS Subscribe](https://billyle.dev/rss.xml)