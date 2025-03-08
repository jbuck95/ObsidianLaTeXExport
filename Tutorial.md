
# 2) Preface

**Define 2 Locations in Obsidian** 

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
    ├── Eisvogel-3.1.0
    ├── uni.latex
    ├── latex-frontmatter

```

---

# 1) Download & Install

## Pandoc

>   https://pandoc.org/installing.html

![](Pasted%20image%2020250308170136.png)
## TeX Live

>   https://tug.org/texlive/windows.html#install

- Install. 

## Eisvogel

>   https://github.com/Wandmalfarbe/pandoc-latex-template/releases/tag/v3.1.0

-> Unzip and copy folder in your obsidian Template folder. 

## Templates

1) **Install UNITADE - Plugin to view and edit .latex in Obsidian:** 

![](Pasted%20image%2020250308173834.png)

##### Latex-Template
```latex
% !TeX program = lualatex
% !TeX encoding = UTF-8

\documentclass[12pt,a4paper]{article}
\setlength{\parindent}{0pt}

%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%% Farben definieren


% Pakete
\usepackage[flushmargin]{footmisc}  % Für bündige Fußnoten
\usepackage[margin=2cm]{geometry}
\usepackage{fontspec}
\usepackage{fancyhdr}
\usepackage{longtable}
\usepackage{array}
\usepackage{calc}
\usepackage{booktabs}
\usepackage{graphicx}
\usepackage{hyperref}
\usepackage[dvipsnames]{xcolor}
\usepackage{amsmath,amssymb}
\usepackage{listings}
\usepackage{csquotes}
\usepackage{polyglossia}
%\usepackage{microtype}
\usepackage{caption}
\usepackage{titlesec}
\usepackage{setspace}
\usepackage{quoting}
\usepackage{xurl}
\usepackage{fancyvrb}
\usepackage{footnote}
\usepackage{footnotebackref}
\usepackage[absolute,overlay]{textpos}

%%%%%%%%%%%%% Picprocessing
\makeatletter
\def\maxwidth{\ifdim\Gin@nat@width>\linewidth\linewidth\else\Gin@nat@width\fi}
\def\maxheight{\ifdim\Gin@nat@height>\textheight\textheight\else\Gin@nat@height\fi}
\makeatother

