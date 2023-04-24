<template>
    <div class="con">
        <v-card 
            class="rounded-lg overflow-hidden" 
            elevation="8" 
            height="680"
            style="background-color: #D5B15B;">
            <v-form @submit.prevent="onSubmit">
                <v-row class="pa-15">
                    <v-text-field
                        label="DAY"
                        v-model="day"
                        :rules="rulesForDays"
                        variant="underlined"
                        color="#1F2460"
                        clearable>
                    </v-text-field>
                    <v-text-field
                        label="MONTH"
                        v-model="month"
                        :rules="rulesForMonths"
                        variant="underlined"
                        color="#035DC3"
                        clearable>
                    </v-text-field>
                    <v-text-field
                        label="YEAR"
                        v-model="year"
                        :rules="rulesForYears"
                        variant="underlined"
                        color="#1F2460"
                        clearable>
                    </v-text-field>
                </v-row>
                <v-row class="pa-15">
                    <v-btn 
                        class="rounded-lg"
                        style="color: #1F2460;"
                        color="#D5B15B"
                        type="submit">
                        Calculate
                    </v-btn>
                </v-row>
            </v-form>
            <div 
                v-if="show"
                class="font-weight-bold"
                style="font-size: 50px">
                    {{ calc() }}
            </div> 
            <div 
                v-else
                class="font-weight-bold pa-15">
                <h1>
                    Fill in all fields above to find out your age in years, months and days!
                </h1>
            </div>
        </v-card>
    </div>
</template>
<script>

export default {
    data(){
        return {
            day: '',
            month: '',
            year: '',
            show: false,
            rulesForDays: [
                value => {
                    if (value) return true
                        return 'Required'
                },
                value => {
                    if (value <= 31 && value >= 1) return true
                        return 'Invalid day'
                },
            ],
            rulesForMonths: [
                value => {
                    if(value) return true
                        return 'Required'
                },
                value => {
                    if(value <= 12 && value >= 1) return true
                        return 'Invalid month'
                }
            ],
            rulesForYears: [
                value => {
                    if(value) return true
                    return 'Required'
                },
                value => {
                    if(value < new Date().getFullYear() && value >= 1) return true
                        return 'Invalid year'
                }
            ]
        }
    },
    methods: {
        onSubmit(){
            if(this.day.trim() && this.month.trim() && this.year.trim()){
                this.show = true
            }
        },
        calc(){
            let date = new Date();
            let d2 = date.getDate();
            let m2 = 1 + date.getMonth();
            let y2 = date.getFullYear();
            let month = [31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31]

            if(this.day > d2){
                d2 = d2 + month[m2 - 1];
                m2 = m2 - 1;
            }
            if(this.month > m2){
                m2 = m2 + 12;
                y2 = y2 - 1;
            }
            let y = y2 - this.year;
            let m = m2 - this.month;
            let d = d2 - this.day;

            let res = [
                y, 'years',
                m, ' months',
                d, ' days'
            ]

            let finRes = res.join(" ");

            return finRes;
        }
    }
}
</script>
<style scoped>
.font-weight-bold {
    color: #1F2460;
    /* color: #035DC3;
    color: #9F0220; */
    font-family: Impact, Haettenschweiler, 'Arial Narrow Bold', sans-serif;
}
.rounded-lg {
    font-family: Impact, Haettenschweiler, 'Arial Narrow Bold', sans-serif;
}
.text-h2 {
    color: #035DC3;
    font-family: Impact, Haettenschweiler, 'Arial Narrow Bold', sans-serif;

}
</style>
