# Environments on Platform.sh

[Platform.sh](https://platform.sh) helps a coder with the development
workflow by making it easy to manage project environments, including the
live enviornment which runs the actual website.

![](images/clone-hierarchy.png)

The [platform](https://github.com/platformsh/platformsh-cli) tool helps
you manage your local environment, copy code, data and resources between
your local development machine and remote Platform.sh environments.

## Enviroments are hierarchical - like Git branches

![](images/clone-hierarchy.png)

Platform.sh encourages you to structure your
environments \<environment\> as you want. New environments are tied to
Git branches, and are considered children of the environment that they
were branched from.

Each child environment can sync code and/or data down from its parent,
and merge code up to his parent.

### The Master environment

Platform.sh projects always have a Master environment which corresponds
to the Master branch in Git. This environment is your live site (on
production plans), and is the environment that is mapped to a
domain name.

### Branches

Any branches that are created with the Platform.sh user interface or the
platform CLI tool become child environments. These are used for
development, staging, and testing.

## Workflows and environments

Platform.sh gives you the flexibility to create your own workflows.

There are no rules you must follow when branching the master environment. You can use a style that best fits your workflow:

* *agile* - one master parent, branch a few children to use for sprints,
and branch each sprint to make stories for feature development.
* *developer-centric* - one production master, one QA environment and a few development environments - one per coder.
* *testing* - one production master, an operational test environment, a user test environment and a few unit test environments.
* *fix* - one master parent and two children - one for testing bug fixes and one for security updates.

Here is an example of an agile workflow:

* The administrator creates a sprint environment and gives each of the
developers permission to create new feature environments. Another
approach is that the administrator could create an environment for each
developer.

* As a feature is completed, the adimistrator can review the work by
accessing the website of the feature environment. When they are
satisfied, they can merge the new feature back into the Sprint
environment.

* The remaining features will sync with the Sprint environment to ensure
their working environment is up-to-date with the latest code.

* When the objectives of the sprint are complete, the administrator can
then make a backup of the live site, then merge the sprint environment
into the live environment.

The adminstrator can then synchronize the live site with any existing
Sprint environments to repeat the process and continue the development
process.

## Environment conventions

Platform provides great flexibility on the way you can organize and work
with your development environments. To improve readability and
productivity, it's important to think carefully about how to name and
structure those environments.

### Naming

The name should represent the purpose of the environment. Is it a
Staging site to show to your client? Is it an implementation of a new
feature? Is it a hot fix?

If you're working Agile, for example, you could use hierarchical
environments and name them like this:

```console
Sprint1
  Feature1
  Feature2
  Feature3
Sprint2
  Feature1
  Feature2
...
```

If you prefer splitting your environments per developer and having a
specific environment per task or per ticket, you could use something
like this:

```console
Staging
  Developer1
    Ticket-526
    Ticket-593
  Developer2
    Ticket-395
  ...
```
