# postman 读写环境变量方式
//参考：https://testerhome.com/topics/6555
#在线验证tv4在线生成器https://jsonschema.net/#/editor
let json = JSON.parse(responseBody);  // responseBody是包含整个返回内容的字符串

// 提取某字段的值：
let foobar = json.foo.bar[0].foobar;  // 假设结构为 {"foo": {"bar": [{"foobar": 1}, {"baz": 2}]}}
//通用的代码块记录
// 想用在自动化测试可以多写点：返回不是json报错
//'use strict';会在用到这些变量的地方出警告提示--慎用
//以下为亲测有用输出跑的次数及输入变量输出变量
'use strict';
let json;
try {
  json = JSON.parse(responseBody);
} catch (err) {
  tests['Expect response body to be valid JSON'] = false;
  tests[`Response body: ${responseBody}`] = true;
  console.error(err);
}
tests[`[INFO] Request params: ${JSON.stringify(request.data)}`] = true;  // 显示所有请求参数（在自动化测试里很有用）
tests[`跑第${iteration }次`] = true;  // 用在runner里循环很多次时


／／调试说明
Type chrome://flags inside your Chrome URL window
"inspect element".or tag ／chrome://inspect/#apps
