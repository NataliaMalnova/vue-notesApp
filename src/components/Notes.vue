<template>
  <!-- note list -->
    <div class="notes">
        <div class="note" :class="{ full: !grid, priorityClass: note.priority}"  v-for="(note, index) in notes" :key="index">
            <div class="note-header" :class="{ full: !grid}">
                <p>{{ note.title }}</p>
                <p style="cursor: pointer;" @click="removeNode(index)">x</p>
            </div>
            <div class="note-body">
                <p>{{ note.descr }}</p>
                <span>{{ note.date }}</span>
            </div>
        </div>
    </div> 
</template>

<script>
export default {
    props: {
        notes: {
            type: Array,
            required: true
        },
        grid: {
            type: Boolean,
            required: true
        }
    },
    methods: {
        removeNode(index) {
            console.log('removeNode', index)
            this.$emit('remove', index)
        }
    }
}
</script>

<style lang="scss">
    .notes{
        display: flex;
        align-items: center;
        justify-content: space-between;
        flex-wrap: wrap;
        padding: 40px 0px;
        
    }
    .note {
        width: 46%;
        padding: 18px 20px;
        margin-bottom: 20px;
        background: #fff;
        transition: all .6s cubic-bezier(.02,.01,.47,1);
        box-shadow: 0 30px 30px rgba(0,0,0,.02);
        @media screen and (max-width: 575px) { 
            width: 100%;
        }
        &:hover {
            box-shadow: 0 30px 30px rgba(0,0,0,.04);
            transform: translate(0,-6px);
            transition-delay: 0s !important;
        }
        &.full{
            width: 100%;
            text-align: center;
        }
        &.priorityClass{
            background: #ff9d9d42;
        }
    }
    .note-body{
        p{
            margin: 20px 0;
        }
        span{
            font-size: 14px; 
            color: #999;
        }
    }
    .note-header-search{
        display: flex;
        align-items: center;
        justify-content: space-between;
        width: calc(50% + 200px);  
        @media screen and (max-width: 767px) { 
            width: 100%;
            margin-top: 24px;
        }
    }
    .note-header{
        display: flex;
        align-items: center;
        justify-content: space-between;
        @media screen and (max-width: 767px) { 
            flex-direction: column;
        }
        h1{
            font-size: 32px;
        }
        p{
            color: #402caf;
            font-size: 22px;
        }
        svg{
            margin-right: 12px;
            color: #999;
            cursor: pointer;
            &.active{
                 color: #402caf;
            }
            &:last-child{
                margin-right: 0;
            }
            @media screen and (max-width: 575px) { 
                display: none; 
            }
        }
        &.full {
            justify-content: center;
            p {
                margin-right: 16px;
                &:last-child {
                    margin-right: 0;
                }
            }
        }
    }
</style>