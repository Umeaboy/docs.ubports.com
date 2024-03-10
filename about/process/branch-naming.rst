Branch-naming convention
========================

Our branch-naming convention ensures software can be built by our CI and tested easily by other developers.

Every Git repository's README file should state which branch-naming convention is used and any deviations from the norm.

Click-Packages
--------------

Software exclusively distributed as a click-package (and not also as a DEB) only uses one ``master`` branch that is protected. Separate temporary development branches with arbitrary descriptive names can be created and merged into master when the time comes. Ideally Git tags or GitHub releases should be used to mark and archive milestones in the development history.

DEB Packages
------------

We maintain the following branches across Git repositories:

- ``main`` or ``ubports/latest``: this branch represents the latest development code, and will become a part of the next major release of Ubuntu Touch. All kinds of changes are allowed in this branch.
- ``ubports/<major version>.x`` (e.g. ``ubports/24.6.x``): this branch represents the code in a particular major version. It branches of the ``main`` branch before the major release, and will become a part of the releases of that major version. Only bugfixes and non-breaking changes are allowed in this branch.

.. note::
    In the transition period, we consider ``ubports/focal`` to be a major version branch.

To ensure the ``main`` branch doesn't miss any changes, all changes must be made against ``main`` branch first before backporting to the major release branches. An exception is when a change is not applicable to the ``main`` branch anymore due to other changes in that branch.

.. note::
    If the next development version is not available for testing yet, and you need the change to be made available for install for testing, it's allowed to temporarily target the changeset to the major version branch to get packages built against that version. When the changeset is ready for merge, the changeset must be re-targeted to the ``main`` branch.

.. note::
    We used to have a branch naming convention which allows a branch to directly become an APT archive and allow multiple changes to be aggregated for dependency purpose (e.g. ``ubports/focal_-_dependency-1_-_dependency-2``). However, due to its use no longer maps well with the new branching scheme, its use is deprecated. It will no longer be allowed when we no longer support Ubuntu Touch based on Ubuntu 20.04.
