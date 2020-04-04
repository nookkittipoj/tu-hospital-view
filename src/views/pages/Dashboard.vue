<template>
    <v-container fluid>
        <v-row class="flex" dense>
            <v-col cols="6" class="flex">
                <v-card color="grey" style="height: 100%">
                    <GmapMap
                            :center="{lat:15.8700, lng:100.9925}"
                            :zoom="7"
                            map-type-id="terrain"
                            style="width: 100%; height: 100%"
                    >
                    </GmapMap>
                </v-card>
            </v-col>
            <v-col cols="6" class="flex">
                <v-row dense>
                    <v-col cols="4"
                           v-for="(item, i) in summary"
                           :key="i"
                    >
                        <v-card :color="item.color">
                            <v-card-text>
                                <h6 class="white--text">{{ item.text }}</h6>
                                <h2 class="white--text">{{ item.amount }}</h2>
                                <h6 class="white--text">{{ item.unit }}</h6>
                            </v-card-text>
                        </v-card>
                    </v-col>
                </v-row>
            </v-col>
        </v-row>
    </v-container>
</template>

<script>
    export default {
        name: "Dashboard",
        data: () => ({
            summary: [
                {text: 'ทั้งหมด', amount: 8, unit: 'เครื่อง', color: 'primary'},
                {text: 'พร้อมใช้งาน', amount: 0, unit: 'เครื่อง', color: 'green'},
                {text: 'ประตูเปิด', amount: 0, unit: 'เครื่อง', color: 'purple'},
                {text: 'ประตูเปิดไม่มี AED', amount: 0, unit: 'เครื่อง', color: 'red'},
                {text: 'ประตูปิดไม่มี AED', amount: 0, unit: 'เครื่อง', color: 'orange'},
                {text: 'ปลั๊กหลุด', amount: 0, unit: 'เครื่อง', color: 'blue'},
                {text: 'ซ่อมบำรุง', amount: 0, unit: 'เครื่อง', color: 'yellow'},
                {text: 'เชื่อมต่อไม่ได้', amount: 8, unit: 'เครื่อง', color: 'grey'},
            ]
        }),
    }
</script>

<style scoped>

</style>