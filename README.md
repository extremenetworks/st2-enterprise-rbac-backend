# StackStorm Enterprise RBAC Backend for StackStorm Enterprise Edition

[![Circle CI Build Status](https://circleci.com/gh/extremenetworks/st2-enterprise-rbac-backend.svg?style=shield&circle-token=eaf1bdcfc552072706ef0a6e68049f285dd33a03)](https://circleci.com/gh/extremenetworks/st2-enterprise-rbac-backend)

StackStorm RBAC backend for enterprise version which contains all the proprietary RBAC
(permission resolving) business logic.

NOTE: Due to the original code structure and the code originally living as part of the
open source StackStorm/st2 repo, some of the utility RBAC code is still part of the open
source repo (that code is of little use without the permission resolving classes which
contain majority of the business logic though).

## Installation

NOTE: This happens automatically when using bwc installer script.

1. Make sure the backend Python package is installed inside StackStorm virtualenv
   (``/opt/stackstorm/st2/``)
2: Edit StackStorm config (``/etc/st2/st2.conf``):

```ini
...
[rbac]
enable = True
backend = enterprise
...
3. Restart all the services - ``sudo st2ctl restart``

## Running Lint Checks and Tests

To run lint checks and unit tests you can use ``lint`` and  ``unit-tests`` make targets.
This will clone ``StackStorm/st2`` repo into ``/tmp/st2``, install StackStorm dependencies in
a purpose built virtual environment and add all StackStorm Python packages from
``/tmp/st2``  into ``PYTHONPATH`` for those make targets.

```bash
make lint
make unit-tests
```

If virtual environment is already created and all the dependencies installed, you can skip
dependency steps by simply running lint and tests:

```bash
make .lint
make .unit-tests
```

If you want to test those changes against a specific version of StackStorm/st2 repo, you can set
``ST2_REPO_BRANCH`` environment variable. For example:

```bash
ST2_REPO_BRANCH=my-super-feature make unit-tests
```

Keep in mind that you can also simply symlink your working copy of ``StackStorm/st2`` repo to
``/tmp/st2``. This way you can test changes with your work which hasn't been committed / pushed
upstream yet.

## Copyright, License, and Contributors Agreement

Copyright 2015-2020 Extreme Networks, Inc.

Unauthorized copying of this file, via any medium is strictly prohibited. Proprietary and confidential. See the [LICENSE](LICENSE) file included with this work for details.

By contributing you agree that these contributions are your own (or approved by your employer) and you grant a full, complete, irrevocable copyright license to all users and developers of the project, present and future, pursuant to the license of the project.
