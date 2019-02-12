## Message消息提示
- 默认调用方法. **this.$message**,可以接受一个字符串也可以接受一个VNode
`javascript
const h = this.$createElement;
        this.$message({
          message: h('p', null, [
            h('span', null, '内容可以是 '),
            h('i', { style: 'color: teal' }, 'VNode')
          ])
        });
`