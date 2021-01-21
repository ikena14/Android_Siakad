<template>
    <ion-page>
        <ion-header>
            <ion-toolbar color="dark">
                <ion-title>Siswa</ion-title>
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
        IonLabel
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
            IonLabel
        },

        mounted(){
            axios.post("http://174.129.50.75/api/siswa",{
                "user_id": localStorage.getItem("user_id")
            })
            .then(response =>{
                this.siswa = response.data.data
            })
        }
    })
</script>

<style scoped>

</style>