<template>
    <div class="loadmore-wrapper">
        <div class="loadmore-content">
            <ul>
                <li v-for="item in dataList">{{item}}</li>
            </ul>
        </div>
    </div>
</template>

<script>
    import Loadmore from '../scripts/loadmore.js'
    export default {
        data() {
            return {
                dataList: []
            }
        },
        mounted() {
            let self = this
            let loadmoreInstance = new Loadmore({
                el: document.querySelector('.loadmore-content'),
                scrollLoad: false,
                topMethod() {
                    setTimeout(() => {
                        loadmoreInstance.onTopLoaded()
                    }, 1000)
                },
                bottomMethod: function() {
                    self.getDataList()
                }
            })
            this.loadmoreInstance = loadmoreInstance
            loadmoreInstance.on('translate', (distance) => {
                // console.log(distance)
            })
        },
        methods: {
            getDataList() {
                this.loadmoreInstance.trigger('changeBottomStatus', 'loading')
                setTimeout(() => {
                    let num = 10
                    let length = this.dataList.length
                    for (let i = length; i<length + 10; i++) {
                        this.dataList.push(i)
                    }
                    this.loadmoreInstance.trigger('changeBottomStatus', 'pull')
                    this.$nextTick(() => {
                        this.loadmoreInstance.onBottomLoaded()
                    })
                    if (length > 50) {
                        this.loadmoreInstance.destroy()
                    }
                }, 500)
            }
        }
    }
</script>
<style>
html,body{
    height:100%;
}
body{
    overflow: hidden;
}
ul,li{
    margin:0;
    padding:0;
}
li{
    list-style: none;
    line-height: 50px;
    text-align: center;
}
.loadmore-wrapper{
    overflow: hidden;
}
.wa-loadmore-top {
  margin-top: -50px;
  line-height: 50px;
  text-align: center;
}
.wa-loadmore-bottom {
  margin-bottom: -50px;
  line-height: 50px;
  text-align: center;
}
.wa-nomore-text{
  line-height: 50px;
  text-align: center;
}
</style>