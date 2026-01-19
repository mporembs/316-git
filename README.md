# Guessing Game
## Initial Branch Structure
- **main:** The main production branch.
- **dev:** Wishes the user good luck at game start.
- **feature1:** Adds user game control functionality that enables users to quit a game or play again. Also provides additional 
  hint language in response to incorrect guesses.
- **feature2:** The game is limited to a maximum of 10 incorrect guesses.
- **feature3:** Provides user feedback if they are close or very close to guessing correctly. Only active after 3 guesses.

## Learning Summary
Consider a situation where we want to merge our feature branch into the dev branch. The dev branch has some changes that are not currently present in our feature branch. 

When we merge feature from dev git creates a new commit in the dev branch, which is pointed to by the latest commit on each branch as well as their common ancestor. This is called a three-way merge. In this situation, there maybe merge conflicts we will have to resolve by hand. As part of this resolution process we will have to run tests and verify the software is working as intended. This opens up the possibility of the dev branch being broken. It is a better idea to bring the latest changes from dev into our feature branch first. That way we can take more time to verify that everything is working as intended before we make changes to the dev branch.

We can to that by merging dev into the feature, which will keep all the commits on both branches as they currently are, or we can rebase dev onto our feature. With rebase git will make duplicates of our the commits in our feature branch and apply them one at time on top of the latest commit from the dev branch. These duplicates will be identical in content, but have different hashes. They will also appear in our log in a after the latest dev commit, even if they were originally commited sooner. So rebase rewrites history in a sense. For this reason you should only rebase private local branches.

Once our feature branch has all the latest changes from dev we can merge it into dev. Because the feature branch has all the latest changes from dev, this will be a fast forward merge. No merge commit will be created, the commits from feature will just be added to the dev timeline.

When merging we have option to squash our commits. This means that we will leave all the individual commits in the feature branch and summarize them into one single commit for the dev branch. This can keep things neater in the dev branch, but we will have to look in the feature branch if we want to look at them. They won't be referenced by the dev branch. The feature3 branch of the repo for this exercice is a good example of when this could be a good tool to use. The commit messages in its history were not very informative, so made sense that we squashed then before merging. They didn't have any information that would be useful from the dev branch.

The final concept to mention is cherry-pick. This is simply a command to apply a single commit to a branch. This often used to quickly resolve important issues, like a bug in the main/release branch.


