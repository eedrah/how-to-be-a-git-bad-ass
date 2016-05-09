# How to be a `git` bad-ass
## Logging/Information
### `git log --oneline`
Show a concise form of the log
#### Boss level
```bash
> git log --oneline
```
```bash
3a1e99a Merge branch 'package-development' into 'master'
e5026ba remove unused files
583c018 remove unnecessary lodash package
d46c3b6 use packages
a1ab583 Merge branch 'master' into package-development
7376699 update packages
```
#### Wizard level
`--graph` shows the graph of branches and merges

`--decorate` adds annotations of branches, such as `(master, origin/master)`

`--all` also shows branches that you are not descended from

This comes in pretty colors on the command line
```bash
> git log --oneline --graph --decorate --all
```
```bash
*   3a1e99a (HEAD -> master, origin/master, origin/HEAD) Merge branch 'package-development' into 'master'
|\
| | * 35af8f1 (origin/demo) add select
| | * d1ffa22 add textinput
| | * a363b16 remove other cards
| | * b4e9821 add elementwrapper
| | * 8f2bb41 add more cards
| | * c4b9f15 add card
| | * 4f463be add dashboard
| | * bc07575 add styles
| | * d831f28 add appframe
| | * 01aa308 remove styles
| | * 4bc8aff tweak setup
| | * 76c2395 setup demo
| | * 8e5fe7f enableDevServer
| |/
| * e5026ba remove unused files
| * 583c018 remove unnecessary lodash package
| * d46c3b6 use packages
| *   a1ab583 Merge branch 'master' into package-development
| |\
| |/
|/|
* |   744d95c Merge branch '260-display-group-category-filters-on-appliance-list-page-manufacturer-customer-specific' in
to 'master'
|\ \
| * | 14d7592 Remove unneeded key from Cards
| * | 200ed0d Create front-end for filtering appliances by category
| * | 5634673 Start adding categories
```
#### Bad-ass level
```bash
> log --graph --date=relative --abbrev=4 --color --decorate --pretty=format:'%Cred%h%C(yellow)%d %C(bold blue)%an %Creset%s %Cgreen(%ad)%Creset'
```
```bash
*   3a1e (HEAD -> master, origin/master, origin/HEAD) Andrew Cox Merge branch 'package-development' into 'master' (3 day
s ago)
|\
| * e502 Jesse Eedrah remove unused files (3 days ago)
| * 583c Jesse Eedrah remove unnecessary lodash package (3 days ago)
| * d46c Jesse Eedrah use packages (3 days ago)
| *   a1ab Jesse Eedrah Merge branch 'master' into package-development (3 days ago)
| |\
| |/
|/|
* |   744d Andrew Cox Merge branch '260-display-group-category-filters-on-appliance-list-page-manufacturer-customer-spec
ific' into 'master' (4 days ago)
```
### `git log -p`
Show the log with the patch
```diff
commit 83ebcef712caafc2291a36cc77b5c86486fc67ac
Author: Jesse Eedrah <jesse@end-game.com>
Date:   Fri May 6 12:47:52 2016 +1200

    remove rocket--ui-fields

diff --git a/package.json b/package.json
index cb97f13..62e780c 100644
--- a/package.json
+++ b/package.json
@@ -69,7 +69,6 @@
     "react-input-slider": "^1.5.0",
     "react-moment-proptypes": "^1.1.1",
     "react-router": "^2.0.0",
-    "rocket--css-base": "^0.2.0",
-    "rocket--ui-fields": "^0.5.0-1"
+    "rocket--css-base": "^0.2.0"
   }
 }

commit a941df84b3e8af8ed3835c91b2b2930426e213ff
Author: Jesse Eedrah <jesse@end-game.com>
Date:   Fri May 6 12:10:52 2016 +1200

    remove empty files

diff --git a/Futronix.Web.Portal/Styles/Rocket/Placeholders/card-background.scss b/Futronix.Web.Portal/Styles/Rocket/Pla
ceholders/card-background.scss
deleted file mode 100644
index 2449052..0000000
--- a/Futronix.Web.Portal/Styles/Rocket/Placeholders/card-background.scss
+++ /dev/null
@@ -1 +0,0 @@
-@import 'variables';
```
### `git diff` and friends
#### Boss level
`git diff` does a diff on your unstaged edits

