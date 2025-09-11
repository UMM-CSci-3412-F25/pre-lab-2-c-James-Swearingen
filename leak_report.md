# Leak report


`result` for `*strip()` in line 36 is never freed, but is passed to `cleaned` where it is also never freed
solution: free `cleaned` after it is used in defining `result` for `is_clean()`
