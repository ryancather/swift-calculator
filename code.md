# Code

Now it's time to attack the code. By the end of this tutorial, you should have a working calculator!

### Set the initial value

So the calculator displays a value to start off with, find the viewDidLoad() method and set the starting value to 0.

![][14]

[14]: images/swift-calculator/set-the-initial-value.png

### Create a Boolean variable 

At the top of the class, create a boolean variable called firstValue to determine whether this is the first digit entered into the display. This will be used to override the 0 at the start, or add the value to the end of the existing number.

![][15]

[15]: images/swift-calculator/create-a-boolean-variable-.png

### Write the pressOne() method

This method first queries the firstValue boolean variable. If it is true, then the display only shows the initial 0. If it's true, then replace the 0 with a 1. If it's false, add the 1 onto the end of the value to build up a multiple digit value.

![][16]

[16]: images/swift-calculator/write-the-pressone---method.png

### Complete the other digits: 2-9

The logic for the other digits (2-9) are the same as the button for 1. 0 is slightly different and will be handled in the next step.

The only changes you need to make for the buttons 2-9 are the digits to update the screen with.

![][17]

[17]: images/swift-calculator/complete-the-other-digits--2-9.png

### pressZero() Method

The logic for pressing the 0 button is almost identical to the other digits. The only change is that if the calcDisplay already displays a 0, then you don't want the button to add an addition 0 to the end of it so that calcDisplay now displays 00 or (00000).

The only change you need is to **not** change the firstValue variable if the value is already true. This means that if the user hits the 0 button when the display already shows 0, then it simply replaces the 0 with a 0, so the user doesn't see any change at all.

![][18]

[18]: images/swift-calculator/presszero---method.png

### Test out your code

Run the app in the iPad simulator, or on an iPad, and test it by pressing some of the digit buttons to test it out.

![][19]

[19]: images/swift-calculator/test-out-your-code.png

### clearCalculations()

Write the initial version of your clearCalculations() method to clear the display and set the firstValue back to true. 

You will need to update this as the app gets more complex, but this will work for now.

![][20]

[20]: images/swift-calculator/clearcalculations--.png

### Declare an enum

An enum is a custom data type which allows for only certain values. In this case you want to declare the operators as only +, -, * or /.

Apple's documentation defines a enumerated type as:

     An *enumeration* defines a common type for a group of related values and enables you to work with those values in a type-safe way within your code.

which means that you can only define a variable as one of the values you define. If you tried to set a value, such as .percent, it would cause an error.

![][21]

[21]: images/swift-calculator/declare-an-enum.png

### Define a variable of the new enum

Declare a variable called lastOperator that is declared as the new enum data type you defined.

Make sure you put the ? at the end of the line. This declares it as an Optional and will be explained at a later time.

![][22]

[22]: images/swift-calculator/define-a-variable-of-the-new-enum.png

### Write the pressPlus() method

When the user presses the plus button, you want the app to follow the following logic:

     If there's already a value in memory to add to, add the displayed number to it.
     If not, then store the displayed number in memory for the next operation.
     Also, keep track of the plus button being pressed (allows for when the user presses the equals button later)
     Set the firstValue back to true. This tells the app not to add the next number to the end of the string.
     Display the sub total to the display.

The if structure below is called "Optional Binding". In essence it is saying that if there is a value stored in the subTotal optional, then store it in a constant called currentSubTotal. If there's isn't a value stored in subTotal, then the conditional equates to false, and runs the code in the else block.

![][23]

[23]: images/swift-calculator/write-the-pressplus---method.png

### Complete the other operator methods

The logic of each of the other methods is the same, mostly.

The only issue that will be faced int he future is the division method - if the user decides to divide by zero. You'll fix that later.

![][24]

[24]: images/swift-calculator/complete-the-other-operator-methods.png

### pressEquals() method!

This method might look a bit complex as it has to cover a few situations, based on the last operator selected. This is why you created the lastOperator variable. As the user would typically enter the first number, such as 1, and then the plus button, and then the second number, let's say 7 and then equals. When the user selects the equals button, the app needs to know what the last operator was in order to complete the calculation.

After performing the calculation and storing it in result, it displays the value and resets the system by setting the subTotal to nil and the firstValue back to true.

![][25]

[25]: images/swift-calculator/pressequals---method-.png

### Test out your code!

Your calculator should now work for most situations, with only a few situations where the behaviour doesn't meet the expectations. Your job is now to fix those logic errors.  How many errors can you find?