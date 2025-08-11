# 📝 Unit 1 – Git & GitHub Assignment Answers
_CodingGita Edition_

This file contains the **exact Git commands** that answer all 200 Unit‑1 Git & GitHub assignment questions.

---

## **Part A – Git Initialization & Cloning (1–40)**

1. `git init`  
2. `git clone https://github.com/example/repo.git`  
3. `git init --bare central-repo`  
4. `git clone https://github.com/example/repo.git project-app`  
5. `git init`  
6. `git clone --branch main https://github.com/example/repo.git`  
7. `git clone git@github.com:user/repo.git`  
8. `git init --bare`  
9. `git clone https://github.com/example/repo.git && git remote rename origin upstream`  
10. `git init /home/student/projects/notes`  
11. `git clone /home/student/repos/sample.git`  
12. `git clone -b feature https://github.com/example/repo.git`  
13. `git init --initial-branch=main`  
14. `git clone --depth 1 https://github.com/example/repo.git`  
15. `git init && git config core.ignorecase true`  
16. `git clone https://github.com/example/repo.git cg-project`  
17. `git clone https://<TOKEN>@github.com/user/repo.git`  
18. `mkdir my-folder && cd my-folder && git init`  
19. `git clone --mirror https://github.com/example/repo.git`  
20. `git init && git add . && git commit -m "start"`  
21. `git clone --recurse-submodules https://github.com/example/repo.git`  
22. `git clone --branch v1.0 https://github.com/example/repo.git`  
23. `git clone --recursive https://github.com/example/repo.git`  
24. `git init && git config user.name "Your Name"`  
25. `git clone --mirror https://github.com/example/repo.git`  
26. `git clone https://gitlab.com/username/repo.git`  
27. `git clone -c http.sslVerify=false https://github.com/example/repo.git`  
28. `git clone --depth 5 https://github.com/example/repo.git`  
29. `git clone --filter=blob:none https://github.com/example/repo.git`  
30. `git init -b dev`  
31. `git fetch --all`  
32. `git clone --no-checkout --branch feature https://github.com/example/repo.git`  
33. `git init && git config --global user.email "you@example.com"`  
34. `git clone https://github.com/example/repo.git && git config credential.helper store`  
35. `git clone --no-lock https://github.com/example/repo.git`  
36. `git clone -c core.sshCommand="ssh -i ~/.ssh/custom_key" git@github.com:user/repo.git`  
37. `git init && git config core.autocrlf input`  
38. `git clone -c gc.auto=0 https://github.com/example/repo.git`  
39. `git clone https://github.com/example/repo.git && git remote set-url --push origin git@github.com:user/repo.git`  
40. `git init && git remote add origin https://github.com/example/repo.git`  

---

## **Part B – Git Status & Staging (41–80)**

41. `git status`  
42. `git add index.html`  
43. `git add .`  
44. `git reset HEAD README.md`  
45. `git add docs/`  
46. `git add *.js`  
47. `git add -p`  
48. `git add "my file.txt"`  
49. `git commit -am "message"`  
50. `git status -sb`  
51. `git add app.js`  
52. `git add -u`  
53. `git add old_data.csv`  
54. `git reset`  
55. `git add -u`  
56. `git add ../shared-folder`  
57. `git add *.txt`  
58. `git add -p`  
59. `git add . ':!secret.key'`  
60. `git ls-files --others --exclude-standard | xargs git add`  
61. `git reset HEAD file.txt`  
62. `git add *.md`  
63. `git diff --name-only HEAD^ | xargs git add`  
64. `git add --ignore-errors`  
65. `git update-index --assume-unchanged file.txt`  
66. `git add --all`  
67. `git add config*`  
68. `git add -u`  
69. `git add -u`  
70. `git status --ignored`  
71. `git rm file.txt`  
72. `git add symlink`  
73. `git add 'pattern*'`  
74. `git add **/*.md`  
75. `git add . ':!*.log'`  
76. `git show --name-only <commit> | xargs git add`  
77. `git add -p ':!dir/*'`  
78. `git add --dry-run .`  
79. `git add *fix*`  
80. `git reset`  

---

## **Part C – Git Commit & Logs (81–120)**

