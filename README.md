All of the "don't exist" things below might be wrong.

- [ ] [`Data.Bool.Xor`](https://github.com/idris-lang/Idris2/blob/main/libs/base/Data/Bool/Xor.idr)
  - Available in agda (Bool.Properties)
    - `xor-is-ok : ∀ x y → x xor y ≡ (x ∨ y) ∧ not (x ∧ y)`
    - The definition of `xor` covers some idris properties (`xorFalseNeutral`, `xorTrueNot`) listed below
      ```agda
      _xor_ : Bool → Bool → Bool
      true  xor b = not b
      false xor b = b
      ```
  - Available in idris
    - `xorSameFalse`
    - `xorFalseNeutral`
    - `xorTrueNot`
    - `notXor`
    - `notXorCancel`
    - `xorAssociative`
    - `xorCommutative`
    - `xorNotTrue`
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
  - Associative, Commutative, Interaction and De Morgan's laws probably not that obvious from the definitions.
    - `andSameNeutral`
    - `andFalseFalse`
    - `andTrueNeutral`
    - `andAssociative`
    - `andCommutative`
    - `andNotFalse`
    - `orSameNeutral`
    - `orFalseNeutral`
    - `orTrueTrue`
    - `orAssociative`
    - `orCommutative`
    - `orNotTrue`
    - `orSameAndRightNeutral`
    - `andDistribOrR`
    - `orDistribAndR`
    - `notAndIsOr`
    - `notOrIsAnd`
    - `notTrueIsFalse`
    - `notFalseIsTrue`
- [X] [`Data.Zippable`](https://github.com/idris-lang/Idris2/blob/main/libs/base/Data/Zippable.idr)
  - `zipN` and the functions below do not exist in agda but they are not very important
    - ~`zipWith3`~
    - ~`zip3`~
    - ~their `unzip` counterparts~
- [ ] [`Data.List`](https://github.com/idris-lang/Idris2/blob/main/libs/base/Data/List.idr)
  - Functions
    - `isNil` (is this really required?)
    - `isCons` (is this really required?)
    - `iterateN`
    - `iterate` (exists for `Vec`)
    - `unfoldr`
    - `nub`
    - `nubBy`
    - `find` (similar to `filter` in `agda`, but `filter` returns a `List`)
    - `findIndex`
    - `findIndices`
    - `lookupBy` (`lookup` exists in `agda`)
    - `insertAt`
    - `deleteAt`
    - `deleteBy`
    - `delete`
    - `deleteFirstsBy`
    - `replaceAt`
    - `replaceWhen`
    - `unionBy` (probably there with a different name / location)
    - `union` (probably there with a different name / location)
    - `span`
    - `spanBy`
    - `intersectAllBy` (probably there with a different name / location)
    - `intersectAll` (probably there with a different name / location)
    - `intersectBy` (probably there with a different name / location)
    - `singleton` (is this really required?)
    - `splitOn`
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
    - `appendNilRightNeutral`
    - `appendAssociative`
    - `dropFusion`
- [ ] [`Data.Vec`](https://github.com/idris-lang/Idris2/blob/main/libs/base/Data/Vect.idr)
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
- [x] [`Data.Maybe`](https://github.com/idris-lang/Idris2/blob/main/libs/base/Data/Maybe.idr)
  - ~`isItJust`~
  - ~`raiseToMaybe`~
- [ ] [`Data.String`](https://github.com/idris-lang/Idris2/blob/main/libs/base/Data/String.idr)
  - Equivalent functions don't exist
    - `trim`, `ltrim`, rtrim` (written in Haskell?)
    - `stringToNatOrZ` (`primCharToNat` exists)
    - `split`, `break`, `span`
    - `parseInteger`, `parsePositive`, `parseNumWithoutSign`
    - `isInfixOf`, `isSuffixOf`, `isPrefixOf`
    - `strSubstr`
