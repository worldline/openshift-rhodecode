RhodeCode on OpenShift
=========================

``RhodeCode`` is a fast and powerful management tool for Mercurial_ and GIT_
with a built in push/pull server, full text search, pull requests and
code-review system. It works on http/https and has a few unique features like:
advanced permission system with IP restrictions, web based file editing,
side-by-side diffs, snippets (gist) system and pluggable
authentication system with the ability to authenticate via LDAP, ActiveDirectory,
Atlassian Crowd, Container, Pam.

RhodeCode also provides simple API, and multiple event hooks so it's easy
integrable with existing external systems.

RhodeCode is similar in some respects to github_ or bitbucket_,
however RhodeCode can be run as standalone hosted application on your own server.
RhodeCode can be installed on \*nix or Windows systems.

More information can be found at https://rhodecode.com/

Running on OpenShift
--------------------

Create an account at http://openshift.redhat.com/

Create a DIY application. If you may add a PostgreSQL cartridge.

    rhc app create rhodecode diy-0.1 postgresql-9.2

Add this upstream RhodeCode quickstart repo

    rm -R diy .openshift misc README.md
    git remote add upstream -m master https://github.com/worldline/openshift-rhodecode.git
    git pull -s recursive -X theirs upstream master

Push the repo upstream to OpenShift

    git push

Head to your application at:

    http://rhodecode-$yourdomain.rhcloud.com

Default Credentials
-------------------
<table>
<tr><td>Default Admin Username</td><td>admin</td></tr>
<tr><td>Default Admin Password</td><td>rhodecode</td></tr>
</table>

To give your new RhodeCode site a web address of its own, add your desired alias:

    rhc app add-alias -a rhodecode --alias "$whatever.$mydomain.com"

Then add a cname entry in your domain's dns configuration pointing your alias to $whatever-$yourdomain.rhcloud.com.

