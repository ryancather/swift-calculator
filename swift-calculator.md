#Swift Calculator

Create a working calculator using the Swift programming language.

## Final Result


## Create Project

Create a new Xcode 6 project calling it Swift Calculator

![][2]

[2]: images/swift-calculator/create-project.png

## User Interface

In this section, you'll be designing the user interface (UI) so that the calculator looks similar this.

In this tutorial, you will be concentrating on creating the interface for an iPad to utilise the extra screen space. You will be able to easily extend this app by using Auto Layout to adapt the screen for an iPhone 4/5/6/6+.

![][3]

[3]: images/swift-calculator/user-interface.png

### Open the storyboard

Open the Main.storyboard file.

![][4]

[4]: images/swift-calculator/open-the-storyboard.png

### Drag out a button 

![][5]

[5]: images/swift-calculator/drag-out-a-button-.png

### Change the Label

![][6]

[6]: images/swift-calculator/change-the-label.png

### Drag Out more buttons

![][7]

[7]: images/swift-calculator/drag-out-more-buttons.png

### Even More Buttons

![][8]

[8]: images/swift-calculator/even-more-buttons.png

### Add a Text Field

![][9]

[9]: images/swift-calculator/add-a-text-field.png

### Change to Assistant View

![][10]

[10]: images/swift-calculator/change-to-assistant-view.png

### Create clearCalculations

Control Click and Drag from the Clear button (C) to the ViewController.swift and set up an Action called "clearCalculations".

![][11]

[11]: images/swift-calculator/create-clearcalculations.png

### Create calcDisplay outlet

Control Click & Drag from the text field to ViewController.swift and create and outlet called "calcDisplay"

![][12]

[12]: images/swift-calculator/create-calcdisplay-outlet.png

### Create Remaining Actions

Create actions for each of the remaining buttons. Call each action "press<button>", so "pressTwo", "pressPlus" etc.

![][13]

[13]: images/swift-calculator/create-remaining-actions.png

## Code

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

## Extensions

You can easily extend this app by introducing new operations, such as percent, square, cube, square root etc.

The other area that you can improve is the interface by making the button layout appropriate to the device its being run on. This is using Auto Layout.

## Final Code - ViewController.swift

In case you need it, here's a copy of the whole ViewController.swift file at the end of the tutorial.

     //
     //  ViewController.swift
     //  Swift Calculator
     //
     //  Created by Ryan Cather on 26/01/2015.
     //  Copyright (c) 2015 Lake Tuggeranong College. All rights reserved.
     //
     import UIKit
     class ViewController: UIViewController {
         
         var firstValue = true
         var subTotal: Int?
         
         enum operatorType {
             case plus
             case subtract
             case multiply
             case divide
         }
         
         var lastOperator: operatorType?
         
         @IBOutlet weak var calcDisplay: UITextField!
         @IBAction func pressEquals(sender: AnyObject) {
             var result: Int?
             if let finalOperator = lastOperator {
                 switch(finalOperator) {
                 case .plus : result = subTotal! + calcDisplay.text.toInt()!
                 case .subtract : result = subTotal! - calcDisplay.text.toInt()!
                 case .multiply : result = subTotal! * calcDisplay.text.toInt()!
                 case .divide : result = subTotal! / calcDisplay.text.toInt()!
                 }
             }
             calcDisplay.text = "\(result!)"
             subTotal = nil
             firstValue = true
         }
         
         @IBAction func pressMultiply(sender: AnyObject) {
             if let currentSubTotal = subTotal {
                 subTotal = calcDisplay.text.toInt()! * currentSubTotal
             } else {
                 subTotal = calcDisplay.text.toInt()!
             }
             lastOperator = operatorType.multiply
             firstValue = true
             calcDisplay.text = "\(subTotal!)"
         }
         
         @IBAction func pressDivide(sender: AnyObject) {
             if let currentSubTotal = subTotal {
                 subTotal = calcDisplay.text.toInt()! / currentSubTotal
             } else {
                 subTotal = calcDisplay.text.toInt()!
             }
             lastOperator = operatorType.divide
             firstValue = true
             calcDisplay.text = "\(subTotal!)"
         }
         
         @IBAction func pressMinus(sender: AnyObject) {
             if let currentSubTotal = subTotal {
                 subTotal = calcDisplay.text.toInt()! - currentSubTotal
             } else {
                 subTotal = calcDisplay.text.toInt()!
             }
             lastOperator = operatorType.subtract
             firstValue = true
             calcDisplay.text = "\(subTotal!)"
         }
         
         
         @IBAction func pressPlus(sender: AnyObject) {
             if let currentSubTotal = subTotal {
                 subTotal = calcDisplay.text.toInt()! + currentSubTotal
             } else {
                 subTotal = calcDisplay.text.toInt()!
             }
             lastOperator = operatorType.plus
             firstValue = true
             calcDisplay.text = "\(subTotal!)"
         }
         
         @IBAction func pressZero(sender: AnyObject) {
             if firstValue {
                 calcDisplay.text = "0"
             } else {
                 calcDisplay.text = calcDisplay.text + "0"
             }
         }
         @IBAction func pressNine(sender: AnyObject) {
             if firstValue {
                 calcDisplay.text = "9"
                 firstValue = false
             } else {
                 calcDisplay.text = calcDisplay.text + "9"
             }
         }
         @IBAction func pressEight(sender: AnyObject) {
             if firstValue {
                 calcDisplay.text = "8"
                 firstValue = false
             } else {
                 calcDisplay.text = calcDisplay.text + "8"
             }
         }
         @IBAction func pressSeven(sender: AnyObject) {
             if firstValue {
                 calcDisplay.text = "7"
                 firstValue = false
             } else {
                 calcDisplay.text = calcDisplay.text + "7"
             }
         }
         @IBAction func pressSix(sender: AnyObject) {
             if firstValue {
                 calcDisplay.text = "6"
                 firstValue = false
             } else {
                 calcDisplay.text = calcDisplay.text + "6"
             }
         }
         @IBAction func pressFive(sender: AnyObject) {
             if firstValue {
                 calcDisplay.text = "5"
                 firstValue = false
             } else {
                 calcDisplay.text = calcDisplay.text + "5"
             }
         }
         @IBAction func pressFour(sender: AnyObject) {
             if firstValue {
                 calcDisplay.text = "4"
                 firstValue = false
             } else {
                 calcDisplay.text = calcDisplay.text + "4"
             }
         }
         @IBAction func pressThree(sender: AnyObject) {
             if firstValue {
                 calcDisplay.text = "3"
                 firstValue = false
             } else {
                 calcDisplay.text = calcDisplay.text + "3"
             }
         }
         @IBAction func pressTwo(sender: AnyObject) {
             if firstValue {
                 calcDisplay.text = "2"
                 firstValue = false
             } else {
                 calcDisplay.text = calcDisplay.text + "2"
             }
         }
         @IBAction func pressOne(sender: AnyObject) {
             if firstValue {
                 calcDisplay.text = "1"
                 firstValue = false
             } else {
                 calcDisplay.text = calcDisplay.text + "1"
             }
         }
         
         @IBAction func clearCalculations(sender: AnyObject) {
             calcDisplay.text = "0"
             firstValue = true
         }
         
         override func viewDidLoad() {
             super.viewDidLoad()
             calcDisplay.text = "0"
             // Do any additional setup after loading the view, typically from a nib.
         }
         override func didReceiveMemoryWarning() {
             super.didReceiveMemoryWarning()
             // Dispose of any resources that can be recreated.
         }
     }