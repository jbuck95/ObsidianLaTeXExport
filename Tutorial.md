
# 0) Preface

**Define 2 Locations in Obsidian** (you probably already did so..)

1) **Folder For Pictures** 
	- holding your pictures for latex! (Pictures in .md will get rendered, but need to be in. .md syntax, not wiki links! If you have problems, i suggest installing link-converter plugin)

2) **Folder for Templates**
	- holding your frontmatter-Template and your latex template. You can set different Paths for these if you want. 

Shoud look something like this after Install: 

---
```
Vault/
└── Pictures/
└── Templates/
    ├── Eisvogel-X.X.X
    ├── uni.latex
    ├── Frontmatter-Template.md
```

---


# 1) Download & Install

## 1. Font: libertinus-otf

I use libertinus-otf which allows you to use math, old greek etc. and other symbols. Aswell (and Serif + Ligatures)

## 2. Pandoc

>   https://pandoc.org/installing.html

## 3. TeX Live

>   https://tug.org/texlive/windows.html#install

- Install. 

## 4. Eisvogel

>   https://github.com/Wandmalfarbe/pandoc-latex-template/releases/tag/v3.1.0

-> Unzip and copy folder in your obsidian Template folder. 

## 5. Templates

1) **Install UNITADE - Plugin to view and edit .latex in Obsidian:** 

->  should look like `txt > latex` in the settings. 

**Download my Template:** 


### Setting up the Latex-Template 


2)  open the .latex template inside Obsidian
3) Change the 5 lines i maked with % CHANGE
	1) Language
	2) Image path
	3) Picture University
	4) & 5) Signatures


# 2) Enhancing-Export Setup

1) **Set "Default Folder for Exported File"**

2) **Set Arguments**
```
-f ${fromFormat} --resource-path="${currentDir}" --resource-path="${attachmentFolderPath}" --resource-path="PATH/TO/PICTURE/FOLDER/" --resource-path="${pluginDir}/textemplate" --template="PATH\TO\TEMPLATE.latex" --pdf-engine=lualatex --listings -o "${outputPath}" -t pdf
```

- **Set your Paths:** 

	1) *(Folder-)Path* to your Resources or Picture Folder in Obsidian 
	2) *(File-)Path* to your .latex Template 



# 3) Extra: Convert your .docx to .md

Check my Plugin *Docx-To-Md-Converter* (working Footnotes for latex conversion but still in Beta):

	https://github.com/jbuck95/DTM



# 4) Debugging 

If you want to debug, i highly suggest not doing it with the enhancing-export error notifications (can't copythem?!). You should open the folder of your .md Note you want to export, and then open a terminal in that folder. 

Directly try to run pandoc from there with --verbose option, so you have a full error message in the console:

```powershell
 pandoc Test.md -o example.pdf --from markdown --template="I:/PATH/TO/uni.latex" --listings --pdf-engine=xelatex --resource-path="I:/PATH/TO/Pictures" --verbose 
```





