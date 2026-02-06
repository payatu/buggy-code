---
weight: 800
title: "Software or Data Integrity Failures"
description: ""
icon: "code"
date: "2025-10-15T16:21:50+05:30"
lastmod: "2025-10-15T16:21:50+05:30"
draft: false
toc: false
authors: Mukund Kedia
menu:
  docs:
    parent: "software-or-data-integrity-failures"
---

{{< tabs tabTotal="2">}}
{{% tab tabName="Challenge" %}}

- Insufficiently sanitized calls to dangerous functions can lead to interesting vulnerabilities. We require you excellent skills to figure out the vulnerability.

main.py

````python {linenos=true,anchorlinenos=true}
from flask import Flask, request, jsonify, render_template, make_response, redirect, Response
 
import re, pickle, json
from base64 import b64encode, b64decode
 
app = Flask(__name__, static_url_path='/', static_folder='static', template_folder='templates')
 
@app.route('/')
def index():
	return render_template('index.html')
 
def validation(userinput):
		res = bool(re.match("^[A-Za-z0-9]*$"), userinput)
		if(res==False):
			raise Exception("Invalid input")
 
@app.route('/login', methods=['POST'])
def login():
	try:
		user_data = request.get_json()
		validation(userdata['username'])
		users = mongo.db.users
		user = users.find_one({'username': user_data['username']})
 
		if user in user_data['username']:
			token =json.dumps(user_data)
			serialized_token = b64encode(pickle.dumps(token)).decode('utf-8')
			response = make_response(jsonify({'status': 'ok', 'message': 'Login successful'}), 200)
			response.set_cookie('auth', serialized_token)
			return response
	except:
		response = make_response(jsonify({'status': 'error', 'message': 'Invalid Input'}), 200)
		return response
 
 
@app.route("/update", methods=['POST'])
def update():
	try:
		user_data = request.get_json()
		phoneno = int(user_data['phoneno'])
		cookieval = pickle.loads(b64decode(request.cookies['auth']))
		current_user=cookieval['username']
		validation(current_user)
		mongo.db.users.update_one({'username': current_user}, {'$set':{'phoneno':phoneno}})
		response = make_response(jsonify({'status': 'ok', 'message': 'Updated successful'}), 200)
		return response
	except:
		response = make_response(jsonify({'status': 'error', 'message': 'Invalid Input'}), 200)
		return response
 
 
if __name__ == '__main__':
	app.run(debug=False, host='127.0.0.1', port=4040)
````
{{% /tab %}}
{{% tab tabName="Solution" %}}


````python {linenos=table,hl_lines=[3,"5-7"],anchorlinenos=true}
Stay tuned for updates on the solution !!
````
{{% /tab %}}
{{< /tabs >}}

## References

- [https://cheatsheetseries.owasp.org/](https://cheatsheetseries.owasp.org/)
- [https://owasp.org/Top10/2025/A08_2025-Software_or_Data_Integrity_Failures/](https://owasp.org/Top10/2025/A08_2025-Software_or_Data_Integrity_Failures/)
- [https://docs.microsoft.com/en-us/dotnet/standard/security/](https://docs.microsoft.com/en-us/dotnet/standard/security/)
- [https://github.com/guardrailsio/awesome-dotnet-security](https://github.com/guardrailsio/awesome-dotnet-security)
- [https://owasp.org/Top10/2025/](https://owasp.org/Top10/2025/)
