# Lane Detection code using OpenCV (cv2) library without Deep Learning.

The sequence of the code is as follows:
1. Using canny function:
    - changing the color channels from 3 to 1 (from RGB to Grayscale)
    - bluring the grayscaled view in order to make the sharp transitions smooth for future detection
    - using cv2.Canny, detecting edges of blurred view

<img src="https://user-images.githubusercontent.com/64093617/111852610-e722c200-8917-11eb-85ad-f2e2287ce902.png" width=50% height=50%>

2. Defining region of interest
    - defining the triangle which the future lines probably will fit inside
    - applying the image into a black mask with same dimension of our view
    - filling the black mask with white colored triangle
    - combining our image and the mask
    - by applying the output of canny to this function we will get the cropped image of edge detected view

3. Displaying lines
   - by applying cv2.HoughLinesP function, getting the lines of the cropped image.
   - understanding Hough Space and its function in cv2 will help you define the arguments accordingly.

4. Average slope intercept
   - averaging all the candidate lines (both for the left and right side separately) in order to get one final line for each side
   
6. Defining coordinates
    - lines will be shown from the bottom until to the point indicated in this part of the code
    








If you want to try the code with the same video, upload it and change the path of the video accordingly.

If you want to try the code with your own video, you need to change the lines indicating triangle (52-54) and y1, y2 (9-10) to show the yellow line up to that coordinate.

Useful link for more explicit explainations:
https://www.youtube.com/watch?v=eLTLtUVuuy4
