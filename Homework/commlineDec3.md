#Command Line Exploratory Data Analysis of Chipotle Orders
*by Andrew Pederson, submitted December 3, 2015*

Chipotle.tsv contains 4623 records comprising the inidiviual items from 1834 orders.  Each row is a separate item purchased at the restaraunt, and the dataset contains 5 columns including the index: 

Variable Name | Content and Formatting
------------ | -------------
'order_id' | index of order numbers, ranging from 1-1834
'quantity' | single integer indicating how many of that item were purchased in that order number
'item_name' | name of the item as a character string
'choice_description' | list of ingredients as character strings, possibly incomplete, that also indicates salsa type 
'item_price' | 3 digit decimal integer with preceding dollar signs indicating the items unit cost. 'item_price' has 79 unique values 

```sh
cd ~/Google_Drive/GenAssemblyDataScience/DAT_SF_19/data
(head -5; tail -5) < chipotle.tsv
grep 'Steak Burrito' chipotle.tsv > steak.tsv
grep 'Chicken Burrito' chipotle.tsv > chick.tsv
awk '{s+=$2} END {print s}' steak.tsv
awk '{s+=$2} END {print s}' chicken.tsv 

grep 'Black Beans' chick.tsv > bbchick
wc -l bbchick
awk '{s+=$2} END {print s}' bbchick
grep 'Pinto Beans' chick.tsv | awk '{s+=$2} END {print s}'
grep '195' chipotle.tsv 
```

<p>These orders include 386 steak burritos and 591 chicken burritos, 307 with black beans and 108 with pinto.  Though black and pinto beans only account for a combined 415 (70%) of the 591, it is possible that some chicken burritos were made with a third kind of beans, and some manually reviewed burrito orders had no beans at all, for example order number 195.</p>

##Something Extra Fun about Burritos

```sh
awk -F '\t' '{print $5}' chipotle.tsv | sort | uniq -c | sort -nr > Chipprices.txt
wc -l Chipprices.txt
```

<p>The 79 unique item price values are surprising at first; does Chipotle really sell 79 SKUs at each location? The most likely explanation is that adding certain ingredients changes the base price of the burritos that account for the bulk of the items sold. Manually inspecting chicken burrito prices shows values from 8.49 to 17.50 - what ingredients are the greatest drivers of price variation? Which combinations of ingredients are the most common?</p>

<p>If we exlude counts under 100, 10-20 items seem to account for large portions of total purchases.  The most commonly purchased item costs $8.75 and accounted for about 15% (730) of the 4623 total items purchased. Since diving further into the price distribution from the command line seemed daunting, I avoided the impulse to load the data into R so that I could learn some new stuff about the command line, markdown, and what I hope will be a more efficient and productive workflow.</p>    


http://stackoverflow.com/questions/450799/shell-command-to-sum-integers-one-per-line

:neckbeard: Seriously, markdown?
 _____________
< WHOA NELLY! >
 -------------
        \   ^__^
         \  (oo)\_______
            (__)\       )\/\
                ||----w |
                ||     ||

```sh
cd MydataScienceToolbox/
vagrant ssh
servewd 2>/dev/null & 
< fashion.csv Rio -ge 'g + geom_freqpoly(aes(as.Date(date), color=type), '\ 'binwidth=7) + scale_x_date() + labs(x="date", title="Coverage of New York'\ ' Fashion Week in New York Times")' > ~/figures/output.png

echo 'I am just a cow, but this program is amusing' | cowsay
```
<p>As it turns out, R plots can be executed from the command line using Jeroen Janssens very helpful method: http://datascienceatthecommandline.com/#dst.  While there was not enough time in the weekend to create a fancy R plot for the Chipotle dataset, I am looking forward to working much more with the UNIX command line!</p>
