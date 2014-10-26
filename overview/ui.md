The Platform Web UI
===================

![](/overview/images/ui-header.png)

You can see on the top right of the Platform UI the 5 main actions that you can use to interace with your environments.

------------------------------------------------------------------------

![image](/overview/images/icon-branch.png)


Branch
------

Branching an environment means creating an exact copy of that
environment.

A Platform branch includes code, and also the services that are needed
to run the whole application. This means that when you branch an
environment, you also branch the complete infrastructure. A fork will be
done of all the services, their configuration as well as their data.

During a `branch`, three things happen:

-   a new branch is created in Git
-   the branch is deployed
-   the application is rebuilt

------------------------------------------------------------------------

![image](/overview/images/icon-merge.png)


Merge
-----

Merging an environment means introducing the code changes from a branch
to its parent branch.

During a `merge`:

-   the code changes are merged via Git to the parent branch
-   the parent branch is deployed
-   the application is rebuilt

------------------------------------------------------------------------

![image](/overview/images/icon-sync.png)


Sync
----

Synchronizing an environment means updating an environment with the code
and/or data of its parent.

Note that `sync` is only available if your branch has no unmerged
commits, and can be fast-forwarded. On `sync`, your code branch will be
fast-forwarded to its parent's tip, and the data (e.g. databases) of the
services on the branch will be overwritten with an exact copy of the
parent's. Syncing of data and code can be done individually, so if
desired, you can benefit from having only code changes applied for
instance.

------------------------------------------------------------------------

![image](/overview/images/icon-backup.png)


Backup & Restore
----------------

Backing up an environment means saving a copy of the database, so that
it could be restored, if need be.

> **Warning** Restoring environments is not yet available in the Platform UI.

------------------------------------------------------------------------

![image](/overview/images/icon-git.png)


Push
----

Pushing code to a branch will update the code repository and also
automatically triggers a rebuild of the application that is running on
the infrastructure branch that was pushed to.

Which means you can test a new service, a different module version, or
any specific configuration by simply pushing code to your Git
repository.

During a `push`, here is what happens:

-   the code repository is updated
-   the branch is deployed
-   the application is rebuilt

