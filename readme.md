# How to add new images

## 1. Add the image
Copy your new image into the `images/` folder.
Rename it to the next number in the sequence, e.g. `art131.jpeg`
(match the extension to the file type: .png or .jpeg).

## 2. Generate the gallery code
Open Git Bash in the project folder (Shift + right-click → "Git Bash Here") and run:

    for f in images/*; do
      echo "<a href=\"$f\" target=\"_blank\"><img src=\"$f\" alt=\"\" loading=\"lazy\"></a>"
    done

Select all the lines that start with `<a href=` (NOT the command itself),
press Enter to copy.

## 3. Paste into index.html
Open `index.html` in Notepad. Find the line:

    <div class="gallery">

Click on the line after it, select everything down to `</div>`, and PASTE
(replacing the old lines). Save with Ctrl+S.

## 4. Check it worked
Back in Git Bash:

    grep -c "<img" index.html

The number should be your total images + 1 (the banner).
If it looks wrong, the paste/save didn't work — redo step 3.

## 5. Test it
Double-click `index.html`. Hard-refresh the browser with Ctrl+Shift+R
if it looks stale.

## 6. Push to GitHub
Open GitHub Desktop:
- READ the changes list first — it should only show index.html + your new image(s).
- If it shows a pile of DELETED files you didn't delete: STOP.
  In Git Bash run `git restore .` and start again.
- Commit (e.g. "Added 5 new artworks") → Push origin.

Done! The live site updates in a minute or two.

## Emergency: images disappeared locally
Don't panic. In Git Bash:

    git restore .

That restores everything to the last pushed state.
Never commit a wall of "deleted" files you didn't intend.