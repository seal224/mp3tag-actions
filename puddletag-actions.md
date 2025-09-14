# puddletag-actions

Replicating the actions in [mp3tag-actions](https://github.com/seal224/tagging-actions/blob/main/mp3tag-actions.md) with slightly adjusted commands. See there for explanations.

## display artist/composer → artist/composer

```
Format artist using $if(%display artist%,%display artist%,%artist%)
Format composer using $if(%display composer%,%display composer%,%composer%)
<blank> DISPLAY ARTIST, DISPLAY COMPOSER
```

## split artist/composer and create display tag when needed

```
Format DISPLAY ARTIST using $if($grtr($len(%artist%),$len($replace($replace($replace($replace($replace(%artist%,",",""),"&","")," (",""),"(",""),")",""))),%artist%,)
Format DISPLAY COMPOSER using $if($grtr($len(%composer%),$len($replace($replace($replace($replace($replace(%composer%,",",""),"&","")," (",""),"(",""),")",""))),%composer%,)
Split using separator artist, composer: sep=', '
Split using separator artist, composer: sep=' & '
Split using separator artist, composer: sep=' ('
Split using separator artist, composer: sep='('
Replace artist, composer: ')' → '', Match Case: No, Words Only: No
```
