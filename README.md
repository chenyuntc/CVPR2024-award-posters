# posters for all CVPR2024 Award papers (Highlight+Oral)

## script used to download
```python
import requests
from bs4 import BeautifulSoup

url = 'https://cvpr.thecvf.com/virtual/2024/awards_detail'
response = requests.get(url)
soup = BeautifulSoup(response.text, "html.parser")

id2title = dict() 
for link in soup.find_all('a'):
    if link.get('href').startswith('/virtual/2024/poster/'):
        paper_id = (link.get('href').split('/')[-1])
        id2title[paper_id] = link.get_text()


for paper_id, title in id2title.items():
    url = f"https://cvpr.thecvf.com/media/PosterPDFs/CVPR%202024/{paper_id}.png"
    title = title.replace(' ','_').replace(':','-').replace('\\','').replace('/','')
    save_path = f"{paper_id}_{title}_poster.png"
    get_ipython().system('wget $url -O $save_path')
```


# [Poster for CVPR 2023 Award Papers](https://github.com/chenyuntc/CVPR2023-highlight-posters)



