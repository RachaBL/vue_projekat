<template>
    <form @submit="onSubmit" class="add-form">
        <div class="form-control">
            <label>Obaveza</label>
            <input type="text" v-model="text" name="text" placeholder="Dodaj opis obaveze">
        </div>

        <div class="form-control">
            <label>Dan i vrijeme</label>
            <input type="text" v-model="day" name="day" placeholder="Dodaj dan i vrijeme">
        </div>

        <div class="form-control form-control-check">
            <label>Postavi podsjetnik</label>
            <input type="checkbox" v-model="reminder" name="reminder" />
        </div>

        <input type="submit" value="Sacuvaj" class="btn btn-block">
    </form>
</template>

<script>
export default {
    name: 'Comp-AddTask',
    data() {
        return {
            text: '',
            day: '',
            reminder: false,
        }
    },
    methods: {
        onSubmit(e) {
            e.preventDefault()

            if(!this.text) {
                alert('Opis obaveze nije unesen')
            }

            const newTask = {
                id: Math.floor(Math.random() * 100000),
                text: this.text,
                day: this.day,
                reminder: this.reminder
            }

            this.$emit('add-task', newTask)

            this.text = ''
            this.day = ''
            this.reminder = false
        }
    }
}
</script>

<style scoped>
    .add-form {
        margin-bottom: 40px;
    }

    .form-control {
        margin: 20px 0;
        border-color: #00FFAA;
    }
    .form-control label {
        display: block;
    }
    .form-control input {
        width: 100%;
        height: 40px;
        margin: 5px;
        padding: 3px 7px;
        font-size: 17px;
        border-color: rgba(0, 0, 0, .1);
        border-radius: 5px;
    }
    
    .form-control-check {
        display: flex;
        align-items: center;
        justify-content: space-between;
    }
    .form-control-check label {
        flex: 1;
    }
    .form-control-check input {
        flex: 2;
        height: 20px;
    }

    .btn{
        width: 100%;
        background-color: #00FFAA;
        color: white;
        transition: .5s ease all;
    }

    .btn:hover {
        color: black;
    }

</style>