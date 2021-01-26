<template>
    <ion-page>
        <ion-header>
            <ion-toolbar color="dark">
                <ion-title>Keseluruhan Status Siswa</ion-title>
                <ion-button @click="nilai" class="kanan" color="primary">Nilai Keseluruhan Siswa</ion-button>
            </ion-toolbar>
        </ion-header>
        <ion-content>
            <ion-list>
                <ion-item v-for="item in siswa" :key="item.id">
                        <ion-label>
                            <h3>Nis: {{item.nis}}</h3>
                            <h4>Nama: {{item.nama}}</h4>
                            <h4>Jurusan: {{item.jurusan}}</h4>
                            <h4>Tahun Angkatan: {{item.tahunangkatan}}</h4>
                            <h4>Status Aktif Siswa: {{item.status}}</h4>
                        </ion-label>      
                </ion-item>
            </ion-list>
        </ion-content>
    </ion-page>
</template>

<script>
import{
        IonPage,
        IonHeader,
        IonToolbar,
        IonTitle,
        IonContent,
        IonList,
        IonItem,
        IonLabel,
        IonButton
    }from '@ionic/vue'
import axios from 'axios'
    import { defineComponent } from 'vue'
    export default defineComponent({
        data(){
            return{
                siswa:[]
            }
        },
        components:{
            IonPage,
            IonHeader,
            IonToolbar,
            IonTitle,
            IonContent,
            IonList,
            IonItem,
            IonLabel,
            IonButton
        },

        mounted(){
            axios.post("http://174.129.50.75/api/siswa",{
                "user_id": localStorage.getItem("user_id")
            })
            .then(response =>{
                this.siswa = response.data.data
            })
        },
        methods:{
            nilai(){
                this.$router.push("/siswa/nilai")
            }
        }
    })
</script>

<style scoped>
    .kanan{
        float: right;
    }
    .kanan_{
        float: right;
    }
</style>