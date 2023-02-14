The easiest way would be to find the head commit of the branch as it was immediately before the rebase started in the reflog...
````
git reflog
````
and to reset the current branch to it (with the usual caveats about being absolutely sure before reseting with the --hard option).

Suppose the old commit was HEAD@{2} in the ref log:

````
git reset --hard HEAD@{2}
````

In Windows, you may need to quote the reference:
````
git reset --hard "HEAD@{2}"
````
