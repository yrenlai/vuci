<template>
    <div>
        <Input v-model="log" type="textarea" :autosize="true" readonly></Input>
    </div>
</template>

<script>
    export default {
        data () {
            return {
                log: ''
            }
        },

        mounted: function() {
            this.$ubus.call('vuci.system', 'dmesg').then((r) => {
                if (r.log) {
                    this.log = r.log;
                }
            });
        }
    }
</script>
