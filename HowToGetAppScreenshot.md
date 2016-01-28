# How to get app screenshots #
```
$gir = new GetImageRequest();
$gir->setImageUsage(GetImageRequest_AppImageUsage::SCREENSHOT);
$gir->setAppId("7059973813889603239");
$gir->setImageId(1);


$reqGroup = new Request_RequestGroup();
$reqGroup->setImageRequest($gir);
$response = $session->execute($reqGroup);

$groups = $response->getResponsegroupArray();
foreach ($groups as $rg) {
	$imageResponse = $rg->getImageResponse();
	file_put_contents("../".$appId."_".$imageId.".png", $imageResponse->getImageData());

	?><img src="../<?= $appId."_".$imageId.".png"; ?>"><?
}
```

_Need to add explainations for setImageId - splitfeed_