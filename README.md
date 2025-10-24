<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Public File Uploader</title>
    <style>
        body { font-family: sans-serif; max-width: 600px; margin: 40px auto; padding: 20px; border: 1px solid #ccc; }
        .file-upload-container { padding: 20px; border: 1px dashed #aaa; }
        input[type="file"] { display: block; margin-bottom: 15px; }
        button { padding: 10px 20px; background-color: #007bff; color: white; border: none; cursor: pointer; }
        button:hover { background-color: #0056b3; }
    </style>
</head>
<body>

    <h1>Upload Files to Public Storage</h1>

    <form action="/upload-endpoint" method="post" enctype="multipart/form-data">
        <div class="file-upload-container">
            <label for="public-files">Select Photos, Videos, or Files to Upload:</label>
            <input 
                type="file" 
                id="public-files" 
                name="public_files[]" 
                accept="image/*,video/*,.pdf,.doc,.docx,.zip" 
                multiple
                required
            >
            
            <button type="submit">Upload Files</button>
        </div>
    </form>

    <p><em>*A server-side script is required to process and save these files. This HTML only provides the interface.</em></p>

</body>
</html>
