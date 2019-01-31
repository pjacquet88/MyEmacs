;; added by Package.el.  This must come before configurations of
;; installed packages.  Don't delete this line.  If you don't want it,
;; just comment it out by adding a semicolon to the start of the line.
;; You may delete these explanatory comments.
(package-initialize)

;;; Set location for external packages.
(add-to-list 'load-path "~/.emacs.d/some_el_file")

(custom-set-faces
 ;; custom-set-faces was added by Custom.
 ;; If you edit it by hand, you could mess it up, so be careful.
 ;; Your init file should contain only one such instance.
 ;; If there is more than one, they won't work right.
 '(font-lock-comment-face ((t (:foreground "cadet blue"))))
 '(font-lock-function-name-face ((t (:inherit bold :foreground "deep sky blue"))))
 '(font-lock-keyword-face ((t (:foreground "DarkGoldenrod2" :weight bold))))
 '(font-lock-string-face ((t (:foreground "coral"))))
 '(font-lock-type-face ((t (:inherit bold :foreground "cornflower blue"))))
 '(font-lock-variable-name-face ((t (:foreground "PaleGreen2"))))
 '(helm-grep-file ((t (:foreground "DodgerBlue1"))))
 '(helm-grep-match ((t (:inherit bold :foreground "tomato2"))))
 '(helm-selection ((t (:inherit bold :background "dark cyan"))))
 '(helm-source-header ((t (:inherit bold :background "turquoise4" :foreground "#212936"))))
 '(isearch ((t (:background "dark cyan" :weight bold))))
 '(lazy-highlight ((t (:background "SeaGreen1" :foreground "black" :weight bold))))
 '(linum ((t (:inherit default :foreground "gray42" :strike-through nil :underline nil :slant normal :weight normal))))
 '(mode-line-buffer-id ((t (:inherit bold :foreground "medium sea green"))))
 '(vertical-border ((t (:background "white" :foreground "white")))))

(require 'package)
(let* ((no-ssl (and (memq system-type '(windows-nt ms-dos))
		    (not (gnutls-available-p))))
       (proto (if no-ssl "http" "https")))
  (when no-ssl
    (warn "\
Your version of Emacs does not support SSL connections,
which is unsafe because it allows man-in-the-middle attacks.
There are two things you can do about this warning:
1. Install an Emacs version that does support SSL and be safe.
2. Remove this warning from your init file so you won't see it again."))
  ;; Comment/uncomment these two lines to enable/disable MELPA and MELPA Stable as desired
  (add-to-list 'package-archives (cons "melpa" (concat proto "://melpa.org/packages/")) t)
  ;;(add-to-list 'package-archives (cons "melpa-stable" (concat proto "://stable.melpa.org/packages/")) t)
  (when (< emacs-major-version 24)
    ;; For important compatibility libraries like cl-lib
    (add-to-list 'package-archives (cons "gnu" (concat proto "://elpa.gnu.org/packages/")))))
(package-initialize)

(add-to-list 'package-archives
	     '("melpa-stable" . "https://stable.melpa.org/packages/") t)

(ac-config-default)






;; ------- MY CONFIG START HERE --------------------------

;; Move ~ and # file into : ~/.emacs.d/var/backup/
(require 'no-littering)
(setq auto-save-file-name-transforms
      `((".*" ,(no-littering-expand-var-file-name "auto-save/") t)))



;; Set a custom line in the column 80
(setq fci-rule-column 80)
(setq fci-rule-width 2)
(setq fci-rule-color "orange")
(global-set-key [f7] 'fci-mode)



;;          KEYBINDINGS

;; C-x C-c C-v C-z C-ENTER
(cua-mode 1)

;; Supress Emacs sound
(setq ring-bell-function 'ignore)

;; Duplicate a line
(global-set-key "\M-D" "\C-a\C- \C-n\M-w\C-y\C-p\C-a")

;; Kill all line
(global-set-key (kbd "M-k") 'kill-whole-line)

;; Display line number
(global-linum-mode 1)

;; Shortcut to call c-mode-common-hook with hs-minor-mode
(add-hook 'c-mode-common-hook #'hs-minor-mode)

;; Concatenate routines
(global-set-key (kbd "C-c <right>") 'hs-show-block)
(global-set-key (kbd "C-c <left>")  'hs-hide-block)
(global-set-key (kbd "C-c <up>")    'hs-hide-all)
(global-set-key (kbd "C-c <down>")  'hs-show-all)

;; Highlight parentheses
(show-paren-mode)

;; Highligh the current line
(global-hl-line-mode)

;; Change the cursor
(setq-default cursor-type 'bar)


;;     STUFF FOT LATEX
;; F1 = launch compile.sh script
(global-set-key (kbd "<f1>") (kbd "M-! sh SPC compile.sh RET"))
;; LATEX Shortcuts
(global-set-key (kbd "C-$ C-$") (kbd "$\\$ <left>"))
(global-set-key (kbd "C-ù C-ù") (kbd "\\begin{} RET RET \\end{} <up> <up> <right>"))



;;    HELM + PROJECTILE
(require 'helm-config)
(require 'helm-projectile)
(projectile-mode +1)
(setq helm-grep-file-path-style 'relative)

;; Enable TAB use in helm
(define-key helm-map (kbd "<tab>") 'helm-execute-persistent-action)

;; Change the buffer list with the helm buffer list
(global-set-key (kbd "C-x b") 'helm-buffers-list)

;; Helm bookmarks shortcut
(global-set-key (kbd "C-x r b") 'helm-bookmarks)

;; Display Helm command
(global-set-key (kbd "C-x m") 'helm-M-x)

;; Helm show erased things
(global-set-key (kbd "M-y") 'helm-show-kill-ring)

;; Change find files command into the Helm one
(global-set-key (kbd "C-x C-f") 'helm-find-files)

;; Grep into the git repository
(defun my-helm-grep-do-git-grep (not-all)
  (interactive "P")
  (helm-grep-git-1 default-directory (null not-all)))
(global-set-key (kbd "M-G") 'my-helm-grep-do-git-grep)

;; Global projectile grep
(global-set-key (kbd "M-F") 'helm-projectile-ack)

;; set the white space into small dots
(setq whitespace-style '(space-mark))
(setq whitespace-display-mappings '((space-mark 32 [183] [46])))
(custom-set-variables
 ;; custom-set-variables was added by Custom.
 ;; If you edit it by hand, you could mess it up, so be careful.
 ;; Your init file should contain only one such instance.
 ;; If there is more than one, they won't work right.
 '(custom-enabled-themes (quote (doom-one)))
 '(custom-safe-themes
   (quote
    ("a3fa4abaf08cc169b61dea8f6df1bbe4123ec1d2afeb01c17e11fdc31fc66379" "d2e9c7e31e574bf38f4b0fb927aaff20c1e5f92f72001102758005e53d77b8c9" "75d3dde259ce79660bac8e9e237b55674b910b470f313cdf4b019230d01a982a" "ecba61c2239fbef776a72b65295b88e5534e458dfe3e6d7d9f9cb353448a569e" "b54826e5d9978d59f9e0a169bbd4739dd927eead3ef65f56786621b53c031a7c" "6b2636879127bf6124ce541b1b2824800afc49c6ccd65439d6eb987dbf200c36" "6d589ac0e52375d311afaa745205abb6ccb3b21f6ba037104d71111e7e76a3fc" "7e78a1030293619094ea6ae80a7579a562068087080e01c2b8b503b27900165c" default)))
 '(inhibit-startup-screen t))
