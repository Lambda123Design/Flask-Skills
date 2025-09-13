# Flask-Skills

A) Understanding Simple Flask App Skeleton

B) Integrating HTML with Flask Web App

C) HTTP Verbs Get and Post

D) Building Dynamic Url ,Variables Rule And Jinja 2 Template Engine

E) Working With Rest API's And HTTP Verbs Put And Delete

A) Understanding Simple Flask App Skeleton

### WSGI Application

app=Flask(__name__)

@app.route("/") [Decorator] (/ - This takes to the homepage)
def welcome() - Defining the function:
return "Welcome to the Flask course"

### The below code needs to be at every .py files to run

if __name__=="__main__":
app.run()

#### First Krish ran with app.run alone and then changed to "Welcome to the Flask course". This should be an amazing course"

### But till he restarted the page didn't get updated;

#### Everytime we can't restart server; Everytime developing we can restart servers

##### Once we use app.run(debug=True), it gets updated automatically

#### Anytime we make changes, it restarts the server

#### We can add as many as routes we like; We add "Index" route too;

@app.route("/index") [Decorator] (/ - This takes to the Index Route)
def index() - Defining the function:
return "Welcome to the Index Page"

#### **We can see in Local_Host/index (Say https://127.0.0.1:5000/index)**

B) Integrating HTML with Flask Web App

HTML Files is a Web Framework

We have updated to:

@app.route("/")
def welcome() - Defining the function:
return "<html><H1>Welcome to Flask Course</H1></html>"

Ran it through "python app.py"

If we inspect it, it will be a HTML Tag;

This is an easy way on how we can integrate HTML and Flask

### This is not a very good practice because we need to write a lot of HTML Codes in most of the applications

### We will create a separate HTML Page

#### Whenever we go to this particular home page, we want it to get redirected to the HTML Page; We will use a library called "render_template"

#### render_template will be responsible to redirect to that particular HTML Page

@app.route("/index") [Decorator] (/ - This takes to the Index Route)
def index() - Defining the function:
return render_template('index.html')

## We may be thinking that we are redirecting it to index.html page, but we have not created any index.html page 

## We will use Jinja 2 Template Engine

#### That template works under particular template called, "render_template", which is responsible for redirecting to that particular HTML Page; And when it is redirecting it is going to look inside the particular folder and will look for a folder called "Templates"

### It will go inside "templates" folder and look for "index.html" file

### Krish wantedly created index1.html and when ran in Python and went to "https://127.0.0.1:5000/index", it gave a error that "Template not found: index.html"

### Now he created the "index.html" file and wrote the below code:

<h2>

Welcome to the Index Page of Flask Course
  
</h2>

### Now it works; and that's how we create entire HTML Page

#### As a Data Scientist, it is fine if we didn't know basic knowledge of HTML, because in a team in a company there will be frontend developers who knows HTML

## Created another Route:

@app.route('/about')
def about():
return render_template('about.html')

Krish pasted code in templates --> about.html and it worked when we went to "https://127.0.0.1:5000/about"

C) HTTP Verbs Get and Post

## HTTP Verbs has 4 Types - Get, Post, Put, Delete

Here We will learn about Get and Post

1. @app.route("/index"); This will have a parameter in Brackets, which by default be GET

### When we search for "wwww.google.com", it gets connected to a Web Server and from that Server, it is going to interact with "Google Web Application", and the default content that should come will displayed in front of us

### This is a GET Request; We are hitting a URL and getting content; We aren't Posting anything

### He seacrhed for "Krish Naik" in Google and able to get some response;

### This is an example of "Post" Request; In URL, we get as searchquery="KrishNaik"; 

### Some input is going to Web Server and it will interact with Web Application, which in turn communicate to the Database and get that information, crawl that entire information and get the information about "Krish Naik"

2. @app.route("/index",methods=['GET'])

**We used the above same example, but just mentioned "GET" and went to "index" and it was same; as by default GET is method mentioned**

#### 3. Creating a POST Request:

