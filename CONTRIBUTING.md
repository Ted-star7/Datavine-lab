# Contributing — Datavine-lab (Group 13)

`main` is protected. Nobody pushes to it directly. All work goes through
 (PRs) that the repo owner reviews and merges.

## What is a PR?

A **Pull Request** is how you ask for your finished work on your branch to be
 and merged into `main`. You open it on GitHub; it shows your changes,
the owner reviews them, and **Merge**.

## Branch ownership

| Person        | Branch                            | Notebook                              |
|---------------|-----------------------------------|---------------------------------------|
| Dennis        | `feature/wine-classification`     | `notebooks/01_wine_classification.ipynb` |
| Jeff          | `feature/feed-recommendation`     | `notebooks/02_feed_recommendation.ipynb` |
| Eglen & Teddy | `feature/arrests-clustering`      | `notebooks/03_arrests_clustering.ipynb`  |
| Teddy         | `feature/integration-evaluation`  | `notebooks/04_integration_evaluation.ipynb` |



## Every time you start work

```bash
git checkout main
git pull origin main                 # get the latest main
git checkout feature/your-branch     # your branch from the table above
git merge main                       # bring your branch up to date
```

## Save and push your work

```bash
git add .
git commit -m "short message about what you did"
git push origin feature/your-branch
```

## Open a Pull Request

On GitHub, the repo will show a **"Compare & pull request"** button after you push.
Click it, make sure base = `main` and compare = your branch, then
**Create pull request**. The owner is notified, reviews, and merges.

After a PR is merged, everyone runs `git checkout main && git pull` to stay current.


- Coordinate on chat before touching shared files.
