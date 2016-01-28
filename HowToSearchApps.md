# How to search for apps #
```
include("../local.php");
include("../proto/protocolbuffers.inc.php");
include("../proto/market.proto.php");
include("../Market/MarketSession.php");

$session = new MarketSession();
$session->login(GOOGLE_EMAIL, GOOGLE_PASSWD);
$session->setAndroidId(ANDROID_DEVICEID);

$ar = new AppsRequest();
$ar->setQuery("maps");
$ar->setStartIndex(0);
$ar->setEntriesCount(10);
$ar->setWithExtendedInfo(true);

$reqGroup = new Request_RequestGroup();
$reqGroup->setAppsRequest($ar);

$response = $session->execute($reqGroup);
```

The search string can be anything you normally use in the market, such as pub:<publisher name> or packages pname:<package name>

See the [official Android docs](http://developer.android.com/guide/publishing/publishing.html) for more search string info