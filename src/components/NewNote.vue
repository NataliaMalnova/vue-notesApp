<template>
   <!-- new note -->
    <div class="new-note">
        <div class="new-note_task">
            <div class="new-note_title">
                <label>Название заметки</label>
                <input v-model="note.title" type="text">
            </div>
            
            <div class="new-note_priority">
                <label>Приоритет заметки</label>
                <div class="new-note_change">
                    <div class="change">
                        <input type="radio" id="check1" name="radio_priority" checked><label for="check1">Стандартная задача</label>
                    </div>
                    <div class="change">
                        <input type="radio" id="check2" name="radio_priority"><label for="check2"> Важная задача</label>
                    </div>
                </div>
            </div>
        </div>
        <label>Описание заметки</label>
        <textarea v-model="note.descr"></textarea>
        <button class="btn btnPrimary" @click="addNote">Добавить заметку</button>
    </div>
</template>

<script>

export default {
    props: {
        note: {
            type: Object,
            required: true
        }
    },
    methods: {
        addNote () {
            this.$emit('addNote', this.note)
        }
    }
}
</script>

<style lang="scss">
    .new-note{
        text-align: center;
         
        .btn{
            margin-top: 16px;  
            margin-bottom: 24px;
        }
    }
    .new-note_priority{
        display: flex;
        flex-direction: column;
        align-items: flex-start;
        width: 50%;
        padding-left: 24px;
        @media screen and (max-width: 767px) { 
            width: 100%;
            padding-bottom: 24px;
        }
    }
    .new-note_change{
        display: flex;
        width: 100%;
        @media screen and (max-width: 575px) { 
          flex-direction: column;
        }
        input{
            width: auto;
            margin: 0;
            padding: 0;
            margin-right: 8px;
        }
        label{
            margin: 0;
        }
        .change{
            height: 55px;
            display: flex;
            justify-content: flex-start;
            align-items: center;
            margin-right: 12px;
        }
    }
    .new-note_task{
        display: flex;
        @media screen and (max-width: 767px) { 
           flex-direction: column;
        }
    }

    .new-note_title{
        width: 50%;
        @media screen and (max-width: 767px) { 
            width: 100%;
        }
    }
</style>