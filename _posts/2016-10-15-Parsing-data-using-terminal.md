---
layout: post
title: Parsing data using the UNIX terminal
author: Angelos Ikonomakis
---

[figure_1]: ../images/parsing_data_using_terminal_screens/figure_1.png "Figure 1"
This is an example of how we can do simple data parsing using the **Unix terminal**. We will use applications like *chmod, find, grep, sed, apt-get, nano, cut, sort, uniq, head, tail, less, cat, ssh, wc, echo, man* and more.

## Tip 1 - How to write a command that finds the 10 most popular words in a file

Lets suppose that we have a txt file named draft.txt with the following content.    
> *HANGZHOU, China — The image of a 5-year-old Syrian boy, dazed and bloodied after being rescued from an airstrike on rebel-held Aleppo, reverberated around the world last month, a harrowing reminder that five years after civil war broke out there, Syria remains a charnel house.*    
> *But the reaction was more muted in Washington, where Syria has become a distant disaster rather than an urgent crisis. President Obama’s policy toward Syria has barely budged in the last year and shows no sign of change for the remainder of his term. The White House has faced little pressure over the issue, in part because Syria is getting scant attention on the campaign trail from either Donald J. Trump or Hillary Clinton.*    
> *That frustrates many analysts because they believe that a shift in policy will come only when Mr. Obama has left office. “Given the tone of this campaign, I doubt the electorate will be presented with realistic and intelligible options, with respect to Syria,” said Frederic C. Hof, a former adviser on Syria in the administration.*    
> *The lack of substantive political debate about Syria is all the more striking given that the Obama administration is engaged in an increasingly desperate effort to broker a deal with Russia for a cease-fire that would halt the rain of bombs on Aleppo.*    
> *Those negotiations moved on Sunday to China, where Secretary of State John Kerry met for two hours with the Russian foreign minister, Sergey V. Lavrov, at a Group of 20 meeting. At one point, the State Department was confident enough to schedule a news conference, at which the two were supposed to announce a deal.*    
> *But Mr. Kerry turned up alone, acknowledging that “a couple of tough issues” were still dividing them.*

I will display the query and the output and later I will describe what each one of the applications does.

```terminal
tr -c '[:alnum:]' '[\n*]'<draft.txt | sort | uniq -c | sort -nr | head -11 | tail -10
```
![alt text][figure_1]

* The command **tr** creates a list of the words in draft.txt, one per line, where an alphanumeric character is taken to be a maximal string of letters. 

* Then we used piping to sort the listing of words **sort** 

* Later with **uniq -c** we put each output line with the count of the number of times the line occurred in the input, followed by a single space. 

* Then **sort -nr** to sort the listing by numbers on descending order. 

* Lastly we used **head -11** for the eleven most frequent words and **tail -10** to avoid the blanks as it was calculated  as the most frequent word in the document.

## Tip 2 - How to write a command that removes all rows from a table where the price is more than 10,000$

Let's again suppose that we have a txt file named cars.txt with the following content.

|plym   |fury   |77 |73  |2500  |
|chevy  |nova   |79 |60  |3000  |
|ford   |mustang|65 |45  |17000 |
|volvo  |gl     |78 |102 |9850  |
|ford   |ltd    |83 |15  |10500 |
|Chevy  |nova   |80 |50  |3500  |
|fiat   |600    |65 |115 |450   |
|honda  |accord |81 |30  |6000  |
|ford   |thundbd|84 |10  |17000 |
|toyota |tercel |82 |180 |750   |
|chevy  |impala |65 |85  |1550  |
|ford   |bronco |83 |25  |9525  |

