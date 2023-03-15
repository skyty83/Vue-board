<template>
    <div class="board-write">
        <table>
            <colgroup>
                <col style="width:15%;"/>
                <col />
            </colgroup>
            <tr>
                <th>제목</th>
                <td><input type="text" v-model="title"  placeholder="제목"/></td>
            </tr>
            <tr>
                <th>글쓴이</th>
                <td><input type="text" v-model="writer" placeholder="글쓴이"/></td>
            </tr>
            <tr>
                <th>내용</th>
                <td><textarea v-model="content" placeholder="내용" /></td>
            </tr>
        </table>
        <button @click="index !== undefined ? update() : write()" class="btn">{{ index !== undefined ? '수정' : '작성' }}</button>
    </div>
</template>

<script>

import data from '@/data'

export default {
    name: 'Create',
    data() {
        const index = this.$route.params.contentId;
        return {
            data: data,
            index:  index,
            writer: index !== undefined ? data[index].writer : "",
            title:index !== undefined ? data[index].title : "",
            content: index !== undefined ? data[index].content : ""
        }
    },
    methods: {
        write() {
            this.data.push({
                title:  this.title,
                writer:  this.writer,
                content:  this.content,
            })
            this.$router.push({
                path:'/'
            })
        },
        update() {
            data[this.index].writer = this.writer
            data[this.index].title = this.title
            data[this.index].content = this.content
            this.$router.push({
                path:'/'
            })
        }
    }
}
</script>

<style>
    .board-write table {
        border-spacing: 0;
        border-top:1px solid #212121;
        table-layout: fixed;
        margin:0 auto;
        max-width:1000px;
        width:100%;
    }
    .board-write table th {
        padding:12px 0;
        text-align: center;
        border-bottom:1px solid #212121;
        font-size:14px;
        color:#212121;
    }
    .board-write table td {
        padding:12px 20px;
        text-align: center;
        border-bottom:1px solid #212121;
        border-left:1px solid #212121;
        font-size:14px;
        color:#212121;
        text-align: left;
    }
    .board-write table td input {
        border:1px solid #ddd;
        height:40px;
        width:100%;
        padding:10px;
        font-size:14px;
        line-height: 50px;
        background: #fff;
        box-sizing: border-box;
    }
    .board-write table td textarea {
        width:100%;
        height:300px;
        padding:10px;
        font-size:14px;
        line-height: 1.5;
        background: #fff;
        border:1px solid #ddd;
        box-sizing: border-box;
    }
    .btn  {
        display: inline-block;
        margin-top:20px;
        background:#fff;
        border:1px solid #212121;
        padding:10px 50px;
        border-radius: 4px;
        cursor: pointer;
    }
</style>