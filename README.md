Resolution in propositional logic
Resolution rule
The resolution rule in propositional logic is a single valid inference rule that produces a new clause implied by two clauses containing complementary literals. A literal is a propositional variable or the negation of a propositional variable. Two literals are said to be complements if one is the negation of the other (in the following, {\displaystyle \lnot c}  is taken to be the complement to {\displaystyle c} ). The resulting clause contains all the literals that do not have complements. Formally:

{\displaystyle {\frac {a_{1}\lor \ldots \vee a_{i-1}\lor c\lor a_{i+1}\vee \ldots \lor a_{n},\quad b_{1}\lor \ldots \vee b_{j-1}\lor \lnot c\lor b_{j+1}\vee \ldots \lor b_{m}}{a_{1}\lor \ldots \lor a_{i-1}\lor a_{i+1}\lor \ldots \lor a_{n}\lor b_{1}\lor \ldots \lor b_{j-1}\lor b_{j+1}\lor \ldots \lor b_{m}}}} 
where

all {\displaystyle a} s, {\displaystyle b} s and {\displaystyle c}  are literals,
the dividing line stands for entails
The clause produced by the resolution rule is called the resolvent of the two input clauses. It is the principle of consensus applied to clauses rather than terms.[3]

When the two clauses contain more than one pair of complementary literals, the resolution rule can be applied (independently) for each such pair; however, the result is always a tautology.

Modus ponens can be seen as a special case of resolution (of a one-literal clause and a two-literal clause).

{\displaystyle {\frac {p\rightarrow q,p}{q}}} 
is equivalent to

{\displaystyle {\frac {\lnot p\lor q,p}{q}}} 
A resolution technique
When coupled with a complete search algorithm, the resolution rule yields a sound and complete algorithm for deciding the satisfiability of a propositional formula, and, by extension, the validity of a sentence under a set of axioms.

This resolution technique uses proof by contradiction and is based on the fact that any sentence in propositional logic can be transformed into an equivalent sentence in conjunctive normal form.[4] The steps are as follows.

All sentences in the knowledge base and the negation of the sentence to be proved (the conjecture) are conjunctively connected.
The resulting sentence is transformed into a conjunctive normal form with the conjuncts viewed as elements in a set, S, of clauses.[4]
For example {\displaystyle (A_{1}\lor A_{2})\land (B_{1}\lor B_{2}\lor B_{3})\land (C_{1})}  gives rise to the set {\displaystyle S=\{A_{1}\lor A_{2},B_{1}\lor B_{2}\lor B_{3},C_{1}\}} .
The resolution rule is applied to all possible pairs of clauses that contain complementary literals. After each application of the resolution rule, the resulting sentence is simplified by removing repeated literals. If the sentence contains complementary literals, it is discarded (as a tautology). If not, and if it is not yet present in the clause set S, it is added to S, and is considered for further resolution inferences.
If after applying a resolution rule the empty clause is derived, the original formula is unsatisfiable (or contradictory), and hence it can be concluded that the initial conjecture follows from the axioms.
If, on the other hand, the empty clause cannot be derived, and the resolution rule cannot be applied to derive any more new clauses, the conjecture is not a theorem of the original knowledge base.
One instance of this algorithm is the original Davis–Putnam algorithm that was later refined into the DPLL algorithm that removed the need for explicit representation of the resolvents.

This description of the resolution technique uses a set S as the underlying data-structure to represent resolution derivations. Lists, Trees and Directed Acyclic Graphs are other possible and common alternatives. Tree representations are more faithful to the fact that the resolution rule is binary. Together with a sequent notation for clauses, a tree representation also makes it clear to see how the resolution rule is related to a special case of the cut-rule, restricted to atomic cut-formulas. However, tree representations are not as compact as set or list representations, because they explicitly show redundant subderivations of clauses that are used more than once in the derivation of the empty clause. Graph representations can be as compact in the number of clauses as list representations and they also store structural information regarding which clauses were resolved to derive each resolvent.

A simple example
{\displaystyle {\frac {a\vee b,\quad \neg a\vee c}{b\vee c}}} 

In plain language: Suppose {\displaystyle a}  is false. In order for the premise {\displaystyle a\vee b}  to be true, {\displaystyle b}  must be true. Alternatively, suppose {\displaystyle a}  is true. In order for the premise {\displaystyle \neg a\vee c}  to be true, {\displaystyle c} must be true. Therefore regardless of falsehood or veracity of {\displaystyle a} , if both premises hold, then the conclusion {\displaystyle b\vee c}  is true.

