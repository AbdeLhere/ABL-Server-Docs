---
description: >-
  If your MySQL service in XAMPP isn’t starting and you're seeing InnoDB-related
  errors, it usually means the database has become corrupted. Here's a clear way
  to fix it:
---

# Xampp Mysql Module Not Starting

***

## <mark style="color:yellow;">Step 1: Back Up Your Data (If Possible)</mark>

Before doing anything, **create a backup** of your MySQL data directory.

* Navigate to: `C:\xampp\mysql\data`
* Copy the entire `data` folder to a safe location.

## <mark style="color:yellow;">Step 2: Fix Corrupted InnoDB Files</mark>

* **Stop MySQL Services**
  * Open XAMPP and completely stop the MySQL service.
* **Go to the Data Directory**
  * Path: `C:\xampp\mysql\data`
* **Delete the Following Files** _(They’ll be auto-regenerated)_:
  * `ib_logfile0`
  * `ib_logfile1`
  * `ibdata1` → ⚠️ _Only delete this if you have a backup, as it stores your database contents._

***

## <mark style="color:green;">Alternative (If You Don’t Want to Delete</mark> <mark style="color:green;"></mark><mark style="color:green;">`ibdata1`</mark><mark style="color:green;">)</mark>

If you prefer to keep `ibdata1`, try forcing MySQL to start in recovery mode:

* Open your MySQL configuration file:
  * Usually named `my.ini` or `my.cnf` (located in your XAMPP installation folder).
*   Under the `[mysqld]` section, add the following line:

    ```ini
    innodb_force_recovery = 4
    ```

***

## <mark style="color:yellow;">Step 3: Restart MySQL</mark>

* Start MySQL again from the XAMPP control panel.
* If all goes well, your MySQL should be up and running again.

***

#### ✅ Done!

Your issue should now be resolved. If not, consider increasing the `innodb_force_recovery` value (up to `6`), but only as a temporary measure.

***
