#一、数据格式转换
+ **更改数据输出格式**
```
events2['thour']=map(lambda x: '%02.f:00-%02.f:59 ' % (x,x),events1.thour)
```
+ **小数按照百分比输出**
```
print '%.2f %%'%(count_prop[0]*100)
```

#二、列表操作
+ **list.index(value)返回的是等于value的第一索引值**
+ **取值**
```
size=[2,3,4]
print size[:-2] ##输出2。表示输出从开始到倒数位置为2之间的所有数。最后一个数位置为0。
```
+ **两列表一对一组合**
```
x=zip(size[1:],size[:-1])
print x
```
+ **指定位置插入元素**
```
list.insert(index, obj)
```
+ **判断列表所有元素满足一个条件时，返回TRUE**
```
zz1=all(re.search(r'^\S[\s\S]*', y) for y in zz)
```
+ **map：可对列表中的每一个元素应用函数**
```
idx=map(lambda x:x+1,idx)
```
+ **两列表应用函数**
```
for (v,k) in zip(x,y):
    x=''.join([v,k])
    z.append(x)
```
+ **判断是否含有某个元素**
```
print None in m
```
+ **去掉某个特定值**
```
y.remove('其他')
```
+ **列表元素替换**
```
out_list=[m1[0] if v==m[0] else v for v in out_list]
```
+ **对列表中多个值的替换**
```
m=['归属于母公司股东的综合收益总额','归属于母公司股东的净利润','归属于母公司股东的其他综合收益的税后净额']
m1=['归属于母公司所有者的综合收益总额','归属于母公司所有者的净利润','归属于母公司所有者的其他综合收益的税后净额']
out_list=[m1[m.index(v)] if v in m else v for v in out_list]
```




#二、数据框操作
+ **查看数据框前几行**
```
print phone.head(n=10)
```
+ **在已有dataframe中添加新列**
```
x1.loc[:,'group']=np.nan
```
+ **不同dataframe的行合并rbind**
```
pd.concat([x,x1],ignore_index=True)
```
+ **取dataframe中的前指定行或是指定列**
```
x1=gender_age_test.ix[0:5,].copy(deep=True)
```
+ **返回数据框dataframe的维度**
```
print train_test.shape
```
+ **判断dataframe中某些特征是否重复**
```
x1=x.duplicated(['device_id'])
```
+ **去除dataframe中重复行**
```
x1=x.drop_duplicates()
```
+ **返回Series满足特定条件时的索引**
```
x1[x1==True].index[0:10]
```
+ **求交集、并集**。。
```
print len(set(x).intersection(set(x1)))
print len(set(x).union(set(x1)))
print len(set(x).difference(set(x1)))
```
+ **集合转成列表**
```
list()
```
+ 查看方法的帮助文档：
```
x=train_phone.phone_brand.value_counts()
print help(pd.value_counts)
```
+ **数组和Series转换**
```
x2=np.array(x1)
x3=pd.Series(np.cumsum(x2),index=x.index)
```
+ **数据框dataframe满足条件的某些行**
```
print train_phone1[train_phone1.gender=='M']
xiaomi=train_phone1[train_phone1.phone_brand.isin(name)]
```
+ **数据框dataframe替换某些列的值**
```
train_phone1.ix[train_phone1.phone_brand.isin(name)==False,'phone_brand']='Others'
```
+ **数据框dataframe求行和**
```
data.sum(axis = 1)
```
+ **数据框dataframe求行比例**
```
x= data.div(data.sum(axis = 1), axis = 0)
```
+ **使用方法时，返回None，因为方法不能赋值**
```
name1.append("Others")
```
+ **数据框纵向合并**
```
train.append(test,ignore_index=True)
```
+ **修改数据框列名**
```
df_test.rename(columns={'index':'device_id'},inplace=True)
```
+ **数据框输出**
```
import sys
reload(sys)
sys.setdefaultencoding('utf8')
table_list.to_excel('E:\\pythonWorkSpace\\financial report\\hhh.xlsx', sheet_name='Sheet1',index=False,encoding='utf-8')
```
+ **数据框增加一行series**
```
df.loc['df']=series
df_table.loc[i]=list_1
```
```
one_table_df=pd.DataFrame(columns=titles)
one_table_df = one_table_df.append(one_series,ignore_index=True)
print one_table_df
```



#三、Series操作
+ **判断某个Series是否在另一个Series中**
```
test.ix[:,'device_id'].isin(events.ix[:,'device_id'])
```
+ **合并两个series，形成dataframe**
```
pd.concat([s1, s2], axis=1)
```
+ **
+ **增加元素**
```
Series.set_value('公司',5)
```
+ **series增加元素时，如果之前没有元素，则text会变成float格式**
```
one_series['起始日期'] = qsrq_dict[gglb_dict_sub[x_term]]
```


