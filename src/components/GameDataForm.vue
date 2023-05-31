<script>
export default {
    props:{
        setGameData : {
            type : Function,
            required : true
        }
    },
    data(){
        return{
            playerCount: "",
            spyCount : ""
        }
    },
    methods : {
        handleClick(){
            this.setGameData(this.playerCount,this.spyCount)
        }
    }
}
</script>

<template>
    <div class="w-full max-w-[85vw] mx-auto">
        <div class="flex flex-col gap-[16px]">
            <div class="flex flex-col gap-[8px]">
                <label>تعداد بازیکن</label>
                <input type="number" v-model="playerCount"/>
            </div>

            <div class="flex flex-col gap-[8px]">
                <label>تعداد جاسوس</label>
                <input type="number" v-model="spyCount"/>
                <small>تعداد پیشنهادی جاسوس ۳۰٪ کل بازیکنان است.</small>
            </div>

            <button @click="handleClick">شروع بازی</button>
        </div>
    </div>
</template>