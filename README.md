import requests
from bs4 import BeautifulSoup
res = requests.get('http://news.sina.com.cn/china/')#获取目标网页
res.encoding = 'utf-8'#抓取网页出现乱码
#print(res.text)
soup = BeautifulSoup(res.text,'html.parser')#爬取网页
for news in soup.select('.news-item'): 
    if len(news.select('h2')) > 0:
        time = news.select('.time')[0].text#新闻发布时间
        h2 = news.select('h2')[0].text #新闻发布的标题
        a = news.select('a')[0]['href']#新闻链接
        print(time+"\t\t",h2+"\t",a)