Resolution in first order logic
Resolution rule can be generalized to first-order logic to:[5]

{\displaystyle {\frac {\Gamma _{1}\cup \left\{L_{1}\right\}\,\,\,\,\Gamma _{2}\cup \left\{L_{2}\right\}}{(\Gamma _{1}\cup \Gamma _{2})\phi }}\phi } 
where {\displaystyle \phi }  is a most general unifier of {\displaystyle L_{1}}  and {\displaystyle {\overline {L_{2}}}}  and {\displaystyle \Gamma _{1}}  and {\displaystyle \Gamma _{2}}  have no common variables.

Example
The clauses {\displaystyle P(x),Q(x)}  and {\displaystyle \neg P(b)}  can apply this rule with {\displaystyle [b/x]}  as unifier.

Here x is a variable and b is a constant.

{\displaystyle {\frac {P(x),Q(x)\,\,\,\,\neg P(b)}{Q(b)}}[b/x]} 
Here we see that

The clauses {\displaystyle P(x),Q(x)}  and {\displaystyle \neg P(b)}  are the inference’s premises
{\displaystyle Q(b)}  (the resolvent of the premises) is its conclusion.
The literal {\displaystyle P(x)}  is the left resolved literal,
The literal {\displaystyle \neg P(b)}  is the right resolved literal,
{\displaystyle P}  is the resolved atom or pivot.
{\displaystyle [b/x]}  is the most general unifier of the resolved literals.
Informal explanation
In first order logic, resolution condenses the traditional syllogisms of logical inference down to a single rule.

To understand how resolution works, consider the following example syllogism of term logic:

All Greeks are Europeans.
Homer is a Greek.
Therefore, Homer is a European.
Or, more generally:

{\displaystyle \forall x.P(x)\Rightarrow Q(x)} 
{\displaystyle P(a)} 
Therefore, {\displaystyle Q(a)} 
To recast the reasoning using the resolution technique, first the clauses must be converted to conjunctive normal form (CNF). In this form, all quantification becomes implicit: universal quantifiers on variables (X, Y, ...) are simply omitted as understood, while existentially-quantified variables are replaced by Skolem functions.

{\displaystyle \neg P(x)\vee Q(x)} 
{\displaystyle P(a)} 
Therefore, {\displaystyle Q(a)} 
So the question is, how does the resolution technique derive the last clause from the first two? The rule is simple:

Find two clauses containing the same predicate, where it is negated in one clause but not in the other.
Perform a unification on the two predicates. (If the unification fails, you made a bad choice of predicates. Go back to the previous step and try again.)
If any unbound variables which were bound in the unified predicates also occur in other predicates in the two clauses, replace them with their bound values (terms) there as well.
Discard the unified predicates, and combine the remaining ones from the two clauses into a new clause, also joined by the "∨" operator.
To apply this rule to the above example, we find the predicate P occurs in negated form

¬P(X)
in the first clause, and in non-negated form

P(a)
in the second clause. X is an unbound variable, while a is a bound value (term). Unifying the two produces the substitution

X ↦ a
Discarding the unified predicates, and applying this substitution to the remaining predicates (just Q(X), in this case), produces the conclusion:

Q(a)
For another example, consider the syllogistic form

All Cretans are islanders.
All islanders are liars.
Therefore all Cretans are liars.
Or more generally,

∀X P(X) → Q(X)
∀X Q(X) → R(X)
Therefore, ∀X P(X) → R(X)
In CNF, the antecedents become:

¬P(X) ∨ Q(X)
¬Q(Y) ∨ R(Y)
(Note that the variable in the second clause was renamed to make it clear that variables in different clauses are distinct.)

Now, unifying Q(X) in the first clause with ¬Q(Y) in the second clause means that X and Y become the same variable anyway. Substituting this into the remaining clauses and combining them gives the conclusion:

¬P(X) ∨ R(X)
The resolution rule, as defined by Robinson, also incorporated factoring, which unifies two literals in the same clause, before or during the application of resolution as defined above. The resulting inference rule is refutation-complete,[6] in that a set of clauses is unsatisfiable if and only if there exists a derivation of the empty clause using resolution alone.
