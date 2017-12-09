# servercow-dns-api
Custom DNS API script (host [Servercow](https://servercow.de)) for [acme.sh](https://github.com/Neilpang/acme.sh)

# Prerequisites
Create a new user for the servercow DNS API inside the Servercow control center. Don't forget to check the **DNS API** on *Login and Rights*

Before the very first run you need to export your DNS API username/password. These data will be stored inside the **~/.acme.sh/account.conf** after the first run.

    export SERVERCOW_API_Username=username
    export SERVERCOW_API_Password=password

Moreover you need a CAA entry in your DNS like

   www.example.com CAA 120 0 issue "letsencrypt.org"

of your (sub)-domain(s).

# Teststage

Before issuing your productive certificates, it is a good idea to run acme.sh against the [staging server](https://letsencrypt.org/docs/staging-environment/). Simply add **--staging** to your call

    acme.sh --staging --issue --dns dns_servercow -d example.com -d www.example.com

# Usage
Copy the script dns_servercow.sh to **~/.acme.sh** or **~/.acme.sh/dnsapi**.

Then get you certificates with

    acme.sh --issue --dns dns_servercow -d example.com -d www.example.com

# Troubleshooting

If you run into any errors, you can enable the debug mode:

    acme.sh ... --debug

or even more detailed

    acme.sh ... --debug 2

If this doesn't help, try to get [help](https://github.com/jhartlep/servercow-dns-api/issues).
