---
layout: post
title: Undoing a Git Merge
published: true
redirect_from:
  - /blog/2014/12/19/undoing-a-git-merge/
---

I recently needed to merge several topic branches into a client's staging branch, starting the
 process apparently before I drank enough morning coffee and wound up with a pretty nasty set of merge conflicts. The conflicts came about because I merged the branches in an improper order, starting by merging a branch which was based off the other branch that additionally required merging, winding up with a mess that looked like this:

    $ git merge add_client_comments_83612372
    Auto-merging db/schema.rb
    CONFLICT (content): Merge conflict in db/schema.rb
    Auto-merging app/views/specifications/show.html.erb
    CONFLICT (content): Merge conflict in app/views/specifications/show.html.erb

Fortunately, undoing a Git merge containing conflicts you&rsquo;d rather avoid is pretty easy. Begin by reviewing your recent commits:

    $ git log --oneline -n3
    6c1557d Merged branch add_comments_83612372
    0fd0892 Merge branch 'editable_82327726' into staging
    c07eca0 finish with edits to top nav

I want to revert back to the commit associated with `0fd0892`, and so I'll next execute `reset`, identifying the commit SHA:

    $ git reset --hard c07eca0
    HEAD is now at c07eca0 finish with edits to top nav

With that done, I can begin the merge process anew.

The bottom line on this matter is that Git can be a bit scary at times, however when circumstances such as the above arise it's a certainty you'll be able to deal with them in a sane fashion; just be sure to do a bit of homework before executing any commands which deal with effectively destroying uncommitted data, because once that data is gone it is gone forever (or until you rewrite the code)!
