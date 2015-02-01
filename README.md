<div id="table-of-contents">
<h2>Table of Contents</h2>
<div id="text-table-of-contents">
<ul>
<li><a href="#sec-1">1. Introduction</a></li>
<li><a href="#sec-2">2. Latest change</a></li>
<li><a href="#sec-3">3. My environment</a></li>
<li><a href="#sec-4">4. org-mode settings</a></li>
</ul>
</div>
</div>


# Introduction<a id="sec-1"></a>

This file **IS NOT** the tutorial, and the **PDF file** in the repo is that.

In **Latest change**, I introduce changes of the tutorial.
This part is for readers.

In **My environment**, I show my envinronment information.
This part is for those who want to write and export.

In **org-mode settings**, I list my settings about org-mode.
Both readers and writers can use it.

# Latest change<a id="sec-2"></a>

For those who want to have a glance at the newest commit,
I add this part.
You can download the new compiled PDF file only when you find
something which you're interested in here.

---

<p class="verse">
2015-02-01<br  />
Add contents about org-mode exporting to PDF, including how to set your own LATEX CLASS<br  />
2015-01-31<br  />
Add some contents of org-mode exporting to PDF<br  />
</p>

# My environment<a id="sec-3"></a>

I write this document in Emacs 24.3.1 with org-mode 8.3beta.

According to my experience, there are some changes between org-mode 7.9 and 8.3beta.
So I suggest you'd better use org-mode greater than 8.0 to export the org file.

# org-mode settings<a id="sec-4"></a>

Here is my settings about org-mode.
While satisfing all the dependences, you can use it directly when exporting to PDF files.

Dependences are listed below:

-   latex pakcages
    -   listings
    -   color
    -   hyperref
    -   xcolor
    -   fontspec
    -   indentfirst
    -   xunicode
    -   amsmath
    -   graphicx
-   fronts
    -   SimSun
    -   DejaVu Sans
    -   DejaVu Serif
    -   DejaVu Sans Mono

I list two latex classes, my-org-book-zh and my-org-aritcle-zh,
they both support Chinese.
You can use what you like, or create a new one.

    ; org-mode export to latex
    (require 'ox-latex)
    (setq org-export-latex-listings t)
    ; org-mode source code setup in exporting to latex
    (add-to-list 'org-latex-listings '("" "listings"))
    (add-to-list 'org-latex-listings '("" "color"))
    
    (add-to-list 'org-latex-packages-alist
                 '("" "hyperref" t))
    (add-to-list 'org-latex-packages-alist
             '("" "xcolor" t))
    (add-to-list 'org-latex-packages-alist
             '("" "listings" t))
    (add-to-list 'org-latex-packages-alist
             '("" "fontspec" t))
    (add-to-list 'org-latex-packages-alist
             '("" "indentfirst" t))
    (add-to-list 'org-latex-packages-alist
             '("" "xunicode" t))
    (add-to-list 'org-latex-packages-alist
             '("" "amsmath"))
    (add-to-list 'org-latex-packages-alist
             '("" "graphicx" t))
    
    (add-to-list 'org-latex-classes
              '("my-org-book-zh"
    "\\documentclass{book}
    \\usepackage[slantfont, boldfont]{xeCJK}
    % chapter set
    \\usepackage[Lenny]{fncychap}
    [NO-DEFAULT-PACKAGES]
    [PACKAGES]
    \\setCJKmainfont{SimSun} % 设置缺省中文字体
    \\parindent 2em
    
    \\setmainfont{DejaVu Sans} % 英文衬线字体
    \\setsansfont{DejaVu Serif} % 英文无衬线字体
    \\setmonofont{DejaVu Sans Mono} % 英文等宽字体
    
    
    \\defaultfontfeatures{Mapping=tex-text} %如果没有它，会有一些 tex 特殊字符无法正常使用，比如连字符。
    
    % 中文断行
    \\XeTeXlinebreaklocale \"zh\"
    \\XeTeXlinebreakskip = 0pt plus 1pt minus 0.1pt
    
    % 代码设置
    \\lstset{numbers=left, 
    numberstyle= \\tiny, 
    keywordstyle= \\color{ blue!70},commentstyle=\\color{red!50!green!50!blue!50}, 
    frame=shadowbox, 
    breaklines=true,
    rulesepcolor= \\color{ red!20!green!20!blue!20} 
    } 
    
    [EXTRA]
    "
                 ("\\chapter{%s}" . "\\chapter*{%s}")
                 ("\\section{%s}" . "\\section*{%s}")
                 ("\\subsection{%s}" . "\\subsection*{%s}")
                 ("\\subsubsection{%s}" . "\\subsubsection*{%s}")
                 ("\\paragraph{%s}" . "\\paragraph*{%s}")
                 ("\\subparagraph{%s}" . "\\subparagraph*{%s}")))
    
    (add-to-list 'org-latex-classes
              '("my-org-article-zh"
    "\\documentclass{article}
    \\usepackage[slantfont, boldfont]{xeCJK}
    [NO-DEFAULT-PACKAGES]
    [PACKAGES]
    \\setCJKmainfont{SimSun} % 设置缺省中文字体
    \\parindent 2em
    
    \\setmainfont{DejaVu Sans} % 英文衬线字体
    \\setsansfont{DejaVu Serif} % 英文无衬线字体
    \\setmonofont{DejaVu Sans Mono} % 英文等宽字体
    %\\punctstyle{DejaVu Sans} % 开明式标点格式
    
    
    \\defaultfontfeatures{Mapping=tex-text} %如果没有它，会有一些 tex 特殊字符无法正常使用，比如连字符。
    
    % 中文断行
    \\XeTeXlinebreaklocale \"zh\"
    \\XeTeXlinebreakskip = 0pt plus 1pt minus 0.1pt
    
    % 代码设置
    \\lstset{numbers=left, 
    numberstyle= \\tiny, 
    keywordstyle= \\color{ blue!70},commentstyle=\\color{red!50!green!50!blue!50}, 
    frame=shadowbox, 
    breaklines=true,
    rulesepcolor= \\color{ red!20!green!20!blue!20} 
    } 
    
    [EXTRA]
    "
                 ("\\section{%s}" . "\\section*{%s}")
                 ("\\subsection{%s}" . "\\subsection*{%s}")
                 ("\\subsubsection{%s}" . "\\subsubsection*{%s}")
                 ("\\paragraph{%s}" . "\\paragraph*{%s}")
                 ("\\subparagraph{%s}" . "\\subparagraph*{%s}")))
    
    (setq org-latex-pdf-process
          '("xelatex -interaction nonstopmode %b"
        "xelatex -interaction nonstopmode %b"))
    
    ; org-mode babel load languages
    (org-babel-do-load-languages
     'org-babel-load-languages
     '((ditaa . t)
       (shell . t)))
