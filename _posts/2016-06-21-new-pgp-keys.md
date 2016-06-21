---
layout: post
title: "Migrating to new PGP keys"
date: 2016-06-21T09:00:00:00+01:00
---

Recently, I've been reading a bit about PGP and GPG, so now that I actually know
what I'm doing, I decided to migrate to a new keychain.

As far as I know, my old keys have not been compromised, but the private keys
are stored on OneDrive (password-protected, but still, PGP is a good time to
be really paranoid ;)).



## Details about the keys
Old keychain:

```
pub   rsa4096/FD525189 2015-04-05 [SCA] [expires: 2020-04-03]
      Key fingerprint = 61F4 C465 4DE2 523A 0F72  F06F 5317 BC1B FD52 5189
sub   rsa4096/B9ACAEAE 2015-04-05 [E] [expires: 2020-04-03]
```

New keychain:

```
pub   rsa4096/5C65C3D4 2016-06-20 [C] [expires: 2017-06-20]
      Key fingerprint = 89DC 9AD7 B97F 5362 0FF5  AF16 BCC0 9F8B 5C65 C3D4
sub   rsa4096/9275C482 2016-06-20 [S] [expires: 2018-06-20]
sub   rsa4096/4037B984 2016-06-20 [A] [expires: 2018-06-20]
sub   rsa4096/8189A15D 2016-06-20 [E] [expires: 2017-06-20]
```

### How do you know it's actually *me* who is doing this?
You can find [a signed version of this post here](/assets/2016-06-21-new-pgp-keys.md.asc),
since Jekyll barfs when you try to add the PGP headers and footers around your
Markdown files. It's signed by both my old key as well as my new key. You can
also verify that the signature of the commit adding this post is my old key
([the repository is right here](https://github.com/iamarcel/iamarcel.github.io)).
GitHub will probably not show the "verified" badge once I've replaced my key there
with the new one.



## Generating these keys
My previous keys were generated using the default settings, but this time around
I took a bit more care.

The master key, `0x5C65C3D4`, is only used for certification. It was generated
on an airgapped machine running Tails, its private key is only stored on an
encrypted USB drive (not on any of my computers). This allows me to keep my
identity if my subkeys would be compromised.




## Join me in promoting good security!
Let's start using good security practices together! From now on I'm signing all
my e-mails. If you want to contact me, don't hesitate to encrypt your messages.
One day, we'll all be James Bond ;)

These articles really helped me through this journey. Hopefully you'll enjoy
them as well.

- [Alan Eliasen's excellent GPG Tutorial](https://www.futureboy.us/pgp.html)
  He walks through many of the day-to-day uses of GPG and teaches you a lot of
  good practices regarding keeping everything secure.
- [Mike English's step-by-step key generation guide](https://spin.atomicobject.com/2013/11/24/secure-gpg-keys-guide/)
  Mike gives you simple instructions to generating this kind of super-safe keys.
- The Debian Wiki entries on [Keysigning](https://wiki.debian.org/Keysigning)
  (basics of working with PGP keys),
  [AirgappedMasterKey](https://wiki.debian.org/GnuPG/AirgappedMasterKey) and
  [Subkeys](https://wiki.debian.org/Subkeys) (the subtleties of separating your
  master key from the subkeys)
