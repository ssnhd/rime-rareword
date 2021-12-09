# Rime 鼠须管输入法删除生僻字（候选词字体不一样）

macOS 本身不包含一些生僻字，安装花园明朝字体后生僻字可显示，但是字体无法统一，因此，这些不常用的生僻字我们将它删除。

例如：𫔭、𧹒、𫔮、𢧐、𫄙

![](https://tvax3.sinaimg.cn/large/008eZBHKgy1gqq4svx6fkj31aq04swem.jpg)

---

1. 打开【TSCharacters.txt】删除里面字体不一的生僻字（默认已删除，可能存在个别被忽略）。

![](https://tva4.sinaimg.cn/large/008eZBHKgy1gqq4sw2e36j31aq0d2mx8.jpg)

---

2. 前往 `/Library/Input Methods/Squirrel/Contents/SharedSupport/opencc/ `，将【TSCharacters.txt】放进去。

![](https://tva3.sinaimg.cn/large/008eZBHKgy1gqq54zovhuj31aq0cegmm.jpg)

---

3. 打开【t2s.json】将最后两行代码修改为 `type": "text` 和 `file": "TSCharacters.txt`，保存并重新部署。

    > 注：`t2s.json` 打开读与写权限：选中文件，按 `Command + i`，解开小黄锁修改权限。

```
{
  "name": "Traditional Chinese to Simplified Chinese",
  "segmentation": {
    "type": "mmseg",
    "dict": {
      "type": "ocd2",
      "file": "TSPhrases.ocd2"
    }
  },
  "conversion_chain": [{
    "dict": {
      "type": "group",
      "dicts": [{
        "type": "ocd2",
        "file": "TSPhrases.ocd2"
      }, {
        "type": "text",
        "file": "TSCharacters.txt"
      }]
    }
  }]
}
```

---

延伸：[Rime 鼠须管（Squirrel）朙月拼音、小鹤双拼、自然码双拼配置详解](https://github.com/huatliu/rime)
