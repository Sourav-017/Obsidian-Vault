[[Git]]
Pulling will update your project with the latest version from the remote repository.

But here’s the key idea:

### When you run `git pull`, Git does two things:

1. `git fetch` → downloads the latest changes
    
2. `git merge` → merges those changes into your working tree
    

So after `git pull`, your local project will contain:

- new files added by others
    
- edits to existing files
    
- deleted files
    
- updated commit history
    

---

### 📌 Example

You have this locally:

`file1.txt file2.txt`

Someone adds `file3.txt` on GitHub.

After `git pull`, your local folder becomes:

`file1.txt file2.txt file3.txt`

---

### ⚠️ One important thing to know

Pulling **updates your code**, but if:

- you modified files locally and
    
- remote has conflicting changes
    

you may get a **merge conflict**.

Example:

You changed `main.py`,  
someone changed `main.py` too.

Pull won’t overwrite silently.  
Git will ask you to fix conflicts manually.

---

### Simple summary

- If you have no local edits → pull updates safely.
    
- If you have local edits → pull may require merging.
    

---

### 🌳 In short:

`git clone`: get project first time  
`git pull`: update existing project