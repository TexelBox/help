# FREQUENTLY ASKED QUESTIONS & OTHER USEFUL TIPS/REMINDERS
- **[HOW DO I ADD A NEW GIT SUBMODULE?](#how-do-i-add-a-new-git-submodule)**
- **[HOW DO I INITIALIZE/UPDATE ALL GIT SUBMODULES RECURSIVELY?](#how-do-i-initializeupdate-all-git-submodules-recursively)**
- **[HOW DO I STAGE A NEW SHELL SCRIPT WITH EXECUTABLE PERMISSION?](#how-do-i-stage-a-new-shell-script-with-executable-permission)**
- **[HOW DO I UPGRADE GIT SUBMODULES TO THEIR LATEST COMMITS?](#how-do-i-upgrade-git-submodules-to-their-latest-commits)**
- **[I JUST ADDED A NEW GIT SUBMODULE THAT USES GIT SUBMODULES ITSELF. WHY ARE THEY MISSING AND HOW DO I FIX THIS?](#i-just-added-a-new-git-submodule-that-uses-git-submodules-itself-why-are-they-missing-and-how-do-i-fix-this)**

---

#### HOW DO I ADD A NEW GIT SUBMODULE?
1. Copy the URL of the dependency's repository.
2. From the project root directory, execute...
```
git submodule add -b <branch> <url> <path>
```
where `<branch>` is the branch name of the dependency repository to clone from (usually `master`), `<url>` is obviously the URL copied in step 1 and `<path>` is the path to a new directory that will act as the root directory for the clone. For example...
```
git submodule add -b master https://github.com/onqtam/doctest deps/doctest
```
will clone the latest master branch commit of the doctest repository into the deps/doctest directory that gets created.

**NOTE: this will populate `.gitmodules` with a new entry with hard-tab indentation. If you wish to enforce soft-tab (space) indentation, you may edit the file directly, restage, and commit/push as usual.**

---

#### HOW DO I INITIALIZE/UPDATE ALL GIT SUBMODULES RECURSIVELY?
```
git submodule update --init --recursive
```

---

#### HOW DO I STAGE A NEW SHELL SCRIPT WITH EXECUTABLE PERMISSION?
- If the file is untracked, stage for the first time with...
```
git add --chmod=+x <path/to/script>
```
- If the file is already tracked, you can update the permission with...
```
git update-index --chmod=+x <path/to/script>
```

---

#### HOW DO I UPGRADE GIT SUBMODULES TO THEIR LATEST COMMITS?
- Upgrade one...
```
cd deps/<submodule root>
git checkout <submodule branch>
git pull
cd ../..
git commit -am "upgraded <submodule> to latest commit"
git push origin <branch>
```
- Upgrade all...
```
git submodule update --remote --merge
git commit -am "upgraded all submodules to latest commits"
git push origin <branch>
```
**NOTE: maintainers of template repositories should keep an eye on new releases of dependencies and upgrade frequently to stable versions.**

---

#### I JUST ADDED A NEW GIT SUBMODULE THAT USES GIT SUBMODULES ITSELF. WHY ARE THEY MISSING AND HOW DO I FIX THIS?
- After adding a new submodule, it seems like recursive submodules simply exist as commit references and still require initialization/updating to be cloned properly. Fix this by running...
```
git submodule update --init --recursive
```

---
