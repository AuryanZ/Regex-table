# Regex-table

## 常用正则符号参考
| 符号      | 意义          | 示例        | 匹配                |
| ------- | ----------- | --------- | ----------------- |
| `.`     | 任意字符（除换行）   | `a.c`     | `abc`, `axc`      |
| `\d`    | 数字 `[0-9]`  | `\d+`     | `123`             |
| `\w`    | 字母、数字或下划线   | `\w+`     | `abc_1`           |
| `\s`    | 空格或制表符      | `\s+`     | `"  "`            |
| `^`     | 字符串开头       | `^abc`    | `abc123`          |
| `$`     | 字符串结尾       | `abc$`    | `123abc`          |
| `*`     | 0 次或多次      | `go*gle`  | `ggle`, `google`  |
| `+`     | 1 次或多次      | `go+gle`  | `google`          |
| `?`     | 0 或 1 次     | `colou?r` | `color`, `colour` |
| `[]`    | 匹配集合内任意一个字符 | `[abc]`   | `a`, `b`, `c`     |
| `[^]`   | 匹配集合外的字符    | `[^0-9]`  | 非数字               |
| `()`    | 捕获组         | `(abc)+`  | `abcabc`          |
| `{n,m}` | 重复 n~m 次    | `\d{2,4}` | 2~4 位数字           |

## C# 正则表达式速查表 (Cheat Sheet)
```
using System.Text.RegularExpressions;

// 🔍 基本匹配
Regex.IsMatch("abc123", @"\d+")          // 是否包含数字
Regex.Match("abc123", @"\d+")            // 返回第一个匹配结果
Regex.Matches("a1b2c3", @"\d+")          // 返回所有数字
Regex.Replace("abc:123", @":.*", "")     // 删除冒号及其后的内容
Regex.Split("a,b;c|d", @"[;,\|]")        // 用分号、逗号或竖线分割

// 🧹 替换示例
string input = "abc:aaa:bbb:ccc";
string result = Regex.Replace(input, @"^[^:]*:", ""); // 删除第一个冒号及之前 → "aaa:bbb:ccc"

// 🧾 提取示例
string text = "Order #1234 shipped on 2025-10-20";
var orderId = Regex.Match(text, @"#(\d+)").Groups[1].Value;  // "1234"
var date = Regex.Match(text, @"\d{4}-\d{2}-\d{2}").Value;    // "2025-10-20"

// ✅ 验证示例
Regex.IsMatch("abc@test.co.nz", @"^[\w.-]+@[\w.-]+\.\w+$")   // 邮箱格式检查
Regex.IsMatch("192.168.0.1", @"^(\d{1,3}\.){3}\d{1,3}$")     // IPv4 地址
Regex.IsMatch("Password123!", @"^(?=.*[A-Z])(?=.*\d).{8,}$") // 至少8位含大写字母和数字

// 🔢 捕获组
string nameText = "Name: Rui, Age: 30";
var match = Regex.Match(nameText, @"Name:\s*(\w+),\s*Age:\s*(\d+)");
string name = match.Groups[1].Value; // "Rui"
string age = match.Groups[2].Value;  // "30"

```
