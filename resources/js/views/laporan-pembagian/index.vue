<template>
    <v-app>
        <Progress v-if="loading"/>
        <v-container v-if="!loading">
            <v-btn small color="teal darken-2" class="white--text" tile>Data Pembagian Zakat</v-btn>
            <v-card
            class="border-edit"
            tile
            >
                <v-card-text class="text-center">
                    <v-container>
                        <v-row justify="center" align="center">
                            <v-col
                                cols="6"
                            >
                            <v-text-field
                                v-model="keyword"
                                label="Pencarian"
                                v-on:keyup = "go"
                                color="teal darken-2"
                            ></v-text-field>
                            </v-col>

                            <v-col
                                cols="6"
                                align="right"
                            >
                                <v-btn color="primary"  :to="urlcreate" small tile>
                                    Cetak
                                </v-btn>
                            </v-col>
                        </v-row>
                    </v-container>

                    <v-simple-table>
                        <template v-slot:default>
                        <thead>
                            <tr>
                            <th class="text-left">Nama Lembaga</th>
                            <th class="text-left">Alamat Tujuan</th>
                            <th class="text-left">Total Uang</th>
                            <th class="text-left">Total Beras</th>
                            <th class="text-left">Tanggal</th>
                            </tr>
                        </thead>
                        <tbody>
                            <!-- <tr v-for="item in data" :key="item.id">
                                <td class="text-left">{{item.name}}</td>
                                <td class="text-left">{{item.email}}</td>
                                <td class="text-left">{{item.role.description}}</td>
                                <td class="text-left" width="30%">
                                <v-btn color="success" v-on:click="edit(item.id)" fab x-small dark >
                                    <v-icon>mdi-circle-edit-outline</v-icon>
                                </v-btn>
                                <v-btn color="error" fab x-small @click="dialogDelete(item.id)" >
                                    <v-icon>mdi-delete-outline</v-icon>
                                </v-btn>
                                </td>
                            </tr> -->
                            <tr>
                                <td class="text-left">Warga Masjid Al Insan</td>
                                <td class="text-left">Jl Impact</td>
                                <td class="text-left">Rp. 30.000.000</td>
                                <td class="text-left">30Kg</td>
                                <td class="text-left">2020-06-01</td>
                            </tr>


                        </tbody>
                        </template>
                    </v-simple-table>
                </v-card-text>
                <div class="text-center">
                    <v-pagination
                    v-model="page"
                    :length="lengthpage"
                    :total-visible="7"
                    @input="go"
                    color="teal darken-2"
                    ></v-pagination>
                </div>
                <v-card-actions class="">

                </v-card-actions>
            </v-card>

            <v-dialog
            v-model="dialog"
            max-width="340"
            >
            <v-card>
                <v-card-title class="headline">Apa anda yakin menghapus ?</v-card-title>

                <v-card-actions>
                <v-spacer></v-spacer>

                <v-btn

                    text
                    @click="dialog = false"
                >
                    Cancel
                </v-btn>

                <v-btn
                    color="red"
                    text
                    @click="deleteData()"
                >
                    Delete
                </v-btn>
                </v-card-actions>
            </v-card>
            </v-dialog>
        </v-container>
    </v-app>

</template>
<script>

import CrudMixin from '../../mixins/CrudMixin'
export default {
    name: 'users',
    mixins:[CrudMixin]
}
</script>

