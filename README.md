
**Irish Sign Language Detection Program**

----------

**Overview:**

My team and I have decided to create an Irish sign language detection program. The objective of the program is to accurately identify Irish sign language letters from an input image.

**sample input:**

![](https://habeebalao504460699.files.wordpress.com/2023/10/sample-d.jpg?w=640)

This sample input image represents the letter "D" in Irish sign language. Our program aims to take in this input image or ones similar to it and identify the ISL's sign associated letter.

**Research publications:**

I began my research by familiarising my-self more with the Irish sign language letter structure. I then researched if similar projects had been done before. I also researched if there where any algorithms or datasets in peer reviewed studies that could help. After doing so these where my findings:

**Research Comparisons:**

-   I found projects similar to our project idea, but the majority of them used a different flavour of Sign language either American sign language or Indian sign language and used some form of deep learning technique to predict a letter to a certain degree of confidence.

-   Also I found some datasets that could be used for the project if we decide to take the deep learning approach to this project.

**Research Theory:**

-   I found a studies discussing ways of identifying ISL letters using approaches such as hand segmentation, Blob method, sift technique, Gradient Hough Transform and many more which all vary in levels difficulty to implement.
-   After doing this research i found that the Hand Segmentation approach was amongst the most viable ways of implementing the logic to identify ISL letters. i will share my findings with my group and discuss what they have found also to decide the best plan to implement the script.

**Research Citations:**

[1] W. Kubinger, M. Vincze, and M. Ayromlou, “The role of gamma correction in colour image processing,” in _9th European Signal Processing Conference (EUSIPCO 1998)_, Sep. 1998, pp. 1–4. Accessed: Oct. 28, 2023. [Online]. Available: https://ieeexplore.ieee.org/abstract/document/7090032

[2] S. Rahman, M. M. Rahman, M. Abdullah-Al-Wadud, G. D. Al-Quaderi, and M. Shoyaib, “An adaptive gamma correction for image enhancement,” _EURASIP J. Image Video Process._, vol. 2016, no. 1, p. 35, Oct. 2016, doi: 10.1186/s13640-016-0138-1.

[3] K. Nimisha and A. Jacob, “A Brief Review of the Recent Trends in Sign Language Recognition,” in _2020 International Conference on Communication and Signal Processing (ICCSP)_, Jul. 2020, pp. 186–190. doi: 10.1109/ICCSP48568.2020.9182351.

[4] M. Safeel, T. Sukumar, S. K. S, A. M. D, S. R, and P. S. B, “Sign Language Recognition Techniques- A Review,” in _2020 IEEE International Conference for Innovation in Technology (INOCON)_, Nov. 2020, pp. 1–9. doi: 10.1109/INOCON50539.2020.9298376.

[5] D. Team, “Sign Language Recognition Using Python and OpenCV,” DataFlair. Accessed: Oct. 04, 2023. [Online]. Available: https://data-flair.training/blogs/sign-language-recognition-python-ml-opencv/

[6] M. Garimella, “Sign Language Recognition with Advanced Computer Vision,” Medium. Accessed: Oct. 04, 2023. [Online]. Available: https://towardsdatascience.com/sign-language-recognition-with-advanced-computer-vision-7b74f20f3442

Approach Discussion:

This week i have discussed my findings with my team members and listened to their findings. After some deliberations we have agreed to use template matching as our core approach to identifying ISL letters.  
Template matching in simple terms is taking a test image x and processing the contents of the image to a bunch of template images that represent an ISL letter and determining which image template the test image matches to identify the ISL letter.

Beginning Development:

later last week i set up a GitHub repository where my team and I can centralise all our code. I've added them as collaborators so we can all contribute to the repo. I made small pr with the "main.py" file that will house the entirety of the ISL recognition program. Right now the file contains foundational code such as imports we will use, a brief program description, and a simple print statement.  
  
This coming week when my team and i all get together, I plan on beginning to list out the tasks required to complete the code of the program and begin delegating the workload equally to each team member.

**Design Specifications:**

this week my team and I have outlined the design specification of the ISL Program. we have broken down our program into three parts:  
  
1. Preprocessing / feature extraction

-   Preprocessing consist of reading in the image of the ISL sign letter and performing flesh detection, thresholding, segmentation to extract the hand as the region of interest.
-   With the hand extracted from the background we then perform various feature extraction methods including contour detection.

2. Extraction of data from templates

-   We will have a set of images that will have each of the sign language letter represented.  
    we will then process the image and store the feature data from it so we can later compare it with the input image.

3. Template matching

-   Template matching will consist of taking preprocessed sample image then comparing it with the data in the template images that represent an ISL letter and determining which image template best matches it to then detect which letter the input image contains.

Here is a visual representation of the flow our ISL detection python program will follow:

![](https://habeebalao504460699.files.wordpress.com/2023/11/screenshot-2023-11-12-at-13.28.51.png?w=984)

Continuing Development

This week week I added code to our repository. the code does the initial preprocessing of the image and performs skin detection, thresholding and edge detection to get the mask of the input ISL image.

Here is the output of the processed image.

![](https://habeebalao504460699.files.wordpress.com/2023/11/screenshot-2023-11-22-at-17.21.13.png?w=1024)

This image is a copy of the binary image that shows the outline of the input image. we will use this for template matching against the other input image with each letter of the alphabet in the Irish sign language.

**Design Testing**

During the development process I had done a lot of testing in aims of enhancing the image the the mask would be taken from and subsequently used in the template matching portion of the program.

I had experimented with using just canny edge detection which produced a mask that looked like this:

![](https://habeebalao504460699.files.wordpress.com/2023/11/screenshot-2023-11-22-at-17.21.13.png?w=1024)

I then implemented skin detection in the program so input images with not so clear backgrounds could also be used.

After implementing skin detection and using morphology techniques including erosion, dilation, opening and closing techniques this is what the mask produced looked like:

![](https://habeebalao504460699.files.wordpress.com/2023/11/screenshot-2023-11-29-at-17.04.33.png?w=1024)

After implementing skin detection the detail of the mask had reduced.

However, after further testing and the addition of Gamma Correction and adjustments to the shapes using in the erosion, opening and closing morphology operation the mask looked like this:

![](https://habeebalao504460699.files.wordpress.com/2023/11/screenshot-2023-11-29-at-17.32.22.png?w=1024)

With further modification I got the mask to look like this:

![](https://habeebalao504460699.files.wordpress.com/2023/11/screenshot-2023-11-29-at-19.59.11.png?w=1024)

I then tested my modified code with other similar images and got these outputs:

![](https://habeebalao504460699.files.wordpress.com/2023/11/screenshot-2023-11-29-at-20.03.33.png?w=971)

![](https://habeebalao504460699.files.wordpress.com/2023/11/screenshot-2023-11-29-at-20.03.00.png?w=982)

![](https://habeebalao504460699.files.wordpress.com/2023/11/screenshot-2023-11-29-at-20.08.01.png?w=1024)

![](https://habeebalao504460699.files.wordpress.com/2023/11/screenshot-2023-11-29-at-20.07.39.png?w=1024)

![](https://habeebalao504460699.files.wordpress.com/2023/11/screenshot-2023-11-29-at-20.13.56-1.png?w=1024)

![](https://habeebalao504460699.files.wordpress.com/2023/11/screenshot-2023-11-29-at-20.13.40-1.png?w=1024)

**Design Innovation** & **Design Complexity**

There are Two main parts of innovation and complexity in this project:

Firstly, we have built this program to work with Irish Sign Language with differs from the majority of other solutions currently available which focus on more popular sign language's such as ASL(American Sign Language).

Secondly, in the preprocessing and feature extraction Gamma Correction was done which isn't typically done but due this accuracy of the template matching depending on quality of the mask which depends on the color detection. Ensuring the color of the hand in the image was at the richest quality was paramount.

This is a visual representation of how Gamma Correction can affect the quality of an image using two different gamma correction values:

![](https://habeebalao504460699.files.wordpress.com/2023/11/image.png?w=1000)

![](https://habeebalao504460699.files.wordpress.com/2023/11/image-2.png?w=850)

This is how it was implemented in code:

![](https://habeebalao504460699.files.wordpress.com/2023/11/screenshot-2023-11-30-at-18.24.57.png?w=768)

**Further Design Testing**

Once my fellow team members had finished coding up the template feature extraction and template matching respectively.

I added a nice visual representation of the template with the highest match to the inout image and a couple stats about the result. Including the **Accuracy** of the match the **letter** corresponding to the template and the **runtime speed**.

Here are some of the tests that passed and failed using different input images:

passed test

![](https://habeebalao504460699.files.wordpress.com/2023/12/screenshot-2023-12-02-at-13.33.44.png?w=895)

passed test

![](https://habeebalao504460699.files.wordpress.com/2023/12/screenshot-2023-12-02-at-18.38.30.png?w=898)

here are some of the failed tests

![](https://habeebalao504460699.files.wordpress.com/2023/12/screenshot-2023-12-02-at-13.40.15.png?w=840)

![](https://habeebalao504460699.files.wordpress.com/2023/12/screenshot-2023-12-02-at-14.01.45.png?w=897)
