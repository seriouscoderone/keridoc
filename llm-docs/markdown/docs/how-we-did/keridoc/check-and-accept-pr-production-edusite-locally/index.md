# Check and accept PR production KERISSE site locally

Why this _how-we-did_: To test pull request offered before accepting them in github

For who: crew responsible for acceptance of PRs offered by content developers

What is the objective: To check content and code that is uploaded to the team as a PR.
```
git stash
git status
git fetch upstream main
git log
```
-   `fix-mdfiles` is the name of the PR.
-   `testSC1` is the acronym of the developer that I use in this example.
```
git checkout -b testSC1
git fetch upstream
git merge upstream/fix-mdfiles
```
Now the changes that the PR proposes have been locally applied to the new branch
```
npm run build
npm run serve
```
Now you can locally test the site at the address that look something like `http://localhost:3000keridoc/`. The result of `npm run serve` will tell you the exact URL.
```
git checkout main
git merge testSC1
```
```
git push -u upstream main
```
![](https://hackmd.io/_uploads/SkPSW_L6i.png)
```
git stash pop
git branch -D testSC1
```