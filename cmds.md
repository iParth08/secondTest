# GIT Commands CheatSheet

LookOnce
--------
learn later
>> git config --global core.editor [linux-editor]

rarely Used

>> git                 :: cmd list
>> git config --list   :: list of global config
>> git --help          :: 

Special Tasks
---------------

1. Configuration of author
>> git config --global user.name "______"
>> git config --global user.email "_____"

2. Delete git repo itself
>> rm -rf .git [highly_dangerous]

3. setting custom alias for git commands
git config --global alias.[custom] "commands"
>> git config --global alias.unstaged 'restore --staged --'
>> git unstaged <file>      :: git restore --staged --[file.txt]


commonly used
-----------------
1. ls           :: list all files  in dir
2. pwd          :: present working directory
3. cd           :: change directory
>> cd /c           ::: /c directory
4. touch        :: create a blank file 
>> touch error.log
5. 


Initiate a Repo (in local)
-----------------------------
1. git init             :: create a repo [empty]
2. git status           :: give status of repo
3. git add file         :: stag particular file
4. git add --a  [.]        :: stag all files
5. git commit -m "msg"  :: commit and msg
6. git log              :: show all commit [snaps]

more_cmds
-----------

7. git diff              :: compare working & Stag
8. git clone [url]       :: clone a repo from web
9. git commit -a -m "tracked only" :: direct commit
10. git rm file          :: remove and stag
11. git mv file newName  :: rename(move) and stag
12. git rm --cached file :: untrack, now gitignore

Cloning a REMOTE Repo
-----------------------
1. git clone url_here [y_folder]
>> git clone https://www.github.com/repos/ starkFile
    takes time in downloading....
    committing here will change your copy only
    origin/master is not changed by commit
    logs can be listed

2. git remote add origin [url]
    :: origin is name given to url not any command

3. git remote -v
    :: view pull push origin links
[Pull] - fetch all
[Push] - send modifications

4. git push -u origin master        
    :: origin |alias for source link |
    :: master |branch name|
    :: pushes to master brain and not [main] branch

ignore files from status{stag}
------------------------------
>> touch .gitignore
{
    in file add files to ignore untracked files
    error.log   [ignore_particular_file]
    *.log [ignore_all_log_files]
}
{learn...path combinations about ignore}

difference feature
-------------------
1. git diff             :: working area ~ staging
2. git diff --staged    :: previous commit ~ staging
if run after modification, 
compare working and staging area file.
Show the modification

@example{
    --file.txt [stag] 
    ++file.txt [working]
    >> git diff
    + this line is added in new modification 
}

view your commits
----------------------
>> git log
>> git log -p       :: commits with  full diff
>> git log -p -3    :: 3 commits with full diff
>> git log --stat   :: very short view of changes
>> git log --pretty=oneline :: commits in singleline
>> git log --pretty=short   :: just author
>> git log --pretty=full    :: author+commiter
>> git log --pretty=format:"%h -- %an"  
    :: refer doc for formatting detail
>> git log --since=[2].[days/months/weeks/year] :: filter time based commit


>> git commit --amend       ::amend previous commit
    ::opens vim editor
    - i for inser/write
    - esc for cmd tab
    - :wq to exit vim

unstage files
---------------
>> git restore --staged  <file>
    :: unstage --> not commit in next command
>> git checkout -- <file>       
    :: fetch previous [commit] data to file
    :: important but dangerous
>> git checkout -f
    :: unstaged files --> prev. commit []

branching
----------



# Theory Part

Snap-shot technique
---------------------
video1

Three stage Architecture
-------------------------
1. working dir
    local directory
    computer local files

2. stagging area
    file ready to commit/change
    waiting room for commit

3. git dir (repository)
    commit files reach here
    snapshot taken
    .git folder

File Status Lifecycle
----------------------
untracked --> unmodified --> modified --> staged
[init]        [add][2]       [changed_ctrl+s]      [commit]

[add][1] ==> for first, all files tracked => unmodified

[changed] ==> any files {stagged} gets modified

[add][2] ==> stag all modifications

[commit] ==> commit files are unmodified/saved


[NOTE::] tracks folder having trackable files 
------------------------>
>> git init [U] 
    :: Untracked
>> git add --a [1_A] 
    :: Tracking/Unmodified/stagged
>> ctr+s    [M] 
    :: changed/modified
>> git add file.txt    [2_A]
    :: Unmodified/Stagged
>> git commit -m "msg" [null]
    ::tracking/commit/unmodified

--------------->