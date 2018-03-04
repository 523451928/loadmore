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
        topDistance: 50,
        bottomDistance: 50,
        distanceIndex: 2,
        topPullText: '下拉刷新',
        topDropText: '释放更新',
        topLoadingText: '更新中...',
        bottomPullText: '上拉加载更多...',
        bottomDropText: '释放更新',
        bottomLoadingText: '更新中...',
        noMoreText: '没有更多了...',
        autoFill: true,
        scrollLoad: false,
        sideSlipDisabled: false,
        preLoadDistance: 50
        topMethod() {
            //todo
        },
        bottomMethod: function() {
           //todo
        }
})
```

| Option | Description |
| ----- | ----- |
| el | String or Element |
