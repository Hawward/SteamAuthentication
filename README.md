#SteamAuthenitication

SteamAuthentication is a basic set of PHP files that enable users to login using their steam account to view protected content on your website. it creates a session using their steamid as the sessionID and checks for the session when a user visits the page. It also includes a file which allows you to use their profile information such as their avatar and online status.

jQuery News is a basic [jQuery](https://github.com/jquery/jquery/) plugin that fetches headlines on a given topic from [Google News](https://news.google.com/) and puts them into the selected class as a `<li>`.

See a demo at * link coming soon - just updating my website ;) *

##Foreword

Thanks goes to:
- JTX for the original steam openid script (http://pastebin.com/6vZT4RhD)
- The LightopenID library (http://gitorious.org/lightopenid)

##To Install

Upload the `steamauth` folder.

Open up steamauth.php and change localhost to your domain
Find $api_key on line 5 and set it to the api key you got from http://steamcommunity.com/dev/apikey

Now in your file add the following:

    <?php

    require 'steamauth/steamauth.php';

    if(!isset($_SESSION['steamid'])) {

        steamlogin(); //login button
    
    }  else {
        //Protected content

        logoutbutton(); //Logout Button
    }     
    ?>
    
##Using Profile Variables

I have create a userInfo.php file which creates an array of ready to use variables that includes profile information of the steam user that has logged in:

* `$steamprofile['steamid'] = $content['response']['players'][0]['steamid'];` - The users unique SteamID
* `$steamprofile['communityvisibilitystate']` - This represents whether the profile is visible or not.
* `$steamprofile['profilestate']` - If set, indicates the user has a community profile configured (will be set to '1')
* `$steamprofile['personaname']` - Their current set profile name
* `$steamprofile['lastlogoff']` - Last time the user was online in unix time
* `$steamprofile['profileurl']` - The URL to their steam profile
* `$steamprofile['avatar']` - The image URL to the smallest size of their avatar (32px x 32px)
* `$steamprofile['avatarmedium']` - The image URL to the smallest size of their avatar (64px x 64px)
* `$steamprofile['avatarfull']` - The image URL to the smallest size of their avatar (184px x 184px)
* `$steamprofile['personastate']` - The users current state, 1 - Online, 2 - Busy, 3 - Away, 4 - Snooze, 5 - looking to trade, 6 - looking to play
* `$steamprofile['primaryclanid']` - The users primary group
* `$steamprofile['timecreated']` - When the account was created

Please note that some of these variables may be unavailable for some users as it depends on their privacy settings. 

 

