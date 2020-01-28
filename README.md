![MIKES DATA WORK GIT REPO](https://raw.githubusercontent.com/mikesdatawork/images/master/git_mikes_data_work_banner_01.png "Mikes Data Work")        

# Granting View Permissions in 2005 With SQL
**Post Date: May 31, 2007**        



## Contents    
- [About Process](##About-Process)  
- [SQL Logic](#SQL-Logic)  
- [Build Info](#Build-Info)  
- [Author](#Author)  
- [License](#License)       

## About-Process

<p>Ever have a case where a developer needs to see the source code
behind some procedures, tables, or views on the production databases?
well instead of receiving 100 requests to send the object definitions of
these objects to them you can simply GRANT them permissions to
VIEW definitions.
here's one example to grant a user permissions to see all definitions
of all Tables, Views, and Procedures of a particular database.
this will produce a single script for every object in the database. you
can use just one script per file, or run it all at once.
remember to set the output to text by pressing CTRL+T</p>      


## SQL-Logic
```SQL
use MyDatabase
go
set nocount on
select
'use [MyDatabase] ' + char(10) + 
'GRANT VIEW DEFINITION ON [dbo].[' + name + '] TO [DOMAIN\User]' + char(10) + 'go' + char(10)
from sysobjects where xtype = 'P' or xtype = 'U' or xtype = 'V' or xtype = 'X' 
```

<p>Some developers need to see the definition of particular database objects in production so they
can create those objects under their test/development platforms. 
well normally when you think about it… you don't want to perform grants per object. that would take
for ever, and the developers would constantly be coming back for more objects. 
one solution is to just give them dbo which is not warranted right so the next best thing is just
give them the ability to see the definition wihout granting them any extra permissions. so you
give just the 'view definition' permission per object. 
thats it.</p>


[![WorksEveryTime](https://forthebadge.com/images/badges/60-percent-of-the-time-works-every-time.svg)](https://shitday.de/)

## Build-Info

| Build Quality | Build History |
|--|--|
|<table><tr><td>[![Build-Status](https://ci.appveyor.com/api/projects/status/pjxh5g91jpbh7t84?svg?style=flat-square)](#)</td></tr><tr><td>[![Coverage](https://coveralls.io/repos/github/tygerbytes/ResourceFitness/badge.svg?style=flat-square)](#)</td></tr><tr><td>[![Nuget](https://img.shields.io/nuget/v/TW.Resfit.Core.svg?style=flat-square)](#)</td></tr></table>|<table><tr><td>[![Build history](https://buildstats.info/appveyor/chart/tygerbytes/resourcefitness)](#)</td></tr></table>|

## Author

[![Gist](https://img.shields.io/badge/Gist-MikesDataWork-<COLOR>.svg)](https://gist.github.com/mikesdatawork)
[![Twitter](https://img.shields.io/badge/Twitter-MikesDataWork-<COLOR>.svg)](https://twitter.com/mikesdatawork)
[![Wordpress](https://img.shields.io/badge/Wordpress-MikesDataWork-<COLOR>.svg)](https://mikesdatawork.wordpress.com/)

    
## License
[![LicenseCCSA](https://img.shields.io/badge/License-CreativeCommonsSA-<COLOR>.svg)](https://creativecommons.org/share-your-work/licensing-types-examples/)

![Mikes Data Work](https://raw.githubusercontent.com/mikesdatawork/images/master/git_mikes_data_work_banner_02.png "Mikes Data Work")

