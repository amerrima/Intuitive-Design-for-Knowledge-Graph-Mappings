<template>
<v-card flat tile outlined height="400">
    <div class="text-right">
        <v-btn :loading="loading3" :disabled="loading3" color="blue-grey" class="ma-2 white--text" @click="loader = 'loading3'">
            Upload
            <v-icon right dark> mdi-cloud-upload </v-icon>
        </v-btn>
    </div>

    <v-textarea no-resize rounded filled readonly color="transparent" background-color="transparent" v-model="json"></v-textarea>
</v-card>
</template>

<script>
export default {
    props:{
        file:{
            type: Object,
            default: function(){
                return{}
            }
        }
    },
    data: () => ({
        
    }),
    created() {
        this.file = JSON.stringify(this.file, null, 2);
    },

    watch: {
        loader() {
            const l = this.loader
            this[l] = !this[l]

            setTimeout(() => (this[l] = false), 3000)

            this.loader = null
        },
    },
};
</script>
