# Piece by Piece

This challenge is about finding a flag from splitted parts in a directory. First we launch the instance, and we have to connect as ctf-player to an address dolphin-cove.picoctf.net at port 59890 : 
ssh ctf-player@dolphin-cove.picoctf.net -p 59890
We enter the given password, and we arrive to a workspace with 
<img width="1203" height="87" alt="image" src="https://github.com/user-attachments/assets/7e1e6c1b-b7ce-47b4-9983-48e3781cd04c" />

So we have an instructions.txt file
With the nano command, we can read it, and we have to find a way to group all of the different parts to make a complete zip file, that we can unzip with a password they give us.
We check the type of the other files with file part_aa, it's a ZIP file. I tried first to directly use the unzip command but I get this error : 

<img width="1780" height="291" alt="image" src="https://github.com/user-attachments/assets/543ce395-1ce8-43a6-af1e-7e54ed7be428" />

So we have to do something else before opening it. It's about grouping split files, so we had to concatenate all of the parts to make it complete : 

cat part_* > archive.zip

We use a wildcard here to concatenate all of the parts. I can now unzip it with the password and get the flag.txt and the flag : 
picoCTF{z1p_and_spl1t_f1l3s_4r3_fun_78b76e61}
