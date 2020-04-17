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

## COQ
### 1. Company-coq
(Needs MELPA)
```M-x package-refresh-contents RET 
```
followed by 
```M-x package-install RET company-coq RET
```

Add the following to .emacs

```;; Load company-coq when opening Coq files
(add-hook 'coq-mode-hook #'company-coq-mode)
```
