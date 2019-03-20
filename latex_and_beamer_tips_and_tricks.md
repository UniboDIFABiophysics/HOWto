# General LaTeX

## number alignment in a table by decimal place
To align the numbers in a column based on the position of the decimals, one can use the `siunitx` package.

one can then replace in the tabular definition of the columns the normal alignment with a special one: `S`.

For example, to have the numbers without any sign, where there are at most 4 and 3 digits on the two sides of the dots, one can use `S[table-format=4.3]` 

    ...
    \usepackage{siunitx}
    ...
    \begin{tabular}{llrrS[table-format=4.3]}
    \textbf{particella} & \textbf{simbolo} & \textbf{carica (e)} & \textbf{massa (kg)}  & \textbf{massa (MeV)}  \\
    \hline\\
    elettroni ($\beta^-$) & e-, $\beta^-$ & -1 & 9.109$\cdot 10^{-31}$ & 0.511 \\
    positroni ($\beta^+$) & e+, $\beta^+$  & +1 & 9.109$\cdot 10^{-31}$& 0.511 \\
    protoni & p & +1 & 1.673$\cdot  10^{-27}$ & 938.3 \\
    deutoni & d & +1 & 3.348$\cdot  10^{-27}$& 1875.6 \\
    particelle $\alpha$ & $\alpha$ & +2 & 6.647$\cdot  10^{-27}$& 3727.3 \\
    neutroni & n  & 0 & 1.675$\cdot  10^{-27}$ & 939.6       
    \end{tabular}

## good practices for writing scientific LaTeX documents

with figures generated in Python or Matlab. 

https://github.com/Wookai/paper-tips-and-tricks
