<template>
    <header class="text-center">
        <div id="title" class="p-3 m-3"><span>IRIS 이슈 통계 페이지</span></div>
        <div class="counting m-3">
            <div class="count p-3" v-for="(count,i) in issueCountList" :key="i">
                <span>오늘 {{ count.name }} 이슈 :  {{ count.total}} </span>
            </div>
        </div>
    </header>
</template>

<script>
    import axios from "axios";

    export default {
        data() {
            return {
                issueCountList: []
            }
        },
        mounted() {
            axios
                .get('/iris-issues/count')
                .then(response => {
                    this.issueCountList = response.data.list;
                    console.log(response.data);
                });
        }
    };
</script>

