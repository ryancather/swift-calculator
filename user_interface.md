# User Interface

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