@app.route('/form', methods=['GET','POST'])
def form():
  if request.method=='POST':
      pass
  return render_template('form.html')

  ### Krish created a 'form.html' to get inputs as a "form" from the user

  ## Form code is (An important part alone): 

  <h1>Submit a form</h1>
  <form>method="post"
  <label for="name">Name:</label>
    <input type="text" id="name" name="name">
    <input type="submit" value="Submit">
  </form>

  ### Once he ran in VS Code and go to "https://127.0.0.1:5000/form"; It goes to a "GET REQUEST" and said "Submit a form" ;Gave his name and clicked on "Submit"; But Nothing has happened as we just wrote "pass" in Python code

  **Updating the Python code to Capture it**

  @app.route('/form', methods=['GET','POST'])
def form():
  if request.method=='POST':
      name=request.form['name']
      return f'Hello {name}!'
  return render_template('form.html')

### This is one route we are handling both "GET" and "POST"

### Id=name in "form.html" file; So we are retrieving it in POST Method

### Once we ran it in VS Code; Once Krish typed his name and submit it; It took to fresh page and showed "Hello Krish Naik"

### What happened - The POST request got successful, it is retrieving the name and showing "Hello Krish Naik"

**POST we can redirect it to another HTML Page; We will see also how we can use the name to that particular HTML Page; That is where JINJA2 technique will come; We will learn later in this course**

D) Building Dynamic Url ,Variables Rule And Jinja 2 Template Engine

Hello guys. So we are going to continue our discussion with respect to statistics. In our previous video, I had actually shown you how we can work with Get and Post. Uh, we had actually created one form dot HTML. Uh, we filled some of the information in the name field, and then we were able to get that particular information in the slash form. Right. Like slash form.

Now one more thing that I really want to show you over here. Uh, in this form method, you also have something like action parameter. Now inside this action parameter, whatever URL you give, you can directly go ahead and hit it over here. Let's say if I go ahead and hit slash form here, you can see that I'll be hitting this particular form itself. Let's say if I go ahead and copy this same thing and paste it over here, and let's say that I want to go ahead and create my submit form. Then I can actually do this. Okay. So here what I will do instead of writing slash form I will just go ahead and write slash submit. Right. So what will happen is that when this entire page is basically getting loaded, if I click on the submit button, it will go ahead and hit the slash submit route.

Okay. So let me just go ahead and execute this and see whether this is working fine or not. So here I'm going to just go ahead and write "python get_post.py" once we execute this. So okay I'm getting an error. Let's see okay the function name is same. I'll just go ahead and change the function name because I just copied and pasted it. So here I'll just go ahead and write submit. Perfect. Now I think it should not give us an error okay. So if I go ahead and execute it. So yes my flask app has been started. So let's go ahead and click over here. Let me go ahead and write slash form. Oops. Slash form. Okay, so if I go ahead and write this now, I'll just go ahead and write crush scenic. Okay. Once I click the submit button it is hitting the slash submit button over here. See over here slash submit. And then basically it is hitting the slash submit route. And from this we are able to extract the name and we are able to display it. Right. So this is what we discussed in the previous video.

Now uh, what we are going to do is that we are going to go ahead and continue with the discussion. So in this video, what we are going to discuss about is that how you can build your URL dynamically. And second thing that we are going to discuss in this is about Jinja2 template engine. Both are very important. Uh, you can probably say a module in uh, developing a web application using flask. So we'll be discussing about both of them. Okay.

Uh, just to give you an idea, right now, we are able to get this particular name over here right now. Once we get this name, we should be able to, you know, redirect it to a HTML page. Let's say from here I will go ahead and redirect to an HTML page. And after I redirect to an HTML page, I should be able to pass this particular information dynamically to my HTML page where I will be able to display it. Okay, so that is my entire task. Right now I'm just going and displaying it over here. I'm just saying, hey, return this particular name. But what will be my task is that I will go ahead and call render template and call an HTML page. And in that HTML page I will pass this specific information. And that is where your Jinja2 template engine will come into uh working.

And in this video we are going to discuss about three main important topics. One is building URL dynamically. Then you have about something called as variable rule. And then you also have something about Jinja2 template engine. Now with the help of this Jinja2 template engine, any information that I get from the form, right. So let's say I want to probably, uh, take this entire name and pass it to my HTML page. I will be able to do it, and that is where your Jinja2 template engine will work. And we'll go one by one, step by step. Uh, first of all, we'll see what is building URL dynamically. Then we'll see variable rule. Then we'll see Jinja2 template engine. So let's go ahead and let's go ahead with step by step okay.

