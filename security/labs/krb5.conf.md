[root@ip-172-31-43-254 krb5kdc]# cat /etc/krb5.conf
[libdefaults]
default_realm = PUNEETHA.COM
dns_lookup_kdc = false
dns_lookup_realm = false
ticket_lifetime = 86400
renew_lifetime = 604800
forwardable = true
default_tgs_enctypes = aes128-cts arcfour-hmac
default_tkt_enctypes = aes128-cts arcfour-hmac
permitted_enctypes =  aes128-cts arcfour-hmac
udp_preference_limit = 1
kdc_timeout = 3000
[realms]
PUNEETHA.COM = {
kdc = ip-172-31-43-254.eu-west-3.compute.internal
admin_server = ip-172-31-43-254.eu-west-3.compute.internal
default_domain = PUNEETHA.COM
}
[domain_realm]
PUNEETHA.COM = PUNEETHA.COM

[logging]
kdc = FILE:/var/log/kdc.log
admin_server = FILE:/var/log/kadmin.log