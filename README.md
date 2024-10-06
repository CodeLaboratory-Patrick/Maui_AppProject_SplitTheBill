# Tip Calculator Application

This guide provides an overview of the Tip Calculator application created using .NET MAUI. It allows users to input a bill amount, select a tip percentage, and split the bill among multiple people. The interface is developed with XAML, while the logic is implemented in C#. The following sections will explain the components, functionalities, and the screenshots to illustrate the user experience.

## MainPage.xaml Overview

The `MainPage.xaml` file defines the layout of the Tip Calculator user interface. Here are some of the key features:

- **Color Resources**: Several colors are defined for consistent styling throughout the app, including the `SectionsColor`, `LightFont`, and `DarkFont`.
  ```xml
  <Color x:Key="SectionsColor">#444444</Color>
  <Color x:Key="LightFont">#d6d6d6</Color>
  <Color x:Key="DarkFont">#4fd8eb</Color>
  ```
- **UI Elements**: The UI contains a `Grid` with multiple `RowDefinitions` and `ColumnDefinitions` for arranging the main sections of the application, which include:
  - **Total Per Person Display**: Displays the calculated total amount to be paid per person.
  - **Bill Entry**: An entry field for users to input the bill amount.
  - **Tip Selection**: Predefined buttons for selecting tip percentages (10%, 15%, 20%) and a `Slider` for selecting a custom tip percentage.
  - **Number of People**: Buttons (`+` and `-`) to set the number of people splitting the bill.
- **Layout**: The visual elements, including labels, frames, and sliders, are arranged to provide an intuitive interface for users.

## MainPage.xaml.cs Overview

The `MainPage.xaml.cs` file handles the application logic for calculating the bill, tip, and total amount per person.

- **Variables**: The class defines variables to store the `bill` amount, `tip` percentage, and `noPersons` (number of people splitting the bill).
- **Calculate Total (`CalculateTotal`)**: This function calculates the tip and total cost for each person based on the bill amount, tip percentage, and number of people.
  ```csharp
  private void CalculateTotal()
  {
      //Total tip
      var totalTip = (bill * tip) / 100;

      //Tip by person
      var tipByPerson = (totalTip / noPersons);
      lblTipByPerson.Text = $"{tipByPerson:C}";

      //Subtotal
      var subtotal = (bill / noPersons);
      lblSubtotal.Text = $"{subtotal:C}";

      //Total
      var totalByPerson = (bill + totalTip) / noPersons;
      lblTotal.Text = $"{totalByPerson:C}";
  }
  ```
- **Tip Slider (`sldTip_ValueChanged`)**: When the value of the slider changes, the corresponding tip percentage label is updated and `CalculateTotal` is invoked to adjust the values.
- **Tip Button Click (`Button_Clicked`)**: Predefined tip buttons allow users to quickly select a tip percentage, which also updates the slider value and triggers the calculation.
- **People Count Buttons (`btnMinus_Clicked`, `btnPlus_Clicked`)**: These buttons allow users to adjust the number of people splitting the bill. The total is recalculated whenever the count is changed.

## Screenshots and UI Flow

Here are the three main screenshots showing the UI of the Tip Calculator:

1. **Basic UI Layout**:
<img width="426" alt="기본 화면" src="https://github.com/user-attachments/assets/8e38398d-39b3-48d7-92bf-3e5f254b77b6">

   - The initial state of the application with an empty bill input and default tip selection.

2. **Tip Button Selection and People Count**:
<img width="426" alt="팁 3개 버튼 과 인원수" src="https://github.com/user-attachments/assets/792e9d2f-4e67-49ac-965b-4196ba9d83b7">

   - Demonstrates selecting a tip percentage and setting the number of people splitting the bill.

3. **Custom Tip Selection**:
<img width="426" alt="팁 자유선택" src="https://github.com/user-attachments/assets/e2a32fe2-0116-407e-8129-a8b7d6025d2d">

   - Shows adjusting the tip percentage using the slider for a custom tip value, and the corresponding total amount per person.

## Summary

The Tip Calculator application is designed to help users quickly and easily calculate the total amount per person, including tip, for a shared bill. It offers both preset and custom tip options, as well as the ability to split the bill between multiple people. The UI is developed with a focus on simplicity and user-friendliness.

### Key Features:
- Input a bill amount and see the total cost per person.
- Predefined tip percentages for quick selection.
- Slider for selecting a custom tip percentage.
- Adjust the number of people sharing the bill.

