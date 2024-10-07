<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Customer Voices</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>

    <section class="customer-voices">
        <h2>Success Stories</h2>
        <h3>Customer Voices</h3>

        <div class="slider-container">
            <div class="slider">
                <div class="review">
                    <h4>Parents Name 1</h4>
                    <p>Location</p>
                    <blockquote>
                        <p>"Lorem ipsum dolor sit amet, consectetur adipiscing elit."</p>
                    </blockquote>
                    <div class="rating">
                        <span>★</span><span>★</span><span>★</span><span>★</span><span>★</span>
                    </div>
                </div>

                <div class="review">
                    <h4>Parents Name 2</h4>
                    <p>Location</p>
                    <blockquote>
                        <p>"Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua."</p>
                    </blockquote>
                    <div class="rating">
                        <span>★</span><span>★</span><span>★</span><span>★</span><span>★</span>
                    </div>
                </div>

                <div class="review">
                    <h4>Parents Name 3</h4>
                    <p>Location</p>
                    <blockquote>
                        <p>"Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris."</p>
                    </blockquote>
                    <div class="rating">
                        <span>★</span><span>★</span><span>★</span><span>★</span><span>★</span>
                    </div>
                </div>
            </div>

            <button class="prev" onclick="moveSlide(-1)">&#10094;</button>
            <button class="next" onclick="moveSlide(1)">&#10095;</button>
        </div>

    </section>

    <script src="script.js"></script>

</body>
</html>
body {
    font-family: Arial, sans-serif;
    background-color: #f4f7f8;
    margin: 0;
    padding: 0;
}

.customer-voices {
    text-align: center;
    background-color: #e0f7fa;
    padding: 40px;
    position: relative;
    overflow: hidden;
}

.customer-voices h2 {
    font-size: 24px;
    font-weight: 600;
    margin-bottom: 10px;
}

.customer-voices h3 {
    font-size: 32px;
    font-weight: 700;
    margin-bottom: 30px;
}

.slider-container {
    position: relative;
    width: 100%;
    max-width: 1000px;
    margin: 0 auto;
    overflow: hidden;
}

.slider {
    display: flex;
    transition: transform 0.5s ease-in-out;
    width: 300%;
}

.review {
    background-color: white;
    padding: 20px;
    border-radius: 15px;
    box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
    max-width: 300px;
    margin: 0 15px;
    text-align: left;
    flex: 0 0 33.3333%; /* Set equal width to allow sliding */
}

.review h4 {
    font-size: 18px;
    font-weight: bold;
    margin-bottom: 5px;
}

.review p {
    font-size: 14px;
    color: grey;
    margin-bottom: 15px;
}

blockquote {
    font-style: italic;
    color: #333;
    margin-bottom: 15px;
}

.rating span {
    color: gold;
    font-size: 24px;
}

/* Arrow Buttons */
button.prev, button.next {
    position: absolute;
    top: 50%;
    transform: translateY(-50%);
    background-color: rgba(0,0,0,0.5);
    border: none;
    padding: 10px;
    color: white;
    cursor: pointer;
    font-size: 18px;
    border-radius: 50%;
}

button.prev {
    left: 10px;
}

button.next {
    right: 10px;
}

button.prev:hover, button.next:hover {
    background-color: rgba(0,0,0,0.8);
}

@media screen and (max-width: 768px) {
    .slider {
        width: 300%;
    }

    .review {
        flex: 0 0 100%; /* Adjust for smaller screens */
    }
}
let currentSlide = 0;
const slides = document.querySelector('.slider');
const totalSlides = document.querySelectorAll('.review').length;

function moveSlide(direction) {
    currentSlide += direction;

    if (currentSlide >= totalSlides) {
        currentSlide = 0; // Wrap around to the first slide
    } else if (currentSlide < 0) {
        currentSlide = totalSlides - 1; // Wrap around to the last slide
    }

    const newPosition = -currentSlide * 100 / totalSlides;
    slides.style.transform = `translateX(${newPosition}%)`;
}

// Auto slide every 5 seconds
setInterval(() => {
    moveSlide(1);
}, 5000);
