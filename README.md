# btlabs-inat-tools - iNaturalist user tools

This is a collection of tools for iNaturalist users.

- A Bluff Trail Labs production (https://btlabs.ca/).

## topinat - Tool to report an iNaturalist user's top days

### Description:

Counts the days with most observations and longest streak of days with
observations for the specified user.

Based on a prototype that was discussed and improved on iNaturalist
Discord (invite link: https://discord.gg/kHAUzVR) shortly after the
City Nature Challenge 2019 had finished.

### Prerequisites:

A command shell with bash, ruby, and curl in the PATH.

### Usage:

```
$ ./bin/topinat <userid>
```

### Example:

```
$ ./bin/topinat benarmstrong
benarmstrong: 2015-05-22 - 2019-05-11 (1451 days)
  Top 5 days:
     166 observations (2018-07-27)
     138 observations (2019-04-28)
      99 observations (2017-09-17)
      95 observations (2019-04-26)
      91 observations (2018-07-11)
  Top 5 streaks:
     6 days (2017-09-12 - 2017-09-17)
     5 days (2018-09-01 - 2018-09-05)
     5 days (2018-08-26 - 2018-08-30)
     5 days (2018-06-09 - 2018-06-13)
     4 days (2019-05-08 - 2019-05-11)
```

### Development notes:

- iNaturalist API doc for observations histogram at:
  - http://api.inaturalist.org/v1/docs/#!/Observations/get_observations_histogram

### TODO:
  - merge both histograms to find longest created_on or observed_on streak
    - i.e. append &date_field=created_on to URL to return created_on histogram
  - count how many identifications a user made on one day & merge that, too
  - tidier output

### Similar software:

Isn't it nice to have choices? There is other software available to
dig user activity statistics out of the iNaturalist database,
inspiring users to out-compete themselves and others in the iNat
community.

If *topinat* isn't for you, maybe one of these will suit you better:

- **inat-streak** *web app based on the idea for topinat*
    - Webapp site at:
        - https://mapsandapps.github.io/inat-streak/
    - *inat-streak*  vs. *topinat*:
        - *inat-streak* was written and hosted on @mapsandapps's own
          site to give iNat users a convenient way to check their
          longest iNat observations streaks on the web instead of the
          commandline like *topinat*
        - *inat-streak* is original code that shares no common code
          with *topinat*, but we have benefitted from discussion with
          each other, borrowing each other's ideas liberally to
          improve the two tools in parallel.
- **inat-days** *tool to report top users by streaks of days with iNaturalist activity*
    - Development site at:
        - See https://github.com/kueda/inat-days
    - Comparison with *topinat*:
        - Any activity vs. just observations
            - *inat-days* counts days on which any iNat activity occurred
              (observations, uploads, OR ids).
            - *topinat* counts only observations
        - All database records vs. one user
            - *inat-days* performs a database query on a copy of the
              iNaturalist database
            - *topinat* remotely accesses the iNaturalist observations
              histogram API on the web
        - Admin tool vs. user tool
          - As such, the *topinat* author's impression is that
            *inat-days* is more suited as a tool for admins of the
            iNaturalist site whereas *topinat* (and *inat-streak*) are
            aimed at personal use by individual iNaturalist users.
- **www.inaturalist.org stats**
    - This is by far and away the best stats site for iNaturalist
      there is! There are tons of charts & statistics across the
      whole project, as well as personal stats a user can generate for
      themselves.
    - However, so far as the *topinat* author can tell, it does not
      serve the same purpose as any of the above tools, i.e. to report
      on best days & longest streaks.
    - Home page:
        - https://www.inaturalist.org/stats
    - Web app for personal stats:
        - add *year* and *userid* to the URL, e.g.
            - https://www.inaturalist.org/stats/2019/benarmstrong

