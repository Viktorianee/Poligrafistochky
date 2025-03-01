# Poligrafistochky
<!DOCTYPE html>
<html lang="uk">
<head>
    
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Новини</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>

<header>
    <h1>Новини</h1>
</header>

<nav>
    <button class="category" data-category="all">Всі</button>
    <button class="category" data-category="політика">Політика</button>
    <button class="category" data-category="спорт">Спорт</button>
    <button class="category" data-category="технології">Технології</button>
</nav>

<div id="news-container"></div>

<script src="script.js"></script>

</body>
</html>body {
    font-family: Arial, sans-serif;
    background: #f9f9f9;
    margin: 0;
}

header {
    background: #333;
    color: #fff;
    padding: 15px;
    text-align: center;
}

nav {
    text-align: center;
    padding: 10px;
}

button.category {
    background: #ddd;
    border: none;
    padding: 8px 15px;
    margin: 5px;
    border-radius: 20px;
    cursor: pointer;
}

button.category:hover {
    background: #bbb;
}

#news-container {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 15px;
    padding: 20px;
}

.news-card {
    background: #fff;
    padding: 15px;
    border-radius: 10px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    cursor: pointer;
    transition: transform 0.3s;
}

.news-card:hover {
    transform: translateY(-5px);
}

.news-card img {
    width: 100%;
    height: 180px;
    object-fit: cover;
    border-radius: 10px;
}

.news-card h3 {
    margin: 10px 0;
    font-size: 18px;
}

.news-card p {
    font-size: 14px;
    color: #333;
}document.addEventListener("DOMContentLoaded", () => {
    const newsData = [
        {
            id: 1,
            title: "Україна отримала новий пакет допомоги",
            description: "ЄС схвалив фінансову допомогу...",
            image: "https://mil.in.ua/wp-content/uploads/2024/01/229928_ukraine-eu_gettyimages_new_960x380_0.webp",
            category: "політика"
        },
        {
            id: 2,
            title: "Нова перемога української збірної",
            description: "Збірна України здобула перемогу...",
            image: "https://shotam.info/wp-content/uploads/2024/06/pp.jpg",
            category: "спорт"
        },
        {
            id: 3,
            title: "В Україні стартував масштабний IT-форум",
            description: "У Києві відбувся один із найбільших IT-форумів, на якому представили нові технології штучного інтелекту та кібербезпеки.",
            image: "https://independentview.net/wp-content/uploads/2017/09/256880.jpg", // Використовуй зображення, яке я згенерував
            category: "технології"
        }
    ];

    const newsContainer = document.getElementById("news-container");

    function renderNews(category = "all") {
        newsContainer.innerHTML = "";
        newsData
            .filter(news => category === "all" || news.category === category)
            .forEach(news => {
                const newsCard = document.createElement("div");
                newsCard.classList.add("news-card");
                newsCard.innerHTML = `
                    <img src="${news.image}" alt="Новина">
                    <h3>${news.title}</h3>
                    <p>${news.description}</p>
                `;
                newsCard.addEventListener("click", () => {
                    window.location.href = `news.html?id=${news.id}`;
                });
                newsContainer.appendChild(newsCard);
            });
    }

    renderNews();

    document.querySelectorAll(".category").forEach(button => {
        button.addEventListener("click", () => {
            renderNews(button.dataset.category);
        });
    });
});
