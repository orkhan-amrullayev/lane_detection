# Lane Detection code using OpenCV (cv2) library without Deep Learning.

Result:
Even the car does not follow the exact path and slides right & left as it moves, lanes are detected correctly.
<br>
![ezgif com-gif-maker](https://user-images.githubusercontent.com/64093617/111854899-150d0400-8922-11eb-8659-2a06b643df64.gif)



As we need to approach a video as a set of image frames, we need to use one pample frame first. 
<div align="center"> 
<img src="https://user-images.githubusercontent.com/64093617/111854283-a8443a80-891e-11eb-894c-0e9865a88f4c.png" width=50% height=50% >
    <p> One frame of the original footage </p>
</div>


The sequence of the code is as follows:
1. Using canny function:
    - changing the color channels from 3 to 1 (from RGB to Grayscale)
    - bluring the grayscaled view in order to make the sharp transitions smooth for future detection
    - using cv2.Canny, detecting edges of blurred view

<div align="center"> 
<img src="https://user-images.githubusercontent.com/64093617/111852610-e722c200-8917-11eb-85ad-f2e2287ce902.png" width=50% height=50% >
    <p> Output of Canny </p>
</div>


2. Defining region of interest
    - defining the triangle which the future lines probably will fit inside
    - applying the image into a black mask with same dimension of our view
    - filling the black mask with white colored triangle
    - combining our image and the mask
    - by applying the output of canny to this function we will get the cropped image of edge detected view

<div align="center"> 
<img src="https://user-images.githubusercontent.com/64093617/111854457-afb81380-891f-11eb-91a1-45f3a379931d.png" width=50% height=50% >
    <p> Region of interest - Cropped image of edge-detected view </p>
</div>

3. Displaying lines
   - by applying cv2.HoughLinesP function, getting the lines of the cropped image.
   - understanding Hough Space and its function in cv2 will help you define the arguments accordingly.

4. Average slope intercept
   - averaging all the candidate lines (both for the left and right side separately) in order to get one final line for each side
   
6. Defining coordinates
   - lines will be shown from the bottom until to the point indicated in this part of the code

============

If you want to try the code with the same video, upload it and change the path accordingly.

If you want to try the code with your own video, you need to change the lines indicating triangle (52-54) and y1, y2 (9-10) to show the blue line up to that coordinate.

Useful link for more explicit explainations:
https://www.youtube.com/watch?v=eLTLtUVuuy4
