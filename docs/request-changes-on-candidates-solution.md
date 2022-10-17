# Requesting Changes

If a candidate completes a CodeScreen assessment but fails, you can give them a "second shot" by requesting changes on their solution.

To do this, first click into the candidate's report, and then click `Request Changes`. The following pop-up will appear:

<figure>
  <figcaption style="font-style: italic;"></figcaption>
  </br>
  <img style="max-width: 40%;" src="requestChanges.png" alt="Request Changes"/>
</figure>

<br>

You can either then leave comments directly in text box shown above & click the Submit button, or you can leave comments inside the candidate's GitHub repo (see section below for more details) and then click the Submit button.

That's it! The candidate will receive an email containing your comments, the candidate is granted back access to their GitHub repo and the candidate is moved back into the In Progress column.

Your access to the candidate's GitHub repo will be revoked once you hit the Submit button. Once the candidate addresses your comments and submits their updated solution, we re-run our analysis and grant you back access to the repo.

**Note** that all hidden unit test files are removed from the candidate's repo before we grant them back access.

- - -

### Adding Comments to GitHub repo


**1.** Navigate to the candidate's **GitHub** repository, and click on the commits section.

<figure>
  <figcaption style="font-style: italic;"></figcaption>
  </br>
  <img style="max-width: 60%;" src="repo.png" alt="GitHub repo"/>
</figure>

<br>

**2.** Now click on one of the candidate's commits.

<figure>
  <figcaption style="font-style: italic;"></figcaption>
  </br>
  <img style="max-width: 50%;" src="commitsList.png" alt="Commits list"/>
</figure>

<br>

**3.** You can either leave your comments on the commit or on a line of code in a particular file of that commit:

<br>

**3.1** To leave a comment on a commit, scroll down to the bottom of the commit page and you will see the `Leave a comment` box:

<figure>
  <figcaption style="font-style: italic;"></figcaption>
  </br>
  <img style="max-width: 60%;" src="commentOnCommit.png" alt="Comment on commit"/>
</figure>

Enter your comment about where the candidate went wrong and what you think they need to do to improve their solution, and then click the green `Comment on this commit` button. You can add as many comments as you like.

<br>

**3.2** To leave a comment on a line of code in a particular file, find the line(s) of code in the files shown in the commit and click on the **+** on the left-hand side.

<figure>
  <figcaption style="font-style: italic;"></figcaption>
  </br>
  <img style="max-width: 40%;" src="sourceFile.png" alt="Source file"/>
</figure>

<br>

Enter your comment about where the candidate went wrong and what you think they need to do to improve their solution, and then click the `Add single comment` button. You can add as many comments (on any number of files) as you like.

<figure>
  <figcaption style="font-style: italic;"></figcaption>
  </br>
  <img style="max-width: 60%;" src="sourceFileComment.png" alt="Resend assessment"/>
</figure>

<br>

Once you have added your comments to the GitHub repo, go back to Request Changes pop-up in the CodeScreen application and click the Submit button.

Please **note** that the candidate won't be able to see the hidden assessment case files after they get access back to the repo.<br>So please **do not** leave comments on the `"Added back hidden assessment files"` commit, as the candidate will not be able to see these comments.
