# adguard-safari-settings

My recommendations for the ultimate configuration of AdGuard on Safari on macOS :)

**NOTE:** This is specifically tailored for AdGuard on Safari on macOS. For Safari on iOS, see [here](https://codeberg.org/Magnesium1062/adguard-safari-settings-ios).

# General

**Launch AdGuard for Safari at Login** -> ✅ *(I personally don't enable this since I only rarely use Safari and would rather not have it run in the background if not needed, but if you do use Safari as your main browser, I would recommend enabling this)*

**Notify for extension updates** -> ✅

**Update interval** -> `Every hour` *(If this causes you any issues, you can go down to `Every 6 hours`)*

**Allow search ads and the self-promotion of websites** -> ❌

**Verbose logging** -> ❌ *(Should be default)*

# Filters

**User rules** -> ✅

User rules:

This is where it can really depend on you and your set-up. I'll provide my recommendations and filters here I myself use below:

First, I would highly recommend setting the following to protect against [IDN Homograph attacks](https://wikipedia.org/wiki/IDN_homograph_attack) *You don't need to set this if your DNS provider already provides IDN Homograph Attacks Protection (i.e. NextDNS)*:

`xn--*`

`xn--*$doc,popup,frame`

I usually also set the following to always enforce blocking Google's Doubleclick & Google Analytics: ((Why?)[https://github.com/gorhill/uBlock/wiki/Privacy-stuff])

`||doubleclick.net^$important`

`||google-analytics.com^$important`

Additionally, I set the following to block social media tracking on websites:

`||facebook.com^$important,third-party`

`||facebook.net^$important,third-party`

`||linkedin.com^$important,third-party`

`||instagram.com^$important,third-party`

`||tiktok.com^$important,third-party`

I also set this to block [tracking from Gravatar](https://github.com/gorhill/uBlock/wiki/Privacy-stuff):

`||gravatar.com^$important,third-party`

I also set these rules to block 3rd party sign-in prompts from Google & Apple, as they're 1: annoying and 2: a tracking concern:

`||accounts.google.com^$third-party`

`||appleid.apple.com^$third-party`

`||appleid.cdn-apple.com^$third-party`

`@@||accounts.google.com^$domain=youtube.com|chromium.org|gstatic.com|googleusercontent.com`

`@@||appleid.apple.com^$domain=appleid.cdn-apple.com`

`@@||appleid.cdn-apple.com^$domain=appleid.apple.com`

Finally, I usually set the following to block the annoying banner on Old Reddit promoting Reddit's new UI.

`www.reddit.com###redesign-beta-optin-btn`

`old.reddit.com###redesign-beta-optin-btn`

Once you are done here, make sure to select **Save**.

Now, here's where it gets fun, to the lists. I would generally recommend enabling most of the built-in filters, besides those under the `Language-specific` category & some of those under the `Other` category. These are all extremely carefully picked lists with strong coverage and minimal breakage, and I would recommend enabling them as follows for the best coverage possible.

**Ad Blocking** -> ✅

Ad Blocking:

**EasyList** -> ✅

**AdGuard Mobile Ads filter** -> ✅

**AdGuard Base filter** -> ✅


**Privacy** -> ✅

Privacy:

**AdGuard Tracking Protection filter** -> ✅

**EasyPrivacy** -> ✅

**Peter Lowe's Blocklist** -> ✅

**Fanboy's Anti-Facebook List** -> ✅

**Fanboy's Anti-thirdparty Fonts** -> ❌ *(See `Custom` below, we're going to use a different list instead for this functionality)*


**Social Widgets** -> ✅

Social Widgets:

**Fanboy's Social Blocking List** -> ✅

**AdGuard Social Media filter** -> ✅


**Annoyances** -> ✅

Annoyances:

**EasyList Cookie List** -> ✅

**Fanboy's Annoyances** -> ✅

**AdGuard Widgets filter** -> ✅

**AdGuard Other Annoyances filter** -> ✅

**AdGuard Mobile App Banners filter** -> ✅

**AdGuard Popups filter** -> ✅

**AdGuard Cookie Notices filter** -> ✅

**AdGuard Annoyances filter** -> ✅

**Adblock Warning Removal List** -> ✅

**Dandelion Sprout's Annoyances List** -> ✅


**Security** -> ✅

Security:

**Online Malicious URL Blocklist** -> ✅


**Other** -> ✅

Other:

**AdGuard DNS filter** -> ✅ *(Only enable this if you don't also have DNS content blocking with this list enabled in place, otherwise keep disabled)*


**Custom** -> ✅

Custom:

**NOTE:** Due to unfortunate limitations from Apple, we can only add up to 150,000 rules here. This means we have to be careful with what we add, which is why you'll see some smaller & more optimized lists here vs. more comprehensive protection like I usually recommend. This is also a great example of one of the many reasons why it's important to have a good DNS content blocker (see `Additional recommendations` below), so we don't have to rely on the extension when unnecessary. 

I would recommend adding the following custom filters:

* ⭐️ Divested Fingerprinting Blocklist: `https://codeberg.org/divested/dnsbl/raw/branch/master/Fingerprinting.ubl`

* ⭐️ pfBlockerNG MS-1: `https://gist.githubusercontent.com/BBcan177/bf29d47ea04391cb3eb0/raw/7290e0681bcd07415420b5c80a253652fd13f840/MS-1`(Even if you use this list in i.e. AdGuard Home, you should also apply it here for an extra level of protection from these IPs outside of just the DNS level)

* ⭐️ Yokoffing's `Block third party fonts` - `https://raw.githubusercontent.com/yokoffing/filterlists/main/block_third_party_fonts.txt`

Additionally, if you don't have a DNS content blocking solution in place *(you should)*, or you just can't use the relevant list on your DNS blocker, you should import the following:

⭐️ Amnesty International Investigations Blocklist - `https://codeberg.org/divested/dnsbl/raw/branch/master/Amnesty.txt`

⭐️ Dandelion Sprout's Anti-Malware List: `https://raw.githubusercontent.com/DandelionSprout/adfilt/master/Dandelion%20Sprout's%20Anti-Malware%20List.txt`

⭐️ Disconnect Blocklist - `https://codeberg.org/divested/dnsbl/raw/branch/master/Disconnect.txt`

⭐️ HaGeZi's Badware Host Blocking: `https://gitlab.com/hagezi/mirror/-/raw/main/dns-blocklists/adblock/hoster.txt`

⭐️ HaGeZi's Dynamic DNS Blocking: `https://gitlab.com/hagezi/mirror/-/raw/main/dns-blocklists/adblock/dyndns.txt`

⭐️ HaGeZi's Most Abused TLDs: `https://gitlab.com/hagezi/mirror/-/raw/main/dns-blocklists/adblock/spam-tlds.txt`

⭐️ HaGeZi's Multi PRO++ mini: `https://gitlab.com/hagezi/mirror/-/raw/main/dns-blocklists/adblock/pro.plus.mini.txt`

⭐️ HaGeZi's Pop-Up Ads: `https://gitlab.com/hagezi/mirror/-/raw/main/dns-blocklists/adblock/popupads.txt`

⭐️ OISD - Small: `https://small.oisd.nl`

Additionally, if you're fine with a little breakage, I would highly recommend:

⭐️ HaGeZi's Multi **Ultimate** mini instead of HaGeZi's Multi **Pro++** mini: `https://gitlab.com/hagezi/mirror/-/raw/main/dns-blocklists/adblock/ultimate.mini.txt`

# Additional recommendations

* Follow my recommendations for Safari [here](https://codeberg.org/Magnesium1062/better-safari-macos).

* Use a private, secure, & reputable DNS provider of your choice. I would recommend setting up your own [NextDNS](https://nextdns.io/) configuration if you are able to (See my recommendations for NextDNS [here](https://codeberg.org/Magnesium1062/nextdns-settings)), otherwise I would recommend [Quad9](https://quad9.net/): `https://dns.quad9.net/dns-query`.

* Enable [Lockdown Mode](https://support.apple.com/105120).

* Enable Safari's [Fraudulent Website Warning](https://www.apple.com/legal/privacy/data/en/safari/).

* Use a (reputable) VPN. I would recommend either [Mullvad](https://mullvad.net/) or [ProtonVPN](https://protonvpn.com/).