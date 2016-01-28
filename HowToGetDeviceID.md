# Android ID #

The Market API requires a correct device ID. This page is meant to serve as a guide to how to identify that ID, but is as of yet incomplete and unverified


## On your device ##
### IMEI/MEID/ESN ###
According to [this](http://developer.android.com/reference/android/telephony/TelephonyManager.html#getDeviceId%28%29) your device ID is "the IMEI for GSM and the MEID or ESN for CDMA phones"

Worked partially for me, allowing me to browse the market but shows no Froyo apps.

DroidDrew wrote
> On a Droid you can easily get the MEID by following the steps on this link http://support.vzw.com/clc/devices/knowledge_base.html?id=26468


### market\_checkin ###
This approach requires a rooted device, but worked in my case.
Download the sqlite database
/data/data/com.google.android.gsf/databases/googlesettings.db and find the field "market\_checkin" in the "partner"-database.
This contains a protobuf that seems to be a Request-object. Paste it into the code below and run it.

```
<?php
include("../proto/protocolbuffers.inc.php");
include("../proto/market.proto.php");
$r = new Request(base64_decode("<market_checkin data>"));
echo "Your Android ID: ".$r->getContext()->getAndroidId()."<br/>";
?>
```

This seems to be working perfectly at the moment.


## In an emulated device ##