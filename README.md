<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Deepa's Baby Shower Invitation</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background-color: #f0f0f0;
      margin: 0;
      padding: 0;
    }
    .container {
      max-width: 600px;
      margin: 20px auto;
      background-color: #fff;
      padding: 20px;
      border-radius: 10px;
      box-shadow: 0 0 10px rgba(0,0,0,0.1);
    }
    h1 {
      text-align: center;
      color: #ff69b4;
      margin-bottom: 20px;
    }
    p {
      text-align: center;
      font-size: 18px;
      color: #333;
    }
    .invitation {
      position: relative;
      width: 100%;
      height: 300px;
      overflow: hidden;
      border-radius: 10px;
      margin-bottom: 20px;
    }
    .slider {
      display: flex;
      transition: transform 0.5s ease;
    }
    .slide {
      flex: 0 0 100%;
      width: 100%;
      height: 100%;
    }
    .slide img {
      width: 100%;
      height: 100%;
      object-fit: cover;
    }
    .invitation-text {
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      color: #fff;
      font-size: 24px;
      text-shadow: 2px 2px 4px rgba(0,0,0,0.5);
    }
  </style>
</head>
<body>
  <div class="container">
    <h1>Deepa's Baby Shower Invitation</h1>
    <div class="invitation">
      <div class="slider">
        <div class="slide"><img src="https://focusu.com/wp-content/uploads/2017/03/team-celebration-clipart.jpg" alt="Slide 1"></div>
        <div class="slide"><img src="https://i.imgur.com/91Pm8iA.jpg" alt="Slide 2"></div>
        <div class="slide"><img src="https://i.imgur.com/Z7tSe8Y.jpg" alt="Slide 3"></div>
      </div>
      <div class="invitation-text">You and your family are invited for Deepa's Baby Shower at Mumbai.</div>
    </div>
    <p>Date: [Insert Date]</p>
    <p>Time: [Insert Time]</p>
    <p>Venue: [Insert Venue]</p>
    <p>Please RSVP by [Insert RSVP Date]</p>
  </div>

  <script>
    const slider = document.querySelector('.slider');
    let isDragging = false;
    let startPos = 0;
    let currentTranslate = 0;
    let prevTranslate = 0;
    let animationId = 0;

    function startTouch(e) {
      if (!isDragging) {
        isDragging = true;
        startPos = e.touches[0].clientX;
        animationId = requestAnimationFrame(animation);
        slider.style.transition = '';
      }
    }

    function moveTouch(e) {
      if (isDragging) {
        const currentPosition = e.touches[0].clientX;
        currentTranslate = prevTranslate + currentPosition - startPos;
      }
    }

    function endTouch() {
      cancelAnimationFrame(animationId);
      isDragging = false;
      const movedBy = currentTranslate - prevTranslate;

      if (movedBy < -100 && currentTranslate !== 0) {
        prevTranslate = currentTranslate;
        currentTranslate -= slider.offsetWidth;
      }

      if (movedBy > 100 && currentTranslate !== (-slider.offsetWidth * (slider.children.length - 1))) {
        prevTranslate = currentTranslate;
        currentTranslate += slider.offsetWidth;
      }

      slider.style.transform = `translateX(${currentTranslate}px)`;
    }

    function animation() {
      slider.style.transform = `translateX(${currentTranslate}px)`;
      if (isDragging) requestAnimationFrame(animation);
    }

    slider.addEventListener('touchstart', startTouch);
    slider.addEventListener('touchmove', moveTouch);
    slider.addEventListener('touchend', endTouch);
    slider.addEventListener('touchcancel', endTouch);
  </script>
</body>
</html>
