
;<Program title>

jmp start

;data
num1: equ 5
num2: equ 12
port1: equ 01
port2: equ 02


;code
start: nop
	;moving first number to b and second one to c 
	mvi b,num1
	mvi c,num2
floatPoint: nop
	mov a,b
	
	;checking if b is bigger than c or not.
	;If not, then "handleSides" subroutine will change the placement of numbers
	sub c 
	jc handleSides
	add c

	call div

	;at the "handleRemain2" subroutine, we can't increment the remain for the last time
	;so the program does that in here
end2: inr e
      dcr d
     
      

end:  inr d
      mov a,d
      out port1
      mov a,e
      out port2
	call handleFloat
      

hlt
	;changing placement of numbers so we can make sure that bigger number is getting divided 
	;instead of dividing the smaller one by the bigger number
handleSides: mov a,b
		mov b,c
		mov c,a
		mvi a,0
		mvi d,0
		add b
		call div
		
	;substracting the bigger number by the smaller number until we hit "0" 
	;every time we didn't hit zero, "d" register will be incremented
	;if he hit zero the program will end and there will be no remain
	;but if the number goes under "-1", "handleRemain1" subroutine will be called
	;so we can handle the remaining number
div: 	sub c
	jz end
	jc handleRemain1
	inr d
	call div
	
	;with this short subroutine we add the last decremented number so the number can be positive again
	;after that we can call the "handleRemain2" subroutine
handleRemain1: add c
	call handleRemain2
	
	;in this subroutine we decrement the remaining number by 1 each time until the number hits 0
	;then we can end the division process
handleRemain2: dcr a
	jz end2
	inr e
	call handleRemain2



handleFloat: mov a,e
	     add e
	     add e
	     add e
	     add e
	     add e
	     add e
	     add e
	     add e
	     add e
	     mov b,a
	     mvi a,0
	     mvi d,0
	     mvi e,0
	     call floatPoint
	     
	     


