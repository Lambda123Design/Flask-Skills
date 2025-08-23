# Flask-Skills

A) Understanding Simple Flask App Skeleton

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

