# mp3tag-actions
Backup of my custom Mp3tag actions in case my computer breaks.

## Convert display artist/composer to artist/composer
Replaces existing ARTIST/COMPOSER fields by DISPLAY ARTIST/DISPLAY COMPOSER if they exist.
```
Format value "ARTIST": $if(%display artist%,%display artist%,%artist%)
Format value "COMPOSER": $if(%display composer%,%display composer%,%composer%)
Remove fields "DISPLAY ARTIST;DISPLAY COMPOSER"
```

## Split artist/composer
Splits multiple artists separated by `,`, `&` and/or `()` and creates corresponding display artist/composer tags if needed.
```
Format value "DISPLAY ARTIST": $ifgreater($strstr(%artist%,'&'),0,%artist%,)
Format value "DISPLAY ARTIST": $ifgreater($strstr(%artist%,','),0,%artist%,%display artist%)
Format value "DISPLAY ARTIST": $ifgreater($strstr(%artist%,'('),0,%artist%,%display artist%)
Replace "ARTIST": "& " -> "\\"
Replace "ARTIST": ", " -> "\\"
Replace "ARTIST": " (" -> "\\"
Replace "ARTIST": ")" -> ""
Replace "ARTIST": "(" -> ""
Format value "DISPLAY COMPOSER": $ifgreater($strstr(%composer%,'&'),0,%composer%,)
Format value "DISPLAY COMPOSER": $ifgreater($strstr(%composer%,','),0,%composer%,%display composer%)
Format value "DISPLAY COMPOSER": $ifgreater($strstr(%composer%,'('),0,%composer%,%display composer%)
Replace "COMPOSER": "& " -> "\\"
Replace "COMPOSER": ", " -> "\\"
Replace "COMPOSER": " (" -> "\\"
Replace "COMPOSER": ")" -> ""
Replace "COMPOSER": "(" -> ""
```

## Remove text in parentheses in [FIELD]
`Regular expression "[FIELD]": "\s*\([^\)]+?\)\s*" -> ""`
