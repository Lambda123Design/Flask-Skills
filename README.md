# Flask-Skills

A) Understanding Simple Flask App Skeleton

B) Integrating HTML with Flask Web App

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
