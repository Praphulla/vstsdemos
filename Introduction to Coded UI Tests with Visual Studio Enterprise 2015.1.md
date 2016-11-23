Hands-On Lab

Introduction to Coded UI Tests with Visual Studio Enterprise 2015
=================================================================

Lab version: 14.0.25123.0

Last updated: 4/29/2016

1.  [./media/image1.png](./media/image1.png)

2.  **TABLE OF CONTENT**

[Introduction to Coded UI Tests with Visual Studio Ultimate 2015
1](#introduction-to-coded-ui-tests-with-visual-studio-enterprise-2015)

[Overview 3](#_Toc430705085)

[Prerequisites 3](#prerequisites)

[Exercises 3](#exercises)

[Exercise 1: Code Generation from Action Recordings
4](#exercise-1-code-generation-from-action-recordings)

[Exercise 2: Code Generation using Coded UI Test Builder 10](#_Toc430705089)

[Exercise 3: Data Driven Demonstration for Coded UI Test 14](#_Toc430705090)

1.  Coded UI tests provide a way to create fully automated tests to validate the
    functionality and behavior of your application’s user interface. In this
    lab, you will gain a basic understanding of coded UI tests by creating a new
    test and adding validation logic to it.

### Prerequisites

1.  In order to complete this lab you will need the Visual Studio 2015 virtual
    machine provided by Microsoft. For more information on acquiring and using
    this virtual machine, please see [this blog post](http://aka.ms/almvm).

### Exercises

1.  This hands-on lab includes the following exercises:

2.  Introduction to Code Generation from Action Recordings

3.  Introduction to Code Generation using Coded UI Test Builder

4.  Data Driven Demonstration for Coded UI Test

5.  Estimated time to complete this lab: **60 minutes**.

Exercise 1: Code Generation from Action Recordings
--------------------------------------------------

1.  In this exercise, you will be introduced to the code generation features in
    Visual Studio that allow testers to quickly and easily create coded UI tests
    directly from existing action recordings. Action recordings contain the
    steps taken during manual testing of an application. To learn more about
    manual testing and action recordings, please see the “*Authoring and Running
    Manual Tests using Microsoft Test Manager 2015*” lab.

    1.  Log in as **Julia** (VSALM\\Julia). All user passwords are **P2ssw0rd**.

    2.  Launch **Visual Studio 2015** from the taskbar and open **Team
        Explorer**.

    3.  Click the **Connect to Team Projects** button.

    4.  [./media/image2.png](./media/image2.png)

    5.  Figure 1

    6.  Connecting to a different team project

    7.  In **Team Explorer – Connect**, double-click on the **Tailspin Toys**
        project.

    8.  [./media/image3.png](./media/image3.png)

    9.  Figure 2

    10. Loading the Tailspin Toys project

    11. Start a new testing project (**File \| New \| Project…**).

    12. In the New Project window, select the **Coded UI Test Project** template
        from **Visual C\# \| Test**, then click **OK** to create the test
        project.

    13. [./media/image4.png](./media/image4.png)

    14. Figure 3

    15. Creating a Coded UI Test Project

    16. There are two ways to generate code for this new coded UI test. The
        first and default option is to use the **Coded UI Test Builder**, which
        allows you to generate test code by manually walking through a test
        scenario. The second option is to use an **existing action recording**.
        Select the second option to use an existing action recording and click
        **OK** to continue.

    17. [./media/image5.png](./media/image5.png)

    18. Figure 4

    19. Using an existing action recording for test generation

    20. Select the **IDs** radio button and enter **41**. For the purposes of
        this lab, assume that we already know that this is the ID of a test case
        with an action recording.

    21. Click **Find** to execute the work item query.

    22. [./media/image6.png](./media/image6.png)

    23. Figure 5

    24. Finding a test case with action recording

    25. Click **OK** to generate a coded UI test from the action recording.

    26. [./media/image7.png](./media/image7.png)

    27. Figure 6

    28. Selecting a test case with action recording

    29. Navigate to the **CodedUITestMethod1** method in the generated
        CodedUITest1.cs file. Each line represents a step from the action
        recording used during test generation.

    30. Place the cursor somewhere on the line of the first method call,
        **Openhttpwwwtailspintoyscom()**, and then press **Alt+F12** to peek at
        its definition. This will load the **UIMap** class from the
        **UIMap.Designer.cs** file, which contains the generated test logic.
        This generated method launches Internet Explorer and navigates to a
        specified URL.

    31. [./media/image8.png](./media/image8.png)

    32. Figure 7

    33. Using Peek Definition

    34. In the peek definition window, scroll down to the
        **ClickFourthCoffeeFlyer** method. This generated method tests clicking
        on a “Fourth Coffee Flyer” hyperlink that is in the Tailspin Toys web
        application.

    35. [./media/image9.png](./media/image9.png)

    36. Figure 8

    37. Generated test method example

    38. The **ClickFourthCoffeeFlyer** test method does not specify the
        hyperlink parameters directly, but instead refers to the
        “UIBlankPageWindowsInteWindow.UIHomeTailspinToysDocument1.UIFourthCoffeeFlyerHyperlink”
        property. Select the “**UIFourthCoffeeFlyerHyperlink**” property (may
        need to scroll to the right) and then press **Alt+F12** to view its
        definition.

    39. [./media/image10.png](./media/image10.png)

    40. Figure 9

    41. Definition of hyperlink property

    42. **Note:** The HtmlHyperlink instance that is created for the
        UIFourthCoffeeFlyerHyperlink property has a number of search and filter
        properties applied that aid the test framework in locating the correct
        HTML hyperlink. In the event that the web application changes some of
        the link properties, such as the inner text, the test harness may still
        be able to find the hyperlink using the remaining search properties.

    43. Press **Escape** to close the code peek window and return to the
        CodedUITest1.cs file.

    44. **Right-click** somewhere within the CodedUITest1.cs source file and
        select **Run Tests**. Do not touch the mouse or keyboard during the
        tests.

    45. [./media/image11.png](./media/image11.png)

    46. Figure 10

    47. Location of Run Tests command

    48. As the tests run, an instance of Internet Explorer will be opened and
        actions automatically taken as they are defined in the coded UI test.
        The test runs more than once because the original manual test that this
        coded UI test was generated from had multiple rows of test parameters.

    49. [./media/image12.png](./media/image12.png)

    50. Figure 11

    51. Example of coded UI test running

    52. Verify that the test passed by viewing the Test Explorer window. In this
        case, however, we are not performing any validation after any of the
        steps.

    53. [./media/image13.png](./media/image13.png)

    54. Figure 12

    55. Test Explorer window showing passed test

    56. In this exercise, you will learn how to use the Coded UI Test Builder to
        generate test code for the Tailspin Toys Web application and modify the
        generated code in order to enable data driven testing.

    57. Open Internet Explorer and click the **Tailspin Toys** button from the
        favorites bar.

    58. Click the **Model Airplanes** link.

    59. Click the **Fourth Coffee Flyer** link.

    60. Click the **Add To Cart** link to load the shopping cart.

    61. Return to Visual Studio, locate the **CodedUITestMethod1** method in the
        CodedUITest1.cs file, and add a blank line after the call to the
        “this.UIMap.Clickonwhitespaceinwebsite” method.

    62. [./media/image14.png](./media/image14.png)

    63. Figure 13

    64. Adding blank line to test source

    65. **Right-click** at the location of the blank line and select **Generate
        Code for Coded UI Test \| Use Coded UI Test Builder…** from the context
        menu. This will load the **Coded UI Test Builder** window (which is
        always displayed over other windows) and the Internet Explorer instance
        that we previously left open.

    66. [./media/image15.png](./media/image15.png)

    67. Figure 14

    68. Starting the Coded UI Test Builder

    69. **Note:** The Coded UI Test Builder is used to record actions and
        assertions within the user interface which are then converted to code.

    70. Now we will add an assertion to verify that the Quantity textbox is
        equal to a value of 1. **Drag and drop** the target icon from the Coded
        UI Test Builder tool window onto the **Quantity** textbox in Internet
        Explorer. This action will load the Coded UI Test Builder window.

    71. [./media/image16.png](./media/image16.png)

    72. Figure 15

    73. Selecting an element to use for assertion

    74. In the Coded UI Test Builder window, select the **Text** property and
        click **Add Assertion**. This will load a dialog to finalize the
        assertion options to use.

    75. [./media/image17.png](./media/image17.png)

    76. Figure 16

    77. Coded UI Test Builder window

    78. Use the **AreEqual** comparator and a comparison value of ‘**1**’. Click
        **OK** to continue.

    79. [./media/image18.png](./media/image18.png)

    80. Figure 17

    81. Selecting the comparator type and value

    82. Verify that a **checkbox** has been added to the **Text** property row.

    83. [./media/image19.png](./media/image19.png)

    84. Figure 18

    85. Text property showing assertion checkbox

    86. Click **Generate Code** from the Coded UI Test Builder tool window.

    87. [./media/image20.png](./media/image20.png)

    88. Figure 19

    89. Generate Code button location

    90. In the Generate Code window, use **QuantityEqualsOne** for the Method
        Name and click **Add and Generate** to generate the validation code.

    91. [./media/image21.png](./media/image21.png)

    92. Figure 20

    93. Generating assertion code

    94. Remove the “**Fourth Coffee Flyer**” item from the shopping cart.

    95. **Close** the Coded UI Test Builder.

    96. **Close** the Internet Explorer window and return to Visual Studio.

    97. Note that the assertion code generation has added the new validation
        step.

    98. [./media/image22.png](./media/image22.png)

    99. Figure 21

    100. Newly created assertion step for coded UI test

    101. Right-click and select **Run Tests** to run the tests with the new
        validation steps. The test should complete successfully.

    102. In this exercise, you will add another set of test parameter values to
        the test case in order to demonstrate that these test parameters are
        hooked up to the coded UI test and that the validation that we recently
        added in is performing as expected.

    103. Launch **Microsoft Test Manager** from the taskbar.

    104. If not already connected, connect to the **Iteration 2** test plan from
        the **Tailspin Toys** team project. You can change this selection by
        clicking on the **Home** button.

    105. [./media/image23.png](./media/image23.png)

    106. Figure 22

    107. Connecting to Tailspin Toys team project

    108. [./media/image24.png](./media/image24.png)

    109. Figure 23

    110. Connecting to Iteration 2 test plan

    111. [./media/image25.png](./media/image25.png)

    112. Figure 24

    113. Location of currently selected team project and test plan

    114. Select the **Test** tab and select **test suite 7** named “As a
        customer I should be able to remove items from my shopping cart”.

    115. [./media/image26.png](./media/image26.png)

    116. Figure 25

    117. Test suite 7 has been selected

    118. Select the first test case with **ID = 41** and click **Open test
        case**.

    119. [./media/image27.png](./media/image27.png)

    120. Figure 26

    121. Opening test case with ID=41

    122. In the **Parameter Values** section at the bottom, add a new row with
        quantity **10**.

    123. **Note:** A value of 10 is a legitimate value for the shopping cart, so
        the cart will refresh to show a quantity of 10 when this value is
        entered. However, since the purpose of this exercise is to show what
        happens when a test iteration fails, we will pretend that this value
        causes the test to fail in order to demonstrate a test case failure. The
        assertion that we added expects that the quantity will remain at 1.

    124. [./media/image28.png](./media/image28.png)

    125. Figure 27

    126. Parameter Value change

    127. **Save** the changes to the test case and return to Visual Studio.

    128. **Run** the **tests** again from **Visual Studio 2015** and note that
        the test fails on the fourth iteration.

    129. Select the **Failed** test within the Test Explorer window to see the
        details. At the bottom of the Test Explorer window we are notified that
        3 out of 4 tests passed, with the fourth data row failing.

    130. [./media/image29.png](./media/image29.png)

    131. Figure 28

    132. Test results showing failed assertion
