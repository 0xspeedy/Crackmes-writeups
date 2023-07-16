After downloading and extracting the file, we get a file caaled CrackMe1.exe  
The file asks for a serial key, Entered a random key but it was wrong  
<img src="wrong.png" width="600" height="400">
<br><br>
Let's disassemble on IDA and go to strings View -> Open subviews -> Strings or Shift+F12  
Found some intersting keywords including the key  
<img src="strings.png" width="600" height="300"> 
<br><br>
Let's try it  
<img src="correct.png" width="600" height="300">  
<br><br>
Now let's try to patch it like whenever we enter any key, it will work  
Let's go to the success function by double-click on the function next to the string "Congrats!"  
We need to force the flow to take the left path to execute (xor eax,eax) and go to the congrats function  
<img src="path.png" width="600" height="400"> 
<br><br>
Create a breakpoint (F2)  
<img src="breakpoint.png" width="600" height="400">  
<br><br>
Now, let's run then it will ask us for the key, we enter any number and click check  
<img src="try.png" width="600" height="400">  
<br><br>
Ida will show us which path is about to take which is still the one we don't want  
We will click on jnz in the breakpoint line then go to Edit -> Patch program -> Assemble then change the jnz to jz and click ok  
<img src="patch.png" width="600" height="200"> 
<br><br>
Then we step over (F8) we will see it took the other path. Let's keep stepping over and when we come across any jump we change it to the other path if it will go through the path we don't want  
Then the program will pop up a sucess message  
<img src="success.png" width="600" height="300"> 
<br><br>
Then we apply the patches to the file. Edit -> Patch program -> Apply patches to input file ... then check Create backup box  
Now, let's run the patched program again and type any random key  
<img src="patched.png" width="600" height="400"> 
<br><br>
