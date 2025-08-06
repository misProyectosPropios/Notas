```


Unset Universe Checking.
Require Export UniMath.Foundations.All.


(* Example 1*)

(* Notes:
- idpath is the name in Unimath for refl.
- Defined as maponpaths in UniMath.Foundations.PartA.*)

(*
The identity type is defined in Unimath as:

Inductive paths {A:UU} (a:A) : A -> UU := paths_refl : paths a a.
Notation "a = b" := (paths a b) : type_scope.
Notation idpath := paths_refl .
*)

Definition ap {A B : UU} (f : A → B) {x y : A} (p : x = y) : f x = f y.
Proof.
  induction p.
  apply idpath.
Defined.

Search (∏ A B : UU , ∏ f : A → B, ∏ x y : A , x = y → f x = f y).

About maponpaths.

About ap.

(* Example 2 *)

Print add.

Definition left_unit (n : nat) : add 0 n = n.
Proof.
  simpl.
  apply idpath.
Defined.

Definition right_unit (n : nat) : add n 0 = n.
Proof.
  induction n.
  - apply idpath.
  - cbn.
    apply ap.
    exact IHn.
Defined.

Definition right_unit_again (n : nat) : add n 0 = n.
Proof.
  induction n.
  - apply idpath.
  - cbn.
    set (myeq := ap S IHn).
    rewrite myeq.
    apply idpath.
Defined.

(* Example 3 *)

Definition reflexive {A : UU} (R: A → A → UU) : UU := ∏ a : A, R a a.

(* We can make the parameter {A:UU} in paths explicit by writing @paths. *)

Lemma reflexive_paths (A : UU): reflexive (@paths A).
Proof.
  unfold reflexive.
  intro a.
  apply idpath.
Defined.

(* Example 4 *)

Definition symmetric {A : UU} (R: A → A → UU) : UU := ∏ (a b : A), R a b → R b a.

Lemma symmetric_paths (A : UU) : symmetric (@paths A).
Proof.
  unfold symmetric.
  intros a b.
  intro p.
  induction p.
  apply idpath.
Defined.

(* Example 5 *)

Definition transitive {A : UU} (R: A → A → UU) : UU := ∏ (a b c : A), a = b → b = c → a = c.

Lemma transitive_paths (A : UU) : transitive (@paths A).
Proof.
  unfold transitive.
  intros a b c p q.
  induction p.
  induction q.
  apply idpath.
Defined.

(* Example 6 *)

Definition equivalence {A : UU} (R: A → A → UU) : UU := (reflexive R) × (symmetric R) × (transitive R).

Theorem equivalence_paths (A : UU) : equivalence (@paths A).
Proof.
  exact (reflexive_paths A,,symmetric_paths A,,transitive_paths A).
Defined.

(* Example 7 *)

(* Everything respects equality. *)

(* Note: transport is defined as transportf in UniMath.Foundations.PartA.*)

Theorem transport {A : UU} {D : A → UU} {a b : A} (d : D a) (p: a = b) : D b.
Proof.
  induction p.
  exact d.
Defined.


(*********************************)

(* Exercise 8 *)

Theorem complicatedTransport {A : UU} {D : A → UU} {a b c : A} (p : a = b) (q : b = c) (d : D c) : D a.
Proof.
  induction p.
  induction q.
  exact d.
Defined.

(* Exercise 9 *)

Lemma add_S_comm : ∏ n m : nat , n + S m = S (n + m).
Proof.
  intros n m.
  induction n.
  - simpl.
    apply idpath.
  - simpl.
    rewrite IHn.
    apply idpath.
Defined. 

Theorem add_comm : ∏ n m : nat , n + m = m + n.
Proof.
  intros n m.
  induction m.
  - apply right_unit.
  - simpl.
    rewrite (! IHm).
    simpl.
    apply add_S_comm.
Defined.

(* Exercise 9 *)

Theorem mul_left_id : ∏ n : nat , mul 1 n = n.
Proof.
  intro n.
  simpl.
  apply idpath.
Defined.

(* Exercise 10 *)

Theorem mul_right_id : ∏ n : nat , mul n 1 = n.
Proof.
  intro n.
  induction n.
  - simpl.
    apply idpath.
  - simpl.
    rewrite IHn.
    (* Search (∏ n m : nat, n + m = m + n). *)
    apply natpluscomm.
Defined.

(* Exercise 11 *)

(* Define what is means to be divisible by 2 and divisible by 4, and show that being divisible by 4 implies being divisible by 2. *)

Definition zeroMod2 (n : nat) : UU :=
  ∑ m : nat , mul m 2 = n.

Definition zeroMod4 (n : nat) : UU :=
  ∑ m : nat , mul m 4 = n.

Theorem zeroMod4to2 : ∏ n : nat , zeroMod4 n → zeroMod2 n.
Proof.
  intros n p.
  induction p as [ndiv4 p].
  use tpair.
  - exact (mul ndiv4 2).
  - simpl.
    (* Search (∏ a b c : nat, (a * b) * c = a * (b * c)). *)
    rewrite natmultassoc.
    exact p.
Defined.
















(* Instructions: there are 10 exercises. Succesfully completing x exercises will earn you a grade of x. (No partial credit will be given.) Please alter the following comment to tell me which exercises you completed below.*)

(* I completed 3 exercises: Exercise 1, 3, 4.*)

(* Exercise 1 *)

Theorem comp_app { P Q R : UU } (f : P → Q) (g : Q → R) (p : P) : R.
Proof.
apply g.
apply f.
exact p.
Defined.

(* Exercise 2 *)

Lemma path_combination {A : UU} {a a' b : A} (p : a = b) (q: a' = b) : a = a'.
(* Another way to combine paths. *)
Proof.
induction p.
induction q.
apply idpath.
Defined.

(* Exercise 3 *)

Lemma path_combination_fact {A : UU} {a b : A} (p : a = b) : idpath a = path_combination p p.
(* Check that the above way of combining paths does the `right thing'. *)
Proof.
induction p.
simpl.
apply idpath.
Defined.

