# Python Color Detection using Pandas and OpenCV

This project demonstrates how to perform color detection in an image using the Python programming language, along with the libraries Pandas and OpenCV. The program identifies the predominant colors in an image and provides information about them.

## Prerequisites

Before running the code, ensure that you have the following libraries installed:

- Python (version 3.6 or above)
- Pandas
- OpenCV

You can install these libraries using pip by running the following command:

```bash
pip install pandas opencv-python
```

## Usage

To use this color detection program, follow these steps:

1. Clone this repository or download the source code files.

2. Place the image you want to analyze in the same directory as the Python script.

3. Open the Python script in your preferred editor or IDE.

4. Modify the script to use the correct image file name:

   ```python
   # Set the image file name
   image_file = "your_image_file.jpg"
   ```

5. Save the changes to the script.

6. Run the Python script:

   ```bash
   python color_detection.py
   ```

7. The program will process the image and display the predominant colors along with their corresponding frequencies.

## How it works

The Python script `color_detection.py` performs the following steps:

1. Imports the necessary libraries:

   ```python
   import cv2
   import pandas as pd
   ```

2. Defines a function to read and process the image:

   ```python
   def process_image(image_file):
       # Read the image
       image = cv2.imread(image_file)
   
       # Convert the image from BGR to RGB color space
       image_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)
   
       # Reshape the image to a list of pixels
       pixels = image_rgb.reshape((-1, 3))
   
       return pixels
   ```

3. Calls the `process_image` function with the image file name.

4. Uses Pandas to create a DataFrame from the pixel data:

   ```python
   # Create a DataFrame from the pixel data
   df = pd.DataFrame(pixels, columns=['Red', 'Green', 'Blue'])
   ```

5. Applies a value count on the RGB values to get the frequencies of each color:

   ```python
   # Count the frequencies of each color
   color_counts = df.value_counts().reset_index()
   color_counts.columns = ['Red', 'Green', 'Blue', 'Frequency']
   ```

6. Displays the predominant colors and their frequencies:

   ```python
   print(color_counts)
   ```

The script assumes that the image is in the JPEG format, but you can modify it to support other formats as well.

## License

This project is licensed under the [MIT License](LICENSE). Feel free to use and modify the code for your own purposes.

## Acknowledgments

- The color detection algorithm used in this project is based on the tutorial by Adrian Rosebrock available at https://www.pyimagesearch.com/2014/05/26/opencv-python-k-means-color-clustering/.
