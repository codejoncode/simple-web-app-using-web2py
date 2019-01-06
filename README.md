# simple-web-app-using-web2py
The following README will include step by step instructions to generate a simple web app using web2py and Python. 
**Download WEB2pY**   

http://web2py.com/init/default/download
 - Choose Windows or Mac depending on your operating system. 
 - Extract the files 
 - go the web2py.exe file and double click 
 - choose a password for the local server then click start server. 

By default you should see the welcome/default/index page created by web2py developers. 
- Click Admin 
- Enter your password 

At this point you should looke at your admin and any installed applications you may have. This is also where you can disable and manage those same applications.  By default you will see the code for the welcome application  and it will be enabled. Anytime we create a new application we will be making a copy of the welcome application. 

**Creating a new application**

- To the right enter in a name 
- Click create 

You will be brought to a page that will say Edit application " your_appName " 
Inside you will have access to Models, Controllers and views, Languages Stactic pages Modules, private files and Plugins. This is where we will create/ edit our page.  Drill down to the applications folder see the source code.  Drill down in the controller we will see our python code.  Drill down the view  and we will see the frontened and server url. These files will be in the same foldeer you downloaded web2py. From here you can go to the applications folder find your newly created applications and then go to the controllers file. There will be a default.py file that you can open up in any code editor. 

MVC is not just a web architecture but a naming convention between the controllers and the view. 

The manage button allows us to have options to begin focus on the edit option which will take you behind the scenes of your applications.   Web2py provides a web base IDE however you can get access to the same files and edit them outside of the web browser if you choose to. 

- To start create a new controller and give it a name (I am going to name it basics and naming yours basics will make the instructions throught this readme make more sense)
- You will see that by default there is a index. Start by creating your own function. 
- Implement a helloworld function
- Inside of the function create a variable message and set it to hello world from the controller
- return locals() 

**locals() taks all local variables created within the function and returns it to the view.**
- save the controller and click edit at the top. 

You will now see your newly create controller_name.py  exposes the helloworld function you created. Awesome work! 

- Next create the view
- go to the bottom of the view section and click create. 
- Remember the nameing convention  [name of controller/function]
- Example if the controller is basics and the function is helloworld our view should be created with the filename  basics/helloworld

This can't be stressed enough **MVC is not just a web architecture in web2py, but, a naming convention betwen the controllers and the view.**

