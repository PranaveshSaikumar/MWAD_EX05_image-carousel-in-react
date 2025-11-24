# MWAD_EX05_image-carousel-in-react
## Date: 24-11-25

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
```
Carousel.jsx
import { useState, useEffect } from "react";
import "./Carousel.css";

function ImageCarousel() {
  const images = [
    "https://th.bing.com/th/id/OIP.qNfoguQF-UXY1F1MdXDXrAHaHY?w=172&h=180&c=7&r=0&o=7&dpr=1.3&pid=1.7&rm=3",
    "https://th.bing.com/th?q=Cat+Meme+Tik+Tok&w=120&h=120&c=1&rs=1&qlt=70&o=7&cb=1&dpr=1.3&pid=InlineBlock&rm=3&mkt=en-IN&cc=IN&setlang=en&adlt=moderate&t=1&mw=247",
    "https://th.bing.com/th/id/OIP.A1PnKjFqsQtf_BnlCmkw4gHaEK?w=310&h=180&c=7&r=0&o=7&dpr=1.3&pid=1.7&rm=3",
    "https://th.bing.com/th?q=Close+Up+Cat+Image+Memes&w=120&h=120&c=1&rs=1&qlt=70&o=7&cb=1&dpr=1.3&pid=InlineBlock&rm=3&mkt=en-IN&cc=IN&setlang=en&adlt=moderate&t=1&mw=247"
  ];

  const [currentIndex, setCurrentIndex] = useState(0);

  const nextImage = () => {
    setCurrentIndex((currentIndex + 1) % images.length);
  };

  const prevImage = () => {
    setCurrentIndex((currentIndex - 1 + images.length) % images.length);
  };

  useEffect(() => {
    const autoSlide = setInterval(() => {
      nextImage();
    }, 3000); 

    return () => clearInterval(autoSlide);
  }, [currentIndex]);

  return (
    <div className="carousel-container">
      <h1>Silly Cats</h1>

      <img src={images[currentIndex]} alt="carousel" className="carousel-img" />

      <div className="btn-group">
        <button onClick={prevImage}>Previous</button>
        <button onClick={nextImage}>Next</button>
      </div>
    </div>
  );
}

export default ImageCarousel;
```
```
Carousel.css
.carousel-container {
  width: 620px;
  margin: 40px auto;
  text-align: center;
  background: #1e1e2f;
  padding: 20px;
  border-radius: 15px;
  box-shadow: 0 0 15px rgba(0,0,0,0.4);
  color: white;
}

.carousel-img {
  width: 600px;
  height: 300px;
  border-radius: 12px;
  object-fit: cover;
  margin-bottom: 15px;
  border: 3px solid #00e6ac;
}

.btn-group {
  display: flex;
  justify-content: center;
  gap: 20px;
}

button {
  padding: 12px 25px;
  font-size: 1rem;
  border: none;
  border-radius: 10px;
  cursor: pointer;
  background: #3c3c55;
  color: white;
  transition: 0.2s;
}

button:hover {
  background: #00e6ac;
  color: black;
}
```
```
App.jsx
import ImageCarousel from "./EXPS/Carousel.jsx";

export default function App() {
  return (
    <div>
      <ImageCarousel />
    </div>
  );
}
```


## OUTPUT

<img width="1130" height="912" alt="image" src="https://github.com/user-attachments/assets/7f771659-1cf7-46c6-b3b7-7bb4f5339fd0" />

## RESULT
The program for creating Image Carousel using React is executed successfully.
