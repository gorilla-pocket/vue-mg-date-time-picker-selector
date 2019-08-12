<template>
    <div class="d-flex">
        <div class="mr-1">
            <date-picker-standard v-model="selected_yyyymmdd" :isInvalid="isInvalid"/>
        </div>
        <select class="form-control mr-1" style="width:4rem;"  v-model="selected_hour" :class="{ 'is-invalid': isInvalid }">
            <option></option>
            <option v-for="hour in hours" :key="hour.value" :value="hour.value">{{hour.value}}</option>
        </select>
        <select class="form-control" style="width:4rem;"  v-model="selected_minute" :class="{ 'is-invalid': isInvalid }">
            <option></option>
            <option v-for="minute in minutes" :key="minute.value" :value="minute.value">{{minute.value}}</option>
        </select>
    </div>
</template>

<script>
import moment from 'moment';
import DatePickerStandard from 'vue-mg-date-picker-standard'
export default {
    props: {
        value: {
            default: '',
        },
        isInvalid: {
            default: false,
        },
        minHour: {
            default: 0,
        },
        maxHour: {
            default: 23,
        },
        minuteRange: {
            default: 10,
        }
    },
    data () {
        return {
            selected_yyyymmdd: '',
            selected_hour: '',
            selected_minute: '',
        }
    },
    mounted: function () {
        // console.log(this.value)
        if (this.value) {
            let d = moment(this.value)
            this.selected_yyyymmdd = d.format('YYYY-MM-DD')
            this.selected_hour = d.get('hour')
            this.selected_minute = ('0' + d.get('minute')).slice(-2)
        }
    },
    watch: {
        value: function (val) {
            if (!val) {
                this.selected_yyyymmdd = ''
                this.selected_hour = ''
                this.selected_minute = ''
                return
            }
            let d = moment(val)
            this.selected_yyyymmdd = d.format('YYYY-MM-DD')
            this.selected_hour = d.get('hour')
            this.selected_minute = ('0' + d.get('minute')).slice(-2)
        },
        selected_yyyymmdd: function () {
            let ret = this.convertDate()
            this.$emit('input', ret)
        },
        selected_hour: function () {
            let ret = this.convertDate()
            this.$emit('input', ret)
        },
        selected_minute: function () {
            let ret = this.convertDate()
            this.$emit('input', ret)
        },
    },
    computed: {
        hours: function () {
            let hours = []
            for (let i = this.minHour; i <= this.maxHour; i++) {
                hours.push({
                    value: i
                });
            }
            return hours
        },
        minutes: function () {
            let minutes = []
            for (let i = 0; i <= 50; i = i + this.minuteRange) {
                minutes.push({
                    value: ('0' + i).slice(-2)
                });
            }
            return minutes
        },
    },
    methods: {
        convertDate: function () {
            let ret = ''
            if (this.selected_yyyymmdd && this.selected_hour) {
                ret = moment(this.selected_yyyymmdd+' '+('00' + this.selected_hour).slice(-2)+':'+('00' + this.selected_minute).slice(-2)).format('YYYY-MM-DD HH:mm')
            }
            return ret
        }
    },
    components: {
        DatePickerStandard,
    }
}
</script>