<span class="tag">Tags</span>:   [[Coding]]  

Created at 2024-10-18 21:10
<span class="tag">Status</span>: <span class="success"> Done but can be better </span>
<span class="danger">Sources</span>: YT - Nick White

# Git
Git is a memory card for code...
We use Git to save our code from ourselves.

```shell
git init
```
We use this command to initialize an empty git repository.

```shell
git add main.c
```
Saves only `main.c`.

```shell
git add .
```
Saves all files.

```shell
git commit -m '-m is used to DESCRIBE the changes'
```
Commits the changes to Git memory.

```shell
git log
```
We can take a look at every commit we did. and it gives us a hash code to be able to get back to it.

```shell
git checkout [THE HASH CODE]
```
This takes us back to the commit of that **hash code**. when we do this we will go to a different branch.

```shell
git branch
```
Shows the branches.

```shell
git remote add origin [URL]
```
It gets your repository from the URL.

```shell
git push -u origin main
```
It pushes your git progress to the website.

## Branches
By default all the code is on the master branch.
If you want to do something that may be risky and you don't want to do it on your main project you'll make a new branch.

```shell
git branch -M main
```
switches to the main branch.






# References
