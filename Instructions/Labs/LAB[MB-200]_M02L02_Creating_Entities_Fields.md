---
lab:
    title: 'Lab: Creating entities and fields'
    module: 'Module 2: Data Model'
---

Module 2: Data Model
====================

## Lesson 2: Practice Lab – Creating entities and fields

Scenario
--------

You are a functional consultant for your organization Contoso. You are assigned
to work on a project for your client Fabrikam. Fabrikam would like to encourage
their employees to continuously learn.  They want to build an application that
allow a small set of employees to create knowledge assessments and then make
them available to all employees to test their knowledge.  The employees need to
be able to pick an assessment and quickly complete it in just a few minutes. In
this practice, you will be creating a data model to support the applications.

Working with the client, you have determined the following basic needs for
storing data:

-   A Knowledge Assessment entity will represent the actual assessment and
    contain one or more questions in an entity Knowledge Question

-   A Knowledge Test Result entity will track when employees take an assessment

-   The employee who took the assessment will be tracked using the existing
    Common Data Model (CDM) User entity

-   The CDM Feedback entity will be used to allow employees to express their
    opinions on the assessment

After consulting with your Solution Architect, you have come up with the
following data model. When you are done with this module, you will have created
the entities, fields and relationship to implement the following data model, **as shown in the Lab Resources as Image[MB-200]_M02L02_Creating_Entities_Fields.png**.

In this practice, you will be creating the entities and fields. Later, when we
discuss relationships you will come back and add the relationships between the
entities. Relationships in the above drawing are the lines connecting the
entities and labeled as 1:N and N:1. The entities that are white with black
writing are standard CDM entities that we will be re-using.

**Important Note:** This lab will provide you with an actual Office 365 tenant
and licenses for the Power Platform applications you will be using in this
course. You will only be provided with one tenant for the practice labs in this
course. The settings and actions you take within this tenant do not roll-back or
reset, whereas the virtual machine you are provided with does reset each time
you close the lab session. Please be aware that Office 365 is evolving all the time. The
instructions in this document may be different from what you experience in your
actual Office 365 tenant. It is also possible to experience a delay of several
minutes before the virtual machine has network connectivity to begin the labs.

Exercise 1 - Acquire Tenant Information and Connect
---------------------------------------------------

**Note:** If you have already completed a practice recently, the virtual machine
might pick up where you left off and you will not need to login again.  In that
case you can skip ahead to exercise two and resume.

### Task 1 – Connect to the Power platform administration portal

1.  On Virtual machine MB200-Dynamics_Lab, sign in as Admin with the password
    Pa55w.rd if you are not already logged in.

2.  Outside the VM in the online lab interface click Files and choose D365
    Credentials. This will allocate an Office 365 tenant for you to use in these
    labs.  It will display the admin email and password for your tenant.  You
    should copy this information to notepad or similar for your reference.

3.  In MB200-Dynamics_Lab launch Microsoft Edge from the taskbar. By default,
    the browser opens Office 365. Use the O365 credentials you just acquired in
    the previous step to login.

