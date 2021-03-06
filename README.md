# AdvancedLangConv

Initially exported from code.google.com/p/advanced-langconv

## Summary
A Python based language converter, which was created primarily to replace the slow LanguageConverter functions of MediaWiki, and also can be adopted by other Chinese website.

We'll create a pure python converter and a C extended python converter both. The pure python can be used for situations without C extension support like GAE. It is slower than C extended version but still faster than PHP's strtr().

Then we can adpot the C extended version as a MediaWiki's extension. The communication between PHP and Python can be established by SOAP.

## 概要
基于Python实现的字词转换器，其实现的首要目的是替代MediaWiki中缓慢的LanguageConverter功能，同时亦能被其他中文网站采用。

我们会同步构造使用纯Python实现的转换器，以及使用C扩展Python实现的转换器。纯Python版本可用于不支持C扩展的场合，如GAE中。它虽然慢于C扩展的版本，但仍然快于PHP的strtr()函数。

然后我们会为C扩展的版本制作MediaWiki扩展。并采用SOAP来实现PHP和Python之间的通讯。

## Build

    python setup.py build # first we build it
    mv build/lib.linux-i686-2.6/langconv ./tests # then we move the converter.so/converter.dll to tests directory
    cd tests
    python test.py # you can test this script

## Usage
```python
import langconv
cvt = langconv.ConverterHandler("zh-hans") # valid variants are defined in settings.py
print cvt.convert_to('zh-hant', u'秒表表达') # output 秒錶表達
```

