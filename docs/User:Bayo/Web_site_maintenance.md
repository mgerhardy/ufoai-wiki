## How to rework main tab header?

- Update [MediaWiki:Sidebar](MediaWiki:Sidebar "wikilink")
- Fix `FixSelectedTab` from
  [MediaWiki:Common.js](MediaWiki:Common.js "wikilink") to select the
  right tab according to the pagename
- Update the forum skin

## How to update screenshots from news page?

- [Template:Random screenshot](Template:Random_screenshot "wikilink")

## How to update [Available translations‎](Available_translations‎ "wikilink") progress bars

- synchronize wiki data to po files (how?)
- generate wiki data with `./src/po/postatus2.sh`
- update the page [Template:Translation
  status/Data](Template:Translation_status/Data "wikilink") with the
  content of `./src/po/postatus.wiki`

<!-- -->

    cd ./src/po/
    ./postatus2.sh . ufoai.pot

## How does the feed for news work?

- [News template](Template:News "wikilink") contain `class` tag to
  identify content type.
- `getnews.sh` script read [the HTML page containing
  news](News "wikilink") and convert it to ATOM xml.

  `/home/users/mattn/atom/getnews.sh`
- Cron call `getnews.sh` every 4 hours

  `0 */4 * * * ...`
- The script [news.php](http://ufoai.ninex.info/news.php) only read the
  already computed ATOM file.

## How to add a news

- [Open the page containing news of the
  year](News/{{CURRENTYEAR}} "wikilink")
- Copy-paste the [template](Template:News "wikilink") on the top of the
  news list
- Complet it. Do not use pipe character (`|`).
  - Use the datetime format look like 2010-06-17T00:00:00

## Forum

    connect mattn;

Number of registration per days

    select DATE(FROM_UNIXTIME(dateRegistered)), count(*) from smf_members group by DATE(FROM_UNIXTIME(dateRegistered));

Number of member per IP (there is also a `memberIP2`)

    select memberIP, count(*) from smf_members group by memberIP order by count(*);

With filter:

    select SUBSTR(memberIP,1, 8), count(*) from smf_members group by SUBSTR(memberIP, 1, 8) order by count(*);

## Forum anti-spam

The forum it ATM protected against spammers with *reCAPTCHA* and *MOD
Stop Spammer* (configuration Admin/Registration/Settings). *MOD Stop
Spammer* share between web sites a list of black listed IPs/user
names/mails.

For a new registration, the default behaviour only check user email
(Admin/Members/awaiting activation). If this account is already black
listed, administration must activate the account (Admin/Members/Awaiting
approval).

About spammer:

- They wait a long time before activation there account by mail.
- They never post anything
- They use signature with URL to useless website

Then some time:

- We should clean up *Awaiting approval* list time to time (1 time a
  month)
- We should clean up/check *Awaiting activation* (1 time a day can be
  nice, cause spammer are slow)
- We should check user without post. (1 time a day/week, the harder job)
  - Check the signature
    - Ban the user/the mail (and the IP, if it create more than 1 user)
      - Delete the account (or not, cause remember the relation user-IP
        can be usefull sometime).
      - Or at least clean up the signature