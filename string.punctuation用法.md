# string.punctuation 用法

### 直接操作字符串，比如一句话，直接用split()，会把标点符号跟单词连在一起
```
>>> sentence
"Why the edits made under my username Hardcore Metallica Fan were reverted? They weren't vandalisms, just closure on some GAs after I voted at New York Dolls FAC. And please don't remove the template from the talk page since I'm retired now"
>>> sentence.split()
['Why', 'the', 'edits', 'made', 'under', 'my', 'username', 
'Hardcore', 'Metallica', 'Fan', 'were', 'reverted?', 'They', "weren't", 
'vandalisms,', 'just', 'closure', 'on', 'some', 'GAs', 'after', 'I', 'voted', 
'at', 'New', 'York', 'Dolls', 'FAC.', 'And', 'please', "don't", 'remove', 'the', 
'template', 'from', 'the', 'talk', 'page', 'since', "I'm", 'retired', 'now']
```
### 可以看到像是'reverted?'这样的，就被split()自动连接跟单词一起了
### 使用for循环，去掉标点符号
```
for i in sentence:
  if i in string.punctuation:
      sentence = sentence.replace(i," ")
>>> sentence
'Why the edits made under my username Hardcore Metallica Fan were reverted  They weren t vandalisms  just closure on some GAs after I voted at New York Dolls FAC  And please don t remove the template from the talk page since I m retired now'
>>> sentence.split()
['Why', 'the', 'edits', 'made', 'under', 'my', 'username', 'Hardcore', 'Metallica', 'Fan', 'were', 'reverted', 'They', 'weren', 't', 'vandalisms', 'just', 'closure', 'on', 'some', 'GAs', 'after', 'I', 'voted', 'at', 'New', 'York', 'Dolls', 'FAC', 'And', 'please', 'don', 't', 'remove', 'the', 'template', 'from', 'the', 'talk', 'page', 'since', 'I', 'm', 'retired', 'now']
```
### 可以看到，经过处理后，标点符号被去除了
