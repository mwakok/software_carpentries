# Software Carpentries materials 

The schedule below was followed during a Software Carpentries Workshop, hosted at the [TU Delft in November 2021](https://4turesearchdata-carpentries.github.io/2021-11-15-tudelft-online/)

## Session 1 - Programming with Python Materials

[https://swcarpentry.github.io/python-novice-inflammation/]

### Program
12:15 - Organizers/instructors/helpers in the Zoom meeting room to check last set ups, introductions etc

12:30 - Welcome and instructions of the day
- Reminder Code of Conduct/How to get help
- Reminder on how to get help
- Programme of the day
- Roll call & Ice breaker
	
12:40 - First 5 mins to check that everybody installed Anaconda and download the datasets 
`swc-python` folder on Desktop

```bash
$ conda --version
$ python --version
$ jupyter --version
```

12:45 - Introducing Jupyter (15 min) 
- [Anaconda and Jupyter Lab/Notebooks](https://www.anaconda.com/products/individual) 10 min - to download Anaconda
- [Setup files](https://swcarpentry.github.io/python-novice-inflammation/setup.html)

- [Slides](python_lecture_1.slides.html) on Jupyter Notebook features (10 min)
	

13:00 - Python Fundamentals (45 mins)
- [Lesson 1](https://swcarpentry.github.io/python-novice-inflammation/01-intro/index.html)
  _Variables and type_
- [Lesson 4](https://swcarpentry.github.io/python-novice-inflammation/04-lists/index.html)
  _Lists and slicing_
- **Skipped:** Nested lists, and append/pop

13:45 - BREAKOUT Session 1 (15 min)
[Exercises 1 and 2](python_exercises_1.slides.html) (open in browser)

14:00 - Coffee break (15 min)

14:15 - Loading and analysing data in Python (30 mins)


- [Lesson 2](https://swcarpentry.github.io/python-novice-inflammation/02-numpy/index.html) (original 60 mins)
  _Import and NumPy and display data (15 mins)_
  _Basic statistics on data (10 mins)_

14:45 - Visualizing Data (45 mins)
- [Lesson 3](https://swcarpentry.github.io/python-novice-inflammation/03-matplotlib/index.html) (original 50 mins)
  _Matplotlib (15 mins)_
  _Plotting (15 mins)_
  _Saving plots (10 min)_

15:30 - Coffee break

15:45 - Repeating actions with FOR Loops (45 mins) 
- [Lesson 5](https://swcarpentry.github.io/python-novice-inflammation/05-loop/index.html) (original 30 mins)
- [Lesson 6](https://swcarpentry.github.io/python-novice-inflammation/06-files/index.html) (original 20 mins)
  _Introducing For Loops__
  _Analyzing data from multiple files__

16:30 - BREAKOUT Session 2 (20 min)
[Exercises 3 and 4](python_exercises_1.slides.html) (open in browser)

16:50 - Final questions for the day + reminder feedback   
17:00 - End    
17:00 - Sharing Feedback Instructors/Helpers   


## Session 2  - Programming with Python

### Program

12:15 - Organizers/instructors/helpers in the Zoom meeting room to check last set ups, introductions etc   
12:30 - Start workshop and let participants in! We should not need time to check installations as any remaining problems are addressed on day 3. 

12:30 - Welcome and instructions of the day @ Paula
- Reminder Code of Conduct/How to get help. 
- Programme of the day
- Ice breaker   

12:40 - Recap of Day 2 (5 minutes)   
12:45 - Making Choices (20 minutes teaching + 5 minutes exercise)   
- [Lesson 7](https://swcarpentry.github.io/python-novice-inflammation/07-cond/index.html)

**Plenary Exercises:**
- Plenum: [How many paths?](https://swcarpentry.github.io/python-novice-inflammation/07-cond/index.html#how-many-paths )

- Together, inspect all datasets for suspicious data

13:15 - Creating Functions (20 minutes teaching + 5 minutes plenum exercises)
- [Lesson 8](https://swcarpentry.github.io/python-novice-inflammation/08-func/index.html)
  _Skipping: Testing and Documentation_

**Plenary Exercises:**
- Plenum: [Mixing Default and Non-Default Parameters](https://swcarpentry.github.io/python-novice-inflammation/08-func/index.html#mixing-default-and-non-default-parameters )


13:35 - Breakout Session 1 (25 min) 
[Exercise 7](python_excercises_2.slides.html) (open in browser)

These exercises can also be found on the SWC website:

- ["Rescaling an Array"](https://scw-ss.github.io/2021-03-16-tudelft-online-python-novice-inflammation/08-func/index.html#rescaling-an-array )
- ["Testing and Documenting Your Function"](https://swcarpentry.github.io/python-novice-inflammation/08-func/index.html#testing-and-documenting-your-function )

- Optional: [Refine the rescale function via "Defining Defaults"](https://swcarpentry.github.io/python-novice-inflammation/08-func/index.html#defining-defaults-1)


14:00: Coffee Break I

**ADDED part on modular code**
1.	[Tidying-up](https://swcarpentry.github.io/python-novice-inflammation/08-func/index.html#tidying-up)   
2.	Create script called `processing.py`   
3.	Copy functions (visualize, detect_problems) to script   
4.	Create new notebook called `inflammation_analysis_refactored.ipynb`   
5.	Import (visualize, detect_problems) in the new notebook and place in for-loop to analyse for all files   
6.	Questions in session:   
a.	Do we still need to import numpy and matplotlib when we are importing them in the `processing.py` script?    
_No, this is handled in the script._   
b.	What happens to the savefig in the loop?    
_Currently, during each loop the file `imflammation.png` is overwritten. Solution for future sessions: We could add new savenames or leave the savefig out of the functions entirely for simplicity._


Resources on structuring python code:
-	https://realpython.com/absolute-vs-relative-python-imports/
-	http://cicero.xyz/v3/remark/0.14.0/github.com/coderefinery/modular-code-development/master/talk.md/#1


14:15: Errors and Exceptions (15 minutes teaching + 5 minutes exercise)
- [Lesson 9](https://swcarpentry.github.io/python-novice-inflammation/09-errors/index.html)

Example plenum:
- **SKIPPED:** [Reading Error Messages](https://swcarpentry.github.io/python-novice-inflammation/09-errors/index.html#reading-error-messages )

14:40: Defensive Programming (20 min)
- [Lesson 10](https://swcarpentry.github.io/python-novice-inflammation/10-defensive/index.html)
- Example for a pre-condition to find empty array
- Add precondition to inflammation_analysis.ipynb
- **Skipped:** Replace previous conditional statements in `inflammation_analysis.ipynb` by assertions

Questions during session:
a. _When would you use assert and when a conditional statement?_
Assert is used to verify the correct usage and executation of your code. Conditional statements are used to handle choices as part of the code functionality.

15:05: **SKIPPED DUE TO LACK OF TIME!**  

- [Lesson 11](https://swcarpentry.github.io/python-novice-inflammation/11-debugging/index.html)
  _Debugging (20 minutes teaching + 5 minutes exercise)_


Exercises:
- Plenum: [Not Supposed to be the Same](https://swcarpentry.github.io/python-novice-inflammation/11-debugging/index.html#not-supposed-to-be-the-same )

15:30: Coffee Break II

15:45: Command-Line Programs (45 min)
- For instructors: Use a [history terminal](https://github.com/4TUResearchData-Carpentries/documentation/blob/master/command-history.md)
- [Lesson 12](https://swcarpentry.github.io/python-novice-inflammation/12-cmdline/index.html)

16:30: Breakout Session 2 (30 min)
- [Exercise 9, 10 and (optional) 11](python_exercises_2.slides.html)
Solutions are already present in the code folder (use code/reading_06.py as starting point):   
Solution exercise 9: `code/reading_08.py`  
Solution exercise 10: `code/reading_09.py`  
Solution exercise 11: `code/my_ls.py`  

16:50 - Wrap up, Questions, etc.   
17:00 - End   
17:00 - Sharing Feedback Instructors/Helpers   
