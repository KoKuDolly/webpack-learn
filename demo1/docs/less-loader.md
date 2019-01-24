1. 为什么extracting style sheets?
绑定css到webpack有几点优势，比如引用图片和字体的时候可以附加hash的urls表示，以及热模块替换的使用。但是，再生产中，样式依赖于js运行不是个好主意，渲染很有可能延迟甚至FOUC(flash of unstyled content)。所以，build中最好把sheets 从bundle中抽离出来。
抽离的方法有两种：
extract-loader,简单，但是再css-loader的输出中比较专业的。
extract-text-webpack-plugin，更复杂，但是在所有的使用例子中通用。