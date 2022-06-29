# dyndns-onion
Dynamic DNS server that serves Tor's onion like domains

## Idea
Hello the Tor Community,

I have a proposition to build a DynDNS server that will host
onion-like addresses for regular websites. And I'll appreciate any
feedback, opinions and thoughts on this.

I am working on a YurtPage which is a small home page server and kind
of light version of NextCloud for inexperienced users.
Some users already have an IP static or dynamic so their site can be
directly accessed from the Internet.
But still they need a domain to be independent from IP changes.
Unfortunately domains are controlled by the DNS mafia and they cost
money.
The NameCoin's .bit domains are cool but they cost money too.

So for users I'll implement a Dynamic DNS (DynDNS) so that they'll
automatically receive a subdomain of mine's jkl.mn site like
SomeonesYurt.jkl.mn
And the user's homepage will send ping to jkl.mn so it can detect the
public IP and update a DNS record.

The problem is that I don't want to have a responsibility to host the
DynDNS service. I may forget to renew its domain or hosting, or its
server dies or I may die.
And I decided to generate an onion-like address so they'll look like
http://jklmnyiyjnwfc6aklubg45o4hbkvz5uu47hcwjinbihi4shcucq5aiid.jkl.mn/

I see a few advantages:
* In case the jkl.mn disappears users may install a Tor Onion Service
and visitors can still open the site by replacing jkl.mn to .onion in
links. I'm going to install the Tor Service by default.
* I don't need to store a database: a homepage may just sign its
request with a private key and the DynDNS can check it and update a
DNS record.
* Yes, the address is not possible to remember but anyone can save a
bookmark or use google to find it. Instead I'll not have
cybersquatters who took all the good domains. Anyone can buy a domain
and use CNAME if they wish.

What do you think about this idea? Will it work?
I created a project to develop it
https://github.com/yurt-page/dyndns-onion but decided to consult with
you first.

To go further I think that the remaining problems may also be solved easily.

Volontiers may start their own DynDNS servers and exchange the records
with each other.
The homepage sends a Ticket to any DynDNS server. The Ticket is just
an encrypted IP and timestamp and anybody can decrypt it with the
public key from the domain. The ticket with last time is considered as
actual and every DynDNS server may return its IP.
Here may be used other technologies like DHT for a quicker lookup and
to be independent if the jkl.mn domain disappears.
Similarly to a .bit TLD we may have .dyn that are free to anyone. But
unlike .onion domains the .dyn domains are not anonymous and lookups
are not blocked on DNS level and can be answered by any.
