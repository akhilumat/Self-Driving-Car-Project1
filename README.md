## Please refer to Project Writeup and Video for more detail of work done

### Finding Lane Lines on the Road

The goals / steps of this project are the following:

*Make a pipeline that finds lane lines on the road
*Reflect on your work in a written report

#### 1. Describe your pipeline.

Firstly, I converted the images to grayscale. Then applied gaussian blur function with kernel size of 7. This function helps in smoothen the image and filter out noise. Then canny function was used to find the edges with upper threshhold value as 90 and lower as 30. Then quadilateral mask was used to build image containing edges only in the quadilateral portion. Lines in the masked region was found using hough lines function and they were made red in color. Combo image containg red lines superimposed on white lines in quadilateral portion was created using cv2.addweighted function. This combo was returned as pipeline image. Code used was referenced from example problems.

#### 2. Testing Pipeline on test images.

Code for testing images in test images folder was made and output files are submitted in Github

#### 3. Process image function for Videos

Changes to pipeline fucntions were made while making a function for videos. Upper threshhold for canny function was changed to 60 and lower to 20. Threshhold for hough transform function was changed to 10 and minimum line length to 10. To make the solid line 4 new array were defined. Points in left line were appended to leftx and lefty array while right line points were appended tor rightx and righty. Then these points were used to find slope and intercept of left and right lines. Maximum and minimum points for right line were found and right red line was made. To make left red line minimum y coordinate of left line was made equal to right line and maximum y coordinate was made equal to 540. Corresponding x for left lines were found using the line equation. Sometimes while running the code two lines overlapped. To prevent this from happening when lines came too close, maximum x for left line was changed to maintain appropriate distance. Function was then tested on videos

#### 4. Identify potential shortcomings with your current pipeline

Current pipeline may not work when the brightness in videos changes drastically. Our parameters for canny edge detection and hough lines are set so that they give preferable results for test videos. For other videos it might not work properly.

#### 5. Suggest possible improvements to your pipeline

Some method should be developed such that our parameters in the pipeline function gets modified if the resulting image gives strange results. For example if the slopes of left and right lines are either too less or too high, then our function is also picking up points outside the lane lines. This could be prevented either by increaseing kernel size to filter out noise or increasing threshold values of canny funciton.
