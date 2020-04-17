# Emacs_configure

## Emacs basics

### 0. Get MELPA

Add the following to ~/.emacs 

```;; Add MELPA
(require 'package)
(add-to-list 'package-archives '("melpa" . "http://melpa.org/packages/") t)
(package-initialize)
```

You will need to restart emacs.

### 1. Remeber buffer history in emacs

Add the following to ~/.emacs 

`(savehist-mode 1)`

### 2. Let Emacs use the same path as shell (Terminal):

In Emacs (Using MELPA) :

`M-x package-install-file RET exec-path-from-shell`

Then add the following to .emacs:

```(when (memq window-system '(mac ns))
  (exec-path-from-shell-initialize))
```

### 3. Add shell path to emacs.

Always open emacs with the shell path

(e.g. this is necessary for Emacs to see GHC)

(e.g. this is necessary for Emacs to see coqtop)

```
(when (memq window-system '(mac ns))
(exec-path-from-shell-initialize))
```

Then add the following to your `custom-set-variables` line (or merge it approprietly)

```
 '(package-selected-packages
   (quote (exec-path-from-shellpackage)))
```

### 4. Disable annoying bells

Disable the annoying bell when scrolling
```
(defun my-bell-function ()
  (unless (memq this-command
        '(isearch-abort abort-recursive-edit exit-minibuffer
              keyboard-quit mwheel-scroll down up next-line previous-line
              backward-char forward-char))
    (ding)))
(setq ring-bell-function 'my-bell-function)
```

Disable the bell completly:
`(setq ring-bell-function 'ignore)`

## COQ
### 1. Company-coq
(Needs MELPA)

`M-x package-refresh-contents RET `

followed by 
`M-x package-install RET company-coq RET`

Add the following to .emacs

```;; Load company-coq when opening Coq files
(add-hook 'coq-mode-hook #'company-coq-mode)
```

 ## Haskell 
 
 See [Haskell mode](https://github.com/haskell/haskell-mode).
 
Add the following to .emacs. If you already have custom-set-variables, merge its contents:

```(require 'package)
(custom-set-variables
 ;; custom-set-variables was added by Custom.
 ;; If you edit it by hand, you could mess it up, so be careful.
 ;; Your init file should contain only one such instance.
 ;; If there is more than one, they won't work right.
 '(package-archives
   (quote
    (("gnu" . "https://elpa.gnu.org/packages/")
     ("melpa" . "https://melpa.org/packages/")))))
(package-initialize)
```
Then run emacs, and evaluate:

`M-x package-refresh-contents`
and then follow by
`M-x package-install RET haskell-mode`
 
 
