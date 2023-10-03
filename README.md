[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-718a45dd9cf7e7f842a935f5ebbe5719a5e09af4491e668f4dbf3b35d5cca122.svg)](https://classroom.github.com/online_ide?assignment_repo_id=11730520&assignment_repo_type=AssignmentRepo)
# Quicksort Pivots

in the lectures I only briefly mentioned strategies for determining a good pivot
for quicksort. The implementation on the slides simply picks the leftmost
element in the part of the array that we consider as a pivot. I also mentioned a
few other ways of picking a good pivot, e.g. randomly.

Median-of-three is also a good way of picking a pivot -- inspect the first,
middle, and last elements of the part of the array under consideration and
choose the median value. Using the probabilities for picking a pivot in a
particular part of the array (in the same way as we did on slide 34), argue
whether this method is more or less (or equally) likely to pick a good pivot
compared to simply choosing the first element. Assume that all permutations are
equally likely, i.e. the input array is ordered randomly.

Your answer must derive probabilities for choosing a good pivot and
quantitatively reason with them.

Add your answer to this markdown file. [This
page](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/writing-mathematical-expressions)
might help with the notation for mathematical expressions.

# Answer

Based on the lesson in the lectures, using the leftmost element as the pivot has a 50% chance of being a good pivot.  A good pivot is between $\frac{n}{2}$ and $\frac{3n}{2}$.

Instead, let's use the median of three random numbers as our pivot.  Each random element has a $\frac{1}{2}$ chance of being a good pivot, while it has a $\frac{1}{4}$ chance of being too low and a $\frac{1}{4}$ chance of being too high.  Let's say L = too low, M = middle (good pivot), and H = too high.  This is all the possible combinations of 3 random numbers, with their calculated probabilities:

LLL ⇒ $\frac{1}{4} * \frac{1}{4} * \frac{1}{4} = \frac{1}{64}$

LLH ⇒ $\frac{1}{4} * \frac{1}{4} * \frac{1}{4} = \frac{1}{64}$

LHH ⇒ $\frac{1}{4} * \frac{1}{4} * \frac{1}{4} = \frac{1}{64}$

HHH ⇒ $\frac{1}{4} * \frac{1}{4} * \frac{1}{4} = \frac{1}{64}$

LLM ⇒ $\frac{1}{4} * \frac{1}{4} * \frac{1}{2} = \frac{2}{64}$

LMH ⇒ $\frac{1}{4} * \frac{1}{2} * \frac{1}{4} = \frac{2}{64}$

MHH ⇒ $\frac{1}{2} * \frac{1}{4} * \frac{1}{4} = \frac{2}{64}$

LMM ⇒ $\frac{1}{4} * \frac{1}{2} * \frac{1}{2} = \frac{4}{64}$

MMH ⇒ $\frac{1}{2} * \frac{1}{2} * \frac{1}{4} = \frac{4}{64}$

MMM ⇒ $\frac{1}{2} * \frac{1}{2} * \frac{1}{2} = \frac{8}{64}$

However, some of these combinations have multiple ways they can be selected before they are sorted:

LLL ⇒ $\frac{1}{64} *$ 1 possibility = $\frac{1}{64}$

LLH ⇒ $\frac{1}{64} *$ 3 possibilities = $\frac{3}{64}$

LHH ⇒ $\frac{1}{64} *$ 3 possibilities = $\frac{3}{64}$

HHH ⇒ $\frac{1}{64} *$ 1 possibilities = $\frac{1}{64}$

LLM ⇒ $\frac{2}{64} *$ 3 possibilities = $\frac{6}{64}$

LMH ⇒ $\frac{2}{64} *$ 6 possibilities = $\frac{12}{64}$

MHH ⇒ $\frac{2}{64} *$ 3 possibilities = $\frac{6}{64}$

LMM ⇒ $\frac{4}{64} *$ 3 possibilities = $\frac{12}{64}$

MMH ⇒ $\frac{4}{64} *$ 3 possibilities = $\frac{12}{64}$

MMM ⇒ $\frac{8}{64} *$ 1 possibility = $\frac{8}{64}$

This accounts for all possible outcomes:

$\frac{1}{64} + \frac{3}{64} + \frac{3}{64} + \frac{1}{64} + \frac{6}{64} + \frac{12}{64} + \frac{6}{64} + \frac{12}{64} + \frac{12}{64} + \frac{8}{64} = 1$

These are the cases where we get a good pivot:

LMH ⇒ $\frac{12}{64}$

LMM ⇒ $\frac{12}{64}$

MMH ⇒ $\frac{12}{64}$

MMM ⇒ $\frac{8}{64}$

Now, add the probabilities together to get the overall odds of a good pivot:

$\frac{12}{64} + \frac{12}{64} + \frac{12}{64} + \frac{8}{64} = \frac{44}{64} = \frac{11}{16}$

Thus, the probability of choosing a good pivot with a median of 3 is $\frac{11}{16}$.  This is better odds than just choosing the first number ($\frac{1}{2}$).  Therefore, using a median of 3 is more likely to choose a good pivot than using the first element.

