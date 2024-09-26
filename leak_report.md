# Leak report

_Use this document to describe whatever memory leaks
you find in `clean_whitespace.c` and how you might fix
them. You should also probably remove this explanatory
text._

==2644354== Memcheck, a memory error detector
==2644354== Copyright (C) 2002-2022, and GNU GPL'd, by Julian Seward et al.
==2644354== Using Valgrind-3.22.0 and LibVEX; rerun with -h for copyright info
==2644354== Command: ./check_whitespace
==2644354== 
The string 'Morris' is clean.
The string '  stuff' is NOT clean.
The string 'Minnesota' is clean.
The string 'nonsense  ' is NOT clean.
The string 'USA' is clean.
The string '   ' is NOT clean.
The string '     silliness    ' is NOT clean.
==2644354== 
==2644354== HEAP SUMMARY:
==2644354==     in use at exit: 46 bytes in 6 blocks
==2644354==   total heap usage: 7 allocs, 1 frees, 1,070 bytes allocated
==2644354== 
==2644354== LEAK SUMMARY:
==2644354==    definitely lost: 46 bytes in 6 blocks
==2644354==    indirectly lost: 0 bytes in 0 blocks
==2644354==      possibly lost: 0 bytes in 0 blocks
==2644354==    still reachable: 0 bytes in 0 blocks
==2644354==         suppressed: 0 bytes in 0 blocks
==2644354== Rerun with --leak-check=full to see details of leaked memory
==2644354== 
==2644354== For lists of detected and suppressed errors, rerun with: -s
==2644354== ERROR SUMMARY: 0 errors from 0 contexts (suppressed: 0 from 0)

This shows that we lost 46 bytes in the compilation process in 6 of the blocks.
One way I think you could fix this is to check the code and make sure their is no unecessary
trimming going on.