(* Exercise 4 *)

Definition mult : nat → nat → nat.
Proof.
  intro n.
  intro m.
  induction m.
  - exact 0.
  - exact (add n IHm).
Defined.


(*
Theorem exp : nat → nat → nat.
Proof.
intro n.
induction n.
- exact (λ x , ).
- intro m.
  exact (mult m (IHn m)).
Defined.

*)

Theorem exp : nat → nat → nat.
Proof.
intro n.
intro m.
induction m.
- exact 1.
- exact (n * IHm).
Defined.

Compute (exp 5 1).

Compute (exp 3 2).

(* Exercise 5 *)

Theorem curried_proj {P Q R : UU} : (P → (Q × R)) → (P → Q).
Proof.
intro pqr.
intro p.
induction pqr.
- exact pr1.
- exact p. 
Defined.

(* Exercise 6 *)

(*Search (∏ X Y : UU, ∏ f : X → Y, ∏ x y : X, X * (Y * Z)).*)

(* This command searches the library for functions of this kind. You should see in the output that ~maponpaths~ is of this kind. You can then print ~maponpaths~ (i.e. write "Print maponpaths.") to see the definition.

You can use this to find other lemmas from the library. You can use any facts without proof from the library about addition and multiplication as well as ~maponpaths~.*)





Theorem exp_hom {l m n : nat} : exp l (m + n) = (exp l m) * (exp l n).
(* `exp l` takes addition to multiplication.*)

Proof.
induction m.
- simpl.
  apply idpath.
- simpl.
  rewrite IHm.
  rewrite natmultassoc.
  apply idpath.
Admitted.





About isaprop.
(* Exercise 7 *)

(* isaprop is defined differently in UniMath than we defined in lectures. Show that these two definitions are the the same. *)

(* Note that this is the hardest exercise, but the ones following depend on it. Feel free to leave it admitted and use the result without proof in the following exercises. *)

