#python project

from flask import flask
app = Flask(__name__)

@app.route("/")
def home():
    return "Health Check Okay"

@app.route("/health")
def health_check():
    return "Ok", 200

if __name__ == "__main__":
    app.run(host="0.0.0.0", port=5000)