`git diff --cached` does a diff on your staged edits

#### Wizard level
```bash
> git diff --word-diff
```

#### Bad-ass level
`-C` matches your file renames
```bash
> diff -C --word-diff-regex=.
```
```diff
var React = require([-"-]{+'+}react[-"-]{+'+});
var ReactDOM = require([-"-]{+'+}react-dom[-"-]{+'+});
var Router = require([-"-]{+'+}react-router[-"-]{+'+}).Router;
var Route = require([-"-]{+'+}react-router[-"-]{+'+}).Route;
var IndexRoute = require([-"-]{+'+}react-router[-"-]{+'+}).IndexRoute;
```

### `git blame`
```bash
> git blame --date=short --abbrev=3 -w codes.js
```
```diff
834f6 (Natalie Johnstone 2016-03-02  1) var codes = {
92bee (Natalie Johnstone 2016-02-19  2)     ApplianceTableColumn: {
92bee (Natalie Johnstone 2016-02-19  3)         SerialNumber: "APPLIANCE_SERIAL_NUMBER",
92bee (Natalie Johnstone 2016-02-19  4)         ManufactureDate: "APPLIANCE_MANFACTURE_DATE",
7612c (Natalie Johnstone 2016-04-15  5)         ModelName: "APPLIANCE_MODEL_NAME",
7612c (Natalie Johnstone 2016-04-15  6)         VersionNumber: "APPLIANCE_VERSION_NUMBER"
92bee (Natalie Johnstone 2016-02-19  7)     },
b6f33 (Natalie Johnstone 2016-03-15  8)     ApplianceSettingTypeCode: {
b6f33 (Natalie Johnstone 2016-03-15  9)         Temperature: "TEMP",
b6f33 (Natalie Johnstone 2016-03-15 10)         ControlMode1: "CONTROLMODE1",
b6f33 (Natalie Johnstone 2016-03-15 11)         LightRange: "LIGHTRANGE",
b6f33 (Natalie Johnstone 2016-03-15 12)         DateTime: "DATETIME",
b6f33 (Natalie Johnstone 2016-03-15 13)         IntervalMin: "INTERVALMIN",
b6f33 (Natalie Johnstone 2016-03-15 14)         TempOffset: "TEMPOFFSET"
b6cf9 (Andrew Cox        2016-03-17 15)     },
b6cf9 (Andrew Cox        2016-03-17 16)     ApplianceStatusCode: {
b6cf9 (Andrew Cox        2016-03-17 17)         UnRegistered: "UNREGISTERED",
b6cf9 (Andrew Cox        2016-03-17 18)         OffLine: "OFFLINE",
b6cf9 (Andrew Cox        2016-03-17 19)         Running: "RUNNING"
b6239 (Jesse Eedrah      2016-03-30 20)     },
052cb (peterheesterman   2016-05-03 21)     CustomerTableColumn: {
052cb (peterheesterman   2016-05-03 22)         CustomerName: "CUSTOMER_NAME"
052cb (peterheesterman   2016-05-03 23)     },
```

## Recovery
### `git reflog`
```bash
> git reflog
```
```diff
3a1e99a HEAD@{0}: reset: moving to head^
f73cafb HEAD@{1}: commit: delete package.json
3a1e99a HEAD@{2}: checkout: moving from master to test
3a1e99a HEAD@{3}: checkout: moving from abce6ccc5678955bc666270b6ac807ecf09e2df5 to master
abce6cc HEAD@{4}: checkout: moving from master to head^^^
3a1e99a HEAD@{5}: checkout: moving from allTheCommits to master
0639b13 HEAD@{6}: commit: love commits
c56b81d HEAD@{7}: commit: love commits
2dece37 HEAD@{8}: commit: love commits
```

