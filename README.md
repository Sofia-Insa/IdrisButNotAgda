All of the "don't exist" things below might be wrong.

- [X] [`Data.Bool.Xor`](https://github.com/idris-lang/Idris2/blob/main/libs/base/Data/Bool/Xor.idr)
  - Available in agda (Bool.Properties)
    - `xor-is-ok : ∀ x y → x xor y ≡ (x ∨ y) ∧ not (x ∧ y)`
    - The definition of `xor` covers some idris properties (`xorFalseNeutral`, `xorTrueNot`) listed below
      ```agda
      _xor_ : Bool → Bool → Bool
      true  xor b = not b
      false xor b = b
      ```
  - Available in idris
    - `xorSameFalse` :heavy_check_mark:
    - `xorFalseNeutral` :heavy_check_mark:
    - `xorTrueNot` :heavy_check_mark:
    - `notXor` :heavy_check_mark:
    - `notXorCancel` :heavy_check_mark:
    - `xorAssociative` :heavy_check_mark:
    - `xorCommutative` :heavy_check_mark:
    - `xorNotTrue` :heavy_check_mark:
   
    [JC : The above seems to indicate that Bool w/ xor forms at least a commutative monoid, possibly 'more']
- [ ] [`Data.Bool`](https://github.com/idris-lang/Idris2/blob/main/libs/base/Data/Bool.idr)
  - these properties are not covered but maybe they are too obvious and can be seen through the definitions -
    ```agda
    _∧_ : Bool → Bool → Bool
    true  ∧ b = b
    false ∧ b = false

    _∨_ : Bool → Bool → Bool
    true  ∨ b = true
    false ∨ b = b
    ```
  - Associative, Commutative, Interaction, and De Morgan's laws are probably not that obvious from the definitions. [JC : some of these are most likely in there already in `Data.Bool.Properties` ; please do another pass]
    - `notAndIsOr` (similar to `not-xor-cancel`)
    - `notOrIsAnd` (similar to `not-xor-cancel`)
    - `notTrueIsFalse` (is this really useful?)
    - `notFalseIsTrue` (is this really useful?)
- [X] [`Data.Zippable`](https://github.com/idris-lang/Idris2/blob/main/libs/base/Data/Zippable.idr)
  - `zipN` and the functions below do not exist in agda but they are not very important
    - ~`zipWith3`~
    - ~`zip3`~
    - ~their `unzip` counterparts~
- [ ] [`Data.List`](https://github.com/idris-lang/Idris2/blob/main/libs/base/Data/List.idr) [JC: skipping `Data.List` on first pass]
  - Functions
    - `isNil` (is this really required?) [JC: no] ❎
    - `isCons` (is this really required?) [JC: no] ❎
    - `iterateN`
    - `iterate` (exists for `Vec`, `replicate` exists for `List` but not `iterate`)
    - `unfoldr` (`unfold` exists)
    - `nub` - should be defined in terms of `deduplicate`, if defined ❎
    - `nubBy` - should be defined in terms of `deduplicate`, if defined ❎
    - `find` ✔️
      - `find` exists in `Data.List.Membership.Setoid`, but it does not return `Maybe`.
      - similarly `lookup` and `index` in `Data.List.Relation.Unary.Any` + `Data.List.Relation.Unary.First`
    - `findIndex` ✔️
    - `findIndices` ✔️
    - `lookup` ✔️
      - (`lookup` exists in `agda` but is different)
      - should be defined in `Data.List.Association`
    - `lookupBy` ✔️
      - should be defined in `Data.List.Association`
    - `insertAt` ✔️
    - `deleteAt` ✔️
    - `deleteBy` (almost `filterᵇ`) ❎
    - `delete` (almost `filterᵇ`) ❎
    - `deleteFirstsBy` ✔️
    - `replaceAt` (exists as `_[_]∷=_`) ❎
    - `replaceWhen` ❎
    - `unionBy` ❎
    - `union` ❎
    - `span` (`spanᵇ` exists) ❎
    - `spanBy` ❎
    - `intersectAllBy` ❎
    - `intersectAll` ❎
    - `intersectBy` ❎
    - `singleton` (`[_]`)
    - `splitOn` ❎
    - `replaceAt`
    - `replaceOn`
    - `replaceWhen`
    - `group` (exists for `Vec`)
    - `groupBy`
    - `groupWith`
    - `groupAllWith`
    - `mergeReplicate`
    - `mergeBy`
    - `sortBy`
    - `prefixOfBy`
    - `isPrefixOf`
    - `isPrefixOfBy`
    - `sufficOfBy`
    - `isSuffixOf`
    - `isSuffixOfBy`
    - `isInfixOf`
    - `transpose` (exists for `Vec`)
  - Properties
    - `appendNilRightNeutral` (`++-identity` properties)
    - `appendAssociative` - (a PR here - https://github.com/agda/agda-stdlib/pull/2023) (`++-assoc`)
    - `dropFusion` ✔️
- [ ] [`Data.List.Elem`](https://github.com/idris-lang/Idris2/blob/main/libs/base/Data/List/Elem.idr)
  - Functions
    - `dropElem` :heavy_check_mark:
    - `get` :heavy_check_mark:
    - `elemToNat` [JC `Data.List.Relation.Unary.Any.index` ? ]
    - `indexElem` [JC : I think there is a `find` somewhere like this ]
    - `elemMap`
  - Properties (or proofs?)
    - `neitherHereNorThere`
    - `isElem`
- [ ] [`Data.List.HasLength`](https://github.com/idris-lang/Idris2/blob/main/libs/base/Data/List/HasLength.idr)
  - Properties (or proofs?)
    - `hasLength` :x:
    - `hasLengthUnique` :x:
- [ ] [`Data.List.Quantifiers`](https://github.com/idris-lang/Idris2/blob/main/libs/base/Data/List/Quantifiers.idr)
  - Properties (or proofs?)
    - `negAnyAll` :x:
    - `anyNegAll` :x:
    - `allNegAny` :x:
    - `decide` :heavy_check_mark:
    - `pushIn` :heavy_check_mark:
    - `pullOut` :heavy_check_mark:
    - `pushInOutInverse` :heavy_check_mark:
    - `pushOutInInverse` :heavy_check_mark:
    - `indexAll` :heavy_check_mark:
- [ ] [`Data.List.Views`](https://github.com/idris-lang/Idris2/blob/main/libs/base/Data/List/Views.idr)
  - Properties
    - `lengthSuc`
    - `lengthLT`
    - `smallerLeft`
    - `smallerRight`
    - `SplitRec`
    - `SnocList`
- [ ] [`Data.Vect`](https://github.com/idris-lang/Idris2/blob/main/libs/base/Data/Vect.idr)
    - Functions
      - `drop'`
      - `allFins` 
      - `replaceAt` (can be derived using `updateAt` maybe?)
      - `mergeBy`
      - `merge` (exists for `List`)
      - `intersperse` (exists for `List`)
      - `scanr` (exists for `List`)
      - `scanl` (exists for `List`)
      - `lookupBy`
      - `hasAny`
      - `hasAnyBy`
      - `find` (exists in `Data.Vec.Membership.Setoid`?)
      - `findIndex`
      - `findIndices`
      - `elemIndexBy`
      - `elemIndex`
      - `elemIndicesBy`
      - `elemIndices`
      - `filter` (maybe a more general `filter` present somewhere else works on `Vec` too?) 
      - `nub`
      - `nubBy`
      - `deleteBy`
      - `partition`
      - `nSplits`
      - `kSplits`
      - `prefixOfBy`
      - `isPrefixOf`
      - `isPrefixOfBy`
      - `sufficOfBy`
      - `isSuffixOf`
      - `isSuffixOfBy`
      - `isInfixOf`
      - `vectToMaybe` (`listToMaybe` exists)
      - `maybeToVec`
      - `permute`
    - Properties
      - `replaceAtSameIndex` (something like this exists for `updateAt`)
      - `replaceAtDiffIndexPreserves` (something like this exists for `updateAt`)
- [ ] [`Data.Vect.Elem`](https://github.com/idris-lang/Idris2/blob/main/libs/base/Data/Vect/Elem.idr)
  - Functions
    - `dropElem`
    - `get`
    - `elemToFin`
    - `indexElem`
    - `mapElem`
    - `replaceByElem`
    - `replaceElem`
  - Properties (or proofs?)
    - `neitherHereNorThere`
    - `isElem`
- [ ] [`Data.Vect.Quantifiers`](https://github.com/idris-lang/Idris2/blob/main/libs/base/Data/Vect/Quantifiers.idr)
  - Properties (or proofs?)
    - `negAnyAll`
    - `notAllHere`
    - `notAllThere`
    - `mapProperty`
    - `all`
    - `zipPropertyWith`
- [x] [`Data.Maybe`](https://github.com/idris-lang/Idris2/blob/main/libs/base/Data/Maybe.idr)
  - ~`isItJust`~
  - ~`raiseToMaybe`~
- [ ] [`Data.String`](https://github.com/idris-lang/Idris2/blob/main/libs/base/Data/String.idr)
  - Equivalent functions don't exist
    - `trim`, `ltrim`, `rtrim` (written in Haskell?)
    - `stringToNatOrZ` (`primCharToNat` exists)
    - `split`, `break`, `span`
    - `parseInteger`, `parsePositive`, `parseNumWithoutSign`
    - `isInfixOf`, `isSuffixOf`, `isPrefixOf`
    - `strSubstr`
- [ ] [`Data.Nat.Order`](https://github.com/idris-lang/Idris2/blob/main/libs/base/Data/Nat/Order.idr)
  - Properties
    - `zeroNeverGreater`
    - `zeroAlwaysSmaller`
      - I think they are already covered under `compare`
        ```agda
        compare : ∀ m n → Ordering m n
        compare zero    zero    = equal   zero
        compare (suc m) zero    = greater zero m
        compare zero    (suc n) = less    zero n
        compare (suc m) (suc n) with compare m n
        ... | less    m k = less (suc m) k
        ... | equal   m   = equal (suc m)
        ... | greater n k = greater (suc n) k
        ```
    - `decideLTE`
    - `decideLTBounded`
    - `lte`
    - `shift`
- [ ] [`Data.Nat`](https://github.com/idris-lang/Idris2/blob/main/libs/base/Data/Nat.idr)
  - Functions
    - `hyper`
  - Properties
    - `compareNatDiag`
    - `compareNatFlip`
    - `NotBothZero`
    - `LTE` (all the `LTE` stuff)
    - `GTE` (all the `GTE` stuff)
    - `plusZeroLeftNeutral`
    - `plusZeroRightNeutral`
    - `plusConstantRight`
    - `plusConstantLeft`
    - `plusOneSucc`
    - `plusLeftLeftRightZero`
    - `multLeftSuccPlus` (covered under distributive properties?)
    - `multRightSuccPlus` (covered under distributive properties?)
    - `multDistributesOverPlusLeft` (covered under distributive properties?)
    - `multDistributesOverPlusRight` (covered under distributive properties?)
