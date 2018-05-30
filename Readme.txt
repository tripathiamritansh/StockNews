 
"Often I am very interested in the latest news of the stock market. I wish to have a tool which could give me the latest headlines 
for any stock easily.I thought terminal will be an interesting medium to make this working hence I wrote a script 
to fetch the latest news for any user provided stock and list the headlines from the json response provide by the API." 

Prerequisites:
1.	Linux 
2.	Terminal
3.	Internet Connection
4. Python 2.6+

API used: https://api.iextrading.com/1.0/stock/<Name of the stock>/news

Steps to run the script:
1.	Download the script from the Github repository
2.	Change the permission to run the script using following command in the terminal: chmod +x  ~/somefolder/stockNews. 
   This will allow any user to run this script.
3.	In order to run the script 
a.	cd ~/somefolder
b.	./stockNews <Name of the stock>
4.	If the Name of the stock is not correct it will give following error:  "Please check the company symbol"
5.	If the stock name is correct, it will list the latest headlines for that stock.

Commands used:
curl -s https://api.iextrading.com/1.0/stock/$1/news : Fetches data from the api
python -m json.tool : pretty prints the fetched data in the json format
grep "headline" : filters for all lines containing "headline" as text
awk '{gsub(/"headline":/,"")}1' : replaces '"headline":' with empty string
sed 's/$/  \\n/' : appends \n after the end of each line so that the echo output has each headline in separate line
grep -o "Unknown symbol" : filters for Unknown symbol text.
 wc -l: counts the number of occurrance of Unknown symbol text

Sample Input and Output

Input Command :  ./stockNews fbb
Output : Please check the company symbol

Input Command : ./stockNews fb
Output : 

Latest fb Headlines

"The 30+1 Portfolio: An Average Investor's Reasoning For Buying A Stock", 
 "France's Macron meeting with tech leaders May 23", 
 "Watch Mark Zuckerberg talk about privacy concerns in this 2010 interview", 
 "Mark Zuckerberg will meet with EU regulators as soon as next week", 
 "Personal email is dead - but I still can't quit it" 
 "Retirement Strategy: I Am Done Being Wrong About This Market", 
 "Fat Dividend Yields To Beef Up Your Portfolio In 2018", 
 "FANG Stocks Are Not Dead - Cramer's Mad Money (5/15/18)", 
 "Here's everything you can do with Whatsapp's new group chat features", 
 "George Soros' fund bought $35 million of Tesla bonds while loading up on Amazon, Netflix stock",
