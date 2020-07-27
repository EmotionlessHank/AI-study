vectorizer = CountVectorizer() #构建一个计算词频（TF）的玩意儿，当然这里面不足是可以做这些

transformer = TfidfTransformer() #构建一个计算TF-IDF的玩意儿

tfidf = transformer.fit_transform(vectorizer.fit_transform(corpus))

#vectorizer.fit_transform(corpus)将文本corpus输入，得到词频矩阵

#将这个矩阵作为输入，用transformer.fit_transform(词频矩阵)得到TF-IDF权重矩阵



TfidfTransformer + CountVectorizer  =  TfidfVectorizer



值得注意的是，CountVectorizer()和TfidfVectorizer()里面都有一个成员叫做vocabulary_（后面带一个下划线）

这个成员的意义是词典索引，对应的是TF-IDF权重矩阵的列，只不过一个是私有成员，一个是外部输入，原则上应该保持一致。



vectorizer = TfidfVectorizer(stop_words=stpwrdlst, sublinear_tf = True, max_df = 0.5)



关于参数：

input：string{'filename', 'file', 'content'}

    如果是'filename'，序列作为参数传递给拟合器，预计为文件名列表，这需要读取原始内容进行分析

    如果是'file'，序列项目必须有一个”read“的方法（类似文件的对象），被调用作为获取内存中的字节数

    否则，输入预计为序列串，或字节数据项都预计可直接进行分析。

encoding：string， ‘utf-8’by default

    如果给出要解析的字节或文件，此编码将用于解码

decode_error: {'strict', 'ignore', 'replace'}

    如果一个给出的字节序列包含的字符不是给定的编码，指示应该如何去做。默认情况下，它是'strict'，这意味着的UnicodeDecodeError将提高，其他值是'ignore'和'replace'

strip_accents: {'ascii', 'unicode', None}

    在预处理步骤中去除编码规则(accents)，”ASCII码“是一种快速的方法，仅适用于有一个直接的ASCII字符映射，"unicode"是一个稍慢一些的方法，None（默认）什么都不做

analyzer：string，{'word', 'char'} or callable

    定义特征为词（word）或n-gram字符，如果传递给它的调用被用于抽取未处理输入源文件的特征序列

preprocessor：callable or None（default）

    当保留令牌和”n-gram“生成步骤时，覆盖预处理（字符串变换）的阶段

tokenizer：callable or None(default)

    当保留预处理和n-gram生成步骤时，覆盖字符串令牌步骤

ngram_range: tuple(min_n, max_n)

    要提取的n-gram的n-values的下限和上限范围，在min_n <= n <= max_n区间的n的全部值

stop_words：string {'english'}, list, or None(default)

    如果未english，用于英语内建的停用词列表

    如果未list，该列表被假定为包含停用词，列表中的所有词都将从令牌中删除

    如果None，不使用停用词。max_df可以被设置为范围[0.7, 1.0)的值，基于内部预料词频来自动检测和过滤停用词

lowercase：boolean， default True

    在令牌标记前转换所有的字符为小写

token_pattern：string

    正则表达式显示了”token“的构成，仅当analyzer == ‘word’时才被使用。两个或多个字母数字字符的正则表达式（标点符号完全被忽略，始终被视为一个标记分隔符）。

max_df： float in range [0.0, 1.0] or int, optional, 1.0 by default

    当构建词汇表时，严格忽略高于给出阈值的文档频率的词条，语料指定的停用词。如果是浮点值，该参数代表文档的比例，整型绝对计数值，如果词汇表不为None，此参数被忽略。

min_df：float in range [0.0, 1.0] or int, optional, 1.0 by default

当构建词汇表时，严格忽略低于给出阈值的文档频率的词条，语料指定的停用词。如果是浮点值，该参数代表文档的比例，整型绝对计数值，如果词汇表不为None，此参数被忽略。

max_features： optional， None by default

    如果不为None，构建一个词汇表，仅考虑max_features--按语料词频排序，如果词汇表不为None，这个参数被忽略

vocabulary：Mapping or iterable， optional

    也是一个映射（Map）（例如，字典），其中键是词条而值是在特征矩阵中索引，或词条中的迭代器。如果没有给出，词汇表被确定来自输入文件。在映射中索引不能有重复，并且不能在0到最大索引值之间有间断。

binary：boolean， False by default

    如果未True，所有非零计数被设置为1，这对于离散概率模型是有用的，建立二元事件模型，而不是整型计数

dtype：type， optional

    通过fit_transform()或transform()返回矩阵的类型

norm：'l1', 'l2', or None,optional

    范数用于标准化词条向量。None为不归一化

use_idf：boolean， optional

    启动inverse-document-frequency重新计算权重

smooth_idf：boolean，optional

    通过加1到文档频率平滑idf权重，为防止除零，加入一个额外的文档

sublinear_tf：boolean， optional

    应用线性缩放TF，例如，使用1+log(tf)覆盖tf
————————————————
原文链接：https://blog.csdn.net/laobai1015/java/article/details/80451371
