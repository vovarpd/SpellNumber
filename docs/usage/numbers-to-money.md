---
outline: deep
---

# Numbers To Money

## Method Value

### Integers

It is very easy to use this solution for systems where you require the value more than in letters, with the specified currency structure.
If you require that an integer have this transformation, you can do it in the following way.

```php
SpellNumber::value(100)->locale('es')->currency('pesos')->toMoney();
// "Cien Pesos"

SpellNumber::value(100)->locale('fa')->currency('تومان')->toMoney();
// "صد تومان"

SpellNumber::value(100)->locale('hi')->currency('रूपये')->toMoney();
// "एक सौ रूपये"
```

### Floating Point

You can also pass a floating point number as an argument to convert it into words in currency format. Only the first two digits after the floating point will be taken.

This method can be useful for invoices, receipts, and similar scenarios. Obtain the supplied value in currency format.

```php
SpellNumber::value(100.12)->locale('es')->currency('Pesos')->fraction('centavos')->toMoney();
// "Cien Pesos Con Doce Centavos"

SpellNumber::value(100.12)->locale('hi')->currency('रूपये')->fraction('पैसे')->toMoney();
// "एक सौ रूपये और बारह पैसे"

SpellNumber::value(100.65)->locale('pl')->currency('złotych')->fraction('groszy')->toMoney();
// "Sto Złotych I Sześćdziesiąt Pięć Groszy"
```

## Method Integer

You can also rely on the `Integer` method to define that the input is a new integer.
Remember to ensure that the input value is of type `int`

```php
SpellNumber::integer(100)->locale('en')->toLetters();
// "One Hundred"
```

## Method Float

Now, if you require it to be translated into letters of more than two decimal places, the solution may be to use the Float method. This method necessarily receives a string value that allows the library to read the complete value sent after the floating point.

```php
SpellNumber::float('12345.23')->locale('en')->toLetters();
//"Twelve Thousand Three Hundred Forty-Five With Twenty-Three"
```