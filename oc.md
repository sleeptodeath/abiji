

#### 继承

```
@Interface derive_class : base_class
```

#### NSLog打印BOOL

```
NSLog((ret? @"YES" : "NO"));
```

#### NSNumber

```
NSNumber *a = [[NSNumber alloc] initWithInt:x];
NSNumber *a = [NSNumber numberWithInt: x];
[a intValue];
```

#### NSString

```
NSString *str = @"hello world";  常量字符串,没创建对象

NSString *str = [NSString stringWithFormat:@"hello"];  类方法创建
NSString *str = [[NSString alloc] initWithFormat:@"world"]  实例方法

// 判断是否相等
 BOOL result = [str isEqualToString:str2];
hasPrefix
hasSuffix
    
// 写文件
NSError *errorl
BOOL result = [str writeToFile:@"\tmp\str.txt" atomically:YES encoding:NSUTF8StringEncoding error:&error]

// 读文件
NSString *result = [NSString stringWithContentsOfFile:@"data.txt" encoding:NSUTF8StringEncoding error:&error];

//转为数字
int a = 56;
NSString *strA = [NSString stringWithFormat:@"%d",a];
int b = [strA intvalue];


NSMutableString *tmp = [[NSMutableString alloc] init];
[tmp appendFormat:@"hello"]
```

NSArray

```
// 只能存对象,本质是int数组

//创建
NSArray *array = [NSArray array]; //空数组
NSArray *array = [NSArray arrayWithObjects:str1, str2, nill];
NSArray *array = [NSArray arrayWithArray:array1]; 


[array count];  //ld

NSMutableArray *mutableArray = [[NSMutableArray alloc] init];

addObject
insertObject: atIndex:
removeAllObjects;
removeObject;
sortUsingComparator;

// 遍历
for (id tmp in mutableArray) {
	NSLog(@"%@", tmp);
}
```



NSDictionary, NSMutableDictionary

```
//NSDictionary
//创建
NSDictionary *dict = [NSDictionary dictionary];
NSDictionary *dict = [NSDictionary dictionaryWithObject:@"18" forKey:@"CityID"];
NSDictionary *dict = [NSDictionary dictionaryWithObjectsAndKeys:@"18",@"CityID",@"广州",@"CityName",nil];

//创建
NSMutableDictionary *dict = [[NSMutalbeDictionary alloc] init];

[dict setObject:@"18" forKey:@"CityID"];

allKeys
allValues;
```



NSSet, NSMutableSet

```
//创建
NSSet *set = [NSSet set];
NSSet *set = [NSSet setWithObject:str];
NSSet *set = [NSSet setWithObjects:str1,str2, nil];

count
allObjects -> NSArray
anyObject
containsObject
isEqualToSet


// 
NSMutableSet *set = [[NSMutalbeSet alloc] init];
[set addObject:str1];


addObjectsFromArray
removeAll
unionSet

```



#### NSFileManager

```

//创建  单例
NSFileManager *filemanager = [NSFileManager defaultManager];
NSString *str = @"hello world";

// 判断存在不存在
BOOL res = [filemanager fileExistsAtPath:@"data.txt"];

fileExistsAtPath
isReadableFileAtPath
removeItemAtPath:  error:


```



#### 当前路径 

```
NSString *path = NSHomeDirectory();

```

#### 文件操作

```
// 判断内文件是否存在
NSFileManager *filemanager = [NSFileManager defaultManager];
if ([filemanager fileExistsAtPath:@"data.txt"]) {
	NSLog(@"文件存在");
	// 读文件
	NSDate *readData = [filemanager contentsAtPath:@"data.txt"];
	NSLog(@"readData = %@",readData);
	NSString *str = [[NSString alloc] initWithData:readData encoding:NSUTF8StringEncoding ]
	NSLog(@"str=%@",str);
} 
```



#### NSURL

```
//http://www.baidu.com
NSString *str = @"http://www.baidu.com";
NSURL *url = [NSURL URLWithString:str];
NSString *host = [url host];
NSString *port = [url port];
```

NSCoding  拷贝对象

```
Movie *m = [[Movie alloc]init];
// 写
BOOL ret = [NSKeyedArchiver archiveRootObject:m toFile:@"/tmp/m.txt"];
// 读
Movie *tmp = [NSKeyedUnarchiver unarchiveObjectWithFile:@"/tmp/m.txt"];



// 编码
-(void)encodeWithCoder:(NSCoder *)aCoder{
	[aCoder encodObject:self.name forKey:@"name"];
	[aCoder encodObject:self.author forKey:@"author"];
	[aCoder encodInt:self.price forKey:@"price"];
}

// 解码
-(id)initWithCoder:(NSCoder *)aDecoder {
	self = [super init];
	if (!self) {
		return nil;
	}
	// 根据key判断
	if ([aDecoder containsValueForKey:@"name"]) {
		self.name = [aDecoder decodeObjectForKey:@"name"];
	}
	if ([aDecoder containsValueForKey:@"author"]) {
		self.author = [aDecoder decodeObjectForKey:@"author"];
	}
	if ([aDecoder containsValueForKey:@"price"]) {
		self.price = [aDecoder decodeIntForKey:@"price"];
	}
}
```



#### Category

```
@interface Person (SayEnglish)

Person+SayEnglish.h   #import "Person.h"
Person+SayEnglish.m	  #import "Person+SayEnglish.h"

main.m中
#import "Person+SayEnglish.h"

```

#### 协议(相当于接口)

```
@interface Person <RepairComputerDelegate>


在RepairComputerDelegate.h

@protocol RepairComputerDelegate <NSObject>

@required
- (void)error;

@optional
- (void)other;
@end

```



```
OC没有垃圾回收机制
手动管理内存
arc机制,让编译器来管理内存的机制-静态的机制


[str2 retain]  // str2指向的内存空间计数器+1
[str2 release]  //保证retain和release次数相同

深拷贝-浪费空间
[str mutablecopy] // 返回可变对象,一定指向不同的独立的内存空间
NSMutalbeCopying

浅拷贝
[str copy]		// 返回不可变对象,如果str不可变,那么指向同一内存空间
NSCopying

#pragma mark
#progma mark NSCopying method
-(id)copyWithZone:(NSZone *)zone
{
	//1.创建对象
	Book *copyBook = [[Book allocWithZone:zone] init]
	//2.把当前对象的实例变量的值赋给他
	copyBook.name = self.name;
	copyBook.price = self.price; 
	return copyBook;
}

```





#### model对象层

```

```

