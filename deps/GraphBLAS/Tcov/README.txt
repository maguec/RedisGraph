SuiteSparse:GraphBLAS, Timothy A. Davis, (c) 2017-2019, All Rights Reserved.
http://suitesparse.com   See GraphBLAS/Doc/License.txt for license.

GraphBLAS/Tcov: statement coverage tests

Since nearly all GraphBLAS tests are in MATLAB, I have taken the unusual step
of creating a statement coverage mechanism to use within a MATLAB mexFunction.
To compile GraphBLAS for statement coverage testing, and to run the tests, type
this in the MATLAB command window.

    grbmake ; testcov

If you get a linking problem on linux, add this directory to your
LD_LIBRARY_PATCH, so that the libgraphblas_tcov.so constructed by grbmake can be
found by the mexFunctions.

Statement coverage tests results will be saved in Tcov/log.txt.  Note that full
coverage requires some or all of the GraphBLAS/User/Examples/*.m4 files to
first be moved into the GraphBLAS/User/ directory (and then run "make cmake" in
the shell before doing testcov in MATLAB).  The tests will work without this
step, but some statements that handle compile-time user-defined semirings in
the User/*m4 files will not be tested.

To list the lines covered by the test, do this in MATLAB:

    grbshow

To remove all compiled files, type this in the Unix/Linux shell:

    make distclean

Or, delete these files manually:

    *.o *.obj *.mex* cover_*.c errlog.txt grbstat.mat tmp*/*

To also remove the log.txt file:

    make purge

--------------------------------------------------------------------------------
Files in GraphBLAS/Tcov:
--------------------------------------------------------------------------------

    Contents.m     for 'help Tcov' in MATLAB; list of files

    grbcover.m     compile GraphBLAS for statement coverage testing
    grbcover_edit.m create a version of GraphBLAS for statement coverage tests
    testcov.m      run all GraphBLAS tests, with statement coverage
    grbshow.m      create a test coverage report in tmp_cover/
    Makefile       just for 'make clean' and 'make purge'
    README.txt     this file

    GB_cover_util.c     get/put the coverage to/from MATLAB
    log_*.txt           100% test coverage certificates

    tmp_cover       where coverage reports are placed
    tmp_include     for include files augmented with coverate tests
    tmp_source      for source files augmented with coverate tests

