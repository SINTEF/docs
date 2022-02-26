# Which Linux distribution should you use?

A Linux distribution is an operating system containing the Linux kernel, some software tools, and often software packages. [There are many Linux distributions](https://en.wikipedia.org/wiki/List_of_Linux_distributions), and choosing the right one can be challenging.

The perfect Linux distribution for every use case does not exist yet, but you have a few good and safe options. Your needs are different if you want to run Linux on your laptop, servers, IoT devices, or software containers.

This guide presents a few Linux distributions with my experiences and opinions. It is not a neutral and fully unbiased guide. However, it can help you choose the proper Linux distribution for your use case.

## Use [Ubuntu](https://www.ubuntu.com/)

Ubuntu can be your default choice. It is popular, easy to use, and is a high-quality Linux distribution. You can always find help and support. It's excellent for almost all use cases, from IoT to desktops to servers.

It is not the most advanced of hipster Linux distribution, but it is, in my opinion, the best in most cases. A few people complain about the snap feature and recommend against Ubuntu because of it. I still recommend Ubuntu because it does not force you to use the snaps. I never used them.

A new version is released every 6 months, and the long term support (LTS) version is released every 2 years in April. You should use the LTS version on servers and the latest and greatest on desktop. LTS versions are a bit duller, but they are more stable than the non-LTS versions. The software is not as leading-edge. You want stable operating systems on your servers. The Ubuntu schedule is, in my opinion, a good compromise between stable software and recent software. 

## [Debian](https://www.debian.org/)

Debian is one of the oldest and best Linux distributions. If you use Ubuntu, which is based on Debian, you already use many Debian tools. Debian is more stable than Ubuntu. The software versions are often older. New releases are published when ready, usually every two years, and not based on fixed deadlines. Debian on a desktop is perhaps slightly more difficult to use than Ubuntu.

I use Ubuntu rather than Debian, but it is a good alternative. It's also the best distribution if you plan to install it on a server and only do security updates for many years.

Unlike Ubuntu, Debian is a community-supported nonprofit project. You can contribute to Debian financially or with your expertise.

## [ArchLinux](https://www.archlinux.org/)

ArchLinux is an excellent distribution for people who love Linux system administration. You probably already know about ArchLinux if you are one of them. If you are not, ArchLinux is presumably not something you will enjoy.

The ArchLinux documentation is excellent, and the community is very active. But it isn't easy to use for beginners and not necessarily stable. ArchLinux uses a rolling release approach. You don't have big releases once in a while, but continuous new versions of the various software packages. Some updates can potentially break your system. You have to read the documentation and be careful. It's part of the experience.

You should probably not use ArchLinux on servers or software containers.

## [Alpine Linux](https://www.alpinelinux.org/)

Alpine Linux is a distribution designed for resource efficiency and simplicity. It's tiny, around 8MB. But it works well, and it is becoming more and more popular for software containers, where the distribution size matters more.

However, it is different from most Linux distributions because it uses a different libc, a critical software component. It is musl and not glibc like almost everywhere else. It also uses Busybox instead of Bash and the GNU core utilities. These alternatives are smaller. In practice, it means that you may experience some bugs or incompatibilities because not all developers test their software in this kind of environment.

The bugs are usually not from Alpine, but the differences in Alpine can highlight bugs in the software you run on it. As the popularity of Alpine goes higher, it's increasingly rare to find software bugs. Still, I would consider it a more risky choice than Debian or Ubuntu.

I use it for my software container images. However, I switch to Debian or Ubuntu if the software I want to run is not very popular. I don't always want to be the first to discover bugs related to a different libc or Unix command.

## [Fedora](https://getfedora.org/)

Fedora is RedHat's free and leading-edge distribution. It is good, but not something I would recommend unless you love RedHat's work. It is not stable enough for servers; the software is too leading edge. You may be one of the first to find the bugs. And for desktop, I would instead use Ubuntu or ArchLinux, depending on my love of Linux system administration.

### [RedHat Enterprise Linux (RHEL)](https://www.redhat.com/en/technologies/linux-platforms/enterprise-linux)

RedHat Enterprise Linux is similar to Fedora. It uses Fedora as a source, but it's stable, adapted for servers, with paid support, and has a good reputation.

I never installed it myself because it's not free and relatively expensive. In my opinion, it's more a distribution that you are forced to use than something you chose deliberately. If you are reading this document and you are not in a meeting with RedHat, there is a high chance that RHEL is not your best option.

## [OpenSuse](https://www.opensuse.org/)

OpenSuse is a good distribution that I would use if Debian and Ubuntu did not exist. I prefer the Debian tools over the SUSE tools, but it's personal tastes. I also think you can find more documentation and tutorials online for Debian than Opensuse. Unlike Fedora, OpenSuse offers long term support versions (LTS) that are good choices for servers and software containers.

### [Suse Linux Enterprise Server (SLES)](https://www.suse.com/products/server/)

Suse offers a commercial version with support like RedHat with RHEL. Like RHEL, I'm not interested in commercial support for my Linux distributions. Still, it is an alternative to RedHat Enterprise Linux if you need professional support and your budget allows it.

## [NixOS](https://nixos.org/)

NixOS is a relatively confidential Linux distribution but with great concepts. It provides reproducible and reliable builds, where software packages work everywhere and cannot break other packages. It also has a declarative domain-specific language (DSL) to configure the packages and your system.

Unfortunately, it is more difficult for most people. The domain-specific language is a hit or miss, and everything is very different from other distributions. In my opinion, it's an intriguing distribution but not something I want to use on my machines.

Try NixOS if you seek an intellectual challenge but use other distributions for critical tasks. Otherwise, you can also explore the same concepts using more conventional tools.

## [Gentoo](https://www.gentoo.org/)

Gentoo is a distribution for people who love to play with Linux distributions. To configure anything to the lowest details, to build something. It's targetting the same kind of user as ArchLinux and is a good alternative. The documentation is excellent, and you can learn a lot about Linux distributions by using it.

One main difference compared to ArchLinux is that Gentoo does not provide pre-compiled and ready to use software packages. Your machines must compile them first, allowing a higher degree of personalisation. However, it can take much time, so Gentoo has a few exceptions for packages that are very slow to compile, such as web browsers.

It is applicable for servers, but I would not recommend it instead of Debian or Ubuntu.

## [Linux from scratch (LFS)](https://www.linuxfromscratch.org/)

Suppose you have much free time and ArchLinux or Gentoo are too easy for you. In that case, Linux from scratch (LFS) is a guide that teaches you about building a Linux distribution from scratch.

It is not something you should use on servers or at work, but it should be a didactic experience. I never took the time to do it.

## The others

 - [Linux Mint](https://linuxmint.com/): It's based on Ubuntu. It's good but without significant reasons to prefer it over Ubuntu.
 - [Devuan](https://www.devuan.org/): It's a Debian but without SystemD, a critical software component. SystemD replaced a lot of existing tools and conventions, which made a few people very upset. I think SystemD is good even though it's not perfect. Don't avoid SystemD, and prefer Debian over Devuan.
 - [Manjaro](https://manjaro.org/): It's also good distribution that it is a simpler ArchLinux for beginners, on desktops and laptops. It is an alternative to Ubuntu for desktops and laptops. However, Manjaro is not as versatile as Ubuntu because you cannot use it on software containers, IoT devices, or servers. If you have to learn one single Linux distribution, it's perhaps not the best choice.
 - [CentOS](https://www.centos.org/): It is discontinued.
 - [Slackware](https://www.slackware.com/): A single person has managed it for almost 30 years, which is admirable. But what happens if the person stops working on it? This distribution choice is risky. Some people have nostalgia about Slackware, but I also think that ArchLinux, Gentoo, or LFS are better alternatives nowadays.
 - [Amazon Linux 2](https://aws.amazon.com/amazon-linux-2/): Amazon's RHEL alternative for AWS. But be careful of vendor lock-ins. Avoid them when you can, and prefer other distributions.

Your favourite Linux distribution is perhaps not on this list. You are free to use the distribution you prefer if you are the only user. However, you should consider using a distribution from this list if you maintain infrastructures at work. It would be best if you chose a Linux distribution that is popular, well documented, with a good reputation, and that has been around for a while. It is crucial if you are not alone working on the infrastructure.

# Conclusion

You should probably use Ubuntu by default. Use Debian for stable long-term deployments. Use Alpine if you want tiny software containers with compatible software. And use ArchLinux if you love Linux system administration.

Other distributions are not necessarily bad choices, but you need to weigh the pros and cons and decide if it's worth using something different. If you are not sure, you can spend time testing a few distributions and see how they work for you and your projects.