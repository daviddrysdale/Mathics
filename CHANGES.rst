CHANGES
=======

1.1.1
-----

This may be the last update before some major refactoring and interface changing occurs.

In a future 2.0.0 release, Django will no longer be bundled here. See `mathics-django <https://github.com/Mathics3/mathics-django>` for the unbundled replacement.

Some changes were made to support `Pymathics Graph <https://github.com/Mathics3/pymathics-graph>`_, a new graph package bundled separately,
and to support the ability for front-ends to handle rendering on their own. Note that currently this doesn't integrate well into the Django interface, although it works
well in ``mathicsscript``.


Package Updates
+++++++++++++++

- sympy 1.7.1

Mathics Packages added:

- ``DiscreteMath`CombinatoricaV0.9`` (preferred) aand
  ``DiscreteMath`CombinatoricaV0.6``.

Both of these correspond to Steven Skiena's *older* book: "Implementing Discrete Mathematics: Combinatorics and Graph Theory" book.

If you have a package that you would like included in the distribution, and it works with Mathics, please contact us

Rubi may appear in a future release, possibly in a year or so. However this might be speeded up if we can get people to help out with this.


New builtins:
++++++++++++++++++++++++++++

- ``StirlingS1``, ``StirlingS2`` (not all WL variations handled)
- ``MapAt`` (not all WL variations handled)
- ``PythonForm``, ``SympyForm``: these is not in WL. It simply will show a crude translation to ``sympy`` or ``python``. Expect more and better translation later
- ``Throw`` and ``Catch``
- ``With``
- ``FileNameTake``

  Enhancements and Bug fixes:
+++++++++++++++++++++++++++

