---
id: 1727549227-regular-expressions
aliases:
  - Regular Expressions
tags:
  - regex
  - notes
---

# Regular Expressions

## syntax

- regex starts and end with a `/` and can be used to search for a pattern in a string
- | **Or**: `/word to search|another word to search/`
- [] **Character Class**: can be use to search a specific range of characters.
  - `/[aeiou]/` will match any letter from a to o.
  - `/[0-9]/` will match any number from 0 to 9
  - `/[a-z]/` will match any letter from a to z
- \* **Star**: can be used to specify how many times a character or group of characters should appear in a string.
- '+' **Quantifier**: can be used to specify how many times a character or group of characters should appear in a string.
- h(i/ey) **Group**: can be used to group characters or other groups together.
- \s **Whitespace**: can be used to match any whitespace character.

## flags

- i flag means that the search ignore case `/word to search/i`
- ? means that the search is optional `/word to search?/`

## js methods

- string.match(regex) is a **String** method that return an array of matches
- regex.test(string) is a **RegExp** method that return a boolean
