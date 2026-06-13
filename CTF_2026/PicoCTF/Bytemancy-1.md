# Bytemancy 1

The goal here is to put the correct input in the given script. We first connect to the program with netcat : 

``` $ nc foggy-cliff.picoctf.net 49995 ```

We also get the source code of the program : 

``` 
while(True):
  try:
    print('⊹──────[ BYTEMANCY-1 ]──────⊹')
    print("☍⟐☉⟊☽☈⟁⧋⟡☍⟐☉⟊☽☈⟁⧋⟡☍⟐☉⟊☽☈⟁⧋⟡☍⟐")
    print()
    print('Send me ASCII DECIMAL 101 1751 times, side-by-side, no space.')
    print()
    print("☍⟐☉⟊☽☈⟁⧋⟡☍⟐☉⟊☽☈⟁⧋⟡☍⟐☉⟊☽☈⟁⧋⟡☍⟐")
    print('⊹─────────────⟡─────────────⊹')
    user_input = input('==> ')
    if user_input == "\x65"*1751:
      print(open("./flag.txt", "r").read())
      break
    else:
      print("That wasn't it. I got: " + str(user_input))
      print()
      print()
      print()
  except Exception as e:
    print(e)
    break

```

With the source code, we see that the correct character is indexed '\x65' on the ASCII table, and it's 'e'.
We now have to return 'e' 1751 times to get the flag. The hint suggests that we shouldn't copy-paste, it's impractical. So we have to use Python and pipe the result directly into the program.

``` python3 -c 'print("e"*1751)' | nc foggy-cliff.picoctf.net 49995 ```

And that's it  : picoCTF{h0w_m4ny_e's???_446bf6f1}
