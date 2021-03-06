



# ngDisabled








This directive sets the `disabled` attribute on the element if the
(expression)[guide/expression] inside `ngDisabled` evaluates to truthy.

A special directive is necessary because we cannot use interpolation inside the `disabled`
attribute.  The following example would make the button enabled on Chrome/Firefox
but not on older IEs:

```html
<!-- See below for an example of ng-disabled being used correctly -->
<div ng-init="isDisabled = false">
 <button disabled="{{isDisabled}}">Disabled</button>
</div>
```

This is because the HTML specification does not require browsers to preserve the values of
boolean attributes such as `disabled` (Their presence means true and their absence means false.)
If we put an Angular interpolation expression into such an attribute then the
binding information would be lost when the browser removes the attribute.








## Directive Info


* This directive executes at priority level 100.


## Usage



* as attribute:
    ```
    <INPUT
      ng-disabled="">
    ...
    </INPUT>
    ```




### Arguments

| Param | Type | Details |
| :--: | :--: | :--: |
| ngDisabled | expression | <p>If the (expression)[guide/expression] is truthy, then the <code>disabled</code> attribute will be set on the element</p>  |




