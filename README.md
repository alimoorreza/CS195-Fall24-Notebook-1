# CS195-Fall24-Notebook #1
## Image whitening and histogram equalization!

<b>Due</b>: Friday, September 13th, 2024

## How this is going to work: 

I've provided some starter code for you. Before you go any further, click on the `notebook1_whiteing_starter.ipynb` and `notebook1_histogram_equalization_starter.ipynb` links in the repository, and then, at the top of the notebook, you will see a button that says `Open in Colab`. Click on this and it will open the starter code in Google Colaboratory.

## The Images
For this notebook, we're going to enter the world of Pokemon.

The data is from Kaggle and can be found in this repository, on Blackboard, and online at [this link](https://www.kaggle.com/abcsds/pokemon).
The data includes the following features:
- **#**: ID for each pokemon
- **Name**: Name of each pokemon
- **Type 1**: Each pokemon has a type, which determines weakness/resistance to attacks
- **Type 2**: Some pokemon are dual type and have 2
- **Total**: sum of all stats that come after this, a general guide to how strong a pokemon is
- **HP**: hit points, or health, defines how much damage a pokemon can withstand before fainting
- **Attack**: the base modifier for normal attacks (eg. Scratch, Punch)
- **Defense**: the base damage resistance against normal attacks
- **SP Atk**: special attack, the base modifier for special attacks (e.g. fire blast, bubble beam)
- **SP Def**: the base damage resistance against special attacks
 -**Speed*and *: determines which pokemon attacks first each round
 
The first step is to get the data loaded and ready to go, make sure the data is in your Google Drive, and mount your Drive to the notebook. Start by printing out the first several lines of the dataset to get an idea of what the data looks like. 

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

>I'm going to write in 1's for the Points awarded, but I will update when I grade if there's something that was missed

| Exercise #  | Points Awarded (out of 1)  | Notes |
| --------- | ------------------- | --------- |
| 1: type          |    1    |    |
| 2: fire_flying   |    1    |    | 
| 3: Attack        |    1    |    |
| 4: Gen 1         |    1    |    | 
| 5: Strongest Type|    1    |    |
| 6: Something cool|    1    |    |
| <b>Total         |     /6 |     </b>   |
