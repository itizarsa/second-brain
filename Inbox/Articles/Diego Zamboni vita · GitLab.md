# Diego Zamboni / vita · GitLab

Source: Notes
Status: Unprocessed
URL: https://gitlab.com/zzamboni/vita

![https://gitlab.com/assets/gitlab_logo-7ae504fe4f68fdebb3c2034e36621930cd36ea87924c11ff65dbcb8ed50dca58.png](https://gitlab.com/assets/gitlab_logo-7ae504fe4f68fdebb3c2034e36621930cd36ea87924c11ff65dbcb8ed50dca58.png)

---

This repository contains the source for my CV. The document is maintained in org-mode. The main export format is to LaTeX and PDF. You can find the rendered document [in my website](https://zzamboni.org/vita/).

My goal is to produce the CV from an Org file which focuses on the semantics of the CV, without worrying about the format. Ultimately, the CV should be exportable to multiple formats from the same document.

The export to LaTeX is done using the [AwesomeCV](https://github.com/posquit0/Awesome-CV) LaTeX class (with some of my own modifications, which you can find in this directory) and the [ox-awesomecv](https://titan-c.gitlab.io/org-cv/#using-awesomecv) exporter I contributed to the [Org-CV](https://titan-c.gitlab.io/org-cv/) package.

Exporting to HTML using the standard `ox-html` exporter works fairly well, but the output is not optimally formatted. The main issue is that a lot of the semantic information (e.g. job dates, employers, etc.) are specified in property drawers, and `ox-html` does not know how to extract/format them. As a workaround, I have configured that those properties should be exported using the `prop` option. This is less than ideal because the properties are exported as-they-are, without any special formatting. You can find an example export in [zamboni-vita.html](https://zzamboni.org/files/vita/zamboni-vita.html).

Exporting to ASCII uses the same trick as for HTML, but the result looks quite reasonable. I use the Plain Text UTF-8 exporter. You can see the output in [zamboni-vita.txt](https://zzamboni.org/files/vita/zamboni-vita.txt).

Read the rest of this document for some more details, if you would like to use it as a starting point to write your own CV. Let me know if you have any questions or feedback!

# Table of contents

# org-mode configuration

Org-CV is not available in MELPA yet, so I it must be installed from its [gitlab repository](https://gitlab.com/Titan-C/org-cv). I use Doom Emacs, so I install it using the `package!` command in the `packages.el` file:

```
(package! org-cv
  :recipe (:host gitlab
           :repo "Titan-C/org-cv"))

```

Once installed, I load it using the `use-package!` command:

```
(use-package! ox-awesomecv
  :after org)

```

If you don’t use Doom Emacs, you can clone the git repository under `~/.emacs.d/lisp/org-cv`, and then use the following code to load the modules:

```
(use-package ox-awesomecv
  :load-path "~/.emacs.d/lisp/org-cv"
  :init (require 'ox-awesomecv))

```

# LaTeX configuration

You need a functional LaTeX install. AwesomeCV requires the use of XeTeX or LuaTeX. I currently use [Tectonic](https://tectonic-typesetting.github.io/en-US/), but you can also use the [TeXLive distribution](https://www.tug.org/texlive/), which contains all the base packages and binaries, or [TinyTeX](https://yihui.org/tinytex/), which allows you only install the packages you need.

This repository contains a slightly customized version of the Awesome-CV package. The LaTeX files are in the `texinput` directory, so you need to add it to the `$TEXINPUT` environment variable for the compile to work (Tectonic does not support `TEXINPUT`, so they are also symlinked into the main directory so they can be found). Tectonic itself takes care of all the compilation phases, but you can also use `latexmk` (included in the TeXLive distribution) to handle the document compilation, you can see its configuration file in [.latexmkrc](https://gitlab.com/zzamboni/vita/-/blob/master/.latexmkrc). I have also put together a simple [Makefile](https://gitlab.com/zzamboni/vita/-/blob/master/Makefile) to compile the document, and to automate publishing the latest version of my CV to [my website](https://zzamboni.org/vita/).

# Document structure

Some things you may find useful:

- By Org-CV convention, the title of the org-document (as specified by `#+title`) is used for the “desired job/position”, since your name is specified using the `#+author` document property.
- You can specify many other properties (e.g. mobile phone, twitter profile, email address, home page URL, etc.) using other document properties. Some are supported by all Org-CV modules, others only by the AwesomeCV exporter, see the [Org-CV](https://titan-c.gitlab.io/org-cv/) documentation for the general properties, and the [AwesomeCV section](https://titan-c.gitlab.io/org-cv/#using-awesomecv) for the `ox-awesomecv` specifics.
- At the top of the Org document there is a block starting with `:CV_CONFIG:`. This block contains all the global document properties to specify AwesomeCV, org-mode and LaTeX configuration properties. The block is optional, I use it only so I can easily collapse the whole block in Emacs when I don’t need it.
- The “Private info” section contains private information which should not be included in the CV by default. It is kept encrypted, so that even if the source file is publicly visible (like mine), the private information is kept protected. The encryption is done automatically thanks to the `org-crypt` Emacs package. The `crypt` tag in the “Private info” section causes it to be encrypted automatically every time the file is saved, and the `noexport` tag in its enclosing section causes it to be omitted when the file gets exported. Its contents, when unencrypted, contains field definitions like this:
    
    ```
    #+mobile: <my mobile number>
    #+address: <my address>
    #+extrainfo: <other private information>
    
    ```
    
    When encrypted, this information is simply ignored. When I want to produce a version of my CV which includes this information, I run `M-x org-decrypt-entry`, which prompts for my GPG passphrase. Then, **without saving the file**, I run the following export command:
    
    ```
    (org-export-to-file 'awesomecv "zamboni-vita-private.tex")
    
    ```
    
- Org-CV does not yet have integration into the org-mode Export menu. For now, the export is done manually by executing a command like the following:
    
    ```
    (org-export-to-file 'awesomecv "zamboni-vita.tex")
    
    ```
    
- You can automate the export by adding an after-save hook to run the export every time you save the org file. To do this, add the following code at the end of the document (see my org file for an example):
    
    ```
    * Local Variables :ARCHIVE:noexport:
    # Local Variables:
    # eval: (add-hook 'after-save-hook (lambda () (org-export-to-file 'awesomecv "zamboni-vita.tex")) :append :local)
    # End:
    
    ```
    

# Next steps and missing stuff

- I would like to improve Org-CV’s ox-hugocv to support the additional properties introduced by ox-awesomecv, so that the Hugo Markdown export looks good and can be used instead of ox-html. This would allow me to publish an HTML version of my CV in my website.
- Add integration of Org-CV’s exporters into the org-mode Export menu.
- I’m torn about the use of fully-semantic properties for specifying information in the CV. On one hand, it’s the cleanest and easiest way of doing it. On the other hand, it makes it harder to use the default org-mode exporters while still preserving the information in the output.
- I wonder if it would make more sense to specify `CV_ENV` as a tag in the headline.