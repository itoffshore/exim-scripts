# exim-scripts
Security shell scripts for Exim mail server

`exim_gencert` 

* Debian's `exim-gencert` patched for use with `ASH` Shell in Busybox. 

* By default certificates are generated with `4096 bit` encryption / 3 year duration.

____________________________________

`exim_genpass` 

* generate & optionally store in a file `SHA-512` password hashes. 

* For the strongest possible hashes install `python-passlib` or `mkpasswd` from Debian (`debian-mkpasswd` in Arch / `mkpasswd` in Alpine) & configure the number of `ROUNDS` up to `999,999,999`. By default `ROUNDS` are `1,250,000` (compared to the `SHA-512` default implementation of `5000 ROUNDS`). 
```
exim_genpass: Generate SHA512 hashed passwords [ in /etc/exim/passwd ]

Usage: exim_genpass [OPTIONS]
	[ -n ] : Don't update file; display results on stdout.
	[ -f ] : Write username:passwd to a different file. (default: /etc/exim/passwd)
	[ -r ] : use the specified NUMBER of rounds (Debian mkpasswd / Python passlib() only => default: 1250000)
					   (Busybox mkpasswd / Python crypt() / Perl crypt() => 5000 rounds)
	[ -h ] : this help message.

Examples:
 exim_genpass		(Update /etc/exim/passwd => username:passwd)
 exim_genpass -f file	(Update file => username:passwd)
 exim_genpass -n	(Don't update /etc/exim/passwd: display results on stdout)
```
Both scripts can also be found in `exim-utils` in [Alpine Linux](https://alpinelinux.org/).
