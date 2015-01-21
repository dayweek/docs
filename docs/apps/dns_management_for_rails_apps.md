page_title: DNS Management for Rails Apps
page_author: Brittany Martin
page_description: Knowledge base article to instruct users on how can manage the DNS for their Rails app
page_keywords: dns domain godaddy rails app namecheap url

## DNS management for Rails apps

Bought yourself a domain for your brand new shiny Rails app or you're (hooray!) moving your app to the Ninefold promiseland? Excellent! Ninefold can manage your DNS once you follow the following steps.

#### Ninefold name servers

Depending on the domain registrar (e.g. GoDaddy, CrazyDomains and NetRegistry) you have purchased/manage your domain on, this can involve some changes and configuration to be conducted on their respective panels or by their support team.

Your domain should be pointing to the following Ninefold Name Servers:

* ns3.ninefold.com (IP: 103.7.166.250)
* ns4.ninefold.com (IP: 103.7.165.250)
* ns5.ninefold.com (IP: 198.89.105.250)

Please consult with your domain registrar for information on how you can point your domain to Ninefold's Name Servers.

_WARNING: If your website or domain is currently in use, you should take care in not delegating the domain without properly and adequately setting up your DNS before hand. DNS changes can take up to 48hrs to propagate, so a mistake or poorly configured DNS records or settings can have some serious consequences._

#### Add your domain (A record)

Once you have deployed your app, you can easily add your domain.

* Sign into the Ninefold Portal
* Click on the __Overview__ tab
* Click the __Add__ button next to __Domain__
* Enter your domain and save

Technically, it can take up to 48 hours for your domain to propagate but normally it is much faster. Go Speed Go!

#### Optional: CNAME and MX records

If you need to manage subdomains or mail exchange, you'll need to add CNAME and MX records to your app. The information to complete these will come from your domain registrar.

Navigate to __Servers__ > __Network__ > __DNS__ in Ninefold. Click __Edit__ next to your existing record (created from the __Overview__ tab above) and then __Add Record__.

_CNAME_

You can add as many CNAMEs as you want. We do support wildcard domains.

* __Name:__ (subdomain URL like 'pop', 'members', 'admin', or whatever you choose)
* __Type:__ CNAME record
* __Content:__ (The full URL with the subdomain included that you want the CNAME to point to)
* __TTL:__ (you can accept the default)
* __Priority:__ (your choice)

_MX_

Add one per record as provided by your registrar.

* __Name:__ (can be blank or a subdomain URL like 'mail', 'imap', etc)
* __Type:__ MX record
* __Content:__ (mail server URL from your registrar)
* __TTL:__ (you can accept the default)
* __Priority:__ (Accept the default or add what your registrar gives you)

***
_WARNING: Do not add additional A records for the domain here if the domain has already been added to the __Overview__ tab. The two A records will conflict with each other causing the domain to stop resolving correctly._
***

#### Troubleshooting

When your DNS is pointed to our name servers and add it the __Overview__ tab, your domain will point to the load balancer of your app. Don't know your load balancer IP? That can be found under Your App > __Infrastructure__ > __Edit__ > __Load Balancer IP__.

If your domain isn't pointing to your app, enter in the magic of [What's My DNS](https://www.whatsmydns.net/). What's My DNS is a great tool to see where the domain is currently pointed at. (hint: you want it pointed to your load balancer IP). If it is not, backtrack and make sure you followed all of the setup steps and contact the domain registrar.

#### Manage via Domain Registrar

Not using Ninefold to manage the domain? Easy: configure your domain registrar to point the domain (via a CNAME record) to the ninefold-apps.com url Ninefold provides in the __Overview__ tab.  

***
Note: if you do not use Ninefold to manage your domain, Ninefold Support will not be able to assist you with any issues you may have with your setup. [What's My DNS](https://www.whatsmydns.net/) will still be your troubleshooting buddy.
***
