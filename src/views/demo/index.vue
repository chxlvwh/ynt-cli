<template lang="html">
    <div class="homepage">
        <div class="home-header">
            <h1>欢迎，现在时间是{{now}}</h1>
        </div>
    </div>
</template>

<script>
import date from "date-and-time";
import { clearInterval } from 'timers';

export default {
    data() {
        return {
            timer: null,
            nowDate: new Date()
        }
    },
    computed: {
        now() {
            return date.format(this.nowDate, 'YYYY-MM-DD HH:mm:ss')
        }
    },
    methods: {
    },
    created() {
        this.timer = setInterval(() => {
            this.nowDate = new Date()
        }, 1000);
    },
    beforeDestroy() {
        window.clearInterval(this.timer)
    }
}
</script>

<style lang="less">
.homepage {
    background:#F4F6F8!important;
    padding: 0!important;
    .home-header {
        margin-bottom: 20px;
        text-align: center;
        >span {
            font-size: 13px;
            line-height:1;
            color:rgba(169,174,181,1);
        }
        .ivu-tooltip-rel {
            font-size: 13px;
            color:rgba(169,174,181,1);
            .ivu-icon {
                vertical-align: baseline;
            }
        }
        .ivu-select {
            float: right;
            margin-top: -6px;
        }
    }
}
</style>
