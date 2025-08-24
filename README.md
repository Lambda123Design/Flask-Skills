# Flask-Skills

A) Understanding Simple Flask App Skeleton

B) Integrating HTML with Flask Web App

C) HTTP Verbs Get and Post

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
