<template>
    <div class="board-detail">
        <table>
            <colgroup>
                <col style="width:15%;"/>
                <col />
            </colgroup>
            <tr>
                <th>제목</th>
                <td>{{data.title}}</td>
            </tr>
            <tr>
                <th>글쓴이</th>
                <td style="text-align: left;">{{data.writer}}</td>
            </tr>
            <tr>
                <th>내용</th>
                <td>{{data.content}}</td>
            </tr>
        </table>
        <button class="btn" @click="updateData">수정</button>
        <button class="btn" @click="deleteData">삭제</button>
    </div>
</template>

<script>
import data from '@/data'

export default {
    name:'Detail',
    data(){
        const index = this.$route.params.contentId
        return  {
            data:  data[index],
            index: index,
        }
    },
    methods: {
        deleteData (){
            data.splice(this.index, 1)
            this.$router.push({
                path:'/'
            })
        },
        updateData () {
            this.$router.push({
                name: 'Create',
                params: {
                    contentId:  this.index
                }
            })
        }
    }
}
</script>
<style>
    .board-detail table {
        border-spacing: 0;
        border-top:1px solid #212121;
        table-layout: fixed;
        margin:0 auto;
        max-width:1000px;
        width:100%;
    }
    .board-detail table th {
        padding:12px 0;
        text-align: center;
        border-bottom:1px solid #212121;
        font-size:14px;
        color:#212121;
    }
    .board-detail table td {
        padding:12px 20px;
        text-align: center;
        border-bottom:1px solid #212121;
        border-left:1px solid #212121;
        font-size:14px;
        color:#212121;
        text-align: left;
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