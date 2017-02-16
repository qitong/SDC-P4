# SDC-P4

## Camera Calibration
#### 1. Have the camera matrix and distortion coefficients been computed correctly and checked on one of the calibration images as a test?

The code for this step is contained in the third code cell of the IPython notebook (adv_lane_dectection.ipynb).

I read in all the chessboard image for undistortion. Assuming all the chessboard are fixing at the plane where z=0, objpoints are filled with (x,y,0), or simply (x,y) where x,y is the coordinate index from (0,0) to (8,5) since there are 9x6 corners should be found on the chessboard. Then, imgpoints are filled by findChessboardCorners function on the chessboard image. For each image with ret=True returned by findChessboardCorners (17 out of 20), the objpoints and imgpoints are constructed and serve as input to calibrateCamera to get the parameters to undistort images.

There is the comparison between the original and undistort image I get from calibration1.jpg (saved as undistorted_calibration1.jpg in output_images/)

TODO####


## Pipeline (single images)

#### 1. Has the distortion correction been correctly applied to each image?

To demonstrate this step, I will describe how I apply the distortion correction to one of the test images like this
one: (saved as undistorted_test1.jpg in output_images/)

TODO####

#### 2. Has a binary image been created using color transforms, gradients or other methods?

To demonstrate this step, I will describe how I apply the distortion correction to one of the test images like this
one: (saved as sobeled_test2.jpg in output_images/)
One thing need to mention is that I apply grayscale to image first, then use single that single channel to do sobel gradient. While, when I play that method on the road that have a gray road surface (other than black surface) the yellow becomes unclear since after grayscale it looks similar to road surface. Thus, I use RGB channels with sobel, then, I defined a function named shrink_image_over_thresh() to shrink them to one channel (e.g, (1,0.9,0) -> 1)

TODO####


#### 3. Has a perspective transform been applied to rectify the image?

To demonstrate this step, I will describe how I apply the distortion correction to one of the test images like this
one: (saved as perspective_straight_lines1.jpg in output_images/)
The code for my perspective transform is includes a function called perspective_transform() , which appears in the first two cell under "Perspective Transform" section. This function takes an image and a transform matrix M as input. M is defined by src and dst points through cv2.getPerspectiveTransform(). For src and dst points, dst is what I suppose it should be after transform, so that a rectangle with coordinate [[400,625],[1035,625],[400,400],[1035,400]]; on the other end, src points is generated from "test_images/straight_lines1.jpg", I use my image software manualy measured as [[255,678],[1053,678],[556,475],[729,475]] (I suppose those lane line as indicated is straight and pick two pairs each from same horizontal value.)

TODO####

#### 4. Have lane line pixels been identified in the rectified image and fit with a polynomial?
Then I did some other stuff and fit my lane lines with a 2nd order polynomial kinda like this:
TODO ####

#### 5. Describe how (and identify where in your code) you calculated the radius of curvature of the lane and the position of the vehicle with respect to center.


#### 6. Provide an example image of your result plotted back down onto the road such that the lane area is identified clearly.
TODO ####

## Pipeline (video)
#### 1. Provide a link to your final video output. Your pipeline should perform reasonably well on the entire project video (wobbly lines are ok but no catastrophic failures that would cause the car to drive off the road!).  
Here is my video link: https://youtu.be/gmVLclvZYUQ


## Discussion
#### 1. Briefly discuss any problems / issues you faced in your implementation of this project. Where will your pipeline likely fail? What could you do to make it more robust?

