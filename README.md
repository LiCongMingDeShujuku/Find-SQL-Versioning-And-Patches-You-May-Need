![CLEVER DATA GIT REPO](https://raw.githubusercontent.com/LiCongMingDeShujuku/git-resources/master/0-clever-data-github.png "李聪明的数据库")

# 查寻SQL Server的版本和所需补丁（Patches）
#### Find SQL Server Versions And Patches That You Need
**发布-日期: 2015年7月10日 (评论)**

![#](images/find-sql-versioning-and-patching-you-may-need.png?raw=true "#")

## Contents

- [中文](#中文)
- [English](#English)
- [SQL Logic](#Logic)
- [Build Info](#Build-Info)
- [Author](#Author)
- [License](#License) 


## 中文
下面是一些SQL逻辑(logic)会显示SQL Server版本，如果你的版本落后，将会列出服务器所需的补丁。 最高适用于SQL Server 2014。


## English
Here’s some SQL logic that will show you the SQL Server Version and will list the Patches the servers need if you’re behind on your versioning. Works up to SQL Server 2014.

---
## Logic
```SQL
use master;
set nocount on
select
 	'SQL Version' = right(left(@@version, 25), 15)
,	'Service Pack' = serverproperty('productlevel')
,	'R2?' =
 case
 	when serverproperty('productversion') between '10.50.0000.0' and '10.51.0000.0' then ' R2'
 	else ''
 end
,	'Current' =
 case
 	when serverproperty('productversion') between '9.0.1399.06' and '9.0.4036' then 'Requires SQL 2005 SP4'
 	when serverproperty('productversion') between '10.0.1600.21' and '10.0.5500.1' then 'Requires SQL 2008 SP4'
 	when serverproperty('productversion') between '10.50.1600.0' and '10.50.4000.1' then 'Requires SQL 2008 R2 SP3'
 	when serverproperty('productversion') between '11.0.2100.59' and '11.0.3000.1' then 'Requires SQL 2012 SP2'
 	when serverproperty('productversion') between '12.0.2000.7' and '11.0.3000.0' then 'Requires SQL 2012 SP2'
 else
 	'Current'
 end
,	'Build Number' = serverproperty('productversion')

```

应用于多个服务器时，结果如下所示。

Results will look like this when applied to multiple servers.




[![WorksEveryTime](https://forthebadge.com/images/badges/60-percent-of-the-time-works-every-time.svg)](https://shitday.de/)

## Build-Info

| Build Quality | Build History |
|--|--|
|<table><tr><td>[![Build-Status](https://ci.appveyor.com/api/projects/status/pjxh5g91jpbh7t84?svg?style=flat-square)](#)</td></tr><tr><td>[![Coverage](https://coveralls.io/repos/github/tygerbytes/ResourceFitness/badge.svg?style=flat-square)](#)</td></tr><tr><td>[![Nuget](https://img.shields.io/nuget/v/TW.Resfit.Core.svg?style=flat-square)](#)</td></tr></table>|<table><tr><td>[![Build history](https://buildstats.info/appveyor/chart/tygerbytes/resourcefitness)](#)</td></tr></table>|

## Author

- **李聪明的数据库 Lee's Clever Data**
- **Mike的数据库宝典 Mikes Database Collection**
- **李聪明的数据库** "Lee Songming"

[![Gist](https://img.shields.io/badge/Gist-李聪明的数据库-<COLOR>.svg)](https://gist.github.com/congmingshuju)
[![Twitter](https://img.shields.io/badge/Twitter-mike的数据库宝典-<COLOR>.svg)](https://twitter.com/mikesdatawork?lang=en)
[![Wordpress](https://img.shields.io/badge/Wordpress-mike的数据库宝典-<COLOR>.svg)](https://mikesdatawork.wordpress.com/)

---
## License
[![LicenseCCSA](https://img.shields.io/badge/License-CreativeCommonsSA-<COLOR>.svg)](https://creativecommons.org/share-your-work/licensing-types-examples/)

![Lee Songming](https://raw.githubusercontent.com/LiCongMingDeShujuku/git-resources/master/1-clever-data-github.png "李聪明的数据库")

