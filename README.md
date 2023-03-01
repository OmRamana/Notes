##Microsoft Windows [Version 10.0.22621.963]  

##(c) Microsoft Corporation. All rights reserved.

C:\Users\keanu\Documents\anatomy_3>git pull origin main
remote: Enumerating objects: 38, done.
remote: Counting objects: 100% (38/38), done.
remote: Compressing objects: 100% (36/36), done.
remote: Total 36 (delta 23), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (36/36), 9.18 KiB | 3.00 KiB/s, done.
From https://github.com/OmRamana/anatomy_3
 * branch            main       -> FETCH_HEAD
   f9237bf..374c1f5  main       -> origin/main
Updating f9237bf..374c1f5
Fast-forward
 README.md | 38 ++++++++++++++++++++++----------------
 1 file changed, 22 insertions(+), 16 deletions(-)

C:\Users\keanu\Documents\anatomy_3>git add tooth_anatomy.png

C:\Users\keanu\Documents\anatomy_3>git commit -m "ta_1"
[main 96680cf] ta_1
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 tooth_anatomy.png

C:\Users\keanu\Documents\anatomy_3>git push origin main
Enumerating objects: 4, done.
Counting objects: 100% (4/4), done.
Delta compression using up to 8 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 93.60 KiB | 13.37 MiB/s, done.
Total 3 (delta 1), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
To https://github.com/OmRamana/anatomy_3.git
   374c1f5..96680cf  main -> main

C:\Users\keanu\Documents\anatomy_3>


---------------------------------------------------------------------------------------------------
Microsoft Windows [Version 10.0.22621.819]
(c) Microsoft Corporation. All rights reserved.

C:\Users\keanu\Documents\anatomy_2>echo "# anatomy_2" >> README.md

C:\Users\keanu\Documents\anatomy_2>git init
Initialized empty Git repository in C:/Users/keanu/Documents/anatomy_2/.git/

C:\Users\keanu\Documents\anatomy_2>git add README.md

C:\Users\keanu\Documents\anatomy_2>git add water_drinking_pattern.png

C:\Users\keanu\Documents\anatomy_2>git commit -m "first commit"
[master (root-commit) 674491c] first commit
 2 files changed, 1 insertion(+)
 create mode 100644 README.md
 create mode 100644 water_drinking_pattern.png

C:\Users\keanu\Documents\anatomy_2>git branch -M main

C:\Users\keanu\Documents\anatomy_2>git remote add origin https://github.com/OmRamana/anatomy_2.git

C:\Users\keanu\Documents\anatomy_2>git push -u origin main
Enumerating objects: 4, done.
Counting objects: 100% (4/4), done.
Delta compression using up to 8 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (4/4), 36.63 KiB | 7.33 MiB/s, done.
Total 4 (delta 0), reused 0 (delta 0), pack-reused 0
To https://github.com/OmRamana/anatomy_2.git
 * [new branch]      main -> main
branch 'main' set up to track 'origin/main'.

C:\Users\keanu\Documents\anatomy_2>

cmd in the current directory;
Once you’re in the right folder, click on the address bar at the top and simply type in cmd and press Enter

Changes made to the github repo online, command line push method;
git pull origin master,
git push origin master

View git remote; git remote -v

Change git remote; git remote set-url <remote_name> <remote_url> eg git remote set-url origin https://git-repo/new-repository.git

