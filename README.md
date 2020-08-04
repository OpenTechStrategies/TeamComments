# Extension:TeamComments

The TeamComments extension adds the <teamcomments /> parser hook tag to allow commenting on articles where the tag is present.

This extension was forked from
[the mediawiki Comments extension](https://www.mediawiki.org/wiki/Extension:Comments)
and then updated to be more visually streamlined, but with more
 authorization controls.  Those include, but aren't limited to:

* UI Updates
* Global on/off switch
* Viewing authorization
* Removal of scoring, profile picture, voting, ignoring
* Adding more nesting

## Installation

* Download and place the file(s) in a directory called TeamComments in your extensions/ folder.
* Add the following code at the bottom of your LocalSettings.php:

```
wfLoadExtension('TeamComments');
```

* Run the update script which will automatically create the necessary database tables that this extension needs.
* Navigate to Special:Version on your wiki to verify that the extension is successfully installed.

## Usage

* `<teamcomments />` - place wherever on a page (usually the bottom) that you want the comments section to appear

User rights

This extension adds three new user rights:

* `teamcomment` (which allows posting comments)
* `teamcommentlinks` (which allows posting external links in comments)
* `teamcommentadmin` (which allows deleting user-posted comments), e.g.
* `teamcommentseeusernames` (which allows seeing usernames on comments, defaults to true)

```
$wgGroupPermissions['sysop']['commentadmin'] = true;
```

Only logged in users can post comments.

## Parameters

* `$wgTeamCommentsEnabled` - Whether the system is enabled on a global scale.  Provided so comments can be turned off while keeping the tags in pages
* `$wgCommentsInRecentChanges` - by default, this variable is set to false. Set it to true to display comments log entries in Special:RecentChanges, too, in addition to the comments log at Special:Log/comments.
* `$wgTeamCommentsCheatSheetLocation` - by default, this variable is set to false.  Set it to a location to have a a link in the comments section to a user specified cheat sheet
* `$wgTeamCommentsUserPseudonymizer` - by default, this is false.  Set it to a callback that takes a username and returns a string, for overriding the anonymous user text that's outputed if `teamcommentseeusernames` is false

## Special Page

The extension adds a special page "Special:TeamCommentsList" that displays
all the comments in the entire system, grouped by the page they are commenting
on.  This is ordered by page, with the top being the most recently commented
on page.

## Logging

TeamComments adds a new logging type, "teamcomments" where it logs actions
taken in the TeamComments extension.  That can be viewed through the normal
logging utility at "Special:Log"

## Internationalization

The TeamComments extension inherited (partial or full) support for 68 different languages from the Comments Extesion, including English.
