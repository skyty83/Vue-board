<template>
    <div>
        <table class="board">
            <colgroup>
                <col style="width:15%;"/>
                <col />
                <col style="width:20%;"/>
            </colgroup>
            <tr>
                <th>제목</th>
                <th>내용</th>
                <th>글쓴이</th>
            </tr>
            <tr :key="index" v-for="(value,index) in data">
                <td>{{value.title}}</td>
                <td style="text-align: left;"><a href="javascript:void(0)" @click="detail(index)">{{value.content}}</a></td>
                <td>{{value.writer}}</td>
            </tr>
        </table>
        <button @click="write" class="btn">글쓰기</button>
    </div>
</template>

<script>
import data from '@/data'

export default {
    name:'Read',
    data(){
        return  {
            data:  data
        }
    },
    methods: {
        write() {
            this.$router.push({
                path: 'create'
            })
        },
        detail(index){
            console.log(index)
            this.$router.push({
                name: 'Detail',
                params: {
                    contentId:  index
                }
            })
        }
    }
}
</script>
<style>
    .board {
        border-spacing: 0;
        border-top:1px solid #212121;
        table-layout: fixed;
        margin:0 auto;
        max-width:1000px;
        width:100%;
    }
    .board th {
        padding:12px 0;
        text-align: center;
        border-bottom:1px solid #212121;
        font-size:14px;
        color:#212121;
    }
    .board td {
        padding:12px 0;
        text-align: center;
        font-size: 14px;
        border-bottom:1px solid #ddd;
    }
    .board td a {
        text-decoration: none;
        color:#212121;
    }
    .btn  {
        display: inline-block;
        margin-top:20px;
        background:#fff;
        border:1px solid #212121;
        padding:10px 50px;
        border-radius: 4px;
        cursor: pointer;
        transition: all .2s;
        color:#212121;
    }
    .btn:hover {
        background:#212121;
        color:#fff;
    }
</style>