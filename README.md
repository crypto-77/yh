# yh

<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Create a Document</title>
  <script>
    function downloadDoc() {
      // Get values from the input fields
      const name = document.getElementById('name').value;
      const content = document.getElementById('content').value;

      // Create a Blob from the content
      const blob = new Blob([content], { type: 'application/msword' });
      const url = URL.createObjectURL(blob);

      // Create a link to trigger the download
      const a = document.createElement('a');
      a.href = url;
      a.download = `${name}.doc`; // Set the filename
      document.body.appendChild(a);
      a.click(); // Programmatically click the link to trigger the download
      document.body.removeChild(a); // Remove the link after downloading

      // Release the object URL
      URL.revokeObjectURL(url);
    }
  </script>
</head>

<body>
  <h1>Create a Document</h1>
  <form onsubmit="event.preventDefault(); downloadDoc();">
    <label for="name">Name:</label><br>
    <input type="text" id="name" name="name" required><br><br>

    <label for="content">Content:</label><br>
    <textarea id="content" name="content" rows="4" required></textarea><br><br>

    <input type="submit" value="Submit">
  </form>
</body>

</html>
