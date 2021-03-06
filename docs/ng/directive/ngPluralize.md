



# ngPluralize








`ngPluralize` is a directive that displays messages according to en-US localization rules.
These rules are bundled with angular.js, but can be overridden
(see (Angular i18n)[guide/i18n] dev guide). You configure ngPluralize directive
by specifying the mappings between
[plural categories](http://unicode.org/repos/cldr-tmp/trunk/diff/supplemental/language_plural_rules.html)
and the strings to be displayed.

# Plural categories and explicit number rules
There are two
[plural categories](http://unicode.org/repos/cldr-tmp/trunk/diff/supplemental/language_plural_rules.html)
in Angular's default en-US locale: "one" and "other".

While a plural category may match many numbers (for example, in en-US locale, "other" can match
any number that is not 1), an explicit number rule can only match one number. For example, the
explicit number rule for "3" matches the number 3. There are examples of plural categories
and explicit number rules throughout the rest of this documentation.

# Configuring ngPluralize
You configure ngPluralize by providing 2 attributes: `count` and `when`.
You can also provide an optional attribute, `offset`.

The value of the `count` attribute can be either a string or an (Angular expression)[guide/expression]; these are evaluated on the current scope for its bound value.

The `when` attribute specifies the mappings between plural categories and the actual
string to be displayed. The value of the attribute should be a JSON object.

The following example shows how to configure ngPluralize:

```html
<ng-pluralize count="personCount"
                 when="{'0': 'Nobody is viewing.',
                     'one': '1 person is viewing.',
                     'other': '{} people are viewing.'}">
</ng-pluralize>
```

In the example, `"0: Nobody is viewing."` is an explicit number rule. If you did not
specify this rule, 0 would be matched to the "other" category and "0 people are viewing"
would be shown instead of "Nobody is viewing". You can specify an explicit number rule for
other numbers, for example 12, so that instead of showing "12 people are viewing", you can
show "a dozen people are viewing".

You can use a set of closed braces (`{}`) as a placeholder for the number that you want substituted
into pluralized strings. In the previous example, Angular will replace `{}` with
<span ng-non-bindable>`{{personCount}}`</span>. The closed braces `{}` is a placeholder
for <span ng-non-bindable>{{numberExpression}}</span>.

If no rule is defined for a category, then an empty string is displayed and a warning is generated.
Note that some locales define more categories than `one` and `other`. For example, fr-fr defines `few` and `many`.

# Configuring ngPluralize with offset
The `offset` attribute allows further customization of pluralized text, which can result in
a better user experience. For example, instead of the message "4 people are viewing this document",
you might display "John, Kate and 2 others are viewing this document".
The offset attribute allows you to offset a number by any desired value.
Let's take a look at an example:

```html
<ng-pluralize count="personCount" offset=2
              when="{'0': 'Nobody is viewing.',
                     '1': '{{person1}} is viewing.',
                     '2': '{{person1}} and {{person2}} are viewing.',
                     'one': '{{person1}}, {{person2}} and one other person are viewing.',
                     'other': '{{person1}}, {{person2}} and {} other people are viewing.'}">
</ng-pluralize>
```

Notice that we are still using two plural categories(one, other), but we added
three explicit number rules 0, 1 and 2.
When one person, perhaps John, views the document, "John is viewing" will be shown.
When three people view the document, no explicit number rule is found, so
an offset of 2 is taken off 3, and Angular uses 1 to decide the plural category.
In this case, plural category 'one' is matched and "John, Mary and one other person are viewing"
is shown.

Note that when you specify offsets, you must provide explicit number rules for
numbers from 0 up to and including the offset. If you use an offset of 3, for example,
you must provide explicit number rules for 0, 1, 2 and 3. You must also provide plural strings for
plural categories "one" and "other".








## Directive Info


* This directive executes at priority level 0.


## Usage




* as element:(This directive can be used as custom element, but be aware of <a href="guide/ie">IE restrictions</a>).
    ```
    <ng-pluralize
      count=""
      when=""
      [offset=""]>
    ...
    </ng-pluralize>
    ```
* as attribute:
    ```
    <ANY
      count=""
      when=""
      [offset=""]>
    ...
    </ANY>
    ```




### Arguments

| Param | Type | Details |
| :--: | :--: | :--: |
| count | string&#124;expression | <p>The variable to be bound to.</p>  |
| when | string | <p>The mapping between plural category to its corresponding strings.</p>  |
| offset | number= | <p>Offset to deduct from the total number.</p>  |




