<template>
    <div class="sidebar">
        <el-menu :default-active="onRoutes" class="el-menu-vertical-demo" theme="dark" unique-opened router>
            <template v-for="item in items">
                <template v-if="item.subs">
                    <el-submenu :index="item.index">
                        <template slot="title"><i :class="item.icon"></i>{{ item.title }}</template>
                        <el-menu-item v-for="(subItem,i) in item.subs" :key="i" :index="subItem.index">{{ subItem.title }}
                        </el-menu-item>
                    </el-submenu>
                </template>
                <template v-else>
                    <el-menu-item :index="item.index">
                        <i :class="item.icon"></i>{{ item.title }}
                    </el-menu-item>
                </template>
            </template>
        </el-menu>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                items: [
                    {
                        icon: 'el-icon-star-off',
                        index: 'readme',
                        title: '首頁'
                    },
                    {
                        icon: 'el-icon-goods',
                        index: '2',
                        title: '商品管理',
                        subs: [
                            {
                                index: 'baseform',
                                title: '小蜜食品'
                            },
                            {
                                index: 'vueeditor',
                                title: '小蜜用品'
                            }
                        ]
                    },
                    {
                        icon: 'el-icon-tickets',
                        index: '3',
                        title: '交易資料',
                        subs: [
                            {
                                index: 'basetable',
                                title: '交易紀錄'
                            },
                            {
                                index: 'vuetable',
                                title: '統計報表'
                            }
                        ]
                    },{
                        icon: 'el-icon-info',
                        index:'4',
                        title:'客戶資料管理'
                    }
                ]
            }
        },
        computed:{
            onRoutes(){
                return this.$route.path.replace('/','');
            }
        }
    }
</script>

<style scoped>
    .sidebar{
position: absolute;

top: 70px;

bottom:0;

left: 0;

display: block;

width: 250px;

background: #2E363F;

}
    .sidebar > ul {
        height:100%;
    }


</style>
