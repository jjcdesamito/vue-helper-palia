<script lang="js">
import dataFood from './data_food.json'

let date = new Date();
var utcDate = new Date(date.toUTCString());
let dtCurrent = new Date(utcDate.toLocaleString("en-US", { timeZone: "America/Santiago" }));
let dtCurrentDateOnly = new Date((new Date(dtCurrent)).setHours(0, 0, 0, 0));
let spanSeconds = ((dtCurrent.getTime() - dtCurrentDateOnly.getTime()) / 1000) + 5;

export default {
    name: "GameClock",
    data() {
        return {
            timestamp: '',
            hour: 0,
            ampm: '',
            minutes: 0,
            seconds: 0,
            dataList: dataFood
        }
    },
    mounted() {
        setInterval(() => this.setTime(), 1000);
    },
    methods: {
        setTime: function () {
            spanSeconds = spanSeconds + 1;

            let paliaSeconds = spanSeconds * 24;

            let paliaMinute = (paliaSeconds / 60) % 60;
            let paliaHour = ((paliaSeconds / 60) / 60) % 24;
            this.timestamp = dtCurrentDateOnly;

            this.hour = String(Math.trunc(paliaHour % 12)).padStart(2, '0');
            this.ampm = paliaHour < 13 ? 'AM' : 'PM';
            this.minutes = String(Math.trunc(paliaMinute)).padStart(2, '0');
            this.seconds = utcDate;
        }
    },
    beforeDestroy() {
        // prevent memory leak
        clearInterval(this.interval)
    },
}
</script>

<template>
    <div class="pageTitle">Palia</div>
    <div class="clockContainer">
        <div class="clockTime">
            <h1>{{ hour }} : {{ minutes }} {{ ampm }}</h1>

        </div>
        <div class="clockDesc">
            Current Time (Approximate)
        </div>
    </div>
    <div>
        <!-- sort -->
    </div>
    <!-- items -->
    <div class="listContainerMain">
        <div class="itemContainer" v-for="item in dataList.data" :key="item.Name">
            <div class="descContainer">
                <div class="descTitle">Name</div>
                <div class="descItem">{{ item.Name }}</div>
            </div>
            <div class="descContainer">
                <div class="descTitle">Furniture</div>
                <div class="descItem">{{ item.Furniture_Initial }}</div>
            </div>
            <div class="descContainer">
                <div class="descTitle">Additional Furnitures</div>
                <div class="descItem" v-for="Furniture_Additional in item.Furniture_Additional" :key="item.Name">
                    <div class="descItemSub1">{{ Furniture_Additional.Name }}</div>
                </div>
            </div>

            <div class="descContainer">
                <div class="descTitle">Effects</div>
                <div class="descItem" v-for="Effects in item.Effects" :key="item.Name">
                    <div class="descItemSub1">{{ Effects.Name }}</div>
                    <div class="descItemSub2">{{ Effects.Description }}</div>
                </div>
            </div>
            <div class="descContainer">
                <div class="descTitle">Initial Ingredients</div>
                <div class="descItem" v-for="Ingredients_Initial in item.Ingredients_Initial" :key="item.Name">
                    <div class="descItemSub1">{{ Ingredients_Initial.Name }}</div>
                    <div class="descItemSub2">x{{ Ingredients_Initial.Count }}</div>
                </div>
            </div>
            <div class="descContainer">
                <div class="descTitle">Additional Ingredients</div>
                <div class="descItem" v-for="Ingredients_Other in item.Ingredients_Other" :key="item.Name">
                    <div class="descItemSub1">{{ Ingredients_Other.Name }}</div>
                    <div class="descItemSub2">x{{ Ingredients_Other.Count }}</div>
                </div>
            </div>
            <div class="descContainerInline">
                <div class="descTitle">Craft Count</div>
                <div class="descItem">x{{ item.Craft_Count }}</div>
            </div>
            <div class="descContainerInline">
                <div class="descTitle">Focus</div>
                <div class="descItem">{{ item.Focus }}</div>
            </div>
            <div class="descContainerInline">
                <div class="descTitle">Cooking Time</div>
                <div class="descItem">{{ item.Cooking_Time }}</div>
            </div>
            <div class="descContainerInline">
                <div class="descTitle">Selling Price</div>
                <div class="descItem">{{ item.Selling_Price_Normal }}</div>
            </div>
            <div class="descContainerInline">
                <div class="descTitle">Selling Price (Star)</div>
                <div class="descItem">{{ item.Selling_Price_Star }}</div>
            </div>
        </div>
    </div>
</template>

<style scoped>
.pageTitle {
    display: block;
    font-size: 3em;
    border-style: solid;
    border-width: 0 0 0.1em 0;
    border-color: white;
    color: white;
    margin-bottom: 1em;
}

.clockContainer {

    border-style: solid;
    border-width: 0.1em;
    border-color: white;
    border-radius: 1em;
    margin: 1em;
    padding: 1em;
    max-width: 18em;
}

.clockTime {
    font-size: 1.5em;
    color: white;
    text-align: center;
}

.clockDesc {
    color: gray;
    font-size: 0.8em;
    text-align: center;
}

.listContainerMain {
    display: block;
    border-style: solid;
    border-width: 0.1em;
    border-color: white;
    border-radius: 1em;
    margin: 1em;
    padding: 1em;
}

.itemContainer {
    display: block;
}


.descContainer {
    display: block;
}

.descContainerInline {
    display: inline-block;
    margin-right: 0.5em;
}

.descTitle {
    display: inline-block;
    margin: 0.1em;
    padding: 0.1em;
    color: gray;
    font-size: 0.8em;

}

.descItem {
    display: inline-block;
    margin: 0.1em 0.1em 0.1em 0.5em;
    color: white;
}

.descItemSub1 {
    display: inline-block;
    margin: 0.1em;
}

.descItemSub2 {
    display: inline-block;
    margin: 0.1em;
    padding: 0 0 0 0.5em;
}
</style>