- Workaround for ``Compile`` so it accepts functions ##1026
- Add ``Trace`` option to ``Get``. ``Get["fn", Trace->True]`` will show lines as they are read.
- Convert to/from Boolean types properly in ``from_python``, ``to_python``. Previously they were 0, and 1.
- Extend ``DeleteCases`` to accept a levelspec parameter.
- Set ``Evaluation#exc_result`` to capture ``Aborted``, ``Timeout``, ``Overflow1``, etc.
- ``ImageData`` changed to get bits {0,1}, not booleans as previously.
- Add tokenizer symbols for <-> and -> and the unicode versions of those.
- Small corrections to ``Needs``, e.g check if already loaded, correct a typo, etc.
- ``System`$InputFileName`` is now set inside ``Needs`` and ``Get``
- Install shell scripts ``dmathicserver``, ``dmathicsscript``, and ``dmathics`` to simplify running docker
- Adjust $InputFileName inside ``Get`` and ``Needs``.

1.1.0
-----

So we can get onto PyPI, the PyPI install name has changed from Mathics to Mathics3.


Enhancements and Bug fixes:
+++++++++++++++++++++++++++

- Add Symbolic Comparisons. PR #1000
- Support for externally PyPI-packagable builtin modules - PyMathics.
- ``SetDirectory`` fixes. PR #994
- Catch ```PatternError`` Exceptions.
- Fix formatting of ``..`` and ``...`` (``RepeatAll``)
- tokenization of ``\.`` without a following space (``ReplaceAll``). Issue #992
- Support for assignments to named ```Pattern```
- Improving support for ```Names``. PR #1003
- Adding a ``MathicsSession`` class to simplify running Mathics from Python. PR #1001
- Improving support for ```Protect``` and ```Unprotect``` list of symbols and regular expressions. PR #1003


1.1.0 rc1
---------

Package Updates
+++++++++++++++

All major packages that Mathics needs have been updated for more recent
releases. Specifically These include:

- Python: Python 3.6-3.9 are now supported.
- cython >= 0.15.1
- Django 3.1.x
- mpmath => 1.1.0
- sympy 1.6.2

New features (50+ builtins):
++++++++++++++++++++++++++++

- ``Association``, ``AssociationQ``, ``FirstPostion``, ``LeafCount``
- ``Association``, ``AssociationQ``, ``Keys``, ``Values`` #705
- ``BarChart[]``, ``PieChart``, ``Histogram``, ``DensityPlot`` #499
- ``BooleanQ``, ``DigitQ`` and ``LetterQ``
- ``CharacterEncoding`` option for ``Import[]``
- ``Coefficient[]``, ``Coefficient[x * y, z, 0]``, ``Coefficient*[]``,
- ``DiscreteLimit`` #922
- ``Environment``
-   File read operations from URLs
- ``FirstPostions``, ``Integers``, ``PrePendTo[]``
- ``GetEnvironment`` # 938
- ``Integers``, ``PrependTo`` and ``ContainsOnly``
- ``Import`` support for WL packages
- ``IterationLimit``
- ``LoadModule``
- ``MantissaExponent[]``, ``FractionalPart[]``, ``CubeRoot[]``
- ``PolynomialQ[]``, ``MinimalPolynomial[]``
- ``Quit[]``, ``Exit[]`` #523, #814,
- ``RealDigits`` #891, #691, ``Interrupt``, ``Unique``
- ``RemoveDiacritics[]``, ``Transliterate[]`` #617
- ``Root`` #806
- ``Sign[]``, ``Exponent``, ``Divisors``, ``QuotientRemainder``, ``FactorTermsList``
- ``Speedups by avoiding inner classes``, #616
- ``StringRiffle[]``, ``StringFreeQ[]``, ``StringContainsQ[]``, ``StringInsert``
- ``SubsetQ`` and ``Delete[]`` #688, #784,
- ``Subsets`` #685
- ``SystemTimeZone`` and correct ``TimeZone`` #924
- ``System\`Byteordering`` and ``System\`Environemnt`` #859
- ``$UseSansSerif`` #908
- ``randchoice`` option for ``NoNumPyRandomEnv`` #820

- support for ``MATHICS_MAX_RECURSION_DEPTH``
- option ``--full-form`` (``-F``) on ``mathics`` to parsed ``FullForm`` of input expressions

Enhancements and Bug fixes:
+++++++++++++++++++++++++++

- speed up leading-blank patterns #625, #933
- support for iteration over Sequence objects in Table, Sum, and Product
- fixes for option handling
- fixes for ``Manipulate[x,{x,{a,b}}]``
- fixes rule -> rule case for ``Nearest``
- fixes and enhancements to ``WordCloud``
- added ``StringTrim[]``
- fixes ``URLFetch`` options
- fixes ``XMLGetString`` and parse error
- fixes ``LanguageIdentify``
- fixes 2 <= base <= 36 in number parsing
- improved error messages
- fixes ``Check``, ``Interrupt``, and ``Unique`` #696
- fixes ``Eigenvalues``, ``Eigenvectors`` #804
- fixes ``Solve`` #806
- proper sympolic expantion for ``Re`` and ``Im``
- fixes a bug in the evaluation of ``SympyPrime`` #827
- clean up ``ColorData``
- fixes unicode characters in TeX document
- update Django gallery examples
- fixes ``Sum`` and ``Product`` #869, #873
- warn when using options not supported by a Builtin #898, #645

Mathematica tracking changes:

- renamed ``FetchURL`` to ``URLFetch`` (according to the WL standard)
- renamed ``SymbolLookup`` to ``Lookup``

Performance improvements:
+++++++++++++++++++++++++

- Speed up pattern matching for large lists
- Quadraditc speed improvement in pattern matching. #619 and see the graph comparisons there
- In-memory sessions #623

Other Changes:
++++++++++++++

- bump ``RecursionLimit``
- blacken (format) a number of Python files and remove blanks at the end of lines
- Adding several CI tests
- Remove various deprecation warnings
- Change shbang from ``python`` to ``python3``
- Update docs

Backward incompatablities:
++++++++++++++++++++++++++

- Support for Python 3.5 and earlier, and in particular Python 2.7,
  has dropped
- The ``graphs`` module (for Graphs) has been pulled until Mathics
  supports pymathics and graphics using networkx better. It will
  reappear as a pymathics module.
- The ``natlang`` (for Natural Language processing) has also been
  pulled.  The problem here too is that the pymathics mechanism needs
  a small amount of work to make it scalable, and in 1.0 these were
  hard coded. Also, both this module and ``graphs`` pulled in some
  potentially hard-to-satisfy non-Python dependencies such as
  matplotlib, or NLP libraries, and word lists. All of this made
  installation of mathics harder, and the import of these libraries,
  ``natlang`` in particular took some time. All of this points to having
  these live in their own repositories and get imported on laziliy on
  demand



1.0
---

New features
++++++++++++

- ``LinearModelFit`` #592
- ``EasterSunday`` #590
- ``DSolve`` for PDE #589
- ``LogisticSigmoid`` #588
- ``CentralMoment``, ``Skewness``, ``Kurtosis`` #583
- New web interface #574
- ``Image`` support and image processing functions #571, #541, #497, #493, #482
- ``StringCases``, ``Shortest``, ``Longest`` string match/replace #570
- ``Quantime`` and ``Quartiles`` #567
- ``Pick`` #563
- ``ByteCount`` #560
- ``Nearest`` #559
- ``Count`` #558
- ``RegularPolygon`` #556
- impoved date parsing #555
- ``Permutations`` #552
- LLVM compilation of simple expressions #548
- ``NumberForm`` #534, #530, #455
- basic scripting with matihcsscript
- Arcs for ``Disk`` and ``Circle`` #498, #526
- download from URL #525
- ``$CommandLine`` #524
- ``Background`` option for ``Graphics`` #522
- ``Style`` #521, #471, #468
- abbreviated string patterns #518
- ``Return`` #515
- better messages #514
- Undo and redo functionality in web interface #511
- ``Covariance`` and ``Correlation`` #506
- ``ToLowerCase``, ``ToUpperCase``, ``LowerCaseQ``, ``UpperCaseQ`` #505
- ``StringRepeat`` #504
- ``TextRecognise`` #500
- axis numbers to integers when possible #495
- ``PointSize`` #494
- ``FilledCurve``, ``BezierCurve``, ``BezierFunction`` #485
- ``PadLeft``, ``PadRight`` #484
- ``Manipulate`` #483, #379, #366
- ``Replace`` #478
- String operator versions #476
- improvements to ``Piecewise`` #475
- Derivation typo #474
- Natural language processing functions #472
- ``Arrow``, ``Arrowheads`` #470
- optional modules with requires attribute #465
- ``MachinePrecision`` #463
- ``Catenate`` #454
- ``Quotient`` #456
- disable spellcheck on query fields #453
- ``MapThread`` #452
- ``Scan`` and ``Return`` #451
- ``On`` and ``Off`` #450
- ``$MachineEpsilon`` and ``$MachinePrecision`` #449
- ``ExpandAll`` #447
- ``Position`` #445
- ``StringPosition`` #444
- ``AppendTo``, ``DeleteCases``, ``TrueQ``,  ``ValueQ`` #443
- ``Indeterminate`` #439
- more integral functions #437
- ``ExpIntegralEi`` and ``ExpIntegralE`` #435
- ``Variance`` and ``StandardDeviation`` #424
- Legacy ``Random`` function #422
- Improved gamma functions #419
- new recursive descent parser #416
- ``TakeSmallest`` and related #412
- ``Boole`` #411
- ``Median``, ``RankedMin``, ``RankedMax`` #410
- ``HammingDistance`` #409
- ``JaccardDissimilarity`` and others #407
- ``EuclideanDistance`` and related #405
- Magic methods for ``Expression`` #404
- ``Reverse`` #403
- ``RotateLeft`` and ``RotateRight`` #402
- ``ColorDistance``, ``ColorConvert`` #400
- Predefine and document ``$Aborted`` and ``$Failed`` #399
- ``IntegerString``, ``FromDigits``, and more #397
- ``EditDistance`` and ``DamerauLevenshteinDistance`` #394
- ``QRDecomposition`` #393
- ``RandomChoice`` and ``RandomSample`` #488
- ``Hash`` #387
- Graphics boxes for colors #386
- ``Except`` #353
- Document many things #341
- ``StringExpression`` #339
- Legacy file functions #338

Bug fixes
++++++++++

- Nested ``Module`` #591, #584
- Python2 Import bug #565
- XML import #554
- ``\[Minus]`` parsing bug #550
- ``Cases`` evaluation bug #531
- ``Take`` edge cases #519
- ``PlotSize`` bug #512
- Firefox nodeValue warning #496
- Django database permissions #489
- ``FromDigits`` missing message #479
- numerfication upon result only #477
- saving and loading notebooks #473
- ``Rationalise`` #460
- ``Optional`` and ``Pattern`` precedence values #459
- fix ``Sum[i / Log[i], {i, 1, Infinity}]`` #442
- added ``\[Pi]``, ``\[Degree]``, ``\[Infinity]`` and ``\[I]`` to parser #441
- fix loss of precision bugs #440
- many minor bugs from fuzzing #436
- ``Positive``/``Negative`` do not numerify arguments #430 fixes #380
- chains of approximate identites #429
- Logical expressions behave inconsistently/incorrectly #420 fixes #260
- fix ``Take[_Symbol, ___]`` #396
- avoid slots in rule handling #375 fixes #373
- ``Gather``, ``GatherBy``, ``Tally``, ``Union``, ``Intersect``, ``IntersectingQ``, ``DisjointQ``, ``SortBy`` and ``BinarySearch`` #373
- symbol string comparison bug #371
- Fix ``Begin``/``BeginPackage`` leaking user-visible symbols #352
- Fix ``TableForm`` and ``Dimensions`` with an empty list #343
- Trailing slash bug #337
- ``Global`` system bug #336
- ``Null`` comparison bug #371
- ``CompoundExpression`` and ``Out[n]`` assignment bug #335 fixes #331
- load unevaluated cells #332

Performance improvements
++++++++++++++++++++++++

- Large expression formatting with ``$OutputSizeLimit`` #581
- Faster terminal output #579
- faster ``walk_paths`` #578
- faster flatten for ``Sequence`` symbols #577
- compilation for plotting #576
- ``Sequence`` optimisations #568
- Improvements to ``GatherBy`` #566
- optimised ``Expression`` creation #536
- ``Expression`` caching #535
- ``Definitions`` caching #507
- optimised ``Position``, ``Cases``, ``DeleteCases`` #503
- optimised ``StringSplit`` #502
- optimised ``$RecursionLimit`` #501
- optimised insert_rule #464
- optimised ``IntegerLength`` #462
- optimised ``BaseExpression`` creation #458
- No reevaluation of evaluated values #391
- shortcut rule lookup #389
- 15% performance boost by preventing some rule lookups #384
- 25% performance boost using same over ``__eq__``
- n log n algorithm for ``Complement`` and ``DeleteDuplicates`` #373
- Avoid computing ``x^y`` in ``PowerMod[x, y, m]`` #342

0.9
---

New features
++++++++++++

- Improved syntax error messages #329
- SVD, LeastSquares, PseudoInverse #258, #321
- Python 3 support #317
- Improvements to Riffle #313
- Tweaks to PolarPlot #305
- StringTake #285
- Norm #268 #270
- Total, Accumulate, FoldList, Fold #264, #252
- Flatten #253 #269
- Which with symbolic arguments #250
- Min/Max with symbolic arguments # 249

Dependency Updates:

- upgraded to ply 3.8 (issue #246)
- dropped interrupting cow #317
- added six (already required by django) #317

Bug fixes:

- Span issues with negative indices #196 fixed by #263 #325
- SVG export bug fixed by #324
- Django runserver threading issue #158 fixed by #323
- asymptote bug building docs #297 fixed by #317
- Simplify issue #254 fixed by #322
- ParametricPlot bug fixed by #320
- DensityPlot SVG regression in the web interface.
- main function for server.py #288, #289 fixed by #298
- ply table regeneration #294 fixed by #295
- Print bar issue #290 fixed by #293
- Quit[] index error #292 partially fixed by #307
- Quit definition fixed by #286
- Conjugate issue #272 fixed by #281

0.8
---

New features
+++++++++++++

- Improvements to 3D Plotting, see #238
- Enable MathJax menu, see #236
- Improvements to documentation

Dependency Updates
++++++++++++++++++

- upgrade to sympy 0.7.6
- upgrade to ply3.6 (new parsetab format, see #246)
- upgrade to mpmath 0.19

Bug Fixes
+++++++++

- IntegerDigits[0]



0.7
+++

New features
++++++++++++

- Readline tab completion
- automatic database initialisation
- support for wildcards in ``Clear`` and ``ClearAll``
- add ``Conjugate``
- More tests and documentation for ``Sequence``
- Context support

Bugs fixed
++++++++++

- Fix unevaluated index handling (issue #217)
- Fix ``Solve`` treating one solution equal to 1 as a tautology (issue
  #208)
- Fix temporary symbols appearing in the result when taking
  derivatives with respect to t (issue #184)
- typo in save worksheet help text (issue #199)
- Fix mathicsserver wildcard address binding
- Fix ``Dot`` acting on matrices in MatrixForm (issue #145)
- Fix Sum behaviour when using range to generate index values (issue #149)
- Fix behaviour of plot with unevaluated arguments (issue #150)
- Fix zero-width space between factors in MathJax output (issue #45)
- Fix ``{{2*a, 0},{0,0}}//MatrixForm`` crashing in the web interface
  (issue #182)

0.6
---

New features
++++++++++++

- ElementData using data from Wikipedia
- added Switch
- added DSolve and RSolve
- More Timing functions AbsoluteTiming, TimeUsed, SessionTime, Pause
- Date functions DateList, DateString, DateDifference, etc
- Parser rewritten using lex/yacc (PLY)
- Unicode character support
- PolarPlot
- IPython style (coloured) input
- VectorAnalysis` Package
- More special functions (Bessel functions and othogonal polynomials)
- More NumberTheory functions
- Import, Export, Get, Needs and other IO related functions
- PyPy compatibility
- added benchmarks (mathics/benchmark.py)
- BaseForm
- DeleteDuplicates
- Depth, Operate Through and other Structure related functions
- Changes to MatrixForm/TableForm printing
- Use interruptingcow to limit evaluation time
- Character Code functions

Bugs fixed
++++++++++

- Fix divide-by-zero with zero-length plot range
- Fix mathicsserver exception on startup with Django 1.6 (issues #194,
  #205, #209)

0.5
---

- 3D graphics and plots using WebGL in the browser and Asymptote in TeX output
- Plot: adaptive sampling
- MathJax 2.0 and line breaking
- new symbols: Graphics3D etc., Plot3D, ListPlot, ListLinePlot, ParametricPlot, Prime, Names, $Version
- fixed issues: 1, 4, 6, 8-21, 23-27
- lots of minor fixes and improvements
- number of built-in symbols: 386

0.4
---

- compatibility to Sage 4.0 and other latest libraries

0.3 (beta only)
---------------

- resolved several issues

0.1 (alpha only)
----------------

- initial version
