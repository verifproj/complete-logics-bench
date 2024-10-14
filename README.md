## Benchmarks for Paper on FO-Complete Heap Logics and the FLV Checker  

The folder benchmarksFL and benchmarks SL contain the benchmark suite of programs annotated with Frame Logic (FL) annotations and 
Separation Logic (SLFL) annotations respectively. Each folder contains 
subfolders containing programs based on the primary data structure being manipulated.


## Structure of benchmark files

Each benchmark file contains variable declarations, followed by function declarations (both pointers as well as recursively defined functions), 
then provides definitions for recursive functions, defines certain inductive lemmas which are checked automatically, and finally the methods. 
These are written in a lisp-like format.  


Some examples of syntax to help read the benchmarks:  

(Var x Loc) -  variable x of location sort. Sorts allowed: Loc, Bool, Int, SetLoc, SetBool, SetInt  

(Function next Loc Int) - function next:Loc --> Int  


(EqSp  (List (Keys))) - Declare that List and Keys (which must be declared afterwards) have the same heap (support).  


(RecFunction List Loc Bool) - recursive function List:Loc --> Bool.  

(RecDef (List x) (ite (= x nil) True
                      (and (List (next x))
                           (not (IsMember x (Sp (List (antiSp (next x)))))))))
				- The definition of recursive function List.  
                                  RecFunctions must be declared
				  before providing a definition. 'Sp' is the support operator, and 'antiSp'
				  is the cloud operator.  

(Program example (x) (ret)) - A program/function called example that takes input x and returns ret.  

(Pre (List x)) - (List x) holds in the precondition.  

(Post (List ret)) - (List ret) holds in the precondition,  
			and the permission set is exactly the support of List(ret).  
(assign ret x)	- assigns x to ret  
(return)	- end of program.  












