#lang rosette

(provide (all-defined-out))

; Takes as input a propositional formula and returns
; * 'TAUTOLOGY if every interpretation I satisfies F;
; * 'CONTRADICTION if no interpretation I satisfies F;
; * 'CONTINGENCY if there are two interpretations I and I′ such that I satisfies F and I' does not.

(define-symbolic* p q r boolean?)

; Number 2 doesn't explicitly state to write the conversion code in Racket/Rosette
;   so I did it by hand and wrote it down in Racket to codify it

; Define input formula
(define input_formula (! (=> (! r) (! (&& p q)))))

; Step 1: Define sub formulas and aux variables
;   (Your conversion should not introduce auxiliary variables for negations. )
(define a_pq (&& p q))
(define a_rpq (! (=> (! r) (! a_pq) ) ) )

; Step 2: Conjunct substitutions and substitution for formula
(define sub (&& a_rpq (<=> a_rpq  (! (=> (! r) (! a_pq) ) ) ) (<=> a_pq (&& p q))   ))

; Step 3: Convert to CNF

; CNF for a_rpq
(define sub_cnf_arpq_1 (=> a_rpq (! (=> (! r) (! a_pq) ) )))
(define sub_cnf_arpq_2 (=> (! (=> (! r) (! a_pq) ) ) a_rpq))

; CNF for a_pq
(define sub_cnf_apq_1 (=> a_pq (&& p q)))
(define sub_cnf_apq_2 (=> (&& p q) a_pq))

; Final CNF form
(define cnf_formula (&& a_rpq sub_cnf_arpq_1 sub_cnf_arpq_2 sub_cnf_apq_1 sub_cnf_apq_2))





