---
layout: post
title: Parsing data using the UNIX terminal
author: Angelos Ikonomakis
---

[figure_1]: ../images/parsing_data_using_terminal_screens/figure_1.png "Figure 1"
[figure_2]: ../images/parsing_data_using_terminal_screens/figure_2.png "Figure 2"
[figure_3]: ../images/parsing_data_using_terminal_screens/figure_3.png "Figure 3"
[figure_4]: ../images/parsing_data_using_terminal_screens/figure_4.png "Figure 4"
[figure_5]: ../images/parsing_data_using_terminal_screens/figure_5.png "Figure 5"
[figure_6]: ../images/parsing_data_using_terminal_screens/figure_6.png "Figure 6"
This is an example of how we can do simple data parsing using the **Unix terminal**. We will use applications like *chmod, find, grep, sed, apt-get, nano, cut, sort, uniq, head, tail, less, cat, ssh, wc, echo, man, awk* and more.

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


<style type="text/css">
.tg{
    border-collapse:collapse;
    border-spacing:0;
}
.tg td{
    font-family:Arial, sans-serif;
    font-size:14px;
    padding:10px 5px;
    border-style:solid;
    border-width:1px;
    overflow:hidden;
    word-break:normal;
}
.tg th{
    font-family:Arial, sans-serif;
    font-size:14px;
    font-weight:normal;
    padding:10px 5px;
    border-style:solid;
    border-width:1px;
    overflow:hidden;
    word-break:normal;
}
.tg .tg-yw4l{
    vertical-align:top;
}
</style>
<table class="tg">
  <tr>
    <td class="tg-yw4l">plym</td>
    <td class="tg-yw4l">fury</td>
    <td class="tg-yw4l">77</td>
    <td class="tg-yw4l">73</td>
    <td class="tg-yw4l">2500</td>
  </tr>
  <tr>
    <td class="tg-yw4l">chevy</td>
    <td class="tg-yw4l">nova</td>
    <td class="tg-yw4l">79</td>
    <td class="tg-yw4l">60</td>
    <td class="tg-yw4l">3000</td>
  </tr>
  <tr>
    <td class="tg-yw4l">ford</td>
    <td class="tg-yw4l">mustang</td>
    <td class="tg-yw4l">65</td>
    <td class="tg-yw4l">45</td>
    <td class="tg-yw4l">17000</td>
  </tr>
  <tr>
    <td class="tg-yw4l">volvo</td>
    <td class="tg-yw4l">gl</td>
    <td class="tg-yw4l">78</td>
    <td class="tg-yw4l">102</td>
    <td class="tg-yw4l">9850</td>
  </tr>
  <tr>
    <td class="tg-yw4l">ford</td>
    <td class="tg-yw4l">ltd</td>
    <td class="tg-yw4l">83</td>
    <td class="tg-yw4l">15</td>
    <td class="tg-yw4l">10500</td>
  </tr>
  <tr>
    <td class="tg-yw4l">Chevy</td>
    <td class="tg-yw4l">nova</td>
    <td class="tg-yw4l">80</td>
    <td class="tg-yw4l">50</td>
    <td class="tg-yw4l">3500</td>
  </tr>
  <tr>
    <td class="tg-yw4l">fiat</td>
    <td class="tg-yw4l">600</td>
    <td class="tg-yw4l">65</td>
    <td class="tg-yw4l">115</td>
    <td class="tg-yw4l">450</td>
  </tr>
  <tr>
    <td class="tg-yw4l">honda</td>
    <td class="tg-yw4l">accord</td>
    <td class="tg-yw4l">81</td>
    <td class="tg-yw4l">30</td>
    <td class="tg-yw4l">6000</td>
  </tr>
  <tr>
    <td class="tg-yw4l">ford</td>
    <td class="tg-yw4l">thundbd</td>
    <td class="tg-yw4l">84</td>
    <td class="tg-yw4l">10</td>
    <td class="tg-yw4l">17000</td>
  </tr>
  <tr>
    <td class="tg-yw4l">toyota</td>
    <td class="tg-yw4l">tercel</td>
    <td class="tg-yw4l">82</td>
    <td class="tg-yw4l">180</td>
    <td class="tg-yw4l">750</td>
  </tr>
  <tr>
    <td class="tg-yw4l">chevy</td>
    <td class="tg-yw4l">impala</td>
    <td class="tg-yw4l">65</td>
    <td class="tg-yw4l">85</td>
    <td class="tg-yw4l">1550</td>
  </tr>
  <tr>
    <td class="tg-yw4l">ford</td>
    <td class="tg-yw4l">bronco</td>
    <td class="tg-yw4l">83</td>
    <td class="tg-yw4l">25</td>
    <td class="tg-yw4l">9525</td>
  </tr>
</table>

I will display the query and the output and later I will describe what each one of the applications does.

```terminal
grep -vE '.* [0]*[1-9][0-9]{4,}$' cars.txt
```
![alt text][figure_2]

Comparing with the initial table, one can see that the lines with the fifth column cell greater then 10000, have been removed.

We can have exactly the same output by using **awk** command which is a whole programming language particularly useful for dealing with inputs. 

```terminal
cat ./cars.txt | awk '{ if ($5 <= 10000) {print} }'
```

In this case, as mentioned before I used a conditional check on the fifth column **$5** to test whether the number was smaller than 10000, and only in that case the program print the whole line. The lines with more than 10000 are not printed and don’t come out on the standard output.



## Tip 3 -  Create a spell checker

Let's assume that we have a dictionary with correctly-spelled words like the one below. This dictionary consists of about 2 million lines, each containing a word(or a letter).    
![alt text][figure_3]    

We will use this dictionary to test how many mis-spelled words are included into a random text. For this particular excercise I have chosen an expcert from Shakespear. Below you may see the first lines.        
![alt text][figure_4]    

In order to check the spelling in each word, firstly we need to have both files in the same format and style. So let's first sort the dictionary alphabetically, convert each word in upper case and then save the result in a new file named *orderDict*     
```terminal
tr 'a-z' 'A-Z' < dict | sort -u > orderDict
```    
Then, we should tokenize each word of the *shakespear.txt* to the same format.

```terminal
grep -oi '[a-z]*' shakespear.txt | tr 'a-z' 'A-Z' | sort -u > words.txt
```
Now the *words.txt* and the *orderDict* look like this.    
![alt text][figure_5] ![alt text][figure_6]    

And finally we can test their similarity by querying the following.
```terminal
comm -23 words.txt orderDict | wc -l
```
The output is a single number of matching words. This particular document, produces **721** matches.

* The **-u** option of **sort** removes all the repeated lines after the sorting. 

* The **grep** command with the option **-o** prints only the matching pattern, while the **-i** option ignores cases.

* The **-23** options for the **comm** utility suppress the output of the second and of both files.