%%%%%%%%%%%%% In-line figures - korrekte Syntax
\let\Oldincludegraphics\includegraphics
\makeatletter
\renewcommand{\includegraphics}[2][]{\Oldincludegraphics[width=\maxwidth, #1]{#2}}
\makeatother

%%%%%%%%%%%%% Markdown-pic (auto-sizing with max-width)
\makeatletter
\def\ScaleIfNeeded{%
  \ifdim\Gin@nat@width>\linewidth
    \linewidth
  \else
    \Gin@nat@width
  \fi
}
\makeatother

%%%%%%%%%%%%% Command für pandoc bounded Images
\newcommand{\pandocbounded}[1]{#1}

%%%%%%%%%%%%%                                                  %    <- Picture Paths!
\graphicspath{                 %CHANGE 1
  {C:/Users/X/Y/Z/}
  {I:/X/Y/Z/}
}

%%%%%%%%%%%%% Spacing Text and Footnotes
\setlength{\skip\footins}{1.3cm}

%%%%%%%%%%%%% Fix for Pandoc-Listen
\providecommand{\tightlist}{%
\setlength{\itemsep}{0pt}\setlength{\parskip}{0pt}}

%%%%%%%%%%%%% Font                                             %    <- Font 
\setmainfont{Libertinus Serif}
\setmainlanguage{german}          %CHANGE 2        %    <- Set your Language

%%%%%%%%%%%%% geometry                                         %    <- Side margins
\geometry{top=3cm, bottom=3cm, left=3cm, right=6cm}

%%%%%%%%%%%%% Zeilenabstand                                    %    <- line spacing
\setstretch{1.56}

%%%%%%%%%%%%% Head / Footnote
\pagestyle{fancy}
\fancyhead{}
\fancyhead[R]{$surname$ \textbar{} $shorttitle$}
\setlength{\headheight}{14.5pt}
\addtolength{\topmargin}{-2.5pt}

% Footnotesettings
\renewcommand{\footnotesize}{\fontsize{9pt}{11pt}\selectfont}
\renewcommand{\footnoterule}{%
  \kern -3pt % spacing upwards
  \hrule width \headwidth height 0.4pt % Linie mit der Breite der Kopfzeile
  \kern 2.6pt % spacing downward
}
% Headerseatting 
\renewcommand{\headrule}{%
  \hrule width \headwidth height 0.4pt % Linie mit der Breite der Kopfzeile
  \kern 2.6pt % 
}

\fancyfoot{}
\fancyfoot[R]{\thepage}

% spacing Text and Footnotes
\setlength{\skip\footins}{1.3cm}


%%%%%%%%%%%%% Section formatting
\titleformat{\section}{\large\bfseries}{\thesection}{1em}{\raggedright}
\titleformat{\subsection}{\normalsize\bfseries}{\thesubsection}{1em}{\raggedright}

%%%%%%%%%%%%% Block quotes
\quotingsetup{vskip=5pt,leftmargin=1.5cm,rightmargin=1.5cm}

%%%%%%%%%%%%% Hyperref-config
\hypersetup{
  pdftitle={$title-meta$},
  pdfauthor={$author-meta$},
  pdfsubject={$subject$},
  pdfkeywords={$for(keywords)$$keywords$$sep$, $endfor$},
  pdfborder={0 0 0},
  breaklinks=true,
  colorlinks=true,
  linkcolor=$if(linkcolor)$$linkcolor$$else$black$endif$,
  citecolor=$if(citecolor)$$citecolor$$else$Blue$endif$,
  urlcolor=$if(urlcolor)$$urlcolor$$else$Blue$endif$,
  filecolor=$if(filecolor)$$filecolor$$else$teal$endif$
}

%%%%%%%%%%%%% Syntax-Highlighting
$if(highlighting-macros)$
$highlighting-macros$
$endif$

%%%%%%%%%%%%% Listings-Settings Code blocks
\lstset{
  basicstyle=\ttfamily\small,
  columns=flexible,
  breaklines=true,
  breakatwhitespace=false,
  keepspaces=true,
  numbers=left,
  numberstyle=\tiny\color{gray},
  showstringspaces=false,
  commentstyle=\color{gray},
  keywordstyle=\color{blue},
  stringstyle=\color{green},
  frame=single,
  framesep=3pt,
  framerule=0.4pt,
  rulecolor=\color{black!30},
  backgroundcolor=\color{black!5},
}

%%%%%%%%%%%%% Table Setting
\renewcommand{\arraystretch}{1.5}

\sloppy

%%%%%%%%%%%%% Deckblatt
\begin{document}

\begin{titlepage}

%%%%%%%%%%%%% Position of the Picture
\begin{textblock*}{6cm}(13cm,2cm) % Breite: 6cm, Position (x=13cm, y=2cm)
\includegraphics[width=6cm]{uni.png}   %CHANGE 3
\end{textblock*}

%%%%%%%%%%%%% Seminar-Info TopLeft
\vspace*{-2cm}
\begin{flushleft}
Seminar: $seminar$\\
$semester$\\
$professor$\\
\end{flushleft}

%%%%%%%%%%%%% Title and Subtitle
\begin{textblock*}{10cm}(5cm,11cm)
\begin{center}
\textbf{\Huge $title$}\\[0.5cm]
\textbf{\Large $subtitle$}\\
\end{center}
\end{textblock*}

%%%%%%%%%%%%% Spacing Author and Author Info
\vfill 


%%%%%%%%%%%%% Author-Info BottomLeft
\begin{flushleft}
\textbf{$name$ $surname$}\\
$address$\\
$email$\\
Matrikel: $matrikel$\\
Studiengang: $studiengang$\\
Modul: $modul$\\
Pr\"ufungsnr.: $pruefungsnr$\\
Abgabedatum: $abgabedatum$\\
\end{flushleft}
\end{titlepage}

$if(abstract)$
\begin{abstract}
$abstract$
\end{abstract}
$endif$

\newpage

$if(toc)$
\tableofcontents
\newpage
$endif$

$if(lot)$
\listoftables
\newpage
$endif$

$if(lof)$
\listoffigures
\newpage
$endif$
%%%%%%%%%%%% Here goes the .md Content
% Rest of your document
$body$

%%Bibliography
\newpage
$if(bibliography)$ \printbibliography$if(biblio-title)$[title=$biblio-title$]$endif$ $endif$


$if(bibliography)$
\printbibliography$if(biblio-title)$[title=$biblio-title$]$endif$
$endif$

%%%%%%%%% Eigenständigkeits- und andere Erklärungen  %CHANGE 4
\newpage
\section*{Eidesstattliche Erklärung}
\addcontentsline{toc}{section}{Eidesstattliche Erklärung}

Ich versichere hiermit an Eides Statt, dass ich die vorliegende Arbeit
mit dem Titel \newline
\textbf{Titel} \newline
selbstständig und ohne unerlaubte fremde Hilfe erbracht habe. Ich
habe keine anderen als die angegebenen Quellen und Hilfsmittel
benutzt. Für den Fall, dass die Arbeit zusätzlich auf einem Datenträger
eingereicht wird, erkläre ich, dass die schriftliche und die
elektronische Form vollständig übereinstimmen. Die Arbeit hat in
gleicher oder ähnlicher Form noch keiner Prüfungsbehörde
vorgelegen. \newline\newline

Germany, den 15. März 2021 \newline
Der Die Das 

\begin{textblock*}{3cm}(10cm,13.5cm) % (x=cm, y=cm)            % Signature 1
\includegraphics[width=4cm]{sign.png}    % <- Size pic
\end{textblock*}

\newpage        % Second Legal Notice 

% Legal Notice (Belehrung)
\section*{Belehrung}
\addcontentsline{toc}{section}{Belehrung}

\textbf{Entzug des Prüfungsanspruchs}

\begin{enumerate}
    \item Das Fälschen fremder Arbeiten oder andere Betrugsversuche können zum Entzug des Prüfungsanspruchs führen.
    \item In schwerwiegenden Fällen kann auch der Anspruch auf eine Wiederholungsprüfung verwirkt sein.
\end{enumerate}

\section*{§ 156 StGB: Falsche Versicherung an Eides Statt}
Wer vor einer zur Annahme einer Versicherung an Eides Statt zuständigen Behörde eine solche Versicherung falsch abgibt oder unter Berufung auf eine solche Versicherung falsch aussagt, wird mit Freiheitsstrafe bis zu drei Jahren oder mit Geldstrafe bestraft.

\section*{§ 161 StGB: Fahrlässige falsche Versicherung an Eides Statt}
\begin{enumerate}
    \item Wenn eine der in den §§ 124 bis 156 bezeichneten Handlungen aus Fahrlässigkeit begangen worden ist, so tritt Freiheitsstrafe bis zu einem Jahr oder Geldstrafe ein.
    \item Straflosigkeit tritt ein, wenn der Täter die falsche Angabe rechtzeitig berichtigt. Die Vorschriften des § 155 Abs. 2 und 3 gelten entsprechend.
\end{enumerate}

\textbf{Die vorstehende Belehrung habe ich zur Kenntnis genommen.}

Germany, den 15. März 2021 \newline
Der Die Das
 
\begin{textblock*}{3cm}(8cm,24.5cm) % (x=cm, y=cm)           % Signature 2
\includegraphics[width=4cm]{sign.png}   % <- Size pic
\end{textblock*}


\end{document}
```

##### Frontmatter-Template
```
---
title: Titel 
subtitle: Subtitle, if needed
shorttitle: Paper
name: Name
surname: Surname
semester: Semester
seminar: Titel Seminars
professor: Prof. Dr. XYZ
address: Behind-the-Moon-Str. 20, Germany
email: XYZ@googlemail.com
matrikel: "0190"
studiengang: Field of Study
modul: XY
pruefungsnr: XY
abgabedatum: 30. März 2022
toc: "true"
---




\pagebreak 

# Bibliographie





\pagebreak




```


##### Setting up the Latex-Template 


2)  open the .latex template inside Obsidian
3) Change the 5 lines i maked with % CHANGE
	1) Language
	2) Image path
	3) Picture University
	4) & 5) Signatures


# 2) Enhancing-Export 

#####  Settings (Export-Setting)
1) Set "Default Folder for Exported File"

![](Pasted%20image%2020250308173940.png)


2) **Set Arguments**
```
-f ${fromFormat} --resource-path="${currentDir}" --resource-path="${attachmentFolderPath}" --resource-path="PATH/TO/PICTURE/FOLDER/" --resource-path="${pluginDir}/textemplate" --template="PATH\TO\TEMPLATE.latex" --pdf-engine=xelatex --listings -o "${outputPath}" -t pdf
```

- **Set your Paths:** 

	1) *(Folder-)Path* to your Resources or Picture Folder in Obsidian 
	2) *(File-)Path* to your .latex Template 

3) **Set Extra-Arguments**

```
--pdf-engine=xelatex
```



# 3) Extra: Convert your .docx to .md

- including footnotes etc. 

**In the Directory of your .docx, open Terminal and run:**
```powershell
pandoc INPUT.docx -o OUTPUT.md --wrap=none --markdown-headings=atx --reference-links --strip-comments --extract-media=./media

```



# 4) Debugging 

If you want to debug, i highly suggest not doing it with the enhancing-export error notifications (can't copythem?!). You should open the folder of your .md Note you want to export, and then open a terminal in that folder. 

Directly try to run pandoc from there with --verbose option, so you have a full error message in the console:

```powershell
 pandoc Test.md -o example.pdf --from markdown --template="I:/PATH/TO/uni.latex" --listings --pdf-engine=xelatex --resource-path="I:/PATH/TO/Pictures" --verbose 
```