## Minimizing work
### `git cherry-pick`
Applies the changes of a commit(s) to your branch

`-n` leaves the changes in your staging area, not making another commits

```bash
git cherry-pick -n 2e95
git diff --cached
```
```diff
diff --git a/Futronix.Web.Portal/Views/Home/Index.cshtml b/Futronix.Web.Portal/Views/Home/Index.cshtml
index c6af781..3a8c324 100644
--- a/Futronix.Web.Portal/Views/Home/Index.cshtml
+++ b/Futronix.Web.Portal/Views/Home/Index.cshtml
@@ -11,7 +11,7 @@
         var CSRF = "@Model.Window.CSRFToken";

     </script>
-    <script src="~/Scripts/bundle.js"></script>
+    <script src="http://localhost:8080/bundle.js"></script>
     <!--[if IE]>
         <script src="http://html5shiv.googlecode.com/svn/trunk/html5.js"></script>
     <![endif]-->
```

### `git revert`
Does the opposite of cherry-pick - it reverses the given commits, leaving the reversal in your commit history. It is much superior to a `git reset --hard head^` and a `git push --force`.

### `git rebase`
Moves commits around on mass. Perfect for cherry-picking a large number of commits or moving your commits away from the branch of which you originally branched off.

### Abusing remotes to scaffold projects
```bash
md rocket-ui-buttons | cd
git init
git remote add scaffold ..\rocket-ui-card-dashboard-system
git fetch scaffold
git cherry-pick ae96
git remove remote scaffold
```

### Small commits lead to reusable commits
When you utilize commits in this way all those arguments about small commits become obsolete. Your commits are a tool - using them in this way will mean you make small commits because you desire, not because you are forced.

### Abusing the index with `git update-index` or `git symbolic-ref`
_Don't do these unless you have an extremely good reason to and you are really bad-ass!_

`git update-index` can ignore files (without using a git ignore)

`git symbolic-ref HEAD refs/heads/myFeatureBranch` can switch your branch to `myFeatureBranch` without checking out any files or resetting the index. This is great for doing sensitive file operations such as removing that 4 gigabyte file someone accidentally committed without having to checkout the file.

### `git clean`
Want a clean build? Don't delete and re`clone` the entire repo - just run `git clean -X -d`

## Staging
### `git add -p`
Will allow to stage part of a file. `-p` is short for `--patch`

### Reset unstaged work
```bash
git commit --allow-empty -m 'temp'
git add -A
git reset --hard
git reset --soft head^
```

### Swap unstaged and staged work
```bash
git commit --allow-empty -m 'temp'
git add -A
git stash
git reset HEAD^
git stash pop --index
```

## Aliases
are your friends! It is much nicer to type `git swap` than the above 5 lines! However, only make aliases to save on typing. Don't make them as a substitute for actually learning how git works under the hood. If you don't know what a command does it shouldn't be in your aliases.

To make an alias:
`git config --global alias.witchhunt "blame -w"`

If you are really bad-ass you can put bash in here. I have `git alias` aliased to view all my aliases:
```bash
alias = "!f() { git config --get-regexp ^alias\\. | sed -r -e 's_^alias\\.([^ ]*)_\\1 ........................_; s_^(.{26}[^.]*)\\.*_\\1_' ;}; f"
```
```bash
ch ....................... checkout
co ....................... checkout
st ....................... status
b ........................ branch
cp ....................... cherry-pick
rv ....................... revert --no-edit
df ....................... diff -C
bl ....................... blame -w
lg ....................... log --graph --date=relative --abbrev=4 --color --decorate --pretty=format:'%Cred%h%C(yellow)%d %C(bold blue)%an %Creset%s %Cgreen(%ad)%Creset'
lga ...................... !git lg --all
lg-status ................ !git lg --name-status
last ..................... log -1 --pretty=%s
...
```

## Final note on technique
When moving files, do a commit for the move and then a commit for the edit. Git will track your changes better, particularly when you are editing a significant portion of the file.
