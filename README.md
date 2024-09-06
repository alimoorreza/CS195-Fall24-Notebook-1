# CS195-Fall24-Notebook #1
## Image whitening and histogram equalization!

<b>Due</b>: Friday, September 13th, 2024

## How this is going to work: 

I've provided some starter code for you. Before you go any further, click on the `notebook1_whiteing_starter.ipynb` and `notebook1_histogram_equalization_starter.ipynb` links in the repository, and then, at the top of the notebook, you will see a button that says `Open in Colab`. Click on this and it will open the starter code in Google Colaboratory.

## The Images
For this notebook, you will need the following two images:
- **Image#1**: [this link](https://github.com/alimoorreza/CS195-Fall24-Notebook-1/blob/main/data/first_photograph.png). *Use this for Task#1*
- **Image#2**: [this link](https://github.com/alimoorreza/CS195-Fall24-Notebook-1/blob/main/data/himalaya_dark.png). *Use this for Task#2*
 
First things first: upload the images to your Google Drive and then mount your Drive to the notebook. I aim to help everyone get familiar with the programming environment and comfortable working with pixel values in images. There will be two tasks: you'll perform various per-pixel transformations on images and observe the results.
# **Task#1**: Whitening Transformation
You will be adjusting the contrast of the image. Your goal is to transform the image so that the resulting image has a zero mean and unit variance. Denote the image as $I(.)$ which is a 2D array of pixel values. Its width and height are $N$ and $M$ pixels respectively. Also $I(x,y)$ denotes the pixel value at 2D location $(x,y)$.

You can compute the mean and variance of the gray-scale image $I(.)$ as follows:

<!--$\mu$ = $\frac{\sum_{x=1}^{N}\sum_{y=1}^{M}I(x,y)}{N \times M}$
\sigma^{2} = \frac{\sum_{x=1}^{N}\sum_{y=1}^{M}(I(x,y)-\mu)^2}{N*M}-->
![mean and variance equations](https://github.com/alimoorreza/CS195-Fall24-Notebook-1/blob/main/etc/whitening_eq1.png)

Now, you can transform each pixel value separately using the above two computed statistics $\mu$ (mean) and $\sigma$ (standard deviation) as follows:
    <!--I^{'}(x,y) = \frac{I(x,y)-\mu}{\sigma}-->
    
![whitening transformation](https://github.com/alimoorreza/CS195-Fall24-Notebook-1/blob/main/etc/whitening_eq2.png)


Apply this *Whitening Transformation* on the provided input image to see how it affects. The following figures show the effect of applying *Whitening Transformation* on the first-ever photograph -- **Image#1**: [this link](https://github.com/alimoorreza/CS195-Fall24-Notebook-1/blob/main/data/first_photograph.png). The result should something like below:

![Result task#1](https://github.com/alimoorreza/CS195-Fall24-Notebook-1/blob/main/etc/task1_result.png)

# **Task#2**: Histogram Equalization
Let's try another type of contrast transformation called *Histogram Equalization* on the input image. You may need to do it in multiple steps.
You need to finish only the first three steps. I have provided code snippet for step#4. As long as, you have correctly implemented the step#1, step#2, and step#3, your code should brighten up the dark intensity regions.

## **Step 1:** 
You need to generate the histogram of intensity values. The simplest way to find the histogram of intensity values is to make use of the **Pillow Library** functionalities (HINT: There is a function called `histogram()' in Pillow). There will be at most 255 intensity values. Let's denote $hist_{b}$ is 1D vector denoting the histogram of intensity values. $b$ denotes a particular bin, and its value ranges from 0 to 255. Now, count how many pixels in image $I(.)$ have the intensity value equal to $b$. Put that total count into the respective bin location, i.e., $hist_{b}$. You can do it for all the intensity values one after another, starting from $b=0$ up until $b=255$.

## **Step 2:**
Now you need to normalize the histogram $hist$ such that the sum of this new histogram is equal to 255. Denote this new histogram as $hist^{'}$. For each bin $b$, you can compute it as follows:

![histogram normalization](https://github.com/alimoorreza/CS195-Fall24-Notebook-1/blob/main/etc/histogram_equalization_eq1.png)

Recall that the image width and height are $N$ and $M$ pixels respectively.

## **Step 3:** 
Compute the cumulative sum of the $hist^{'}$. Denote this histogram as $histcum^{}$. Let's say you have histogram with 4 bins with the following values $[1,2,3,4]$. In this case, you have a histogram with 4 bins, and the frequency values of these bins are given such that
*the first bin contains 1*, *the second bin contains 2*, *the third bin contains 3*, and *the fourth bin contains 4*. The cumulative sum involves progressively adding the values of the histogram bins as you move from the first bin to the last. Essentially, each entry in the cumulative sum array represents the sum of all previous bins' values plus the current bin's value. Cumulative sum of this histogram would be $[1,3,6,10]$

## **Step 4:** 
Use the cumulative histogram $histcum^{}$ as a lookup table to transform the value of each pixel location as follows:

![color lookup](https://github.com/alimoorreza/CS195-Fall24-Notebook-1/blob/main/etc/histogram_equalization_eq2.png)

where $I^{'}(x,y)$ denotes the histogram equalized image value at pixel location $(x,y)$. Apply your newly implemented *Histogram Equalization* on **Image#2**: [this link](https://github.com/alimoorreza/CS195-Fall24-Notebook-1/blob/main/data/himalaya_dark.png) to see how it affects. The following figures show the result:

![Result task#2](https://github.com/alimoorreza/CS195-Fall24-Notebook-1/blob/main/etc/task2_result.png)

Use the two starter notebooks to finish the implementations. Submit this assignment through the CodePost link (find it on Blackboard).

## :white_check_mark: Grading: 
I will update the following rubric with your grade after you have completed the assignment.
### Rubric:

>

| Exercise #  | Points Awarded (out of 1)  | Notes |
| --------- | ------------------- | --------- |
| 1: type          |    1    |    |
| 2: fire_flying   |    1    |    | 
| 3: Attack        |    1    |    |
| 4: Gen 1         |    1    |    | 
| 5: Strongest Type|    1    |    |
| 6: Something cool|    1    |    |
| <b>Total         |     /6 |     </b>   |
