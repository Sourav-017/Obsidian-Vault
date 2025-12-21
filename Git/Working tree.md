[[Git]]
### 👀 Example of a Working Tree

Suppose you have a Git project called `my-website`.

Your working tree might look like this:

`my-website/ 
	│── index.html 
	│── style.css 
	│── script.js 
	│── images/ 
	│     └── logo.png 
	└── README.md`

This folder **is the working tree**.  
You can open files, edit them, delete them — just like any normal folder.

---

### 🧠 The hidden part

Inside that folder is also a hidden Git folder called:

`.git/`

You normally don’t see it unless you turn on "show hidden files".  
This `.git` folder stores Git’s history and tracking info.

So a full view might look like:

`my-website/ 
	│── index.html 
	│── style.css 
	│── script.js 
	│── images/ 
	│     └── logo.png 
	└── README.md 
	│── .git/    <-- Git data (history, commits, branches)`

**Everything except `.git/` is the working tree.**