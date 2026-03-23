# Ex05 Image Carousel
## Date:23.03.2026

## AIM
To create a Image Carousel using React 

## ALGORITHM
### STEP 1 Initial Setup:
Input: A list of images to display in the carousel.

Output: A component displaying the images with navigation controls (e.g., next/previous buttons).

### Step 2 State Management:
Use a state variable (currentIndex) to track the index of the current image displayed.

The carousel starts with the first image, so initialize currentIndex to 0.

### Step 3 Navigation Controls:
Next Image: When the "Next" button is clicked, increment currentIndex.

If currentIndex is at the end of the image list (last image), loop back to the first image using modulo:
currentIndex = (currentIndex + 1) % images.length;

Previous Image: When the "Previous" button is clicked, decrement currentIndex.

If currentIndex is at the beginning (first image), loop back to the last image:
currentIndex = (currentIndex - 1 + images.length) % images.length;

### Step 4 Displaying the Image:
The currentIndex determines which image is displayed.

Using the currentIndex, display the corresponding image from the images list.

### Step 5 Auto-Rotation:
Set an interval to automatically change the image after a set amount of time (e.g., 3 seconds).

Use setInterval to call the nextImage() function at regular intervals.

Clean up the interval when the component unmounts using clearInterval to prevent memory leaks.

## PROGRAM
App.jsx
```
import React, { useState } from "react";
import "./App.css";

function App() {
  const images = [
    "https://picsum.photos/900/500?random=1",
    "https://picsum.photos/900/500?random=2",
    "https://picsum.photos/900/500?random=3",
    "https://picsum.photos/900/500?random=4"
  ];

  const [index, setIndex] = useState(0);

  const nextImage = () => {
    setIndex((prev) => (prev + 1) % images.length);
  };

  const prevImage = () => {
    setIndex((prev) => (prev - 1 + images.length) % images.length);
  };

  return (
    <div className="carousel">
      <h2>🌇 Image Carousel Demo 🌇</h2>

      <div className="carousel-container">
        <button className="arrow left" onClick={prevImage}>❮</button>

        <img
          src={images[index]}
          alt="carousel"
          className="carousel-image"
        />

        <button className="arrow right" onClick={nextImage}>❯</button>
      </div>
    </div>
  );
}

export default App;git 
```
App.css
```
body {
  background: linear-gradient(to right, #1d2b64, #f8cdda);
  height: 100vh;
  margin: 0;
  display: flex;
  justify-content: center;
  align-items: center;
  font-family: Arial;
}

.carousel {
  text-align: center;
  color: white;
}

.carousel-container {
  position: relative;
  display: flex;
  align-items: center;
  justify-content: center;
}

.carousel-image {
  width: 550px;
  height: 320px;
  border-radius: 15px;
  object-fit: cover;
  border: 3px solid white;
}

/* buttons */
.arrow {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  font-size: 2rem;
  background: black;
  color: white;
  border: none;
  padding: 10px;
  cursor: pointer;
}

.left {
  left: -60px;
}

.right {
  right: -60px;
}

.arrow:hover {
  background: gray;
}
```

## OUTPUT
<img width="1913" height="1129" alt="image" src="https://github.com/user-attachments/assets/8da9650e-eaa5-45b2-92c5-4682cc84150d" />
<img width="1919" height="1135" alt="image" src="https://github.com/user-attachments/assets/3c7cf790-ead5-4924-b9cd-17ba9c6f1095" />
<img width="1911" height="1134" alt="image" src="https://github.com/user-attachments/assets/7c063f99-adfd-4a71-b00f-37b9dd819662" />
<img width="1919" height="1131" alt="image" src="https://github.com/user-attachments/assets/d1fb8cf0-e3ce-48cc-bd58-53c697bc87db" />


## RESULT

The program for creating Image Carousel using React is executed successfully.