Theorem prop_thm {P : UU} : isaprop P <-> (∏ x y : P, x = y).
(* The different definitions of isaprop are logically equivalent. *)
Proof.
Admitted.

(* Exercise 8 *)

(* Show that the dependent product type former commutes with `isaprop`.*)

Search "isaprop".

Theorem prop_commutes_Π {A : UU} {B : A → UU} (p : ∏ x : A, isaprop (B x)) : isaprop (∏ x : A, (B x)).
Proof.
intro.
intro.
simpl.
unfold iscontr.
use tpair.


Admitted.

(* Exercise 9 *)

(* Show that isweq f is a proposition. *)

(* Use ~isapropisofhlevel~ from the library. *)

Search "impred_isaprop".

Theorem isweq_is_prop {A B : UU} (f : A → B) : isaprop (isweq f).
apply impred_isaprop.
intro.
change (isaprop (isofhlevel 0 (hfiber f t))).
use isapropisofhlevel.
Admitted.

(* Exercise 10 *)

(* You are allowed to use isweq_iso from the library in this proof: it says if f is a quasiequivalence, then f is an equivalence in that sense.*)

Theorem prop_equiv_to_log_equiv (P Q : hProp) : (P ≃ Q) <-> (P <-> Q).
(* An equivalence between propositions is (logically equivalent to) a logical equivalence. *)
Proof.
Admitted.
```



```
About isaprop.
(* Exercise 7 *)

(* isaprop is defined differently in UniMath than we defined in lectures. Show that these two definitions are the the same. *)

(* Note that this is the hardest exercise, but the ones following depend on it. Feel free to leave it admitted and use the result without proof in the following exercises. *)

Theorem prop_thm {P : UU} : isaprop P <-> (∏ x y : P, x = y).
(* The different definitions of isaprop are logically equivalent. *)
Proof.
Admitted.

(* Exercise 8 *)

(* Show that the dependent product type former commutes with `isaprop`.*)

Search "isaprop".

Theorem prop_commutes_Π {A : UU} {B : A → UU} (p : ∏ x : A, isaprop (B x)) : isaprop (∏ x : A, (B x)).
apply prop_thm.
intro.
intro.
apply funextsec.
intro z.
apply p.
Defined.

(* Exercise 9 *)

(* Show that isweq f is a proposition. *)

(* Use ~isapropisofhlevel~ from the library. *)

Search "impred_isaprop".
Search "isapropisofhlevel".

Theorem isweq_is_prop {A B : UU} (f : A → B) : isaprop (isweq f).
Proof.
apply impred_isaprop.
intro.
change (isaprop (isofhlevel 0 (hfiber f t))).
use isapropisofhlevel.
Defined.
(* Exercise 10 *)

(* You are allowed to use isweq_iso from the library in this proof: it says if f is a quasiequivalence, then f is an equivalence in that sense.*)

Theorem prop_equiv_to_log_equiv2 (P Q : hProp) : (P ≃ Q) <-> (P <-> Q).
(* An equivalence between propositions is (logically equivalent to) a logical equivalence. *)
Proof.
split.
- intro X_equiv_Q.
  split.
+ intro p.
  induction X_equiv_Q.
  simpl isweq in pr2.
  set (e := pr1 p).
  exact e.
+ intro q.
  induction X_equiv_Q as [f is_weq_f].
  simpl isweq in is_weq_f.
  admit. 
- intro.
  induction X.
  destruct e as [f Hf].

Admitted.

Search "isweq_iso".
About isweq.
About hProp.
Theorem prop_equiv_to_log_equiv (P Q : hProp) : (P ≃ Q) <-> (P <-> Q).
(* An equivalence between propositions is (logically equivalent to) a logical equivalence. *)
Proof.
split.
- intro.
  split.
+ intro Y.
  induction X.
  simpl isweq in pr2.
  set (e := pr1 Y).
  exact e.
+ intro Y.
  induction X_equiv_Q as [f is_weq_f].
  -
  admit. 
- intro.
  induction X.
  destruct e as [f Hf].

Admitted.


```