Now first of all uh let me just quickly go ahead and copy this entire code. Okay I will just paste it over here okay. Let's say I don't require this form okay. I'll just keep this slash submit. Now I will just go ahead and write "app.route". Okay. So I will just go ahead and write "app.route". Now inside this app.route I will go ahead and make one URL which is called as success. Success okay. So with respect to this particular URL that is success. Okay. What I am actually going to do is that I'll pass some parameter. Okay. So let's discuss about that particular parameter over here. Let's say in this success, uh, I am just going to make sure that I pass some value. And now in order to pass that value, I'll just go ahead and write score, okay. And I'll keep it like this.

Okay. Right now the first topic that we are discussing over here is something called as variable rule. Okay. Now what exactly is variable rule? I'll just talk in some time okay. Now here you will be able to see that I am able to provide one parameter. Okay. Now what I will do I will go ahead and create my function. And inside this function what happens is that as soon as I probably provide a parameter over here, right, I will be able to read this parameter inside this particular function. So if I go ahead and write "return 'the marks you got is ' , score". Okay. Uh, I'll just say, hey, this is my string operation, and I'll just go ahead and use a string or by default, whatever parameter I'm actually giving that will be considered as a string.

So now let me just go ahead and execute it now in order to execute it. So what I will do, I will go ahead and write "python jinja.py". So let's see whether it will work fine or not. So I'll just go ahead and click this link. Okay. After I click this link I will be able to get this HTML page. Now I here I'm just going to write slash slash. And my route was success. And let's say I'll give some value 55. So here you can see you are able to display this. The marks you got is 55 okay.

Now one important thing over here is that this value that I'm specifying over here is default a string value. Okay. Now since it is a string value, let me just go ahead and close this for time being okay. Terminal. Now if it is a string value you will be able to see that I will be able to give it directly over here. But now what if I just go and say that hey, you need to give an integer value over here. Right. I will just go ahead and write something like this "app.route('/success/int:score
')". Hey, you need to give an integer value over here, right? It will not be considered a string. Now if I try to execute it now. Right. If I try to execute it now, now the problem will be that will I be will I be able to get an any problem.

So that is what we are going to see over here. So now if I just go ahead and write slash okay slash. And let me just go ahead and write success. Success, success and 55. So here you can see I'm getting a type error. Can only concatenate string, not integer. The reason is very much simple. Over here what we have actually done, we have just given a integer value. We are. We are saying that we are assigning a role like the parameter that you really need to give over here should only be an integer. That's it. It cannot be a string. Now what I really need to do is that I really need to typecast this particular parameter.

So whenever we are passing any parameter over here, right. And we are saying we are assigning a role to a variable that, okay, you only have to give an integer value, or you can only give a float value, something like that. Right. So this basically is called as variable role okay. So here we are restricting a parameter with respect to the data type that we are passing it over here okay. So this is one basic example to understand about uh variable role okay.

Now let's go ahead and talk more about building URL dynamically. So these are some small topics. But building URL dynamically is very much important. Now what I will do uh, I will just go ahead and create this particular variable. Okay. And here I'm giving the score. Now let me just go ahead write write one condition. Let's say that I'll go ahead and create my result. And inside this result I'll say "if score >= 50: result = 'pass' else: result = 'fail'". Okay. I'm saying that if my score is greater than 50 then you just make the result as pass. Otherwise you make the result as fail. Okay, now this is, uh, a bit very much easy right now.

Okay. Now here, what I can actually do, uh, here I will say, is that I will try to return this particular result to my HTML page. Okay. So for this I will go ahead and write "return render_template('result.html', results=result)". Okay. And here let me just go ahead and create my "result.html". Okay. Now when I'm redirecting to my result.html page, obviously I need to also give this particular value which is called as result. Okay. So here what I will do I will create a parameter which is called as results okay. And I will assign that particular parameter this value the areas value that I'm assigning it over here okay.

Now I don't have result.html. See over here. Do I have any result.html? The answer is no. So let me just go ahead and create my result.html okay. Now once I create this particular file result.html. Now I need to read this particular value over here right now. How do I do it. So let's say and that is where your Jinja2 template engine will work. Because now this particular value or this particular value is a kind of data source. It has some kind of data. I need to take this particular data and display in the result.html. That is the most important thing.

