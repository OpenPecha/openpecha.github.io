# OpenPecha Repositories

OpenPecha etexts are stored as Git repositories. At its heart, Git is a version control system that manages and stores revisions of digital projects. OpenPecha simply uses Git to store and manage versions of Tibetan texts. Within the Git system, OPF files come with the following branches: 
- **Master**
  The master branch contains the .opf, which is protected
  Only admins and text owners can directly update the master branch from the other online branches 

- **Publication**
  The publication branch is for collaboratively improving the text
  Only admin or text owners can merge changes from the publication branch to the master branch
  Github action is set up in such a way that it looks for commands issued by the owner in the commits, then updates the .opf in the master branch if there are changes in the publication branch

- **Custom repos**:
  This is where users outside of the collaboration team can edit text and export the text into a desirable format—so long as the parser can handle the user’s specifications, they can collaborate with OpenPecha to create it
  These edits are not recorded, so they are not used for updating the master branch OPF
  The exported text is released in the “temp” section of the release

- **Releases**
  Initial section contains the src text as-is; they may be plain text, ebook, HFML, word, etc
  Temp section contains the exported text of the user outside of the collaboration
  V### section contains the official release of the exported text
  
