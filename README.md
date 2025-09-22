# selab
SSH-Keygen: ssh-keygen -t rsa -C atlurivenkat1@gmail.com

git:

config :

git config --global user.name "santu-1506"
git config --global user.email "atlurivenkat1@gmail.com"
git config --list

repo setup:

git remote -v 
git remote add origin <repo_url>
git remote remove origin
git remote set-url origin <new_url>

staging and commit:

git status → Check file states.
git add file.txt → Stage file.
git add . → Stage everything.
git reset file.txt → Unstage file but keep changes.
git commit -m "message" → Commit staged changes.
git commit --amend -m "new message" → Fix last commit message

fetching and pulling:

 git push origin main → Push local commits.
 git push -u origin main → Push & set upstream (first time).
 git pull origin main → Fetch + merge remote changes.
 git fetch origin → Download without merging.
 git fetch origin branch-name → Fetch specific branch.
 git rebase origin/main → Reapply local commits on top of remote.


branching:

 git branch → List branches.
 git branch branch-name → Create branch.
 git checkout branch-name → Switch branch.
 git checkout -b new-branch → Create & switch.
 git branch -d branch-name → Delete branch (safe).
 git branch -D branch-name → Force delete branch.
 git branch -r → List remote branches.
 git branch --merged → See merged branches.
 git remote prune origin → Remove deleted remote branches


merging and conflicts:

 git merge branch-name → Merge into current branch.

 Conflict resolution: open file, fix markers (
 bash
 git add file
 git commit
 <<<<<<< / 
======= / 
>>>>>>> ), then:

 git stash → Save changes temporarily.
 git stash apply → Restore stashed changes


undoing:

 git restore file.txt → Undo changes before staging.
 git reset file.txt → Remove from staging.
 git revert <commit_hash> → Create new commit that undoes a commit.
 git reflog → See history of HEAD, recover deleted branch.


history:

 git log → Full commit history.
 git log --oneline → Short history.
 git show <commit_hash> → Show details of commit.
 git diff → Show unstaged changes.
git blame file.txt → See who changed each line.


-----------------------------------------


docker:

FROM tomcat:9.0
COPY ./target/name.war /usr/local/tomcat/webapps/ROOT.war
CMD ["catalina.sh","run"]

+++++++++++++++++++++++
docker-compse yml

version: "3.9"

services:
  web:
    image: your-image     # App image
    ports:
      - "8000:8080"     # Map local 8000 → container 8080
    depends_on:
      - mysql     # Start MySQL before web app

  mysql:
    image: mysql:8.0     # MySQL DB image
    environment:
      MYSQL_ROOT_PASSWORD: root     # Root password
      MYSQL_DATABASE: university    # DB name
      MYSQL_USER: user              # DB user
      MYSQL_PASSWORD: password      # DB password
    ports:
      - "3306:3306"     # Expose DB port


++++++++++++++++++++++++

docker build -t oles-app .     # Build Docker image
docker run -d -p 8088:8080 --name oles-ooga oles-app     # Run container in detached mode
docker-compose up -d     # Start all services from docker-compose.yml
docker exec -it oles-mysql-1 mysql -u root -p     # Open MySQL shell
docker tag oles-app santu-1506/oles-app     # Tag local image for DockerHub
docker push santu-1506/oles-app     # Push image to DockerHub
