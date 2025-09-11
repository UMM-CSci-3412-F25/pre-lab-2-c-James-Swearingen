# Leak report


`result` for `*strip()` in line 36 is never freed, but is passed to `cleaned` where it is also never freed
solution: free `cleaned` after it is used in defining `result` for `is_clean()`
update: this resulted in an invalid free(), attempting to free a read-only segment
potential solution: only free `cleaned` if its value is of nonzero length, because sometimes `strip()` returns an empty string
update: this seems to have worked!