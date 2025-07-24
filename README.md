# blog-website
This is a simple and elegant Blog Website designed to display multiple articles with featured images, categories, and a dynamic comment section. The platform allows users to read blog posts, filter them by category (e.g., Travel, Tech, Lifestyle), and engage with the content by adding comments in real-time. 


## HTML


<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My Blog</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <header>
        <h1>My Blog</h1>
        <nav>
            <ul>
                <li><a href="#">Home</a></li>
                <li><a href="#">Categories</a></li>
                <li><a href="#">About</a></li>
            </ul>
        </nav>
    </header>

    <main id="blog-posts">
        <!-- Blog posts will be inserted here -->
    </main>

    <footer>
        <p>&copy; 2025 My Blog. All rights reserved.</p>
    </footer>

    <script src="app.js"></script>
</body>
</html>


##CSS


body {
    font-family: Arial, sans-serif;
    margin: 0;
    padding: 0;
    background-color: #f9f9f9;
}

header {
    background-color: #333;
    color: #fff;
    padding: 20px;
    text-align: center;
}

nav ul {
    list-style: none;
    padding: 0;
    display: flex;
    justify-content: center;
    margin-top: 10px;
}

nav ul li {
    margin: 0 15px;
}

nav ul li a {
    color: #fff;
    text-decoration: none;
}

main {
    max-width: 800px;
    margin: 20px auto;
    padding: 0 20px;
}

.blog-post {
    background-color: #fff;
    border: 1px solid #ddd;
    border-radius: 8px;
    padding: 20px;
    margin-bottom: 20px;
}

.blog-post img {
    max-width: 100%;
    border-radius: 5px;
}

.blog-post h2 {
    margin-top: 0;
}

.comment-section {
    margin-top: 20px;
}

.comment-section input,
.comment-section button {
    padding: 10px;
    margin-top: 10px;
    width: 100%;
    box-sizing: border-box;
}

.comment {
    background-color: #f1f1f1;
    padding: 10px;
    margin-top: 10px;
    border-radius: 5px;
}

footer {
    text-align: center;
    padding: 20px;
    background-color: #333;
    color: white;
}


##JavaScript


document.addEventListener("DOMContentLoaded", () => {
    const blogPosts = [
        {
            title: "Exploring the Mountains",
            image: "https://th.bing.com/th/id/R.61b5be101b7f9189ffc62347330327b6?rik=2s18nkzBrl8QlQ&riu=http%3a%2f%2feskipaper.com%2fimages%2fmountains-1.jpg&ehk=dzdr4yMOey3MMOwNEUunWfLRAFndhuMyenoiqKzzwQo%3d&risl=&pid=ImgRaw&r=0",
            content: "Mountains are amazing places to explore. They offer adventure and breathtaking views.",
            comments: []
        },
        {
            title: "City Life Adventures",
            image: "https://c.pxhere.com/photos/f6/5c/city_street_car_building_usa-58734.jpg!d",
            content: "The city never sleeps. Discover the fast-paced life and endless opportunities.",
            comments: []
        }
    ];

    const blogContainer = document.getElementById("blog-posts");

    blogPosts.forEach((post, index) => {
        const postDiv = document.createElement("div");
        postDiv.className = "blog-post";
        postDiv.innerHTML = `
            <h2>${post.title}</h2>
            <img src="${post.image}" alt="${post.title}">
            <p>${post.content}</p>
            <div class="comment-section">
                <input type="text" placeholder="Write a comment..." id="comment-input-${index}">
                <button onclick="addComment(${index})">Post Comment</button>
                <div id="comments-${index}" class="comments"></div>
            </div>
        `;
        blogContainer.appendChild(postDiv);
    });

    window.addComment = function(index) {
        const input = document.getElementById(`comment-input-${index}`);
        const commentText = input.value.trim();
        if (commentText) {
            const commentDiv = document.createElement("div");
            commentDiv.className = "comment";
            commentDiv.textContent = commentText;
            document.getElementById(`comments-${index}`).appendChild(commentDiv);
            input.value = "";
        }
    };
});