Now the basic way of displaying this result is just by using this double bracket and closing bracket. And that is what Jinja2 template engine is all about. Okay, there are also other ways how you can probably display the result over here. So let me just go ahead and talk about one of the way. So here I will just go ahead and call that same result variable that I created over here. So it is a results okay I will say "Based on the marks you have {{ results }}". So passed or fail will basically be getting replaced by this result. So let's see now we will try to run this okay. We will try to run it and we'll try to see it whether everything is working fine or not.

So I will just go ahead and "python jinja2.py". Let me just go ahead and quickly open a browser. And here I will just say, hey, 127 .0. with 5000, 5000 is the default port. And now I'm just going to write success 55. So based on the marks you have passed right. So here you can see you have passed, right? I know spelling is uh, the sentence may not be right, so I will just go ahead and try to do the same thing over here. So I'll say, hey, based on the marks you have, you have, uh, instead of writing over here, I'll say passed, I will say failed. Okay. Done. Right now, if you go ahead and see it. And if I try to reload it now here you can see based on the marks you have passed.

Now, what has actually happened? When I gave 50 marks 55 over here, it went and compared this. Then it saw the result variable over here. Then with the help of render template we redirect it to the result dot HTML and result dot HTML is nothing but this specific part, right. And where we have actually created one additional variable which is acting like a data source, because it has some value over there. And that same value is basically getting displayed over here.

Now this is about Jinja2 template engine. So let me just go ahead and write over here. Okay. So here you can right. So see Jinja2 so quickly I will just stop this. So I will just go ahead and write "Jinja2 template engine". Okay. Template engine here there are multiple ways I will just go ahead and write a comment. There are multiple ways specifically to read the data source from the backend in the HTML page. So the first way which we have discussed is this one. Right. So this is nothing. But this is basically expressions to print output in HTML okay. So these are some of the expressions uh if I just use two brackets opening and closing. And if I write anything inside that, that basically becomes an expression. The second one that we can also use is this one. Right. So this is nothing. But uh, let's say if you have any conditional statement so you can write all the conditional statement inside this kind of braces. So I'll say conditional statement. Or you can have like for loop if condition while loop anything you can specifically. And the third thing that you can basically use in uh Jinja2 template engine is your comment section. So you can basically go ahead and write comment in this way. Okay. Single line comments. So this is for comments.

Now I'll show you both the example and then we'll discuss more about it okay. So now let's quickly do one thing okay. Let me just copy this same thing okay. And let me paste it over here with my another route. So here I will just go ahead and write success underscore results okay. Or I'll say success results okay. Let's say this is my URL. And here I'm giving int score okay. Now this is fine okay. Here I have written a condition. If score is greater than or equal to 50. Else result is like result is equal to passed result equals to fail. Now what I'll do over here is that I will just go ahead and create one expression or this expression is nothing, but it will be my dictionary. So here I will just go ahead and write "results = {'score': score, 'result': result}".

So this becomes my key value pairs where I'm giving two parameters. One is score and one is result. Once I get this particular expression what I will do I will pass this expression over here okay. Now see the magic. What will specifically happen. And this time let me just go ahead and create another HTML page, not in the same HTML page. So here I will just go ahead and write result one HTML page. So here you can go ahead and write result1.html page okay. Now inside this result dot one HTML page okay. Now the thing is that I need to read this particular expression. And you know the expression over here. The value it has is in the form of key value pairs. Now if it is in the form of key value pairs, you have to probably write a for loop.

Now for writing a for loop I can use this condition okay. And that is what I am actually going to show you how you can go ahead and write this condition. So I'll go to my result1.html. Let's say this is my HTML tag okay I will just go ahead and say hey, this becomes my H2 tag. I will say, hey, this are my final results, okay? And let me just go ahead and uh, use uh, uh, something like a table. Okay. So first of all, let me just go ahead and create my body tag. Uh, these are some of the basic skeleton in HTML. Now, what I will do, I'll say, hey, use a table border. Okay. Width is equal to two. Okay. And now with respect to this particular border, I'll just go ahead and use a numerical value okay. I will just close this border tag also.

Okay. Now here inside this border, from the expression that I am actually getting, I will just go ahead and use a key value pairs specifically with the help of for loop. So for that I will be using this conditional. Right. So this is what I have to use right now. My entire expression like how we write our code in Python language. So I can go ahead and write "{% for key, value in results.items() %} <tr><td>{{ key }}</td><td>{{ value }}</td></tr> {% endfor %}". See this is the beautiful thing right? I'm just going to write this particular code. It is just like writing a code in the back end. Right. And just by using this I'll be able to use the conditional statement.