#四、图表制作
+ **画条形图**
```
p=train_phone.group.value_counts().sort_index().plot(kind='bar',figsize=(15,6),rot=0)
_=p.set_xlabel('Group'),p.set_ylabel('Count')
plt.show()
```
+ **改变x轴刻度、旋转（倾斜）刻度、改变刻度字体大小**
```
plt.xticks([1, 2, 3], ['mon', 'tue', 'wed'],rotation=45)
plt.xticks(rotation=45,fontsize=7.5)
```

#五、其它
+ **读写文件，并设置encoding**
```
f = open('test', 'w')
f.write(foo.encode('utf8'))
f.close()
```
```
np.savetxt(r'test.txt',train_IsInvalid_df, fmt='%s\t%s\t%s')
```

+ **读取某个文件夹所有的文件名**
```
import glob
path =r'E:\pythonWorkSpace\xiaolongren\data_to_parse'
filenames = glob.glob(path+'\*')
```
遇到编码问题
```
path =r'E:\pythonWorkSpace\financial report\samples\try'
filenames = glob.glob(path+'\*'+'.xml')
print filenames[0].decode('gbk').encode('utf-8')
```

+ **\_future\_模块**
这个模块可以导入python更高级版本的函数~~可以用2.x版本的python去测试高级一点版本的3.x版本的python。
+ **构造类**
```
#类定义  
    class people:  
        #定义基本属性  
        name = ''  
        age = 0  
        #定义私有属性,私有属性在类外部无法直接进行访问  
        __weight = 0  
        #定义构造方法  
        def __init__(self,n,a,w):  
            self.name = n  
            self.age = a  
            self.__weight = w  
        def speak(self):  
            print("%s is speaking: I am %d years old" %(self.name,self.age))  

      
    p = people('tom',10,30)  
    p.speak()
```
+ **编码问题encoding**
https://docs.python.org/3/howto/unicode.html
http://stackoverflow.com/questions/222386/what-do-i-need-to-know-about-unicode 
    + 将以unicode编码的中文字符串进行转码
```
list3 = unicode(lines2[0], 'unicode-escape') 
```
+ **取pdf某些页面**
```
from pyPdf import PdfFileWriter, PdfFileReader

output = PdfFileWriter()
input1 = PdfFileReader(file("600639_2015_n.pdf", "rb"))

# print the title of document1.pdf
print "title = %s" % (input1.getDocumentInfo().title)

# add page 1 from input1 to output document, unchanged
output.addPage(input1.getPage(50))

# add page 2 from input1, but rotated clockwise 90 degrees
output.addPage(input1.getPage(1).rotateClockwise(90))

# add page 3 from input1, rotated the other way:
output.addPage(input1.getPage(2).rotateCounterClockwise(90))
# alt: output.addPage(input1.getPage(2).rotateClockwise(270))

# add page 4 from input1, but first add a watermark from another pdf:
page4 = input1.getPage(3)
watermark = PdfFileReader(file("600876_2015_n.pdf", "rb"))
page4.mergePage(watermark.getPage(0))

# add page 5 from input1, but crop it to half size:
page5 = input1.getPage(4)
page5.mediaBox.upperRight = (
    page5.mediaBox.getUpperRight_x() / 2,
    page5.mediaBox.getUpperRight_y() / 2
)
output.addPage(page5)

# print how many pages input1 has:
print "document1.pdf has %s pages." % input1.getNumPages()

# finally, write "output" to document-output.pdf
outputStream = file("document-output.pdf", "wb")
output.write(outputStream)
outputStream.close()
```
+ **定义函数时，里面用到的变量都得事先定义，如x=(),list_text=[]**
+ **调用另外一个.py文件的函数**
```
from function import *
```
+ **读取根目录下所有的txt文件**
```
path =r'E:\pythonWorkSpace\financial report\samples\sh'
filenames = glob.glob(path+'\*'+'.txt')
```
+ **使用BeautifulSoup 解析中文乱码**
```
soup = BeautifulSoup(email_id_example,from_encoding='utf8')
```

+ **忽略警告**
```
import warnings
warnings.filterwarnings("ignore")
```
+ **打开中文文件名的文件乱码**
```
a='E:\\pythonWorkSpace\\financial report\\samples\\try\\GQY视讯：2015年年度报告.xml'
f = open(a.decode('utf8'))
print f.read()
```
+ **查找对象所有的属性和方法*
```
print dir(soup)
```

+ **读取指定行**
```
fp = open(r'E:\pythonWorkSpace\wangyiPosTrain_1.txt')
for i, line in enumerate(fp):
    if i <=1000:
        print line
fp.close()
```



+ **路径处理**
路径拆分
```
style_prefix,_ = os.path.splitext(os.path.basename('you.jpg'))
```
```
dataset=r'chainer-fast-neuralstyle-master\sample_images'
fs = os.listdir(dataset) # 查看路径下所有的文件
imagepaths = []
for fn in fs:
    base, ext = os.path.splitext(fn)#路径拆分
    if ext == '.jpg' or ext == '.png':
        imagepath = os.path.join(dataset,fn)#连接路径名
        imagepaths.append(imagepath)
```



