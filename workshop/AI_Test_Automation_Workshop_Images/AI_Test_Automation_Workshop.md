![image1](ai_test_automation_images/image1.png)

AI Test Automation Workshop

This guide outlines the step-by-step process to create tests, add them to test suites, and integrate these suites with the Harness CD pipelines.

Step 0: Setup

Your first step to creating a test starts by creating a project (in the  account) and adding a test environment. If you already have a sandbox project, then this step is optional. 

![image2](ai_test_automation_images/image2.png)

If not, select your account () and navigate to Manage Projects. Once a project is created, like  the one below click on the module selector. 

![image3](ai_test_automation_images/image3.png)

From the module selector, select AI Test AutomatiAITon

![image4](ai_test_automation_images/image4.png)

This action will start your journey with AI Test Automation.

At this point, you should see the following -

Your project selected on the project selector

The create environment page 

![image5](ai_test_automation_images/image5.png)

Enter the following for the two fields and click on Create Environment.

 Ignore the “No login task found” warning

Once the environment is created you should see the following page. You are now ready to create your first test. 

![image6](ai_test_automation_images/image6.png)

Step 1: Creating a New Test

Once you land on the Overview page, you will click on the Create Test button. You will now see a modal that should show the 

environment name as your test environment name. 

start url is the URL of the page where the browser will navigate to first when the test runs

Tunnel which indicates whether Harness cloud can access the environment

Note: If the app is not accessible publicly and is behind a firewall Harness AI Test Automation can access the environment either via  or through i/p .

![image7](ai_test_automation_images/image7.png)

Click on the Create test  button to start creating your test.

Before you proceed further, please note that a tester ( QA or Dev) usually has a test case that they want to convert to a test. In this case, we will use the following test case. 

Once the Create Test button is clicked, we will see the test interactive authoring (IA)  screen is opened. This is essentially opening your desired application into a browser running in the cloud. 

Once the application is displayed within the browser you are ready to record the test. 

![image8](ai_test_automation_images/image8.png)

Recording your first step and adding an assertion

Test step 1: Click on the currency selector and select Euro as the desired currency 

Test step 2: Write an assertion in natural language - “Are the item prices displayed in Euro ?“

![image9](ai_test_automation_images/image9.png)

Once the assertion runs you should see the assertion passing and an explanation confirming why the assertion pass. 

![image10](ai_test_automation_images/image10.png)

Test step 3: Now set the currency back to USD. This will require you to repeat the step you have done in step 1. 

![image11](ai_test_automation_images/image11.png)

Now let us move to the next step of adding the cheapest item to the cart. Keep in mind this is a dynamic step i.e. in a real app ( even in test environments) the item with the lowest price can change. So it is important that we use a method that can adapt to the changing data. 

We will use an AI command to determine the lowest priced item and add it to the cart. 

Test step 4: Add the cheapest priced item to the cart

![image12](ai_test_automation_images/image12.png)

Once the task starts running you will see the AI thoughts displayed in the AI insights tab. 



Navigate to the AI Insights tab and check out what AI is doing - this step may take a minute to run

![image13](ai_test_automation_images/image13.png)

You will see that the cheapest item has been selected once the AI Command is executed, and the shipping address is displayed. Now, click on the Steps tab again. 

Our intention was to add the item and check out of the application. Let us keep the shipping address as is, but change the email address to something else. We will again use AI to do so. 

Test step 5: Select Set a parameter option by clicking on Add Step

![image14](ai_test_automation_images/image14.png)

The Set parameter displays a form with Parameter name and a  value. Here you will end the following 

In the parameter field write the desired parameter name which in this case is - EMAIL

Next up, click the config ( wrench icon) button and select from different options (random.email, custom scripts etc) the `generate with AI`  - Then you can provide the value to AI as - Email Address

![image15](ai_test_automation_images/image15.png)

![image16](ai_test_automation_images/image16.png)

Press Done and then click on Apply. 

Test step 6: Once the parameter is set, add a new step of `Write` to add the email address field 

You will click on the email address field and then select the parameter you just added by clicking on the blue parameter icon 

![image17](ai_test_automation_images/image17.png)

Once you click on Apply you will see a random email is added to the field. 

![image18](ai_test_automation_images/image18.png)

You can now add more test data to the different address fields or click on the continue shopping button 

Test step 7: Click on the Continue Shopping button on the cart page

![image19](ai_test_automation_images/image19.png)

![image20](ai_test_automation_images/image20.png)

Test step 8:  Add an assertion to ensure you have navigated back to the home page

Now we will use a more traditional way of adding a text based assertion. Select Assert text exists from the list of assertions 

![image21](ai_test_automation_images/image21.png)

In the text box add “Hot Products” and click Apply 

![image22](ai_test_automation_images/image22.png)

Now that you have written the test, let's save the test and run it. Click on the save button on the top right and give your test a name.

![image23](ai_test_automation_images/image23.png)

Once the test saves, it will now automatically execute. You can view the progress on the test run page. 

![image24](ai_test_automation_images/image24.png)

Step 2: Adding the Test to a Test Suite

![image25](ai_test_automation_images/image25.png)

Navigate to the test listing page by clicking on tests on the left navigation bar. 



Once you select the checkbox next to the test name you will see a toast menu pop up. Keep in mind, usually a customer groups a number ( often 10+) tests together in a test suite. But for this training let us work with the single test 

![image26](ai_test_automation_images/image26.png)

Once you click on the Add to Suite button you will see an empty modal. There are no pre-existing test suites. Enter the name of the test suite “ My first test suite” or any thing that you please.  Click on Add.

You will now have your first test with one single test in it. 

![image27](ai_test_automation_images/image27.png)

The next step would be to call it from a Pipeline

Step 3: Integrating the Test Suite with Pipelines

![image28](ai_test_automation_images/image28.png)

Please select Continuous Delivery from the list of modules. You may see a screen that talks about the module, please click on the cross sign ( X) and close it. 



And then either create a new pipeline or you can also reuse an existing pipeline. Our goal for this part of the lab is to add the AI Test Automation step and execute the Test suite you just created. 

In this example below, I have created a new pipeline with a “custom stage” and I will add AI Test Automation as a step 

![image29](ai_test_automation_images/image29.png)

![image30](ai_test_automation_images/image30.png)

Click on Add Step and search AI Test Automation from the list. 



Once you have selected the step please add the following details 


The name of your application (project) 

Name of the test environment 

Name of your Test Suite Name

![image31](ai_test_automation_images/image31.png)

Now click Apply Changes and save your pipeline.

Once the pipeline is saved, you can now Run the pipeline. You should see the link to the test suite on the console view. 

![image32](ai_test_automation_images/image32.png)

It should take a few minutes to execute the pipeline. You can also click the link to view the progress of the test suite. 

![image33](ai_test_automation_images/image33.png)

Clicking the link opens a new tab with the details of the test suite run 



| Test environment name | Test |

| Test environment URL | https://qa.boutique.harness-demo.site |

| Make sure the currency selector is working and the user is able to add the cheapest item to the cart and checkout |
