<template>
    <!--楼层-->
    <div class="floor">
        <div class="py-container">
            <div class="title clearfix">
                <h3 class="fl">{{ floor.name }}</h3>
                <div class="fr">
                    <ul class="nav-tabs clearfix">
                        <li class="active" v-for="(nav, index) in floor.navList" :key="index">
                            <a href="#tab1" data-toggle="tab">{{ nav.text }}</a>
                        </li>
                        <!-- <li>
                            <a href="#tab2" data-toggle="tab">大家电</a>
                        </li>
                        <li>
                            <a href="#tab3" data-toggle="tab">生活电器</a>
                        </li>
                        <li>
                            <a href="#tab4" data-toggle="tab">厨房电器</a>
                        </li>
                        <li>
                            <a href="#tab5" data-toggle="tab">应季电器</a>
                        </li>
                        <li>
                            <a href="#tab6" data-toggle="tab">空气/净水</a>
                        </li>
                        <li>
                            <a href="#tab7" data-toggle="tab">高端电器</a>
                        </li> -->
                    </ul>
                </div>
            </div>
            <div class="tab-content">
                <div class="tab-pane">
                    <div class="floor-1">
                        <div class="blockgary">
                            <ul class="jd-list">
                                <li v-for="(keyword, index) in floor.keywords" :key="index">{{ keyword }}</li>
                                <!-- <li>节能补贴</li>
                                <li>4K电视</li>
                                <li>空气净化器</li>
                                <li>IH电饭煲</li>
                                <li>滚筒洗衣机</li>
                                <li>电热水器</li> -->
                            </ul>
                            <!-- <img src="./images/floor-1-1.png" /> -->
                            <img :src="floor.imgUrl" />
                        </div>
                        <div class="floorBanner">
                            <!-- 轮播图 -->
                            <Carousel :list="floor.carouselList"></Carousel>
                        </div>
                        <div class="split">
                            <span class="floor-x-line"></span>
                            <div class="floor-conver-pit">
                                <!-- <img src="./images/floor-1-2.png" /> -->
                                <img :src="floor.recommendList[0]" />
                            </div>
                            <div class="floor-conver-pit">
                                <!-- <img src="./images/floor-1-3.png" /> -->
                                <img :src="floor.recommendList[1]" />
                            </div>
                        </div>
                        <div class="split center">
                            <!-- <img src="./images/floor-1-4.png" /> -->
                            <img :src="floor.bigImg" />
                        </div>
                        <div class="split">
                            <span class="floor-x-line"></span>
                            <div class="floor-conver-pit">
                                <!-- <img src="./images/floor-1-5.png" /> -->
                                <!-- <img :src="recom" /> -->
                                <img :src="floor.recommendList[2]" />
                            </div>
                            <div class="floor-conver-pit">
                                <!-- <img src="./images/floor-1-6.png" /> -->
                                <img :src="floor.recommendList[3]" />
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'Floor',
    mounted() {
        // 可以直接写在mounted里，因为数据请求不在这里发，而是在父组件当中发的请求
        // 因此，当子组件进行渲染的时候，数据已经拿到了
        // 然而，为了使项目性能最佳，将功能、结构相似的代码全局共用，改地方监听
        /*        Swiper.use([Navigation, Pagination, Autoplay])
               var mySwiper = new Swiper('.swiper-container', {
                   // direction: 'horizontal', // 水平切换选项
                   loop: true, // 循环模式选项
                   // observer: true,
                   direction: "horizontal",
       
                   // 如果需要分页器
                   pagination: {
                       el: '.swiper-pagination',
                       // type: "bullets",
                       clickable: true
                   },
       
                   // 如果需要前进后退按钮
                   navigation: {
                       nextEl: '.swiper-button-next',
                       prevEl: '.swiper-button-prev',
                   },
                   autoplay: {
                       delay: 1000
                   }
               }) */
    },
    props: ['floor'],

}
</script>

<style lang="less">
.floor {
    margin-top: 15px;

    .py-container {
        width: 1200px;
        margin: 0 auto;

        .title {
            .fl {
                float: left;
                color: #c81623;
                font-size: 20px;
                line-height: 30px;
                margin: 9px 0;
                font-weight: 700;
            }

            .fr {
                float: right;

                .nav-tabs {
                    margin: 10px 0 0;
                    display: inline-block;

                    li {
                        float: left;
                        line-height: 18px;

                        a {
                            padding-top: 1px;
                            font-weight: 400;
                            background-color: #fff;

                            &::after {
                                content: "|";
                                padding: 0 10px;
                            }
                        }

                        &:nth-child(7) {
                            a {
                                &::after {
                                    content: "";
                                }
                            }
                        }

                        &.active {
                            a {
                                color: #e1251b;
                            }
                        }
                    }
                }
            }
        }

        .tab-content {
            border-top: 2px solid #c81623;
            border-bottom: 1px solid #e4e4e4;

            .tab-pane {
                .floor-1 {
                    height: 360px;
                    display: flex;

                    .blockgary {
                        width: 210px;
                        height: 100%;
                        background: #f7f7f7;

                        .jd-list {
                            padding: 15px 0;
                            overflow: hidden;

                            li {
                                list-style-type: none;
                                float: left;
                                width: 40%;
                                margin: 0 10px;
                                border-bottom: 1px solid #e4e4e4;
                                text-align: center;
                                line-height: 26px;
                            }
                        }

                        img {
                            width: 100%;
                        }
                    }

                    .floorBanner {
                        width: 330px;
                        height: 100%;
                    }

                    .split {
                        width: 220px;
                        height: 100%;
                        position: relative;

                        .floor-x-line {
                            position: absolute;
                            background: #e4e4e4;
                            width: 220px;
                            height: 1px;
                            top: 180px;
                        }

                        .floor-conver-pit {
                            width: 100%;
                            height: 50%;

                            img {
                                width: 100%;
                                height: 100%;
                                transition: all 400ms;

                                &:hover {
                                    opacity: 0.8;
                                }
                            }
                        }
                    }

                    .center {
                        border: 1px solid #e4e4e4;
                    }
                }
            }
        }
    }
}
</style>