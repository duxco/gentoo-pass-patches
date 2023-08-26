# pass-patches

```
  _______________________________________________
/ This repo has been archived!                    \
| Its successor is at:                            |
\ https://codeberg.org/duxsco/gentoo-pass-patches /
  -----------------------------------------------
         \   ^__^
          \  (oo)\_______
             (__)\       )\/\
                 ||----w |
                 ||     ||
```

The .patch files contain my customisations to [pass](https://www.passwordstore.org/):

  - `00_use_dev_random.patch`: Make sure that you have enough entropy with tools like [sys-apps/rng-tools](https://packages.gentoo.org/packages/sys-apps/rng-tools).
  - `01_kill_gpg_agent.patch`: I like to always get asked for my passphrase (no caching).
  - `02_limit-patterns-printed.patch`: Just print the informationen you really want to have.
  - `03_clear_clipboard_after_use.patch`: I like to have a "sane" clipboard.

I use these patches via Gentoo's [/etc/portage/patches](https://wiki.gentoo.org/wiki//etc/portage/patches):

```
$ ls -1 /etc/portage/patches/app-admin/pass-1.7.4/
00_use_dev_random.patch
01_kill_gpg_agent.patch
02_limit-patterns-printed.patch
03_clear_clipboard_after_use.patch
```

Result:

```
$ sudo -i emerge app-admin/pass
Password:
Calculating dependencies... done!
>>> Verifying ebuild manifests
>>> Emerging (1 of 1) app-admin/pass-1.7.4::gentoo
>>> Installing (1 of 1) app-admin/pass-1.7.4::gentoo
>>> Jobs: 1 of 1 complete                           Load avg: 1.82, 1.62, 1.55

 * Messages for package app-admin/pass-1.7.4:

 * User patches applied.
>>> Auto-cleaning packages...

>>> No outdated packages were found on your system.

 * GNU info directory index is up-to-date.
```

Currently, I only print out these entries:

```
$ cat ~/.password-store_limit-patterns-printed.txt
^email:
^e-mail:
^user:
^username:
^vrnetkey:
^vr-netkey:
```

Example:

```
$ pass show -c shop/amazon.de/prime
Username: user@example.org

Copied shop/amazon.de/prime to clipboard. Will clear in 10 seconds.

Waiting for gpg-agent to stop... stopped!
```

## Other Gentoo Linux repos

https://github.com/duxsco?tab=repositories&q=gentoo-
