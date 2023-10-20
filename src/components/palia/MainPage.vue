<script lang="js">

let date = new Date();
var utcDate = new Date(date.toUTCString());
let dtCurrent = new Date(utcDate.toLocaleString("en-US", {timeZone: "America/Santiago"}));
let dtCurrentDateOnly = new Date((new Date(dtCurrent)).setHours(0,0,0,0));
let spanSeconds = ((dtCurrent.getTime() - dtCurrentDateOnly.getTime()) / 1000) + 10;

export default {
    name: "GameClock",
    data() {
        return {
            timestamp: '',
            hour: 0,
            ampm: '',
            minutes: 0,
            seconds: 0
        }
    },
    mounted() {
        setInterval(() => this.setTime(), 1000);
    },
    methods: {
        setTime: function() {
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
    
    <div class="">
        <h1>{{ hour }} : {{ minutes }}  {{ampm}}</h1>
    </div>
    <div class="">
            Current Time (Approximate)
    </div>
</template>
