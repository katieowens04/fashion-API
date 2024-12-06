# fashion-API
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Fashion Trends</title>
    <style>
        #fashionDetails div {
            margin: 20px;
            padding: 10px;
            border: 1px solid #ccc;
            border-radius: 8px;
            width: 300px;
        }

        #fashionDetails img {
            width: 100%;
            border-radius: 8px;
        }
    </style>
</head>
<body>
    <h1>Fashion Trends</h1>
    <div id="fashionDetails">Loading fashion trends...</div>

    <script>
        // Fetch data from the GitHub-hosted Fashion API
        fetch('https://your-username.github.io/fashion-api/fashion.json') // Replace with your GitHub Pages URL
            .then(res => {
                if (!res.ok) {
                    throw new Error(`HTTP error! Status: ${res.status}`);
                }
                return res.json();
            })
            .then(data => {
                const fashionDetails = data.map(item => `
                    <div>
                        <h2>${item.name}</h2>
                        <p><strong>Description:</strong> ${item.description}</p>
                        <p><strong>Height:</strong> ${item.height}</p>
                        <p><strong>Weight:</strong> ${item.weight}</p>
                        <img src="${item.image}" alt="${item.name}">
                    </div>
                `).join('');
                document.getElementById('fashionDetails').innerHTML = fashionDetails;
            })
            .catch(err => {
                console.error('Error:', err);
                document.getElementById('fashionDetails').innerHTML = "Failed to load fashion trends.";
            });
    </script>
</body>
</html>
