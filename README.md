<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Photo Upload</title>

<style>
    body {
        font-family: Arial, sans-serif;
        background: linear-gradient(135deg, #ffd6ec, #fff3a3);
        display: flex;
        justify-content: center;
        align-items: center;
        min-height: 100vh;
        margin: 0;
    }

    .container {
        background: white;
        padding: 25px;
        border-radius: 20px;
        box-shadow: 0 5px 15px rgba(0,0,0,0.2);
        text-align: center;
        width: 320px;
    }

    h1 {
        color: #ff69b4;
    }

    .qr {
        margin: 15px 0;
    }

    input {
        width: 90%;
        padding: 10px;
        margin: 8px 0;
        border: 2px solid #ffd700;
        border-radius: 10px;
    }

    button {
        background: #ff69b4;
        color: white;
        border: none;
        padding: 10px 20px;
        border-radius: 10px;
        cursor: pointer;
        font-size: 16px;
    }

    button:hover {
        background: #ff4da6;
    }

    #preview {
        margin-top: 20px;
    }

    #preview img {
        max-width: 100%;
        border-radius: 15px;
        margin-top: 10px;
    }

    #displayName {
        font-weight: bold;
        color: #ff69b4;
        margin-top: 10px;
    }
</style>
</head>
<body>

<div class="container">
    <h1>📸 Upload Your Photo</h1>

    <!-- QR Code -->
    <div class="qr">
        <img src="https://api.qrserver.com/v1/create-qr-code/?size=180x180&data=https://yourwebsite.com"
             alt="QR Code">
    </div>

    <input type="text" id="nameInput" placeholder="Your Name">

    <input type="file" id="imageInput" accept="image/*">

    <button onclick="showPreview()">Submit</button>

    <div id="preview">
        <div id="displayName"></div>
        <img id="previewImage" style="display:none;">
    </div>
</div>

<script>
function showPreview() {
    const name = document.getElementById("nameInput").value || "Your Name";
    const file = document.getElementById("imageInput").files[0];

    document.getElementById("displayName").textContent = name;

    if (file) {
        const reader = new FileReader();
        reader.onload = function(e) {
            const img = document.getElementById("previewImage");
            img.src = e.target.result;
            img.style.display = "block";
        };
        reader.readAsDataURL(file);
    }
}
</script>

</body>
</html>
