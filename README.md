# Kelompok-5-Sistem-Voting
package com.mycompany.uas_std;
import java.util.ArrayList;
import java.util.LinkedList;
import java.util.List;
import java.util.Map;
import java.util.HashMap;
import java.util.Scanner;

public class Uas_std {

    public record Paslon(String capres, String cawapres, String partai) {}

    public record Caleg(String nama, String partai, int no_urut) {}

    public record Caleglagi(String nama, String partai, int no_urut) {}

    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);
        Map<String, String> riwayatVote = new HashMap<>();
        Map<String, Integer> jumlahSuaraCapres = new HashMap<>();
        Map<String, Integer> jumlahSuaraDPR = new HashMap<>();
        Map<String, Integer> jumlahSuaraDPRD = new HashMap<>();

        Paslon[] paslon = new Paslon[3];
        paslon[0] = new Paslon("Anies", "Muhaimin", "Nasdem");
        paslon[1] = new Paslon("Prabowo", "Gibran", "Gerindra");
        paslon[2] = new Paslon("Ganjar", "Mahfud", "PDIP");

        Caleg[] dpr = new Caleg[6];
        dpr[0] = new Caleg("Habib Syarief", "PKB", 1);
        dpr[1] = new Caleg("Melly Goeslaw", "Gerindra", 2);
        dpr[2] = new Caleg("Anang Setia", "PDIP", 3);
        dpr[3] = new Caleg("Nurul Arifin", "Golkar", 4);
        dpr[4] = new Caleg("M Farhan", "Nasdem", 5);
        dpr[5] = new Caleg("Hj Ledia", "PKS", 6);

        Caleglagi[] dprd = new Caleglagi[6];
        dprd[0] = new Caleglagi("Hadiat", "PKB", 1);
        dprd[1] = new Caleglagi("Hendi", "Gerindra", 2);
        dprd[2] = new Caleglagi("Hen Hen", "PDIP", 3);
        dprd[3] = new Caleglagi("Yasri", "Golkar", 4);
        dprd[4] = new Caleglagi("Imas", "Nasdem", 5);
        dprd[5] = new Caleglagi("Gun Gun", "PKS", 6);

        List<String[]> linkedList = new LinkedList<>();
        List<String[]> arrayList = new ArrayList<>();

        linkedList.add(new String[]{"Asep", "Bandung"});
        linkedList.add(new String[]{"Toni", "Bandung"});