4.  Navigate in the browser to the Power platform admin portal at
    [https://admin.Powerplatform.microsoft.com].

Exercise 2 – Create the Knowledge Assessment Entity
---------------------------------------------------

In this exercise, you will be creating the Knowledge Assessment entity and its
fields. Knowledge Assessment will be a new custom entity you create.

### Task 1 – Create an entity

1.  Navigate to <https://make.powerapps.com>

2.  Make sure you are in the **Practice** environment you created.

3.  Select **Solutions**.

4.  Click to open the **Common Data Services Default Solution**.

5.  Click **New** and select **Entity**.

6.  Enter **Knowledge Assessment** for **Display Name**.

7.  Edit the **Plural Display Name** and **Name** if appropriate.

8.  Click **Create**. It may take a few minutes for your entity to be created.

9. With the **Fields** tab selected, click **Add Field**.

10. Enter **Start Date** for **Display Name** and select **Date Only** for
    **Data Type**.

11. Click **Advanced Options** and make sure **User Local** is selected for
    **Behavior**.

12. Click **Done**.

13. Click **Add Field** again.

14. Enter **End Date** for **Display Name** and select **Date Only** for **Data Type**.

15. Click **Advanced Options** and make sure **User Local** is selected for
    **Behavior**.

16. Click **Done.**

17. You will now add an **Option Set** type filed. Click **Add Field**.

18. Enter **Difficulty** for **Display Name** and select **Option Set** for
    **Data Type**.

19. Click on the **Option Set** dropdown and select **New Option Set**.

20. Enter **Beginner** for **Item 1** and click **Add New Item**.

21. Enter **Intermediate** for **Item 2** and click **Add New Item**.

22. Enter **Advanced** for **Item 3** and click **Save**.

23. Select **Beginner** for the **Default Value** and click **Done**.

25. Click **Save Entity** at the bottom of the screen.

### Task 2 – Create a calculated field

1.  Click **Add Field**.

2.  Enter **Days Remaining** for **Display Name** and select **Whole Number**
    for **Data Type**.

3.  Click **Advanced Options**.

4.  Enter **0** for **Minimum Value** and **1000** for **Maximum Value**.

5.  Click **+Add** next to **Calculated or Rollup**. Click **+Calculation.**

6.  Click **Save**. A pop-up window should appear allowing you to configure the calculation.

9.  Click **Add Action**.

10. Enter *DIFFINDAYS(NOW(), cr240_enddate)* and click on the checkmark. Note
    that cre7F is environment dependent and your prefix will likely be slightly
    different. To find your environment specific prefix, type **cr** and wait
    for the field to auto filter to the correct prefix.

11. Click the check box to **Save Your Changes**.

12. Click **Save and Close**.

13. Click **Done**.

Exercise 3 – Create the Knowledge Question Entity
-------------------------------------------------

In this exercise, you will be creating the Knowledge Question entity and its
fields.

### Task 1 – Create an entity

1.  Go back to <https://make.powerapps.com> and make sure you are in the
    **Practice** environment.

2.  Select **Solutions**.

3.  Open the **Common Data Service Default Solution**.

4.  Click **New** and select **Entity**.

5.  Enter **Knowledge Question** for Display Name.

6.  Click on the **Primary Name** filed.

7.  Change the **Display Name** to **Question**, change the **Name** to
    **Question** and click **Create**.

8.  Make sure the **Fields** tab is selected and click **Add Field**.

9.  Enter **Answer 1** for **Display Name**, select **Text** for **Data Type**
    and click **Done**.

10. Add **3** more with values below:

    - Name: **Answer 2**, Data Type: **Text**.

    - Name: **Answer 3**, Data Type: **Text**.

    - Name: **Answer 4**, Data Type: **Text**.

14. Click **Add Field**.

15. Enter **Answer 1 Points** for **Display Name**, select **Whole Number** for
    **Data Type** and click **Done**.

16. Add 3 more filed with values below. These will store the points awarded if
    someone picks this answer.

    - Name **Answer 2 Points** Data Type **Whole Number**.

    - Name **Answer 3 Points** Data Type **Whole Number**.

    - Name **Answer 4 Points** Data Type **Whole Number**.

    - Click **Save Entity**.

**Note:** There are many ways you could model the answers depending on the complexity of your requirements. The approach shown here is simplified for practice purposes to focus on demonstrating how to work with the entity creation process.

Exercise 4 – Create the Knowledge Test Result Entity
----------------------------------------------------

In this exercise, you will be creating the Knowledge Test Result entity and its
fields.

### Task 1 – Create an entity

1.  On the navigation menu, click **Common Data Services Default Solution** to return to the solution.

2.  Click **New** and select **Entity**.

3.  Enter **Knowledge Test Result** for **Display Name** and click **Create**.

4.  Click **Add Field**.

5.  Enter **Total Points** for **Display Name** and select **Whole Number** for
    **Data Type**.

6.  Click **Done**.

7.  Click **Save Entity**.

Exercise 5 – Add existing entities to the solution
--------------------------------------------------

In this exercise, you will be adding the existing entities Feedback and User.
This ensures when relationships are created later between theses entities they
will be tracked as part of the solution.

### Task 1 – Add existing entities

1.  From the navigation menu, click **Common Data Services Default Solution** to return to the solution.

2.  Click **Add Existing** and select **Entity**.

3.  Select the **Feedback** and **User** entities and click **Next**.

4.  Leave the **Include All Components** and **Include Entity Metadata**
    unchecked and click **Add**.

5.  Your solution will now have **5 Entities** and **1 Option Set**.

6.  Click **Publish All Customizations**.
