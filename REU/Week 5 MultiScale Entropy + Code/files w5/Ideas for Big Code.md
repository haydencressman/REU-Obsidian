[[Table of Contents W5]]

## Steps to Take

---
Since we installed EntropyHub the functions provided can be used instead of the standalone scripts we've been using for the rest of the scripts. Should save on runtime (but it doesn't really matter it wasn't that crazy until now).

A few things, basically since we can't use user input ==the r, m and Standard Deviations are going to need to be hardcoded as constants== at the top. This will make it as easy as possible to change them without being able to get user input.

Other than that, there might be a better way to access all the files we need. Maybe group together all of the excel and cv sheets into one folder, then see if ==pandas has some kind of scan option or whatever so it can just go through and we don't need to type the file path every single stupid time.==

Beyond that, put the file names in an array at least so it can just run through it for however many files there are. Then maybe make better labels on the plots so we can see which is which, or bundle and save the plots for later.

This can be done tomorrow tho, today was literally hell trying to figure out how to get a newer version of spyder to workd but computer scientists don't love us.

---