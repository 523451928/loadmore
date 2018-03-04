# loadmore
原生js写的移动端下拉更新,上拉加载更多的类

##查看demo
```
git clone https://github.com/523451928/loadmore.git
cd loadmore
npm install
npm run dev
```

##loadmore使用方法
```
import Loadmore from '../scripts/loadmore.js'

let loadmoreInstance = new Loadmore({
     el: document.querySelector('.loadmore-content'),
     crollLoad: false,
     topMethod() {
         setTimeout(() => {
                  loadmoreInstance.onTopLoaded()
         }, 1000)
     },
     bottomMethod: function() {
           self.getDataList()
     }
})
```
