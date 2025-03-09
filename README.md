# English world list

- english word list, sorted by frequency
- subset of 2M word vector list from <https://fasttext.cc>

## Generation

```shell
curl https://dl.fbaipublicfiles.com/fasttext/vectors-english/crawl-300d-2M.vec.zip
unzip crawl-300d-2M.vec.zip
rg -o '^[a-z]+ ' crawl-300d-2M.vec | sd ' +$' '' > vectors.csv
curl https://raw.githubusercontent.com/dwyl/english-words/master/words_alpha.txt > words_alpha.csv
qsv join -n 1 vectors.csv 1 words_alpha.csv | qsv select 1 > words.csv
```

