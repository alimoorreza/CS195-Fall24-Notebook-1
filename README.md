# CS195-Fall24-Notebook #1
## Image whitening and histogram equalization!

<b>Due</b>: Friday, September 13th, 2024

## How this is going to work: 

I've provided some starter code for you. Before you go any further, click on the `notebook1_whiteing_starter.ipynb` and `notebook1_histogram_equalization_starter.ipynb` links in the repository, and then, at the top of the notebook, you will see a button that says `Open in Colab`. Click on this and it will open the starter code in Google Colaboratory.

## The Images
For this notebook, you will need the following two images:
- **Image#1**: [this link](https://github.com/alimoorreza/CS195-Fall24-Notebook-1/blob/main/data/first_photograph.png).
- **Image#2**: [this link](https://github.com/alimoorreza/CS195-Fall24-Notebook-1/blob/main/data/himalaya_dark.png).
 
First things first: upload the images to your Google Drive and then mount your Drive to the notebook. I aim to help everyone get familiar with the programming environment and comfortable working with pixel values in images. There will be two tasks: you'll perform various per-pixel transformations on images and observe the results.
# **Task#1**: Whitening Transformation
You will be adjusting the contrast of the image. Your goal is to transform the image so that the resulting image has a zero mean and unit variance. Denote the image as $I(.)$ which is a 2D array of pixel values. Its width and height are $N$ and $M$ pixels respectively. Also $I(x,y)$ denotes the pixel value at 2D location $(x,y)$.

You can compute the mean and variance of the gray-scale image $I(.)$ as follows:

<!--$\mu$ = $\frac{\sum_{x=1}^{N}\sum_{y=1}^{M}I(x,y)}{N \times M}$
\sigma^{2} = \frac{\sum_{x=1}^{N}\sum_{y=1}^{M}(I(x,y)-\mu)^2}{N*M}-->
![mean and variance equations](https://github.com/alimoorreza/CS195-Fall24-Notebook-1/blob/main/etc/whitening_eq1.png)

Now, you can transform each pixel value separately using the above two computed statistics $\mu$ (mean) and $\sigma$ (standard deviation) as follows:
![whitening transformation](https://github.com/alimoorreza/CS195-Fall24-Notebook-1/blob/main/etc/whitening_eq2.png)
    <!--I^{'}(x,y) = \frac{I(x,y)-\mu}{\sigma}-->


Apply this *Whitening Transformation* on the provided input image to see how it affects. The following figures show the effect of applying *Whitening Transformation* on the first-ever photograph -- **Image#1**: [this link](https://github.com/alimoorreza/CS195-Fall24-Notebook-1/blob/main/data/first_photograph.png). The result should something like below:

![Result task#1](https://github.com/alimoorreza/CS195-Fall24-Notebook-1/blob/main/etc/task1_result.png)

# **Task#2**: Histogram Equalization
Let's try another type of contrast transformation called *Histogram Equalization* on the input image. You may need to do it in multiple steps.
You need to finish only the first three steps. I have provided code snippet for step#4. As long as, you have correctly implemented the step#1, step#2, and step#3, your code should brighten up the dark intensity regions.

## **Step 1:** 
you need to generate the histogram of intensity values. The simplest way to find the histogram of intensity values is to make use of the \texttt{\textbf{Pillow Library}} functionalities (HINT: There is a function called `histogram()' in Pillow). Alternatively, if you want, you could write few lines of python code and build your own histogram of intensity values. There will be at most 255 intensity values. Let's denote $hist_{b}$ is 1D vector denoting the histogram of intensity values. $b$ denotes a particular bin, and its value ranges from 0 to 255. 
Now, count how many pixels in image $I(.)$ have the intensity value equal to $b$. Put that total count into the respective bin location, i.e., $hist_{b}$. You can do it for all the intensity values one after another, starting from $b=0$ up until $b=255$.

## **Step 2:**
Now you need to normalize the histogram $hist$ such that the sum of this new histogram is equal to 255. Denote this new histogram as $hist^{'}$. For each bin $b$, you can compute it as follows:

Recall that the image width and height are $N$ and $M$ pixels respectively.

## **Step 3:** 
Compute the cumulative sum of the $hist^{'}$. Denote this histogram as $histcum^{}$. Let's say you have histogram with 4 bins with the following values $[1,2,3,4]$. In this case, you have a histogram with 4 bins, and the frequency values of these bins are given such that
*the first bin contains 1*, *the second bin contains 2*, *the third bin contains 3*, and *the fourth bin contains 4*. The cumulative sum involves progressively adding the values of the histogram bins as you move from the first bin to the last. Essentially, each entry in the cumulative sum array represents the sum of all previous bins' values plus the current bin's value. Cumulative sum of this histogram would be $[1,3,6,10]$

## **Step 4:** 


## What you need to do :exclamation:
<b>Notebook #1 consists of the following exercises</b> [ 1 point each ]:
1. Print out all of the unique values for the `Type 1` column of the dataset. 
  > *Hint: I'm looking for each possible primary type to be ouput once, not a list of the primary type of each pokemon. For example, if I tossed a coin 3 times and got Heads, Tails, Heads, the unique values of the coin flip are Heads and Tails. There is a function for this.*
2. Create a subset of data representing pokemon whose primary type is **Fire** 🔥, and the second type is **Flying** 🦅. Save this DataFrame to the variable name `fire_flying_pokemon`. Display the first 5 lines of this subset.
3. Using `fire_flying_pokemon`, what is the median **Attack** of Fire Flying Pokemon?
4. Create a subset with only pokemon from Generation I. Include 5 columns, the `Generation`, `Name`, `Type 1`, `Type 2`, and `Total`. 
  - *For an extra challenge, see if you can do this in one line.*
5. Which primary type of pokemon is the overall strongest? (not looking for philosophical debates here, I'm looking at the average of the 'Total' column, [grouped by](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.groupby.html) Type--so Fire v Water v Grass etc.). 
6. **Do something cool**. Using the Pokemon dataset, get creative and show me something about the dataset. Use a text cell to explain what you did. 
 - *Need some help getting started here? Try asking a question about the dataset and see if you can use Python and Pandas to answer the question*

Use a Markup cell to put your name at the top of the file. Submit this assignment through the CodePost link (find it on Blackboard).

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