Now let's say if I also go on to go ahead and use my comment section, I can go ahead and write like this "{# This is the comment section #}". And I'll close it over here right now. Let's go ahead and read the key value pairs. Right. We can how we can actually read it. Let's say that I'll go ahead and make my table header. And this will basically be my key. Right. So here I'll be reading my key. And similarly here I will use a TR tag. And here I will be using my value. Right. So see I'm combining both right. How you can read this. Both right.

So here you have for key comma value result dot items. Then this is the comment section. So this will basically run entirely with a for loop. And we can add any number of th and tr right. Based on the number of records that we are specifically getting. And finally, you will be able to see that we are also closing this particular bracket. So now if I go ahead and execute it now see let's see whether it will work or not. So this is my function that I'm actually going to call uh this expression that is success raise. Okay. So let me quickly go ahead and uh see that okay. So I will just go ahead and uh, open my template okay. Sorry. Terminal. And here I'm going to go ahead and write "python jinja2.py".

In Flask, one important thing to remember is that every route should have a unique function name. If you try to define two routes with the same function name, Flask will throw an error. Another common mistake happens on the template side when using Jinja2. For example, if you open a for loop or an if block, you must always close it properly with {% endfor %} or {% endif %}. Even a small typo, like adding a space ({% end for %}), will cause Jinja2 to raise an error saying it found an unexpected tag. Once that is fixed, everything runs smoothly.

When it comes to displaying output, sometimes people overcomplicate things with table tags like <tr> and <td>. To make it simple and clear, you can just use headings. For instance, if you want to show a score and result, you could directly write:

<h1>Score: {{ score }}</h1>
<h2>Result: {{ result }}</h2>

This way, the template is cleaner and the output is easier to understand.

Another powerful feature of Jinja2 is conditional rendering. Instead of doing all the logic in Flask, you can push some of it into the template. Imagine the backend only sends the student’s score. Then, in the template, you can decide whether the student has passed or failed using an if-else block like this:

{% if score >= 50 %}
    <h1>You have passed with marks {{ score }}</h1>
{% else %}
    <h2>You have failed with marks {{ score }}</h2>
{% endif %}

Now, let’s talk about Flask’s url_for. Instead of hardcoding routes, url_for lets Flask build URLs dynamically. This is super useful because even if the route path changes later, your code won’t break. For example, suppose you have a form where a student enters marks for Science, Maths, C, and Data Science. Flask can calculate the average in the backend and then redirect the student to either a /success or /fail page, depending on the result. This is done using redirect(url_for(...)).

Here’s what the backend might look like:

from flask import Flask, request, render_template, redirect, url_for

app = Flask(__name__)

@app.route('/submit', methods=['GET', 'POST'])
def submit():
    total_score = 0
    if request.method == 'POST':
        science = float(request.form['science'])
        maths = float(request.form['maths'])
        c = float(request.form['c'])
        ds = float(request.form['datascience'])
        total_score = (science + maths + c + ds) / 4
        if total_score >= 50:
            return redirect(url_for('success', score=total_score))
        else:
            return redirect(url_for('fail', score=total_score))
    return render_template('get_result.html')

Here, when the form is submitted, Flask retrieves the marks using request.form, converts them to floats, and calculates the average. Based on the average, Flask uses redirect(url_for(...)) to dynamically route the user. If the score is above 50, it redirects to the success route along with the score as a parameter. If not, it redirects to the fail route.

The cool part is that everything works together — the form collects data, Flask processes it, url_for handles clean redirection, and Jinja2 templates decide how to display the result. This integration shows how backend logic and frontend rendering can seamlessly combine to build interactive web applications.

## Summary:

1. Form Handling in Flask

Created a basic HTML form (form.html) where users enter data (e.g., name or marks).

Used the method attribute in the form (GET or POST) to send data.

Used the action attribute to specify the route where the form data should be sent.

<form method="POST" action="/submit">
    <input type="text" name="name">
    <button type="submit">Submit</button>
</form>

2. Flask Route for Form Submission

Defined a unique Flask route to handle form submission:

@app.route('/submit', methods=['GET', 'POST'])
def submit():
    name = request.form['name']
    return f"Hello {name}"


Important: Each route must have a unique function name. Reusing names causes Flask to throw an error.

3. Variable Rule in Flask

