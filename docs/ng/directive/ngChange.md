



# ngChange








Evaluate the given expression when the user changes the input.
The expression is evaluated immediately, unlike the JavaScript onchange event
which only triggers at the end of a change (usually, when the user leaves the
form element or presses the return key).

The `ngChange` expression is only evaluated when a change in the input value causes
a new value to be committed to the model.

It will not be evaluated:
* if the value returned from the `$parsers` transformation pipeline has not changed
* if the input has continued to be invalid since the model will stay `null`
* if the model is changed programmatically and not by a change to the input value


Note, this directive requires `ngModel` to be present.








## Directive Info


* This directive executes at priority level 0.


## Usage



* as attribute:
    ```
    <input
      ng-change="">
    ...
    </input>
    ```




### Arguments

| Param | Type | Details |
| :--: | :--: | :--: |
| ngChange | expression | <p>(Expression)[guide/expression] to evaluate upon change in input value.</p>  |




