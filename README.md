# how to add a Telegram bot as admin in a group using the Telegram Bot API with a bot token in php

Sure, here's an example in PHP on how to add a Telegram bot as admin in a group using the Telegram Bot API with a bot token:

```
<?php
// Replace YOUR_BOT_TOKEN and YOUR_GROUP_CHAT_ID with your bot token and group chat ID
$botToken = 'YOUR_BOT_TOKEN';
$groupChatId = 'YOUR_GROUP_CHAT_ID';
$botUserId = 'YOUR_BOT_USER_ID'; // Usually the same as the bot token without the "bot" prefix
```
```
// Set up the request URL and parameters
$url = "https://api.telegram.org/bot$botToken/promoteChatMember";
$params = array(
    'chat_id' => $groupChatId,
    'user_id' => $botUserId,
    'can_change_info' => true,
    'can_delete_messages' => true,
    'can_invite_users' => true,
    'can_restrict_members' => true,
    'can_pin_messages' => true,
    'can_promote_members' => false,
);
```
```
// Send the request to the Telegram Bot API
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, $url);
curl_setopt($ch, CURLOPT_POSTFIELDS, $params);
curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
$response = curl_exec($ch);
curl_close($ch);

// Output the API response
echo $response;
?>


```
This code uses the cURL library to send a POST request to the Telegram Bot API's "promoteChatMember" method with the necessary parameters to make the bot an admin of the specified group chat. It sets all available permissions except for the ability to promote other members to admins. You can adjust the parameters based on the permissions you want to grant the bot.
