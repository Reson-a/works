<template>    
    <ul class="app-list">
        <li class="app-item" v-for="(app,index) in appData" :key="index">  
            <img :src="app.icon" :alt="app.name" class="f-fl">
            <el-button type="success" size="small" class="f-fr">安装</el-button>            
            <div class="app-list-content border-bottom">
                <div>                     
                     <h1><span v-if="isRank" :class="{'top-three':index<3}">{{index+1}}. </span>{{app.name}}</h1>
                     <span v-if="app.isPromoted">活动</span>                    
                </div>                                  
                <p><span>{{app.size}}MB</span>&nbsp;&nbsp;<span>{{app.userCount}}万人安装</span><br><span v-if="!isRank">{{app.slogan}}</span></p>                    
            </div>                                 
	    </li>        
    </ul>	
</template>

<script>
    import ElementUI from 'element-ui'
    export default {
        props: {
            appData: {
                type: Array,
                required: true
            },
            isRank: {
                type: Boolean,
                required: false
            }
        },
        data() {
            return {
                msg: 'Hello Vue!'
            }
        }
    }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss">
    .app-list {
        list-style: none;
        padding: 0;
        margin: 0;
        .app-item {
            position: relative;
            img {
                width: 4rem;
                height: 4rem;
            }
            .app-list-content {
                margin-left: 5rem;
                padding: 1rem 4rem 1rem 0;
                overflow: hidden;
                div {
                    line-height:1;                              
                    h1 {
                        display: inline-block;
                        font-size: 1.4rem;
                        vertical-align:middle;                  
                        .top-three {
                            color: #F7BA2A;
                        }
                                                
                    }
                    >span {
                        display: inline-block;                        
                        margin-left: 0.4rem;
                        padding: 0.2rem 0.3rem;
                        color: #FFF;
                        background-color: #20A0FF;
                        border-radius: 0.2rem;
                        vertical-align:middle; 
                    }
                }
                p {
                    margin-top: 0.6rem;
                }
                &:after {
                    left: 5rem;
                }
            }
            .el-button.el-button--small{
                font-size:1rem;
                padding:0.4rem 0.8rem;
                border-radius: 0.4rem;
                border-width:0.2rem;
                height: 2.2rem;
            }
        }
    }
</style>