81. `git commit -m "initial commit"`  
82. `git commit -am "message"`  
83. `git commit -m "Fix 'bug' in code"`  
84. `git commit -s -m "message"`  
85. `git commit --amend -m "updated docs"`  
86. `git commit --author="Name <email>" -m "message"`  
87. `git commit -m "message"`  
88. `git commit file.txt -m "message"`  
89. `git commit -am "message"`  
90. `git log --oneline`  
91. `git log --graph --oneline --all`  
92. `git log -n 5`  
93. `git log --author="John Doe"`  
94. `git log --grep="fix"`  
95. `git log -- app.js`  
96. `git log --after="YYYY-MM-DD" --before="YYYY-MM-DD"`  
97. `git show <commit>`  
98. `git show`  
99. `git log --author="email@example.com"`  
100. `git log --reverse`  
101. `git log --reverse`  
102. `git rebase -i --signoff`  
103. `git log --stat`  
104. `git log -- <file>`  
105. `git log --relative-date`  
106. `git diff <commit1> <commit2> -- file.txt`  
107. `git show <commit> --patch`  
108. `git cherry-pick <commit>`  
109. `git reset --soft HEAD~1`  
110. `git log --pretty=%s`  
111. `git log --pretty=format:"%h %an %ae"`  
112. `git rev-list --count HEAD`  
113. `git reset --hard <commit>`  
114. `git commit --allow-empty -m ""`  
115. `GIT_AUTHOR_NAME="Name" GIT_AUTHOR_EMAIL="email@example.com" git commit -m "msg"`  
116. `git show --pretty=fuller`  
117. `git commit --amend`  
118. `git commit -S -m "msg"`  
119. `git revert <commit>`  
120. `git tag -a v1.0 -m "Version 1.0"`  

---

## **Part D – Git Configuration (121–160)**

121. `git config --global user.name "Alice Smith"`  
122. `git config --global user.email "alice@example.com"`  
123. `git config --list`  
124. `git config --global core.editor "code --wait"`  
125. `git config --global core.editor notepad`  
126. `git config --global color.ui auto`  
127. `git config --global init.defaultBranch main`  
128. `git config --global --unset core.editor`  
129. `git config --global --list`  
130. `git config user.name "Local Name"`  
131. `git config --global credential.helper store`  
132. `git config --global credential.helper 'cache --timeout=3600'`  
133. `git config --system --list`  
134. `git config --global merge.tool vimdiff`  
135. `git config --global http.sslVerify false`  
136. `git config --global core.autocrlf true`  
137. `git config --global init.templatedir ~/.git-template`  
138. `git config --global alias.st status`  
139. `git config --global alias.co checkout`  
140. `git config --global alias.br branch`  
141. `git config --global push.default simple`  
142. `git config --global user.signingkey <key-id>`  
143. `git config core.fileMode false`  
144. `git config --global diff.tool vimdiff`  
145. `git config --global core.excludesfile ~/.gitignore_global`  
146. `git config --list --show-origin`  
147. `git config --global gc.auto 1`  
148. `git config --global http.proxy http://proxy.example.com:8080`  
149. `git config --global http.sslVerify false`  
150. `git config --global advice.statusHints true`  
151. `git config --global pull.rebase true`  
152. `git config --global commit.template ~/.gitmessage.txt`  
153. `git remote get-url origin`  
154. `git remote set-url origin https://github.com/user/repo.git`  
155. `git remote rename origin upstream`  
156. `git config --global --unset-all alias.st`  
157. `git log --pretty=email`  
158. `git config user.email "local@example.com"`  
159. `git config --global apply.ignorewhitespace change`  
160. `git config --global help.autocorrect 1`  

---

## **Part E – Git Workflow & Common Operations (161–200)**

161. `git ls-files --others --exclude-standard`  
162. `git add file.txt`  
163. `git commit -m "message"`  
164. `git diff`  
165. `git diff --cached`  
166. `git reset HEAD file.txt`  
167. `git rm file.txt`  
168. `git checkout -- file.txt`  
169. `git restore --staged file.txt`  
170. `echo node_modules/ >> .gitignore`  
171. `git status --ignored`  
172. `touch logs/.gitkeep`  
173. `git show HEAD`  
174. `git rev-parse HEAD`  
175. `git checkout HEAD~1`  
176. `git checkout <commit>`  
177. `git checkout main`  
178. `find .git/objects -type f`  
179. `git status`  
180. `git switch main`  
181. `git checkout -b feature1`  
182. `git checkout main && git merge feature1`  
183. `git branch -d feature1`  
184. `git push origin --delete feature1`  
185. `git branch -m oldname newname`  
186. `git push origin main`  
187. `git pull`  
188. `git fetch`  
189. `git rebase main`  
190. `git branch`  
191. `git remote -v`  
192. `git tag v1.0`  
193. `git push origin --tags`  
194. `git tag`  
195. `git stash`  
196. `git stash apply`  
197. `git stash drop stash@{0}`  
198. `git stash list`  
199. `git stash pop`  
200. `git stash apply stash@{0}`  

---

✅ **Tip for Students:**  
Try to **run each command yourself** in a test repository. Understanding what happens is more important than just memorizing them.
