# Untitled

* e-group:
  * ai-admins: get access GitLab repos and foreman
  * cms-sdt-aibox-admins: Add access CMS SDT Build openstack project
  * cms-git-vocmssdt-admins: To have access to puppet gitlab repos
  * cms-sdt-logs: For jenkins errors logs
* get gibhub user in cms-bot/categories as L2 of externals
* update puppet recipe \(jenkins, vocmssdt, vocmssdt/sdt/builders etc\) to have user CERN access added as administrator
* Update Jenkins configuration to allow all admin rights to user
* Add user in github teams so that he/she is able to manage github repositories
  * [https://github.com/orgs/cms-data/teams/uploaders](https://github.com/orgs/cms-data/teams/uploaders)
  * [https://github.com/orgs/cms-externals/teams/developers](https://github.com/orgs/cms-externals/teams/developers)
* Hypernews fourms to subscribe
  * Computing Project Announcements   _Software Distribution Tools Discussions_   CERN Computing Announcements   _External Package Management_   Offline Announcements   _Release Integration_   Software Development   _Software Development Tools_   Software Release Announcements  \* Computing Tools  
* top level page from there you can find links to various services we maintain: [https://cmssdt.cern.ch/SDT/2](https://cmssdt.cern.ch/SDT/2). github repositories: - our main projects in github are - [https://github.com/cms-sw](https://github.com/cms-sw) - [https://github.com/cms-externals](https://github.com/cms-externals) - [https://github.com/cms-data](https://github.com/cms-data)
  * main repositories we work on day to day basis:     [**https://github.com/cms-sw/cmssw**](https://github.com/cms-sw/cmssw) ****_**\(CMS offilce code C++/python\)**_     ****[**https://github.com/cms-sw/cmsdist**](https://github.com/cms-sw/cmsdist)**: collection of RPM spec files \(kind of build recipes for building externals and cmssw\)**     [https://github.com/cms-sw/pkgtool](https://github.com/cms-sw/pkgtool)_: a home make tools for building externals. It is written in Python which uses cmsdist to generate rpms_     [https://github.com/cms-sw/cmspkg](https://github.com/cms-sw/cmspkg): A home made tool to replace apt-get to upload and distribute rpms    \* [https://github.com/cms-sw/cms-bot](https://github.com/cms-sw/cms-bot): Collection of bash/python scripts for make small tasks/jobs we run in Jenkins \(cmssdt.cern.ch/jenkins\)
* Openstack project for cmssdt: [https://openstack.cern.ch](https://openstack.cern.ch) CMS SDT Build    I think you need to be in an e-group to access it. I will take care of it.
* Foreman for managing hostgroups and puppet configurations: [https://judy.cern.ch/](https://judy.cern.ch/)
* Puppet configurations for our host groups are maintain in gitlab:    [https://gitlab.cern.ch/ai/it-puppet-hostgroup-vocmssdt](https://gitlab.cern.ch/ai/it-puppet-hostgroup-vocmssdt)    [https://gitlab.cern.ch/ai/it-puppet-module-cmssw](https://gitlab.cern.ch/ai/it-puppet-module-cmssw)    We use devel branch of these repos.

CMSSW packages and categories map is availalble here [https://github.com/cms-sw/cms-bot/blob/master/categories.py](https://github.com/cms-sw/cms-bot/blob/master/categories.py)

## This file also havd the github names of users who are responsible for these categories and how can run tests.

These are the commands one can run on our build/dev machines to build RPMs for our externals. 1. clone the repositories needed to build \(cmsdist for RPM spec files and pkgtools for cmsBuild command to build RPM\)git clone git@github.com:cms-sw/cmsdistgit clone git@github.com:cms-sw/pkgtools 2. Checkout the correct cmsdist branch. I am using here the default branch i.e. IB/CMSSW\_9\_1\_X/gcc530 but you can use any branch you are interested. You can find out the cmsdist branches and archs in [https://github.com/cms-sw/cms-bot/blob/master/config.map](https://github.com/cms-sw/cms-bot/blob/master/config.map) file. Use the correct branch for correct architecture. For example you can not use IB/CMSSW\_9\_1\_X/gcc530 to build slc6\_amd64\_gcc700. pushd cmsdst git checkout IB/CMSSW\_9\_1\_X/gcc530 popd 3. If external spec file already exists then update it or if it is a new package then create a new spec file.4. build your updated/new package. For example following command should build boost external for slc6\_amd64\_gcc530 arch using cms.week0 repository ./pkgtools/cmsBuild -a slc6\_amd64\_gcc530 --repo cms -i build -j 10 build boost After this you should have RPMs build/install in `pwd`/build directory. The logs of the build are available under `pwd`/build/BUILD/slc6\_amd64\_gcc530/xxxx directories. Once have some time then try to ply with it. For example just add a empty line in root.spec and try to build. Ideally when we test by hand then we build cmssw-tool-conf package \(which depends on every thing\). So if root package is changed then update root.spec and build cmssw-tool-conf to get every package rebuilt due to root.spec update.

