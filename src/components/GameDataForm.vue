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
    <div class="w-full">
        <div class="flex flex-col gap-[16px]">
            <div class="flex flex-col gap-[8px]">
                <label>تعداد بازیکن</label>
                <input type="number" v-model="playerCount" class="h-[32px] max-w-[250px] border rounded-[8px] px-[8px]"/>
            </div>

            <div class="flex flex-col gap-[8px]">
                <label>تعداد جاسوس</label>
                <input type="number" v-model="spyCount" class="h-[32px] max-w-[250px] border rounded-[8px] px-[8px]"/>
                <small>تعداد پیشنهادی جاسوس ۳۰٪ کل بازیکنان است.</small>
            </div>

            <button 
                @click="handleClick" 
                class="max-w-[250px] py-[8px] px-[16px] rounded-[10px] bg-red-600 text-white">
                شروع بازی
            </button>
        </div>
    </div>
</template>