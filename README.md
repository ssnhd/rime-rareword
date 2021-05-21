# Rime 鼠须管输入法删除字体不一的生僻字

macOS 本身不包含一些生僻字，安装花园明朝字体后生僻字可显示，但是字体无法统一，因此，这些不常用的生僻字我们将它删除。

例如：𫔭、𧹒、𫔮、𢧐、𫄙

![](https://tvax3.sinaimg.cn/large/008eZBHKgy1gqq4svx6fkj31aq04swem.jpg)

打开【TSCharacters.txt】删除里面字体不一的生僻字（默认已删除，可能存在个别被忽略）。

![](https://tva4.sinaimg.cn/large/008eZBHKgy1gqq4sw2e36j31aq0d2mx8.jpg)

前往 `/Library/Input Methods/Squirrel/Contents/SharedSupport/opencc/ `，将【TSCharacters.txt】放进【opencc】文件夹内。

![](https://tva3.sinaimg.cn/large/008eZBHKgy1gqq54zovhuj31aq0cegmm.jpg)

打开【t2s.json】修改为下面代码，保存并重新部署。

> 注：【t2s.json】需打开读写权限方可修改。

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