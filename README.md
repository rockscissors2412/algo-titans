# algo-titans
def bot_reply(user_msg):
    msg = user_msg.lower()
    if "hello" in msg or "hi" in msg:
        return "Hello! How can I help you today?"
    elif "refund" in msg:
        return "I can help with accounts. Can you share your account number/ID?"
    elif "human" in msg or "agent" in msg:
        return "Connecting you to a live agent... Please click the Video button."
    else:
        return "I'm not sure about that. Do you want to talk to a human agent?"
def index():
    return render_template("index.html")
  def agent():
    return render_template("agent.html")
def chat():
    data = request.get_json()
    user_msg = data.get("message", "")
    reply = bot_reply(user_msg)
    return jsonify({"reply": reply})

if __name__ == "__main__":
    app.run(debug=True)
#customer_page
<!DOCTYPE html>
<html>
<head>
  <title>Customer Support Chatbot</title>
  <script src="https://cdn.jsdelivr.net/npm/peerjs@1.5.2/dist/peerjs.min.js"></script>
</head>
<body>
  <h1>Customer Chatbot</h1>

  <div id="chatbox" style="border:1px solid #ccc; padding:10px; width:300px; height:200px; overflow:auto;"></div>
  <input id="msg" type="text" placeholder="Type a message..." />
  <button onclick="sendMsg()">Send</button>
  <button onclick="startVideo()">Video with Agent</button>

  <br><br>
  <video id="myVideo" autoplay playsinline muted width="200"></video>
  <video id="remoteVideo" autoplay playsinline width="200"></video>

  <script src="/static/script.js"></script>
  <script>
    setupCustomer();
  </script>
</body>
</html>
#support_page
<!DOCTYPE html>
<html>
<head>
  <title>Support Agent</title>
  <script src="https://cdn.jsdelivr.net/npm/peerjs@1.5.2/dist/peerjs.min.js"></script>
</head>
<body>
  <h1>Agent Console</h1>

  <video id="myVideo" autoplay playsinline muted width="200"></video>
  <video id="remoteVideo" autoplay playsinline width="200"></video>

  <script src="/static/script.js"></script>
  <script>
    setupAgent();
  </script>
</body>
</html
