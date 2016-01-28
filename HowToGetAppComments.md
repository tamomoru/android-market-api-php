# How to get app comments #

```
$commentsRequest = new CommentsRequest();
$commentsRequest->setAppId("7274788888064689970"); //Google Maps App ID
$commentsRequest->setEntriesCount(3);

$reqGroup = new Request_RequestGroup();
$reqGroup->setCommentsRequest($commentsRequest);

$response = $session->execute($reqGroup);
```