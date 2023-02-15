# Goggles

Goggles enable anyone, be it individuals or a community, to alter the ranking of Brave search by using a set of instructions (rules and filters). Anyone can create, apply, or extend a Goggle. Essentially Goggles act as a custom re-ranking on top of Brave’s search index.

[Quickstart](https://github.com/brave/goggles-quickstart)

[Getting started](https://github.com/brave/goggles-quickstart/blob/main/getting-started.md)

[Submit goggle](https://search.brave.com/goggles/create)

[Update goggle](https://github.com/brave/goggles-quickstart/blob/main/getting-started.md#updating-a-goggle)

[Delete goggle](https://github.com/brave/goggles-quickstart/blob/main/getting-started.md#deleting-a-goggle)

## Create a Goggle

More detailed goggle can be found [here](https://github.com/brave/goggles-quickstart/blob/main/goggles/quickstart.goggle)

```text
! name: My Goggle
! description: What my Goggle does
! public: false
! author: Me
! avatar: #2196F3

! Remove all results from site alltodev.com
$discard,site=alltodev.com

! Remove all results from site pinterestcareers.com and instagram.com
$discard,site=pinterestcareers.com
/pinterest/$discard,site=instagram.com

! Boost all results from site community.brave.com
$site=community.brave.com,boost=2

! Remove results not matching any other rule
$discard

! Generic boosting
*rust*$boost=1,site=rs
*rust*$boost,site=github.com
*rust*$boost,site=stackoverflow.com

! Boost some results
$boost=3,site=async.rs
*rust*$boost=2,site=github.com
/coreutils^$boost=3

! Downrank some results
$downrank,site=medium.com

! Conflicting rules
$downrank=3,site=example.com
/posts/$boost=3
! In the above example, both would match on the URL https://example.com/posts/hello.html.
```
