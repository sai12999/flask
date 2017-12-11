
from flask import *
import requests

app = Flask(__name__)

@app.route('/')
def homepage():
	return "Hello World - Samanth"

@app.route('/authors')
def authors():
	url = 'https://jsonplaceholder.typicode.com/posts/'
	r = requests.get(url)
	data =  r.json()	
	l=[]
	for i in data:
		u=i['userId']
		l.append(u)
	url = 'https://jsonplaceholder.typicode.com/users/'
	res = requests.get(url)
	data = res.json()
	return render_template("authors.html",data=data,l=l)
   

@app.route('/setcookie', methods = ['POST', 'GET'])
def setcookie():
	if request.method == 'POST':
		user = request.form['user']
		age = request.form['age']   
	resp = make_response(render_template('readcookie.html'))
	resp.set_cookie('user', user)
	resp.set_cookie('age',age)
	return resp

@app.route('/getcookie')
def getcookie():
   name = request.cookies.get('user')
   age = request.cookies.get('age')
   return '<h1>welcome '+name+'<br>age '+age+'</h1>'

@app.route('/input')
def send():
	return render_template('input.html')

@app.route('/senddata', methods=['POST'])
def get_data():
	print("Received from Client :")
	print(request.form['input'])
	return render_template('input.html')	

@app.route("/html")
def html():
	return render_template("index.html")

@app.route('/image')
def image():
	return send_file('sam.png', mimetype='image/gif')

@app.route('/robots.txt')
def hello():
    return redirect("http://httpbin.org/deny", code=302)

	

if __name__ == "__main__":
	app.run()
