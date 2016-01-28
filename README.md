GitDummy v3
========

Ever wanted to include your private repository contributions to your contribution panel? Well now you can. This script will read from existing repositories and transcribe all of the commit messages into dummy repositories that you can then add publicly to your GitHub account. This script transfers no source code, only commit stubs and their associated dates. This script can be ran multiple times and will update the dummy repo as you go.

#### Step 1: Create the JSON array of your repositories (repos.json):
```json
[
    {
        "target_repo"         : ["/home/brian/myrepo","/home/brian/myrepo-old"],
        "target_email"        : ["brian@example.org","bob@otherexample.com"],
        "dummy_repo"          : "/home/brian/dummy_myrepo",
        "dummy_repo_data"     : "/home/brian/dummy_myrepo/data",
        "dummy_email"         : "brian@example.org",
        "dummy_name"          : "Brian Seymour",
        "dummy_readme"        : "This public repository reflects the commits from a private repo (minus the actual code)",
        "dummy_ext"           : ".js",
        "dummy_code"          : "'use strict';",
        "hide_commits"        : false,
        "random_file_name"    : false,
        "auto_push"           : true,
        "force"               : false,
        "remote"              : "https://github.com/yourname/dummy_repo"
    },
    {
        "target_repo"         : ["/home/brian/myotherprivaterepo"],
        "target_email"        : ["brian@example.org"],
        "dummy_repo"          : "/home/brian/dummy_myotherprivaterepo",
        "dummy_repo_data"     : "/home/brian/dummy_myotherprivaterepo/data",
        "dummy_email"         : "brian@example.org",
        "dummy_name"          : "Brian Seymour",
        "dummy_readme"        : "This public repository reflects the commits from a private repo (minus the actual code)",
        "dummy_ext"           : "",
        "dummy_code"          : "",
        "dummy_commit_message": "Example other commit message",
        "hide_commits"        : true,
        "random_file_name"    : true,
        "auto_push"           : true,
        "force"               : true,
        "remote"              : "https://github.com/yourname/dummy_privaterepo"
    }
]
```

##### Where is your Git repo (target_repo)
Here you must provide the absolute path to the Git repo that you want to transcribe from. The directory must exist and contain a .git folder inside.

##### Which email address should commits be checked against (target_email)
Here you must provide the email address the script should search for in the repo being transcribed from. This makes it so only your commits will come out and into the repo being transcribed to.

##### Where should the dummy repo be created (dummy_repo)
Here you must provide the absolute path to the folder you want the script to transcribe to. The directory must not exist.

##### Where should the dummy files be created? (dummy_repo_data)
Need Files to add... and is used to help with language statistics. To use random file names just set "random_file_name" to true.

##### Which email address should be used in the dummy commits (dummy_email)
Here you must provide a new email address the dummy commits will be made as. This will most likely be your GitHub email address so GitHub can properly associate the commits with your account.

##### Which name should be used in the dummy commits (dummy_name)
Here you must provide the name the dummy commits will be made as. This really has no bearing, but, it should be your name.

##### What should your readme file contain? (dummy_readme)
Here you must provide the actual text to the readme file associated to that specific repo

##### What the file extension for the dummy files be?
Recommend using whatever primary language your private repo is...

##### Code Sample that reflects the language your private repo is
Needs to be a short snippet of code reflective of the language your private github repo is

##### Whether or not to expose the commit messages (hide_commits)
You may not want to show the commit messages in your dummy repo. If this is the case, set this to true and a simple "private commit message" commit message will be put instead. To change this message just set "dummy_commit_message" (optional).

##### Whether or not to run a `git push origin master` at the end (auto_push)
If this is set to true, you'll be prompted for your repo credentials for the push.

##### Whether or not to run a `git push origin master --force` at the end (force)
If this is set to true, you'll be prompted for your repo credentials for the push.  (use this if you're re-doing a run from scratch)

##### Which remote repo should the dummy repo be pushed to (remote)
Here you must provide the GitHub URL that your dummy repo resides at.

#### Step 2: Run the script as many times as you'd like
```
python gitdummy.py
```

---


Change Log
========
#### Version 3.12 (April 2015)
- Added random file name to completely hide commit data (LeonardoCardoso)
- UTF-8 support (sepehr)

#### Version 3.11 (March 2015)
- Filename truncation to abide by OS imposed 255 char limit (nicolelehrer)

#### Version 3.1 (February 2015)
- Python 3 support (ebrian)
- Custom readme content per repo (omarfouad)
- Clean up and bug fixes (oehokie)

#### Version 3 (December 2014)
- Added Language Statistics (oehokie)
- Compatible with older versions of git cli (oehokie)
- Arrays for email and targets instead of multiple entries (oehokie)

#### Version 2 (November 2014)
- JSON based repo transcription (ebrian)
- Removed single run limitation (ebrian)

#### Version 1 (October 2014)
- Private commit messages (w2pc)
- Single repo transcription (ebrian)
