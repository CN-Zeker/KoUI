<!--
 * @Author: zhangke
 * @Date: 2025-11-13 16:07:50
 * @LastEditors: zhangke
 * @LastEditTime: 2025-11-13 16:32:02
 * @Description: .prettierrc.json 文档注释
-->
```json
{
  "$schema": "https://json.schemastore.org/prettierrc",
  "semi": true,                    // 使用分号结尾语句
  "singleQuote": false,            // 使用双引号而不是单引号
  "printWidth": 100,               // 每行最大字符数为100
  "tabWidth": 2,                   // 指定每个缩进级别的空格数
  "trailingComma": "es5",          // 在对象和数组的最后一项后添加逗号(兼容ES5)
  "arrowParens": "avoid",          // 箭头函数只有一个参数时省略括号
  "vueIndentScriptAndStyle": true, // 对Vue文件中的script和style标签进行缩进
  "overrides": [                   // 针对特定文件覆盖配置 将.prettierrc作为json文件解析
    {
      "files": ".prettierrc",      // 匹配.prettierrc文件
      "options": {
        "parser": "json"           // 使用json解析器处理
      }
    }
  ]
}
```