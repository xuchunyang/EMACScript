# 用 EMACScript 代替 JavaScript

举例：

    <script type="text/emacscript">
      (insert "当前时间: " (current-time-string))
    </script>

EWW 支持：

``` emacs-lisp
(defun EMACScript (script)
  (when (equal (dom-attr script 'type) "text/emacscript")
    (eval (read (dom-text script)) 'lexical)))

(add-to-list 'shr-external-rendering-functions
             '(script . EMACScript))
```
