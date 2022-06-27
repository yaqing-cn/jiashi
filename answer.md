##### 1、深度合并dict

```
def dict_update(source_dict, update_dict):
    for key in update_dict:
        if key not in source_dict.keys():
            continue
        if isinstance(update_dict[key], dict) and isinstance(source_dict[key], dict):
            dict_update(source_dict[key], update_dict[key])
        else:
            source_dict[key] = update_dict[key]


source_dict = {'key0': 'a', 'key1': 'b', 'key2': {'inner_key0': 'c', 'inner_key1': 'd'}}
update_dict = {'key1': [1, 2, 3], 'key2': {'inner_key0': 'y', 'test': 123}}
dict_update(source_dict, update_dict)
print(source_dict)
```

##### 2、电话组合排列



```
def PhoneLetter(digits):
    if not digits:
        return []
    phone = {'2': ['a', 'b', 'c'],
             '3': ['d', 'e', 'f'],
             '4': ['g', 'h', 'i'],
             '5': ['j', 'k', 'l'],
             '6': ['m', 'n', 'o'],
             '7': ['p', 'q', 'r', 's'],
             '8': ['t', 'u', 'v'],
             '9': ['w', 'x', 'y', 'z']}

    def back(con, next_digit):
        if len(next_digit) == 0:
            res.append(con)
        else:
            for letter in phone[next_digit[0]]:
                back(con + letter, next_digit[1:])

    res = []
    back('', digits)
    return res


result = PhoneLetter('23')
print(result)
````

##### 3、内存泄漏

内存泄露是那些使用过后，应该被清理却没有被清理的内存一直占据着系统资源，通过长时间的累积导致系统崩溃

```
a = [1]
b = [2]
a.append(b)
b.append(a)
a和b之间存在循环引用,python的垃圾回收机制失效造成内存泄漏
```

