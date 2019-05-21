.. version-3.2.0-release-notes:

v3.2.0, April 8, 2019
---------------------

What's new
~~~~~~~~~~

|no changes|

Resolved issues
~~~~~~~~~~~~~~~

- Auth tokens expiring during long running backups should no longer result in a failed backup

- Restores should no longer timeout if a retry with an auxiliary volume is required

- Incremental restores should no longer fail immediately when a retry with an auxiliary volume is required

Known issues
~~~~~~~~~~~~

|no changes|