- The html extension will be created automatically. We can then go an d edit the view but clicking edit next to our newly created view name. 
- Change the h1 element so that it has the title you choose for your webpage 
- by the default you will notice {{=something}} change this so that it =your variable you are returning from the helloworld function. 
- You can also wrap the {{=message}} around a html element try a h2 tag h2 {{=message}} h2. (Note I didn't put the actual h2 structure because it changes the code in visual studio and actually uses a h2 tag)

**Everything within the double curly brackets means python code.**

So above we will display our message being returned from python. At this point we should be able to view our website and see our message. 

You may want to have two browser windows up one to view the site and one to eidt. 

You will need the following :  servername/appName/controllername/viewname 

server is likely: http://127.0.0.1:8000/

application name if it is   awesome  
http://127.0.0.1:8000/awesome

controllername if  basics  
http://127.0.0.1:8000/awesome/basics

viewname  if  helloworld 
http://127.0.0.1:8000/awesome/basics/helloword 

This final url should provide you with your website and show your title and returned information on the screen.  Note  we named the view  the controllername/nameWeChooseForView.   The nameWeChooseForView is technically the view name we only had to tie the view to a specific controller. 

Web applications use HTTP protocols for WEB2py  uses two common objects
request and response.   Request  object anything passed from the client to the web server. This can be any device on the internet.  

**Request Arguments & Variables**
Arguments 
- URL - associated
- request.args(0), request.args(1), ...(access)
- The location is important where the arguments are. 

Variables 
- Froms - associated 
- request.vars.form_name (access)

Now to work with requests lets perform a simple example of adding two numbers using  arguments and variables. 

- Go back to the controller you created. 
- define a function  request_args  
- create two variables access the first and second index
- add these two  variables together.  

Things to note,   the arguments will be in the url so they come to you as strings.  We won't be able to add them mathmatically unless you cast the string to int or float.  

- create a variable that sums up the two variables we created. 
- return locals() 
- save the file

We now have three local variables and all three will be available to our view.

- click edit at the top
- We will now create a new view
- Remember we have to refer to a specific controller I am using basics as the title of my controller so if i refer to basics just know this is the controller you orginally created.  We only need the one for now. 
- create the new view   basics/request_args    (remember request_args is our view name but we have to connect a specific controller to the view)
- After creating the file  edit it. 
- Create a h1 header / edit the one that is there already. 
- create a h3 tag that will display the total remember double brackets is how you reference python code.   

- lets view the site  by going to the following  server/app/controller/view/arg1/arg2
- remember  server is likely to be your local server  http://127.0.0.1:8000
- Then you will put in your application name / controller name /  view name
- The arg1 is just a number you wish to add  same with arg2.  
- Remember  arguments are associated with the URL.  Anything after the http://127.0.0.1:8000/appName/controllerName/viewName/ is considered an argument each / seperates them.  We will access these arguments using  indexing starting at 0.  In the  controller file (mines is called basics) you should locate these arguments with the request.args(index)  index starts off at 0 and goes up. To access the first two we only need   arg1 = float(request.args(0))   and arg2 = float(request.args(1)). We use float to cast the string argument to a float, this allows us to add mathmatically and prepares us to accept decimal arguments say  8.6.  
- going to http://127.0.0.1:8000/appName/controllerName/viewName/2.3/4.9 should display 7.2

- Now lets go back to the controller basics (or whatever you called it) 
- define a function called request_vars  
- create a num1 variable num2 and total initialize them at 0 
- add a conditional if request.post_vars  
- set num1 = float(request.post_vars.num1)
- set num2 = float(request.post_vars.num2)
- set total = num1 + num2 
- Importnat the last three steps should be with the conditional block 
- return locals()

request.post_vars basically takes a look at the variables after they have been posted. 

- Create a new view   the view name should be request_vars  
- Remember  we have to specifically tie a controller to our view 
- basics/request_vars   is the name we enter into the field to create a view. 
- edit the h1 element to the title you wish  Request Vars would be a good one. 
- create a form
- add method= 'post to your form   <form method => 
- now add in three inputs   
- The first two inputs will have the type = 'text'  
- The third input should have the type  = 'submit'
- add the name attribute = 'num1' to the first input 
- add the name attribute = 'num2' to the second input 
- name = 'num1'  - example 
- add a value attribute to the third input   set it to 'Add'

You may have noticed the  request.post_vars.num1   and the num2 version. We are able to access this because we are giving these sections a name. If i named it  text1 I would have to refence  request.post_vars.text1.  

- We still need a h3 tag(not neccessairly h3 but a html tag) that will display the total we are going to return.  Remember  double curlys is how you access the  python code. Also note we will say between the double curlys   =total. 
- Go to the site server/appName/ControllerName/ViewName 
- You should see two input boxes and a add button.   
- Enter in a number in both inputs and click the add button. This should return the correct value. 


Other request properties.   
def request_object ():
    app = request.application
    cntr = request.controller
    fx = request.function
    ext = request.extension
    folder = request.folder
    now = request.now
    client = request.client
    isSecure = request.is_https
    return locals()
- add the function above to basics controller
- create a request_object  view
- change the file you just created so that it displays each variable in the function above. Doing this may be easier if it is a li. to do this you will need to first create a ul.
- Do remember  {{=variableName}}.  YOu can also do something between the li tags to identify the variable   APPLICATION: {{=app}}
- save the file
- go to the website 
- server/appname/controllername/viewname
- If my app is named awesome and my controllers name is basics I would be going to  http://127.0.0.1:8000/awesome/basics/request_object/
- Everything should load up on that site   < li > APPLICATION: {{=app}} < li > each of your li tags should look similar to this and the li tags should be nested inside of a ul tag  < ul >  < /ul > only without the spaces. 

Overall the extra properties on request explain more about the request. app provides the app name. Client provides the first part of our server 127.0.0.1 cntr  is the controller name. ext  is the type of the file html. folder shows the folder where the applications is installed.  fx is the view name.  isSecure checks if were are using https: or http   returns true if https: and false if not.  now provides a datetime stamp   year, month day and hour and minute along with the second are sent back. These properties may not be very useful to us sending a request. But it may be useful to us as web developers. We may want to block certain clients. We may have different options for  isSecure == false or true.  We also may have different options for ext types.  This is a simple application at the moment but these other properties could be used to make our application more secure, more complex etc.. 

**Response Objects**

This is the exact opposite of the request.  Response will return something to the client. 

To read more on response  go to http://web2py.com/books/default/chapter/29/04/the-core#response

response.write, response.cookies are very popular you are also able to download using response.download.  

For now we are going to use response.flash to provide a simiple message to the user. response.flash is an optional parameter that may be included in the views. Normally used to notify the user about something that happened. 

- Go back to the basics controller 
- Navigate to the request_vars function
- add in response.flash = T("The total is " + str(total)) to the bottom of the function just before the return statement. Make sure its nested within the conditional code block. 
- Save the file 
- Navigate back to the request_vars portion of our application  serverName/applicationName/viewName
- enter in two numbers one for each input then click add.  
- You will notice thate there is a pop up that shows you the answer along with the answer being where we placed it.  This is just an simple example of how we can communicate back to the client. 


**Business Rules and Libraries**

This is important for the organization of our code. Lets start off by adding some more functions in the basics controller. 

- start by adding the following code to the top of the basics.py file right after the comments

import random

def isPrime(num):

    counter = 2
    while count4er < num-1:
        if num % counter == 0:
            return False
        counter = counter + 1
    return True

def random_number():

    x = random.randint(3,20)
    result = isPrime(x)
    return locals()

The above is a function that figures out if a number is prime and returns true or false based off the results.   The other function randomly picks a number between 3 and 20 and calls isPrime on that number returning all of the locals.  We will have access to x and result with this function. 

Here we have imported a library (random) the business rule is our function isPrime that returns true or false. 

-Lets go ahead and show this in the browser create a veiw random_number 
- create a h3 tag asking whether the random number {{=x}} is prime 
- create a new h3 tag that shows the anser  = {{=result}}
- navigate to the page and check out how it looks
- if you continue to refresh the page you should generate a new number each time. 


**Deployment**

There are many places we can deploy the web2py. It is made for simple deployment. However what we will do is use https://www.pythonanywere.com 

You may know of or wish to look up others however pythonanywhere.com is very simple. 

- go to the website login or create an account 
- Beginner account is free by the way... 
- Pythonanywhere will allow you to run python console's in your browser for many of pythons versions available. For now we will focus on deploying a web application. 
- click  The menu option Web 
- click Add new web app
- Python anywere supports several Python web frameworks   Django, Flask, bottone but we want to click web2py since that is what we are currently using. 
- create an Admin Password 

Note worthy having a free account means if you do not login to the pythonanywhere.com site your site will go down 3 months from now. You will have to come in and click the button run until 3 months from today to keep it going. Pretty cool if you are sending out your profolio and linking your site you can see how many people have visited the link. They have more advanced data if you are paying but this is just fine for now. Upgrade once you come up with a potential money making idea. And even then updgrade once you cover the cost of service in sales.  Keep the bills at 0 until then.  

-  go to your configuration site  this should be your username.pythonanywhere.com 
-  once you get here you will notice that there is already a default welcome page.  Also a hello word pop that appears to use a similar feature as response.flash  
-  we need to go to our localhost code and publish it to our new website.  
-  click the site option on the nav bar 
-  go to your application name and click manage  then choose pack all 
-  It will begin downloading a w2p file. Save at the location of your choice. 
-  Go to the pythonanywehere  configuration page and go to adminstrative interface
-  login 
- you can keep the application name the same as when you created it inside web2py when you name the application. 
-  now we will take the file and publish it to the internet
-  upload the package we just created. (you will notice that you can use a github repo but we didn't do it this way)
-  check the box that says overwrite installed ap  then click install

There is also the ability to deploy on Google App Engine   this is something not covered in this readme but defintely worth looking to for a more complex  application. 

Go ahead and check out the site how I implemented it : 

http://codejoncode.pythonanywhere.com/simple_app_with_pluralsight/basics/helloworld 

http://codejoncode.pythonanywhere.com/simple_app_with_pluralsight/basics/request_args/2/3

http://codejoncode.pythonanywhere.com/simple_app_with_pluralsight/basics/request_object 

http://codejoncode.pythonanywhere.com/simple_app_with_pluralsight/basics/random_number

http://codejoncode.pythonanywhere.com/simple_app_with_pluralsight/basics/request_vars 

Again very simple but hopefully enough to get you excited about the possibilities in Python Web development. Unique stacks can make you stand out and certain the more stacks you have in your tool box the more you stand out as a web engineer.   This readme was create for practice, educational purposes and was used with help from a pluralsight lecture I got the chance to watch.  Besure to check out the views and controllers  I made copies of to include in this repo.  Note that without actually downloading and using the web2py  application the code will not work the same. The copies just , hopefully, illustrates the steps a bit more clearly. 

**Problems**

Ticket Issued  - if you see this every just click on the link and it will give you more information. If you have an error inside of your code you will likely get a Ticket issued internal error  clicking the link will provide more information on what the issue is. 

I did not really see any other problems that might arise. Just try to follow the instructions and have fun. 
