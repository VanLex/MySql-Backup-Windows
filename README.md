# MySql-Backup-Windows
Backup MySQL databases and gzip the output sql files. Using PowerShell script language for Windows. Got the idea from [mysql-backup-windows.bat](https://gist.github.com/sindresorhus/869240).

### Requirements
* [Powershell](http://support.microsoft.com/kb/968929)
* [7-Zip](http://www.7-zip.org/)

### Setup
Download the [github archive](https://github.com/VanLex/MySql-Backup-Wndows/archive/master.zip) and extract to your script folder.

#### On mysqlbackup.ps1 file:
* Change the value of the variable `$cnfFile` to the path to your *my.cnf* file.
* Change the value of the variable `$backupDir` to the path to the folder where the backup files will be stored.
* If required change the value of the variable `$mysqldump` to the path to *mysqldump.exe* file.
* If required change the value of the variable `$mysqlDataDir` to the path to MySql data files directory. Is used to get only the names of the MySQL databases.
* If required change the value of the variable `$zip` to the path to *7z.exe* file.

#### On my.cnf file:
In the `[client]` section, change the user and password to match those of your backup user. This user must be granted the following global privileges: `EVENT`, `LOCK TABLES`, `SELECT`, `SHOW DATABASES`, and `SHOW VIEW`. For example:

```sql
GRANT SELECT, SHOW DATABASES, LOCK TABLES, EVENT, SHOW VIEW ON *.* TO 'backup'@'localhost';
```

#### On Task Scheduler:
Сreate a task to run the *mysqlbackup.ps1* script with the time necessary for you.
