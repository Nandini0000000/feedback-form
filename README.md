# feedback-form

//index.html
//feedback/comment section
main
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Delightful Treats - Feedback & Comments</title>
<link rel="stylesheet" href="styles.css">
</head>
<body>
<div class="container">
  <div id="comments-section">
    <h2>Comments</h2>
    
    <div id="comments-container">
      <!-- Comments will be dynamically added here -->
    </div>
    <form id="comment-form">
      <textarea id="comment-text" placeholder="Write your comment here..." required></textarea>
      <button type="submit">Submit Comment</button>
    </form>
  </div>
  <div id="feedback-section">
    <h2>Feedback Form</h2>
    <form id="feedback-form">
      <div class="form-group">
        <label for="name">Your Name:</label>
        <input type="text" id="name" name="name" placeholder="Enter your name" required>
      </div>
      <div class="form-group">
        <label for="email">Your Email:</label>
        <input type="email" id="email" name="email" placeholder="Enter your email" required>
      </div>
      <div class="form-group">
        <label for="feedback">Your Feedback:</label>
        <textarea id="feedback" name="feedback" placeholder="Share your experience with us" required></textarea>
      </div>
      <button type="submit">Submit Feedback</button>
    </form>
    <div id="success-message"></div>
  </div>
</div>

<footer>
  <div class="footer-content">
    <ul>
      <li><a href="privacy-policy.html">Privacy Policy</a></li>
      <li><a href="terms-and-conditions.html">Terms and Conditions</a></li>
    </ul>
  </div>
</footer>

<script src="script.js"></script>
</body>
</html>

body {
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    background-color: #f6f6f6;
    margin: 0;
    padding: 0;
  }
  
  .container {
    max-width: 500px;
    margin: 50px auto;
    padding: 20px;
    background-color: #fff;
    border-radius: 10px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    text-align: center;
  }
  
  h1 {
    color: #ff7f00;
    font-size: 36px;
    margin-bottom: 20px;
  }
  
  img {
    max-width: 200px;
    margin-bottom: 20px;
  }
  
  .form-group {
    margin-bottom: 20px;
    text-align: left;
  }
  
  label {
    font-size: 18px;
    font-weight: bold;
    color: #333;
  }
  
  input[type="text"],
  input[type="email"],
  textarea {
    width: 100%;
    padding: 10px;
    border: 1px solid #ccc;
    border-radius: 5px;
  }
  
  textarea {
    height: 100px;
  }
  
  button {
    display: block;
    width: 100%;
    padding: 10px;
    background-color: #ff7f00;
    color: #fff;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    font-size: 16px;
  }
  
  button:hover {
    background-color: #ff9933;
  }
  
  #success-message {
    margin-top: 20px;
    padding: 10px;
    background-color: #d4edda;
    color: #155724;
    border-radius: 5px;
    font-size: 16px;
  }

//script.js
document.addEventListener("DOMContentLoaded", function() {
    const feedbackForm = document.getElementById("feedback-form");
    const successMessage = document.getElementById("success-message");
    
    feedbackForm.addEventListener("submit", function(event) {
      event.preventDefault();
      
      const formData = new FormData(feedbackForm);
      const feedbackData = {};
      formData.forEach(function(value, key) {
        feedbackData[key] = value;
      });
      
      // Here you can add code to send feedback data to your backend or handle it as needed
      // For this example, we'll just show a success message
      showSuccessMessage();
    });
    
    function showSuccessMessage() {
      successMessage.textContent = "Thank you for your feedback! We'll get back to you soon.";
      setTimeout(function() {
        successMessage.textContent = "";
      }, 5000);
    }
  
    const commentForm = document.getElementById("comment-form");
    const commentText = document.getElementById("comment-text");
    const commentsContainer = document.getElementById("comments-container");
  
    commentForm.addEventListener("submit", function(event) {
      event.preventDefault();
  
      const commentContent = commentText.value.trim();
      if (commentContent !== "") {
        const comment = document.createElement("div");
        comment.classList.add("comment");
        comment.textContent = commentContent;
        commentsContainer.appendChild(comment);
        commentText.value = "";
      } else {
        alert("Please enter a comment.");
      }
    });
  });


