
# Building an Integration with Power Shell

## Speakers:

- Venkata Koya
- Raghavan Muthuraman
- Chakradhar J

## Lab Goal
In this lab, you'll learn how to build an Integration Hub Spoke and how to build actions using Power Shell
This lab also explains the Best Practices for Spoke Development

1. Lab 1 : Create a Integration hub Spoke
2. Lab 2 : Create a Power Shell action in the Spoke created in Lab 1
3. Lab 3 : Best Practices for Spoke Development


###Microsoft AD(Active Directory): 
Active Directory stores information about network components. It allows clients to find objects within its namespace. The term namespace (also known as console tree) refers to the area in which a network component can be located. For example, the table of contents of this book forms a namespace in which chapters can be resolved to page numbers

Installation & Configuration of AD is out of scope of this lab.


## LAB-1: Create a Integration hub Spoke

A Spoke helps you to identify the area of interest. Following steps helps to create a spoke in Servicenow:
1) Create a scoped app  in Servicenow and name it accordingly. In out case it is AD Spoke
2) Change the Developer scope to this Scoped app now 
3) You are ready with Scoped app in which you can develop actions
![Screen Shot 2018-02-12 at 11.30.52 PM.JPG](../../screenshots/Screen Shot 2018-02-12 at 11.30.52 PM.JPG)


## LAB-2 : Create A Power-Shell action

Once the scoped app creation is successful and changed the scope of development, ensure that the required plugins are installed:
1) com.glide.hub.integrations

           ( OR )
1) com.glide.hub.designer_backend.model
2) com.glide.hub.action_step.powershell

Both will help us creating actions in powershell
P.S. : Integration help can be seen by only licensed users
![Screen Shot 2018-02-12 at 11.39.46 PM.JPG](../../screenshots/Screen Shot 2018-02-12 at 11.39.46 PM.JPG)

### Creating an action:
1) Once landing in Flow-Designer, Click on New Action.
2) Enter Basic details for the action and click on Save

![Screen Shot 2018-02-12 at 11.44.40 PM.JPG](../../screenshots/Screen Shot 2018-02-12 at 11.44.40 PM.JPG)

Once you submit, the action designer opens and you start the action developement

![Screen Shot 2018-02-12 at 11.45.35 PM.JPG](../../screenshots/Screen Shot 2018-02-12 at 11.45.35 PM.JPG)

Add Few inputs which are called as Action inputs ( Think of Action as a function which takes input and provides the output). These inputs are available for the further steps as pills so that you can drag n drop those to the necessary places

Next, we will Create a PowerShell step in our actions. Click on + Icon (Add a  new step) and select PowerShell under Integrations
![Screen Shot 2018-02-12 at 11.49.40 PM.JPG](../../screenshots/Screen Shot 2018-02-12 at 11.49.40 PM.JPG)

![Screen Shot 2018-02-12 at 11.49.30 PM.JPG](../../screenshots/Screen Shot 2018-02-12 at 11.49.30 PM.JPG)

The new step has a bunch of details to be taken care

1) AD Connection (Alias, Connection & Credentials)
2) PowerShell script 
3) Inputs

### AD Connection:
 It is advised to have a single alias for all the actions, so that there is no need to define the connection again and again. Servicenow communicates with AD through MID server, so the pre requisite is having a MID server ready. So following details have to be taken care:
 
 1) MID server to be set up and should be in the same domain as AD. Validated and Up.
 2) while setting up Connection, the HOST should be AD and mid server option should be selected
 3) Credentials should be provided with the user details who is authorized to do all the actions that are in the scope of the Spoke.

### PowerShell Script

Servicenow standard of writing code units is through script files (for powershell), but the option of inline scripting is not denied to the user. it's user's choice to chose the right option.
An inline script can look like:
![Screen Shot 2018-02-12 at 9.57.20 AM.JPG](../../screenshots/Screen Shot 2018-02-12 at 9.57.20 AM.JPG)
It is obvious that the above  inline script requires the parameters to be passed. So, use the input variables section to pass the parameters (Drag and drop the values from the Data section which is on the right side of the Action Designer):
![Screen Shot 2018-02-13 at 12.05.04 AM.JPG](../../screenshots/Screen Shot 2018-02-13 at 12.05.04 AM.JPG)

The possible outcomes of any PowerShell step are : 
- Output
- Error Message
- Windows Error Code

In the Outputs section, drag and drop the above PowerShell step outputs to prepare the Action outputs.

![Screen Shot 2018-02-13 at 12.08.27 AM.JPG](../../screenshots/Screen Shot 2018-02-13 at 12.08.27 AM.JPG)

Save. Publish the action to make it usable
![Screen Shot 2018-02-13 at 12.09.09 AM.JPG](../../screenshots/Screen Shot 2018-02-13 at 12.09.09 AM.JPG)

### Create a Flow
Now user has the choice of creating a flow using the above action. Following steps would help user to create a flow :

1. Go to Home in Flow Designer
2. Click on New -> New Flow
3. Enter flow properties and click on Submit
4. Add a trigger point (her we select when a sys_user record is created)
5. Add action created above in the flow by supplying the input values (again, drag and drop the values required)
6. Save, Test and Activate

![Screen Shot 2018-02-13 at 12.14.36 AM.JPG](../../screenshots/Screen Shot 2018-02-13 at 12.14.36 AM.JPG)

Note: Activating a flow triggers the flow whenever the condition is met

## LAB -3 : Best Practices

The following best practices would help to Develop and Manage Spoke easily
1) Create Spokes for each are of interest. Do not mix
2) Always have only ONE Connection Alias per Spoke
3) Reduce inline scripting. Use MID Server -> Script files
4) Anticipate and handle errors in actions using Script steps
5) While Creating flows, be careful while using conditions. Do not end up in loops

## Conclusion:

In Microsoft world, Power Shell scripting is very powerful and handy. One can achieve a lot with simple commands. Combined with Servicenow Automation tool (Flow Designer and Integration Hub), user is presented with more powerful Automations. Without any human interventions everything is managed easily












 




      








 




