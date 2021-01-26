<template>
    <ion-page>
        <ion-header>
            <ion-toolbar color="dark">
                <ion-buttons slot="end">
                    <ion-back-button>Kembali</ion-back-button>
                </ion-buttons>
                <ion-title>Nilai Keseluruhan Siswa</ion-title>
            </ion-toolbar>
        </ion-header>
        <ion-content>
            <ion-list >
                <ion-item v-for="item in siswanilai" :key="item.id">
                    <ion-label>
                        <h3>Semester:<b>{{item.semester}}</b></h3>
                        <h3>Jurusan:<b>{{item.jurusan}}</b></h3>
                        <h3>Pelajaran:<b>{{item.pelajaran}}</b></h3>
                        <h3>Guru:<b>{{item.guru}}</b></h3>
                        <h3>Tahun Kelas:<b>({{item.tahunkelas}})</b></h3>
                        <h3>Nama Kelas:<b>{{item.kelas}}</b></h3>
                        <h3>Nomor Ruang:<b>{{item.noruang}}</b></h3>
                        <h3>Nama Siswa:<b>{{item.namasiswa}}</b></h3>
                        <h6>Kehadiran:<b><ion-badge color="success">{{item.kehadiran}}(%)</ion-badge></b></h6>
                        <h6>Nilai Tugas 1:<b><ion-badge color="success">{{item.nilaitugas1}}</ion-badge></b></h6>
                        <h6>Nilai Tugas 2:<b><ion-badge color="success">{{item.nilaitugas2}}</ion-badge></b></h6>
                        <h6>Nilai Tugas 3:<b><ion-badge color="success">{{item.nilaitugas3}}</ion-badge></b></h6>
                        <h6>Nilai Tugas 4:<b><ion-badge color="success">{{item.nilaitugas4}}</ion-badge></b></h6>
                        <h6>Nilai Tugas 5:<b><ion-badge color="success">{{item.nilaitugas5}}</ion-badge></b></h6>
                        <h6>Nilai Tugas 6:<b><ion-badge color="success">{{item.nilaitugas6}}</ion-badge></b></h6>
                        <h6>Nilai Tugas 7:<b><ion-badge color="success">{{item.nilaitugas7}}</ion-badge></b></h6>
                        <h6>Nilai UTS:<b><ion-badge color="success">{{item.nilaiuts}}</ion-badge></b></h6>
                        <h6>Nilai UAS:<b><ion-badge color="success">{{item.nilaiuas}}</ion-badge></b></h6>
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
        IonBadge,
        IonButtons,
        IonBackButton
    }from '@ionic/vue'
import axios from 'axios'
    import { defineComponent } from 'vue'
    export default defineComponent({
        data(){
            return{
                siswanilai:[]
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
            IonBadge,
            IonButtons,
            IonBackButton,
        },

        mounted(){
            axios.post("http://174.129.50.75/api/siswanilai",{
                "user_id": localStorage.getItem("user_id")
            })
            .then(response =>{
                this.siswanilai = response.data.data
            })
        }
    })
</script>

<style scoped>
    
</style>