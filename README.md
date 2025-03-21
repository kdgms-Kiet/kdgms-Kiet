KD-International/
│── index.html       (Trang chính)
│── style.css        (Giao diện & hiệu ứng)
│── script.js        (Tương tác & Google Maps)
│── images/          (Hình ảnh công ty)
<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>KD International Corporation</title>
    <link rel="stylesheet" href="style.css">
    <script defer src="script.js"></script>
</head>
<body>

    <header>
        <h1>KD International Corporation</h1>
        <nav>
            <ul>
                <li><a href="#about">Giới thiệu</a></li>
                <li><a href="#services">Dịch vụ</a></li>
                <li><a href="#projects">Dự án</a></li>
                <li><a href="#contact">Liên hệ</a></li>
            </ul>
        </nav>
    </header>

    <section id="about">
        <h2>Về Chúng Tôi</h2>
        <p>KD International chuyên cung cấp giải pháp công nghệ và sản xuất toàn cầu.</p>
    </section>

    <section id="services">
        <h2>Dịch Vụ</h2>
        <ul>
            <li>Phân phối hóa chất công nghiệp</li>
            <li>Cung cấp thiết bị công nghệ cao</li>
            <li>Giải pháp sản xuất thông minh</li>
        </ul>
    </section>

    <section id="projects">
        <h2>Dự Án</h2>
        <div class="project-card">
            <img src="images/project1.jpg" alt="Dự án 1">
            <h3>Dự án năng lượng sạch</h3>
            <p>Cung cấp giải pháp xử lý chất thải công nghiệp.</p>
        </div>
        <div class="project-card">
            <img src="images/project2.jpg" alt="Dự án 2">
            <h3>Ứng dụng công nghệ AI</h3>
            <p>Triển khai hệ thống AI trong sản xuất.</p>
        </div>
    </section>

    <section id="contact">
        <h2>Liên Hệ</h2>
        <form id="contactForm">
            <input type="text" id="name" placeholder="Họ và tên" required>
            <input type="email" id="email" placeholder="Email" required>
            <textarea id="message" placeholder="Tin nhắn của bạn" required></textarea>
            <button type="submit">Gửi</button>
        </form>
        <p id="response"></p>

        <!-- Google Maps -->
        <div id="map"></div>
    </section>

    <footer>
        <p>&copy; 2025 KD International Corporation</p>
    </footer>

    <!-- Thêm Google Maps API -->
    <script src="https://maps.googleapis.com/maps/api/js?key=YOUR_API_KEY&callback=initMap" async defer></script>
</body>
</html>
/* Hiệu ứng nền động */
body {
    font-family: Arial, sans-serif;
    margin: 0;
    padding: 0;
    text-align: center;
    background: linear-gradient(-45deg, #ff9a9e, #fad0c4, #fad0c4, #ffdde1);
    background-size: 400% 400%;
    animation: gradientBG 10s ease infinite;
}

/* Animation nền */
@keyframes gradientBG {
    0% { background-position: 0% 50%; }
    50% { background-position: 100% 50%; }
    100% { background-position: 0% 50%; }
}

/* Header */
header {
    background-color: #222;
    color: white;
    padding: 20px;
    position: fixed;
    width: 100%;
    top: 0;
    z-index: 1000;
}

/* Menu */
nav ul {
    list-style: none;
    padding: 0;
}

nav ul li {
    display: inline;
    margin: 0 15px;
}

nav ul li a {
    color: white;
    text-decoration: none;
    font-size: 18px;
}

/* Các phần nội dung */
section {
    padding: 80px 20px;
}

/* Dự án */
.project-card {
    display: inline-block;
    width: 300px;
    margin: 20px;
    background: white;
    padding: 15px;
    border-radius: 8px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

.project-card img {
    width: 100%;
    border-radius: 8px;
}

/* Google Maps */
#map {
    width: 80%;
    height: 300px;
    margin: 20px auto;
    border-radius: 10px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.2);
}
// Xử lý form liên hệ
document.getElementById('contactForm').addEventListener('submit', function(event) {
    event.preventDefault();
    
    const name = document.getElementById('name').value;
    const email = document.getElementById('email').value;
    const message = document.getElementById('message').value;

    if (name && email && message) {
        document.getElementById('response').textContent = "Cảm ơn! Chúng tôi sẽ liên hệ sớm.";
        this.reset();
    } else {
        document.getElementById('response').textContent = "Vui lòng điền đầy đủ thông tin.";
    }
});

// Hiệu ứng cuộn mượt
document.querySelectorAll('nav a').forEach(anchor => {
    anchor.addEventListener('click', function(event) {
        event.preventDefault();
        const targetId = this.getAttribute('href').substring(1);
        document.getElementById(targetId).scrollIntoView({ behavior: 'smooth' });
    });
});

// Khởi tạo Google Maps
function initMap() {
    const location = { lat: 10.7769, lng: 106.7009 }; // Toạ độ TP. Hồ Chí Minh
    const map = new google.maps.Map(document.getElementById("map"), {
        zoom: 15,
        center: location,
    });

    new google.maps.Marker({
        position: location,
        map: map,
        title: "KD International Corporation",
    });
}