//        linkedList.add(new String[]{"yana", "Bandung"});
//        linkedList.add(new String[]{"sohib", "Bandung"});

        arrayList.add(new String[]{" Capres Cawapres"});
        arrayList.add(new String[]{" DPR RI"});
        arrayList.add(new String[]{" DPRD"});

        boolean kembali = true;
        while (kembali) {
            System.out.println("||================= Menu Pemilihan ================||");
            System.out.println("||_________________||");
            System.out.println("||1. Tambah Peserta                                ||");
            System.out.println("||2. Lakukan Voting                                ||");
            System.out.println("||3. Riwayat Vote                                  ||");
            System.out.println("||4. Kategori dan paslon                           ||");
            System.out.println("||5. Keluar                                        ||");
            System.out.println("||=================================================||");

            System.out.print("Pilih menu (1-5): ");
            int menu = input.nextInt();
            input.nextLine(); // membersihkan buffer

            switch (menu) {
                case 1:
                    //Untuk menambah pesrta
                    System.out.println("||============== Menampilkan Peserta ==============||");
                    System.out.println("||_________________||");
                    //digunakan untuk memnggil setiap elemen dalam linkedList.
                    for (String[] peserta : linkedList) {
                        System.out.println("|| Nama : " + peserta[0]);
                        System.out.println("|| Alamat : " + peserta[1]);
                        System.out.println("||_________________||");
                    }

                    System.out.println("||================== Tambah Peserta ==============||");
                    System.out.println("||        Silakan untuk menambah peserta baru     ||");

                    Scanner scanner = new Scanner(System.in);
                    //inisialisasi
                    String nama = "";
                    String alamat = "";

                    while (nama.isEmpty() || alamat.isEmpty()) {
                        //untuk memastikan (nama dan alamat tidak boleh kosong).
                        System.out.println("||=================================================||");
                        System.out.print("|| Masukkan nama peserta: ");
                        nama = scanner.nextLine().trim();

                        System.out.print("|| Masukkan alamat peserta: ");
                        alamat = scanner.nextLine().trim();
                        System.out.println("||=================================================||");
                        if (nama.isEmpty() || alamat.isEmpty()) {
                            System.out.println("Nama dan alamat tidak boleh kosong. Silakan isi kembali.");
                            
                        }
                    }
                    System.out.println("||=================================================||");
                    String[] newPeserta = {nama, alamat};
                    linkedList.add(newPeserta);
                    System.out.println("Berhasil menambah peserta baru!");

                    System.out.println("||=================================================||");

                    break;

                case 2:
                    //untuk melakukan vot
                    System.out.println("||============== Menampilkan Peserta ==============||");
                    System.out.println("||_________________||");
                    for (String[] peserta1 : linkedList) {
                        System.out.println("||Nama : " + peserta1[0]);
                        System.out.println("||Alamat : " + peserta1[1]);
                        System.out.println("||_________________||");
                    }
                    System.out.println("||================= Pilih Nama Anda ===============||");
                    System.out.println("||_________________||");

                    int index = 1;
                    //digunakan untuk memproses setiap elemen dalam linkedList
                    for (String[] peserta1 : linkedList) {
                        System.out.println("|| " + index + ": " + peserta1[0]);
                        index++;
                    }
                    System.out.println("||_________________||");
                    System.out.print("|| Pilih nomor peserta: ");
                    int pilihindex = input.nextInt();

                    if (pilihindex >= 1 && pilihindex <= linkedList.size()) {
                        String[] pilihPeserta = linkedList.get(pilihindex - 1);
                        System.out.println("||=================== Nama Anda ===================||");
                        System.out.println("||_________________||");
                        System.out.println("|| Nama : " + pilihPeserta[0]);
                        System.out.println("|| Alamat : " + pilihPeserta[1]);

                        System.out.println("");
                        System.out.println("||=============== Kategori Pemilihan ==============||");
                        System.out.println("||_________________||");

                        index = 1;
                        //digunakan untuk memproses setiap elemen dalam arrayList
                        for (String[] kategori : arrayList) {
                            System.out.println("|| " + index + ": " + kategori[0]);
                            index++;
                        }
                        System.out.println("||_________________||");
                        System.out.print("|| Pilih nomor kategori: ");
                        int pilihkategori = input.nextInt();

                        if (pilihkategori >= 1 && pilihkategori <= arrayList.size()) {
                            String[] kategori = arrayList.get(pilihkategori - 1);
                            System.out.println("||============ Kategori Yang di Pilih =============||");
                            System.out.println("||_________________||");
                            System.out.println("|| Kategori : " + kategori[0]);

                            if (pilihkategori == 1) {
                                System.out.println("");
                                System.out.println("||================= Pilih Paslon ==================||");
                                System.out.println("||_________________||");

                                for (int i = 0; i < paslon.length; i++) {
                                    System.out.println("|| " + (i + 1) + ": " + paslon[i].capres + " - " + paslon[i].cawapres + " (" + paslon[i].partai + ")");
                                }
                                System.out.println("||_________________||");
                                System.out.print("|| Pilih nomor paslon: ");
                                int pilihPaslon = input.nextInt();

                                if (pilihPaslon >= 1 && pilihPaslon <= paslon.length) {
                                    String pilihan = paslon[pilihPaslon - 1].capres;
                                    jumlahSuaraCapres.put(pilihan, jumlahSuaraCapres.getOrDefault(pilihan, 0) + 1);
                                    riwayatVote.put(pilihPeserta[0], pilihan);
                                    System.out.println("Pilihan Anda untuk " + kategori[0] + ": " + pilihan);
                                } else {
                                    System.out.println("Pilihan paslon tidak valid!");
                                }
                            } else if (pilihkategori == 2) {
                                System.out.println("");
                                System.out.println("||================= Pilih Caleg ==================||");
                                System.out.println("||_________________||");

                                for (int i = 0; i < dpr.length; i++) {
                                    System.out.println("|| " + (i + 1) + ": " + dpr[i].nama + " - " + dpr[i].partai + " (No Urut: " + dpr[i].no_urut + ")");
                                }
                                System.out.println("||_________________||");
                                System.out.print("Pilih nomor caleg: ");
                                int pilihCaleg = input.nextInt();

                                if (pilihCaleg >= 1 && pilihCaleg <= dpr.length) {
                                    String pilihan = dpr[pilihCaleg - 1].nama;
                                    jumlahSuaraDPR.put(pilihan, jumlahSuaraDPR.getOrDefault(pilihan, 0) + 1);
                                    riwayatVote.put(pilihPeserta[0], pilihan);
                                    System.out.println("Pilihan Anda untuk " + kategori[0] + ": " + pilihan);
                                } else {
                                    System.out.println("Pilihan caleg tidak valid!");
                                }
                            } else if (pilihkategori == 3) {
                                System.out.println("");
                                System.out.println("||================= Pilih Caleg ==================||");
                                System.out.println("||_________________||");

                                for (int i = 0; i < dprd.length; i++) {
                                    System.out.println("|| " + (i + 1) + ": " + dprd[i].nama + " - " + dprd[i].partai + " (No Urut: " + dprd[i].no_urut + ")");
                                }
                                System.out.println("||_________________||");
                                System.out.print("Pilih nomor caleg: ");
                                int pilihCaleg = input.nextInt();

                                if (pilihCaleg >= 1 && pilihCaleg <= dprd.length) {
                                    String pilihan = dprd[pilihCaleg - 1].nama;
                                    jumlahSuaraDPRD.put(pilihan, jumlahSuaraDPRD.getOrDefault(pilihan, 0) + 1);
                                    riwayatVote.put(pilihPeserta[0], pilihan);
                                    System.out.println("Pilihan Anda untuk " + kategori[0] + ": " + pilihan);
                                } else {
                                    System.out.println("Pilihan caleg tidak valid!");
                                }
                            } else {
                                System.out.println("Pilihan kategori tidak valid!");
                            }

                        } else {
                            System.out.println("Pilihan kategori tidak valid!");
                        }

                    } else {
                        System.out.println("Pilihan nama tidak valid!");
                    }

                    break;
                    
                    case 3:
                        //melihat riwayat vot
                        System.out.println("||============== Lihat Riwayat Voting ==============||");
                        System.out.println("||_________________||");
                        
                        
                            //perulangan untuk memproses melalui riwayatVote
                            for (Map.Entry<String, String> entry : riwayatVote.entrySet()) {
                                String pemilih = entry.getKey();
                                String pilihan = entry.getValue();

                                String kategoriPilihan;
                                if (jumlahSuaraCapres.containsKey(pilihan)) {
                                    kategoriPilihan = "Capres & Cawapres";
                                } else if (jumlahSuaraDPR.containsKey(pilihan)) {
                                    kategoriPilihan = "DPR RI";
                                } else if (jumlahSuaraDPRD.containsKey(pilihan)) {
                                    kategoriPilihan = "DPRD";
                                } else {
                                    kategoriPilihan = "Kategori tidak ada";
                                }

                                System.out.println("|| Nama Pemilih: " + pemilih);
                                System.out.println("|| Kategori Pilihan: " + kategoriPilihan);
                                System.out.println("|| Nama Kandidat: " + pilihan);
                                
                                
                                if (kategoriPilihan.equals("Capres & Cawapres")) {
                                    System.out.println("|| Jumlah Suara: " + jumlahSuaraCapres.getOrDefault(pilihan, 0));
                                } else if (kategoriPilihan.equals("DPR RI")) {
                                    System.out.println("|| Jumlah Suara: " + jumlahSuaraDPR.getOrDefault(pilihan, 0));
                                } else if (kategoriPilihan.equals("DPRD")) {
                                    System.out.println("|| Jumlah Suara: " + jumlahSuaraDPRD.getOrDefault(pilihan, 0));
                                } else {
                                    System.out.println("|| Jumlah Suara: Data tidak tersedia");
                                }

                                System.out.println("||_________________||");
                            }

                    System.out.println("||============================================||");
                    break;
                   
                case 4:
                    //melihat data dari kategori dan paslon
                    System.out.println("");
                    System.out.println("||=============== Kategori Pemilihan ==============||");
                    System.out.println("||_________________||");
                    for (String[] kategori : arrayList) {
                        System.out.println("||" + kategori[0]);
                        System.out.println("||_________________||");
                    }

                    System.out.print("Pilih nomor kategori: ");
                    int pilihkategori = input.nextInt();

                    if (pilihkategori >= 1 && pilihkategori <= arrayList.size()) {
                        String[] kategori = arrayList.get(pilihkategori - 1);
                        System.out.println("||============ Kategori Yang di Pilih =============||");
                        System.out.println("||_________________||");
                        System.out.println("|| Kategori : " + kategori[0]);

                        switch (pilihkategori) {
                            case 1:
                                System.out.println("");
                                System.out.println("||=========== Capres & Cawapres ===========||");
                                for (Paslon calon : paslon) {
                                    System.out.println("||Nama Capres : " + calon.capres);
                                    System.out.println("||Nama Wapres : " + calon.cawapres);
                                    System.out.println("||Partai : " + calon.partai);
                                    System.out.println("||_________________||");
                                }
                                break;

                            case 2:
                                System.out.println("");
                                System.out.println("||================== DPR RI =================||");
                                for (Caleg calon : dpr) {
                                    System.out.println("||No Urut : " + calon.no_urut);
                                    System.out.println("||Nama Caleg : " + calon.nama);
                                    System.out.println("||Partai : " + calon.partai);
                                    System.out.println("||_________________||");
                                }
                                break;

                            case 3:
                                System.out.println("");
                                System.out.println("||================== DPRD ==================||");
                                for (Caleglagi calon : dprd) {
                                    System.out.println("||No Urut : " + calon.no_urut);
                                    System.out.println("||Nama Caleg : " + calon.nama);
                                    System.out.println("||Partai : " + calon.partai);
                                   System.out.println("||_________________||");
                                }
                                break;

                            default:
                                System.out.println("Pilihan kategori tidak valid!");
                                break;
                        }

                        System.out.println("||_________________||");
                        System.out.print("Ingin Melihat Jumlah Voting? (Y/N): ");
                        char sudahMemilih = input.next().charAt(0);

                        if (sudahMemilih == 'Y' || sudahMemilih == 'y') {
                            System.out.println("||================== Jumlah Suara =================||");
                            System.out.println("||_________________||");

                            if (pilihkategori == 1) {
                                for (Map.Entry<String, Integer> entry : jumlahSuaraCapres.entrySet()) {
                                    System.out.println("|| Paslon: " + entry.getKey() + " - Jumlah Suara: " + entry.getValue());
                                }
                            } else if (pilihkategori == 2) {
                                for (Map.Entry<String, Integer> entry : jumlahSuaraDPR.entrySet()) {
                                    System.out.println("|| Caleg: " + entry.getKey() + " - Jumlah Suara: " + entry.getValue());
                                }
                            } else if (pilihkategori == 3) {
                                for (Map.Entry<String, Integer> entry : jumlahSuaraDPRD.entrySet()) {
                                    System.out.println("|| Caleg: " + entry.getKey() + " - Jumlah Suara: " + entry.getValue());
                                }
                            }
                            System.out.println("||_________________||");
                        }
                    } else {
                        System.out.println("Pilihan kategori tidak valid!");
                    }

                    System.out.println("||=================================================||");
                    break;

                

                case 5:
                    //menyelesaikan program
                    System.out.println("Terima kasih. Program selesai.");
                    System.exit(0);

                    break;

                default:
                    System.out.println("Menu tidak valid. Silakan pilih menu yang sesuai.");
                    break;
            }
        }
    }
}
