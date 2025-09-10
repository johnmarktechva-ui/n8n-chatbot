# n8n-chatbot
For website chatbot

# 💬 Chatbot Embed Demo

This repository hosts a simple webpage that embeds a chatbot using HTML.  
It can be deployed with **GitHub Pages** to make the chatbot accessible online.

---

## 🚀 Live Demo
Once GitHub Pages is enabled, you can view the site here:  
👉 https://your-username.github.io/my-chatbot-site/

---


---

## 🛠️ How It Works
The `index.html` file contains the chatbot embed code:

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Elite Chatbot</title>
  
  <!-- n8n chat CSS -->
  <link href="https://cdn.jsdelivr.net/npm/@n8n/chat/dist/style.css" rel="stylesheet" />

  <style>
    /* Page styling */
    body {
      font-family: Arial, sans-serif;
      margin: 0;
      padding: 0;
      background-color: #ffffff;
    }

    /* Header */
    header {
      width: 100%;
      background-color: pink;
      color: #000000;
      padding: 20px;
      text-align: center;
      font-size: 24px;
      font-weight: bold;
    }

    /* Override n8n chat widget styles */
    .n8n-chat-container {
      background-color: #ffffff !important; /* Widget background white */
      color: #000000 !important;           /* Text black */
      border-radius: 8px !important;
    }

    /* Position chat widget bottom-right */
    .n8n-chat-floating {
      bottom: 20px !important;
      right: 20px !important;
    }
  </style>
</head>
<body>

  <header>Elite Chatbot</header>

  <script type="module">
    import { createChat } from 'https://cdn.jsdelivr.net/npm/@n8n/chat/dist/chat.bundle.es.js';

    const chat = createChat({
      webhookUrl: 'https://lcswvibes.app.n8n.cloud/webhook/d3340d12-6089-40d8-8d85-be73b9235d93/chat', // Replace with your n8n cloud webhook
      floating: true,
      bubble: true,
      position: 'bottom-right'
    });

    // Wait for chat to initialize, then override bot name and greeting
    chat.then(widget => {
      if(widget && widget.shadowRoot) {
        const root = widget.shadowRoot;

        // Override default greeting text
        const interval = setInterval(() => {
          const botMsg = root.querySelector('.n8n-chat-message.bot .n8n-chat-message-text');
          if(botMsg && botMsg.innerText.includes('Nathan')) {
            botMsg.innerText = "Hi there! My name is Elite, how can I assist you today?";
            clearInterval(interval);
          }
        }, 100);
      }
    });
  </script>

</body>
</html>
