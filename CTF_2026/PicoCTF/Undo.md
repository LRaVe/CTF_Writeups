# Undo

For this challenge we have to reverse a string that was encrypted and transformed with different steps.

First of all, we have to connect to the instance : 
```
$ nc foggy-cliff.picoctf.net 59669
```

So we have a string : KTZvNHFycnE4LWZhMDFnQHplMHNmYTRlRy1nazNnLXRhMWZlcmlyRShTR1BicHZj

The goal is to revert every changes that have been done to get the original flag.

## Step 1 : Base64 encoding 

So for the hint for this one was "Base64 encoded the string."

So we have to use the base64 command on the shell, with the option -d (decode)
```
base64 -d KTZvNHFycnE4LWZhMDFnQHplMHNmYTRlRy1nazNnLXRhMWZlcmlyRShTR1BicHZj
```
We get the correct result : )6o4qrrq8-fa01g@ze0sfa4eG-gk3g-ta1ferirE(SGPbpvc

## Step 2 : Reversed text

The hint here is : "Reversed the text."

So we use the command rev to get it right.
```
rev )6o4qrrq8-fa01g@ze0sfa4eG-gk3g-ta1ferirE(SGPbpvc
```
We have this now : cvpbPGS(Eriref1at-g3kg-Ge4afs0ez@g10af-8qrrq4o6)

## Step 3 : Translated text

The challenge make us use the tr command that was the hint of this challenge, and when looking at the documentation, we see that we have to use it like this to transform the '-' to '_' :
```
tr - _ 
```
And we get this : cvpbPGS(Eriref1at_g3kg_Ge4afs0ez@g10af_8qrrq4o6)

## Step 4 : Translated text 2

We have to replace the '()' to '{}'. Again we use the tr command : 
```
tr '()' '{}'
```

And we have this : cvpbPGS{Eriref1at_g3kg_Ge4afs0ez@g10af_8qrrq4o6}

## Step 5 : ROT13

Now the challenge says that this text was encoded with ROT13, all the letters are shifted by 13 steps, so A becomes N, etc.
We don't have a rot13 command but we can use again the tr command with a group of letters : 
```
tr 'A-Za-z' 'N-ZA-Mn-za-m'
``` 
And we get the flag : picoCTF{Revers1ng_t3xt_Tr4nsf0rm@t10ns_8deed4b6}
