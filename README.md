# Wig (where is grep) 

Make grep prettier by putting a wig on it.

## Synopsis

```perl6
use Wig;

my @even = @numbers.where(* %% 2)
my @prod = @servers.where(.status eq 'Production')
my @matches = @data.where(/pattern/)
```

## Description

This idea comes from a [language proposal](https://gist.github.com/0racle/ea0523759e2da15758d4) I had to make filtering elements read more like English.
The use of of the term `grep` is kind of a misnomer, and unfamiliar to a lot of people, new and old programmers alike. This module adds a new method (and function) that is essentially an 'alias' for `grep` called `where`.

## Limitations / Issues

Rakudo currently has a cache invalidation issue where child classes don't automatically inherit augmented methods from a Parent class (in this case, the Any class).

Until this is fixed, the work around is is to call .^compose on your desired child types. I haven't called it on every class under Any (there's a lot!), just the ones grep is used with most frequently. 

If the class hasn't been recomposed and you try to use `where` on it, Rakudo will report the error `Method 'where' not found for invocant of class 'ClassName'`.

As a quickfix you can just call `ClassName.^compose;` after `use wig;`. Alternatively you can modify the module source.

If you think I've missed a very important class that I shouldn't have, please let me know (email, issues, submit a PR, IRC (freenode, #perl6, user: perlawhirl).

## Licence

Please see the LICENCE file in the distribution`

