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
        scrollLoad: false,
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
## API
| Option | Description | Type | Default |
| ----- | ----- | ----- | ----- |
| el | 需要监听滚动的包裹dom元素 | String or DOM | |
| scrollLoad | 是否滚动加载更多 | Boolean | false |
| topDistance | 触发 topMethod 的下拉距离阈值（像素) | Number | 50 |
| bottomDistance | 触发 bottomMethod 的下拉距离阈值（像素) | Number | 50 |
| distanceIndex | 手指移动与包裹容器移动距离的比值 | Number | 2 |
| topPullText | topStatus 为 pull 时加载提示区域的文字 | String | '下拉刷新' |
| topDropText | topStatus 为 drop 时加载提示区域的文字 | String | '释放更新' |
| topLoadingText | topStatus 为 loading 时加载提示区域的文字 | String | '更新中...' |
| bottomPullText | bottomStatus 为 pull 时加载提示区域的文字 | String | '上拉加载更多...' |
| bottomDropText | bottomStatus 为 drop 时加载提示区域的文字 | String | '释放更新' |
| bottomLoadingText | bottomStatus 为 loading 时加载提示区域的文字 | String | '更新中...' |
| bottomLoadingText | bottomStatus 为 loading 时加载提示区域的文字 | String | '更新中...' |
| noMoreText | 全部加载完毕提示区域的文字 | String | '没有更多了...' |
| autoFill | 是否自动加载至充满其容器 | Boolean | false |
| sideSlipDisabled | 是否禁止当手指滑动为左右方向的时候容器上下滑动 | Boolean | false |
| preLoadDistance | 当scrollLoad 为 true时 距离底部预加载的距离(像素) | Number | 50 |
| topMethod | 下拉刷新执行的方法 | Function | |
| bottomMethod | 上拉加载更多执行的方法 | Function | |

## 注意事项
* Loadmore实例化后会返回Loadmore 对象(loadmoreInstance) 
* loadmoreInstance.trigger('changeBottomStatus', 'loading') 可以改变上拉的bottomStatus 避免多次调用bottomMethod
* 注意 top-method方法执行后要重置(loadmoreInstance.onTopLoaded()) bottom-method 方法执行后要重置(loadmoreInstance.onBottomLoaded()) 

## 可以使用loadmoreInstance实例的方法
| Function | Description |
| ----- | ----- |
| destroy | 所有数据加载完之后调用该方法 该方法可以禁用上拉 |
| refresh | 重置Loadmore |
| trigger | 触发绑定在Loadmore实例上的自定事件 |
