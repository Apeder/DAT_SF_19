#Command Line Burrito homework
*by Andrew Pederson, submitted December 3, 2015*

<p>Chipotle.tsv contains 4623 records comprising the inidiviual items from 1834 orders.  Each row is a separate item purchased at the restaraunt, and The dataset contains 5 columns including the index 

1. 'order_id' is an index of order numbers, ranging from 1-1834
2. 'quantity', is a single integer indicating how many of that item were purchased in that order number 
3. 'item_name', is the name of the item as a character string
4. 'choice_description' is a list of ingredients as character strings, possibly incomplete, that also indicates salsa type 
5. 'item_price' is a 3 digit decimal integer with preceding dollar signs indicating the items unit cost. 'item_price' has 79 unique values 
</p> 

'''
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
'''

<p>These orders include 386 steak burritos and 591 chicken burritos, 307 with black beans and 108 with pinto.  though black and pinto beans only account for a combined 415 (70%) of the 591, it is possible that some chicken burritos were made with a third kind of beans, and some manually reviewed burrito orders had no beans at all, for example order number 195.</p>

##Something Extra Fun about Burritos

'''
awk -F '\t' '{print $5}' chipotle.tsv | sort | uniq -c | sort -nr > Chipprices.txt
wc -l Chipprices.txt
'''

<p>The 79 unique item price values are surprising at first; does Chipotle really sell 79 SKUs at each location? The most likely explanation is that adding certain ingredients changes the base price of the burritos that account for the bulk of the items sold. Manually inspecting chicken burrito prices shows values from 8.49 to 17.50 - what ingredients are the greatest drivers of price variation? Which combinations of ingredients are the most common?</p>


 <p>If we exlude counts under 100, 10-20 items seem to account for large portions of total purchases.  The most commonly purchased item costs $8.75 and accounted for about 15% (730) of the 4623 total items purchased. Since diving further into the price distribution from the command line seemed daunting, I avoided the impulse to load the data into R so that I could learn some new stuff about the command line, markdown, and what I hope will be a more efficient and productive workflow to wow my clients with stuff that will make Tableau and Excel look like absolute crap.</p>    


http://stackoverflow.com/questions/450799/shell-command-to-sum-integers-one-per-line


