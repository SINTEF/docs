# You need a firewall

A firewall is a network system to filter incoming and outcoming network traffic. It's a security component to reduce the attack surface on your infrastructure. It's critical and must always be used and configured correctly for your infrastructures connected to the internet.

A firewall consists of rules to define what network traffic is allowed or not.

## Common firewall rules

Most network firewalls configurations are similar. You prevent all traffic by default, and you make a few exceptions.

### Allow incoming connections to your services.

The first step is to allow the incoming connections to your exposed services if you have any. For a public web server, for example, you configure rule(s) to allow incoming traffic to HTTP (TCP 80) and HTTPS (TCP 443). However, you should not expose all your services. Databases, for example, should not be exposed to the internet, and you should not add any firewall rule to allow incoming connections to them. This document contains some information about how to provide access to internal services for your users without exposing them to the internet.

### You should probably allow all outgoing connections.

Most firewalls allow all outgoing connections by default. It's very cumbersome to manage a firewall for outgoing traffic. Therefore you should focus on other security tasks if this is not one of your security requirements. Time and resources are limited, and we need to make choices. It's usually better to work on other tasks with a higher security impact than managing an egress firewall.

If preventing a machine from specific internet traffic is extremely important for your security, you should consider not connecting the machine to any network. And perhaps limiting physical access to it, but that's another topic.

### Allow incoming traffic to your administration services (SSH, Kubernetes), but not to everyone.

You need to allow incoming traffic to your administration services, such as SSH or Kubernetes. The alternative is physical access which is always safer but not very practical. However, it is *strongly recommended* to **NOT** allow all traffic. Allowing all traffic to SSH exposes your machine to constant attacks from all over the world. A properly configured SSH server should probably resist for many years, but this is an unnecessary risk. A not adequately configured SSH server may be compromised. It may also fill the system logs with information about the attacks or waste resources.

A classic solution for the neverending attacks on your SSH servers is to create firewall rules to block traffic from attackers dynamically. The software [Fail2ban](https://www.fail2ban.org/) can look at the failed SSH login attempts and create software firewall rules on the machine to block the IPs of the attackers. This work relatively well to block brute-force attacks, dictionary attacks, or not to waste too many resources or storage space, but it does not stop all kind of attacks.

You should consider allowing only a set of IP addresses or IP ranges. For example only from your work network and its VPN. If you don't have a VPN, you may want one. You do have alternative solutions such as using a relay server but a VPN is more convenient. 

## Software firewall inside a server cannot be fully trusted

Linux, Mac, Windows and other operating systems contains software firewalls. They are better than nothing, but you can fully trust them. A compromised machine can change the firewall settings, but more often the firewall may not be configured correctly.

A modern common example is [Docker that ignores the firewall rules on Linux](https://github.com/chaifeng/ufw-docker), whitout the administrators knowing about it. The often used iptables is also not the most userfriendly firewall to configure and it sometimes not doing what you want.

Therefore it is prefered to use a firewall outside the servers you manage. Cloud providers offer firewalls and you should use them. Otherwise you can use a hardware firewall or your hardware network routers may be able to do it as well.

You can always have multiple firewalls, one inside the server and one outside but that's more work and it doesn't seem necessary.


## Do not forget IPv6

The Internet Engineering Task Force (IETF) decided in the 90s that it was a good idea to have two network stacks instead of one. IPv4 and IPv6. When configuring a firewall, you must not forget that IPv6 exist. You don't want a machine with a strong IPv4 firewall but everything open without any firewall on IPv6. You will probably have to duplicate some rules and configure your firewall twice if your infrastructure supports both IPv4 and IPv6.

## Using NAT as a firewall may work, but think about UPnP

NAT is a very common tool to have a private network behind one to many public IP addresses. It's used to provide a private network not exposed to the internet, and it's also the popular solution regarding the shortage of public IPv4 addresses. A NAT will often behave like a firewall for most configurations, while it's not strictly one. Some people do not like to use NAT as firewall, but it's better than nothing. It will block all unknown incoming connections by default, and allow all outgoing traffic too. You can configure to map some services to some specific machines in the private network.

However, do consider to disable UPnP on your NAT if it has it. UPnP allows machines in the private network to configure the NAT to redirect incomming connection to them. This is a security risk if you want to prevent machines to be contacted and if you don't fully trust them. UPnP is very convenient at home, it allows you to easily share your favourite Linux ISO or to play some online multiplayer videogames without configuring your home router. But it should not be used in professional secure environments.

## Firewalls between the servers inside your infrastructure

You may want a firewall configured precisely between the servers inside your infrastructure. This may be a lot of work and it's perhaps not worth the hashle. The usual firewall solutions are to allow and trust every network connection inside the infrastructure, or to consider all the other machines as untrusted machines from the internet.

If you feel that you a need of precise network access control inside your infrastructure, instead of writing and maintaining many firewall rules, consider using [Kubernetes' Network Policies](https://kubernetes.io/docs/concepts/services-networking/network-policies/) (and a Kubernetes network plugin supporting them of course). If you are not using Kubernetes, it's perhaps time to use it.

## Allowing access to specific services and specific users

A common use case is to allow access to a specific service to a specific user. For example you have a PostGreSQL database running in your infrastructure and you want to allow someone to use it from its laptop. You have a few options for that. I would recommend not configuring any firewall and using other systems to access the service from an user. It's safer to not update a firewall very often, so you can review and trust its configuration.

### Allow the service to a specific IP address or IP range in the firewall.

Try to not do that. You should consider the other solutions.

### VPN inside the infrastructure

You may create a VPN inside your infrastructure and trust it in the firewall. For example everyone connected to the VPN could access anything allowed from the VPN IP addresses / IP range. You can deploy a VPN or use a cloud provider VPN on the private network.

If you want strict network rules on your VPN, you can configure it to have a static IP per user and write and maintain firewall rules for the IP. But it's maybe better to  consider another solution.

### Port-forwarding using SSH

Port forwarding, also called tunnels, can be done using SSH. It's an alternative to the VPN and is often enabled by default on SSH. The user connects first to SSH and then to the service she wants to access. The SSH server will forward the connection to the service. This can be disabled in the SSH server if you don't want it.

### Port-forwarding using Kubernetes

If your system uses Kubernetes, port-forwarding is the prefered and simplest way to allow your users to access the services not exposed to the internet. You can use the role based access control (RBAC) from Kubernetes.

### Enterprise remote access to your protected services

If you like complexity and over engineering, you have tools allowing very secure, controlled, and audited access to your services. This is much better than playing with firewall rules.

For example at the time of writing this document you have the following tools:

 - [StrongDM](https://www.strongdm.com)
 - [Teleport](https://www.teleport.com)
 - [Boundary](https://www.boundaryproject.io/)


# Conclusion

Firewall are critical to the security of your infrastructure. You should be careful to configure them correctly. You should not forget IPv6.

*And this conclusion was written by an AI (GitHub Copilot).*