Used dynamic URL parameters to pass values directly in the URL:

@app.route('/success/<int:score>')
def success(score):
    return f"The marks you got is {score}"


int:score ensures the parameter is treated as an integer, not a string.

Helps restrict the type of parameter received in the route.

4. Passing Data to Templates Using Jinja2

Instead of returning raw text, Flask can render HTML and pass dynamic data:

return render_template('result.html', results=result)


result.html uses Jinja2 syntax to display dynamic data:

<h1>Score: {{ score }}</h1>
<h2>Result: {{ result }}</h2>

5. Using Conditional Logic in Templates

Jinja2 allows logic directly in HTML:

{% if score >= 50 %}
    <h1>You have passed with marks {{ score }}</h1>
{% else %}
    <h2>You have failed with marks {{ score }}</h2>
{% endif %}


Reduces the need to calculate all logic in the Flask backend.

6. Displaying Key-Value Pairs in a Table

Can pass a dictionary to the template:

results = {'score': score, 'result': result}
return render_template('result1.html', results=results)


Use a loop in Jinja2 to dynamically create table rows:

{% for key, value in results.items() %}
    <tr><td>{{ key }}</td><td>{{ value }}</td></tr>
{% endfor %}

7. Dynamically Building URLs

Instead of hardcoding URLs, Flask's url_for can dynamically generate them:

redirect(url_for('success', score=total_score))


Advantage: If the route changes, url_for automatically updates the URL everywhere.

8. Complete Flow Summary

(i) User fills the form (form.html) and submits it.

(ii) Flask receives the form data in the /submit route.

(iii) Flask calculates values or performs logic (e.g., average score).

(iv) Flask dynamically redirects to another route (/success or /fail) using url_for.

(v) Data is passed to the template using render_template.

(vi) Jinja2 displays data using expressions ({{ }}), loops (for), or conditional statements (if).

(vii) Optional: Use tables or HTML structure for better formatting.

E) Working With Rest API's And HTTP Verbs Put And Delete

In Flask, we can handle more than just GET and POST requests. There are also PUT and DELETE HTTP verbs, which are extremely useful when building APIs. To demonstrate this, we can create a simple To-Do List application. The idea is that users can add tasks, update them, retrieve them, and delete them — all via HTTP requests.

First, we start by creating the Flask app and some initial sample data. This data is usually a list of dictionaries, where each task has an id, name, and description. In real applications, this would typically come from a database like MongoDB or any other NoSQL database. Here’s the basic setup:

from flask import Flask, request, jsonify

app = Flask(__name__)

items = [
    {'id': 1, 'name': 'item one', 'description': 'This is item one'},
    {'id': 2, 'name': 'item two', 'description': 'This is item two'}
]

if __name__ == '__main__':
    app.run(debug=True)


We can create a home route to just welcome users to our app:

@app.route('/')
def home():
    return "Welcome to the sample To-Do List app"


Next, we can retrieve all tasks with a GET request using:

@app.route('/items', methods=['GET'])
def get_items():
    return jsonify(items)


If we want to retrieve a specific item by ID, we can define another GET route that uses a variable in the URL. We loop through the items, match the ID, and return the specific item:

@app.route('/items/<int:item_id>', methods=['GET'])
def get_item(item_id):
    item = next((item for item in items if item['id'] == item_id), None)
    if item is None:
        return jsonify({'error': 'Item not found'})
    return jsonify(item)


To create a new task, we use a POST request. Flask allows us to access the JSON body of the request using request.json. We also handle the case where the JSON or name field might be missing:

@app.route('/items', methods=['POST'])
def create_item():
    if not request.json or 'name' not in request.json:
        return jsonify({'error': 'Invalid input'})
    new_id = items[-1]['id'] + 1 if items else 1
    new_item = {
        'id': new_id,
        'name': request.json['name'],
        'description': request.json.get('description', "")
    }
    items.append(new_item)
    return jsonify(new_item)


For updating an existing task, we use the PUT method. The PUT request includes the task ID in the URL and the updated data in the JSON body. We find the task by ID and then replace the name and description fields:

@app.route('/items/<int:item_id>', methods=['PUT'])
def update_item(item_id):
    item = next((item for item in items if item['id'] == item_id), None)
    if item is None:
        return jsonify({'error': 'Item not found'})
    if not request.json:
        return jsonify({'error': 'No JSON provided'})
    item['name'] = request.json.get('name', item['name'])
    item['description'] = request.json.get('description', item['description'])
    return jsonify(item)


