WhatsOn - WhatsApp wrapper in Python
====================================

```
Usage: python /home/blacklight/local/bin/whatsapp <-n [phone number]> <-i [phone imei]> <-u [jabber username]> <-p [jabber password]> <-f [jabber forwardTo contact]>
	-n      The phone number associated to your WhatsApp account, country code included, without leading + or 0, i.e. 393471234567
	-i      The IMEI of your mobile, for Nokia/Android/Blackberry devices, or the MAC address, for iPhone
	-u      The Jabber/GTalk/XMPP username that will forward the requests to your primary Jabber/GTalk/XMPP, you can get one easily at jabber.org
	-p      The password for your Jabber/GTalk/XMPP account
	-f      Your personal Jabber/GTalk/XMPP account, that is the one you want the received WhatsApp messages to be forwarded
```

How it works?
-------------

* Once started with all the options, a fifo named ~/.whatsapp/whatsapp.fifo will be created
* All the received messages on your WhatsApp account will be forwarded by your Jabber bot (see -u option) to the Jabber account you specified (see -f option). That is usually your personal account. The receipts of the received messages and the typing notices will be forwarded as well
* All the activity will be logged to ~/.whatsapp/whatsapp.log
* If you want to send a message to a contact, just write recipient and message to the fifo pipe. Example:

```bash
$ echo "To: 393471234567" > ~/.whatsapp/whatsapp.fifo
$ echo "Hey dude, how you doing?" > ~/.whatsapp/whatsapp.fifo
$ echo "What about tonight?" > ~/.whatsapp/whatsapp.fifo
```

* The received and sent messages, receipts and contacts will be also saved to the SQLite database ~/.whatsapp/whatsapp.db

