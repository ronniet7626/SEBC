[root@ip-172-31-43-254 krb5kdc]# kinit ronniet7626
Password for ronniet7626@PUNEETHA.COM:
[root@ip-172-31-43-254 krb5kdc]# klist
Ticket cache: FILE:/tmp/krb5cc_0
Default principal: ronniet7626@PUNEETHA.COM

Valid starting       Expires              Service principal
10/18/2018 09:15:02  10/19/2018 09:15:02  krbtgt/PUNEETHA.COM@PUNEETHA.COM
[root@ip-172-31-43-254 krb5kdc]# klist -e
Ticket cache: FILE:/tmp/krb5cc_0
Default principal: ronniet7626@PUNEETHA.COM

Valid starting       Expires              Service principal
10/18/2018 09:15:02  10/19/2018 09:15:02  krbtgt/PUNEETHA.COM@PUNEETHA.COM
	Etype (skey, tkt): aes128-cts-hmac-sha1-96, aes128-cts-hmac-sha1-96