Finally, to delete a task, we use the DELETE HTTP verb. Here, we filter out the item with the matching ID and update the items list:

@app.route('/items/<int:item_id>', methods=['DELETE'])
def delete_item(item_id):
    global items
    items = [item for item in items if item['id'] != item_id]
    return jsonify({'result': 'Item deleted'})


Once this setup is ready, we can test everything using Postman. For example:

GET /items → Returns all tasks.

GET /items/1 → Returns the task with ID 1.

POST /items → Creates a new task by sending a JSON body like {"name": "item three", "description": "This is item three"}.

PUT /items/1 → Updates the task with ID 1 using a JSON body like {"name": "updated item one", "description": "Updated description"}.

DELETE /items/1 → Deletes the task with ID 1.

This approach shows a complete workflow of a CRUD API using Flask. GET retrieves tasks, POST creates new ones, PUT updates existing ones, and DELETE removes tasks. By integrating JSON and these HTTP verbs, we can build fully functional and interactive APIs.

## Summary:

1. Setup Flask App and Sample Data

Imported necessary modules: Flask, request, jsonify.

Initialized the Flask app with app = Flask(__name__).

Created a sample dataset as a list of dictionaries:

items = [
    {'id': 1, 'name': 'item one', 'description': 'This is item one'},
    {'id': 2, 'name': 'item two', 'description': 'This is item two'}
]


Run the app in debug mode:

if __name__ == '__main__':
    app.run(debug=True)

2. Home Route

Created a basic route to welcome users:

@app.route('/')
def home():
    return "Welcome to the sample To-Do List app"

3. GET Requests – Retrieve Data

Retrieve all tasks:

@app.route('/items', methods=['GET'])
def get_items():
    return jsonify(items)


Retrieve a task by ID:

Use a variable in the URL (<int:item_id>)

Loop through items and return the matching task:

@app.route('/items/<int:item_id>', methods=['GET'])
def get_item(item_id):
    item = next((item for item in items if item['id'] == item_id), None)
    if item is None:
        return jsonify({'error': 'Item not found'})
    return jsonify(item)

4. POST Request – Create a New Task

Access JSON data using request.json.

Handle missing JSON or name field.

Generate a new ID and append the new item:

@app.route('/items', methods=['POST'])
def create_item():
    if not request.json or 'name' not in request.json:
        return jsonify({'error': 'Invalid input'})
    new_id = items[-1]['id'] + 1 if items else 1
    new_item = {
        'id': new_id,
        'name': request.json['name'],
        'description': request.json.get('description', "")
    }
    items.append(new_item)
    return jsonify(new_item)

5. PUT Request – Update an Existing Task

Use the task ID in the URL and updated data in JSON body.

Find the task by ID and update its name and description:

@app.route('/items/<int:item_id>', methods=['PUT'])
def update_item(item_id):
    item = next((item for item in items if item['id'] == item_id), None)
    if item is None:
        return jsonify({'error': 'Item not found'})
    if not request.json:
        return jsonify({'error': 'No JSON provided'})
    item['name'] = request.json.get('name', item['name'])
    item['description'] = request.json.get('description', item['description'])
    return jsonify(item)

6. DELETE Request – Remove a Task

Filter out the task with the matching ID and update the list:

@app.route('/items/<int:item_id>', methods=['DELETE'])
def delete_item(item_id):
    global items
    items = [item for item in items if item['id'] != item_id]
    return jsonify({'result': 'Item deleted'})

7. Testing the API with Postman

GET /items → Retrieve all tasks

GET /items/1 → Retrieve task with ID 1

POST /items → Create a new task with JSON body:

{"name": "item three", "description": "This is item three"}


PUT /items/1 → Update task with ID 1 using JSON body:

{"name": "updated item one", "description": "Updated description"}


DELETE /items/1 → Delete task with ID 1

8. Summary of Workflow

(i) Flask app receives HTTP requests.

(ii) GET retrieves tasks (all or by ID).

(iii) POST adds new tasks to the list.

(iv) PUT updates existing tasks by ID.

(v) DELETE removes tasks by ID.

(vi) JSON is used for data transfer between client (Postman or frontend) and backend.

(vii) This workflow demonstrates a full CRUD API using Flask.
