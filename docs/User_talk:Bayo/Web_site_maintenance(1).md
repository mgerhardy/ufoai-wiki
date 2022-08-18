
can't we add the po stats update to cron, too?

--[Mattn](User:Mattn "wikilink") 05:46, 21 September 2010 (UTC)


It need a little more code cause we need to MediaWiki bot to allow to
upload content (po stats result is a wiki page). Anyway i already use
this kind of robot at Wikipedia. The second point is it need a Git
update somewhere, then cron or buildbot? Here i need your help, at least
to know where we can add the script.

[Bayo](User:Bayo "wikilink") 08:39, 21 September 2010 (UTC)


We have a git checkout already - it's in my home dir on ninex

--[Mattn](User:Mattn "wikilink") 10:26, 21 September 2010 (UTC)

<!-- -->


the date format is the xml schema format, but in fact none of our news
entries uses it - imo the script should be smart enough to convert it
into the needed xml format.

--[Mattn](User:Mattn "wikilink") 05:46, 21 September 2010 (UTC)


We should use a full datetime for the content. Cause if we post 2
message at the same day, it will create some warnings. I understand the
date is often used as an UID (2 messages must not used the same date).

We can display it on the wiki like we want (i am waiting for MediaWiki
1.16 cause it will provide better function for that).

And sure the XML generator should understand any date format. But i code
it fast :-)

[Bayo](User:Bayo "wikilink") 08:39, 21 September 2010 (UTC)