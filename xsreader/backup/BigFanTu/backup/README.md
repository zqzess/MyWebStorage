### 新版分类教程

1. 分类快速获取网站： https://bigfantu.gitee.io/xsread/

2. 在线正则网站 ： https://tool.chinaz.com/regex

3. moreKeys模板：https://github.com/Fantuan-cell/XsRead/blob/main/backup/moreKeys.json

4. JSON编辑器：https://github.com/Fantuan-cell/XsRead/blob/main/backup/JSONedit.7z

 5. 影视音频源 正文嗅探模板 ：https://github.com/Fantuan-cell/XsRead/blob/main/backup/%E9%9F%B3%E9%A2%91%E8%A7%86%E9%A2%91%E6%BA%90%E6%AD%A3%E6%96%87%E5%97%85%E6%8E%A2%E6%95%99%E7%A8%8B.xbs

    

```
音乐源正文嗅探代码:
@js:
let pat=".*(m3u8|mp4)$"

return {'url':result,'httpHeaders':config.httpHeaders, 'webView':true,'sourceRegex':pat};

视频源正文嗅探代码:
@js:
let pat= ".*\\.(m3u8|mp4).*";
return {'url':result,'httpHeaders':config.httpHeaders, 'webView':true,'sourceRegex':pat};


```



```
影视源列表匹配 手动js解析代码:

function functionName(config, params, result) {
	
    let ts = result.updateTime.split("\n"); //对updateTime获取的数据进行分割为数组
    
    let list = [];
    
    for (let i = 0; i < ts.length; i++) {
        if ("url" in result["list"][i]) {
            let title = result["list"][i]["title"];
            let titles = title.split("\n");
            let urls = result["list"][i]["url"].split("\n");
            for (let j = 0; j < titles.length; j++) {
                list.push({
                    "title": ts[i] + "-" + titles[j],
                    "url": urls[j]
                })
            }
        }
    }
    return {

        "list": list
    };
}

```



