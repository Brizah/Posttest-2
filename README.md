
#file minuman

    package project.minuman;
    import java.text.DecimalFormat;

    public final class Minuman {
    private final String namaMinuman;
    private final String jenisMinuman;
    private double harga;

    public Minuman(String namaMinuman, String jenisMinuman, double harga) {
        this.namaMinuman = namaMinuman;
        this.jenisMinuman = jenisMinuman;
        this.harga = harga;
    }

    public String getNamaMinuman() {
        return namaMinuman;
    }

    public String getJenisMinuman() {
        return jenisMinuman;
    }

    public double getHarga() {
        return harga;
    }

    public final void setHarga(double harga) {
        this.harga = harga;
    }



    
     public String toString() {
        DecimalFormat decimalFormat = new DecimalFormat("#,##0.00");
        String formattedPrice = decimalFormat.format(harga);

        return "NamaMinuman: " + namaMinuman + ", Jenis: " + jenisMinuman + ", Harga: Rp " + formattedPrice;
    }

       
}

Deklarasi Kelas Minuman:
Kode dimulai dengan deklarasi kelas Minuman dengan aksesibilitas default, yang berarti kelas ini 
dapat diakses dari dalam paket yang sama.
Atribut Kelas Minuman:
Kode berisi beberapa atribut (variabel) yang digunakan untuk merepresentasikan minuman:
namaMinuman: Ini adalah atribut yang menyimpan nama minuman, seperti "Kopi Hitam" atau "Teh 
Manis".
jenis: Ini adalah atribut yang menyimpan jenis minuman, misalnya, "Kopi" atau "Teh".
harga: Ini adalah atribut yang menyimpan harga minuman dalam bentuk bilangan pecahan.
Konstruktor Minuman:
Kelas Minuman memiliki sebuah konstruktor yang digunakan untuk membuat objek Minuman. 
Konstruktor ini memiliki tiga parameter, yaitu namaMinuman, jenisMinuman, dan harga, yang 
digunakan untuk menginisialisasi atribut-atribut objek Minuman saat objek dibuat.
Metode getNamaMinuman, getJenisMinuman, dan getHarga:
Kode ini menyediakan tiga metode publik untuk mengambil nilai dari atribut-atribut objek Minuman.
getNamaMinuman(): Mengembalikan nama minuman.
getJenisMinuman(): Mengembalikan jenis minuman.
getHarga(): Mengembalikan harga minuman.
Metode setHarga:
Metode setHarga() adalah metode publik yang memungkinkan Anda mengubah harga minuman. 
Dengan metode ini, Anda dapat memperbarui harga minuman


#File postest 2
                        
    package project.posstest2;
    import java.util.ArrayList;
    import java.util.Scanner;
    import java.util.Iterator;
    import project.minuman.Minuman;

    public  final class Posstest2 {
    
    public final static void main(String[] args) {
        ArrayList<Minuman> daftarMinuman = new ArrayList<>();
        Scanner scanner = new Scanner(System.in);
        
        while (true) {
            System.out.println("Menu:");
            System.out.println("1. Tambah Menu Minuman");
            System.out.println("2. Lihat Daftar Minuman");
            System.out.println("3. Cari Menu Minuman");
            System.out.println("4. Update Menu Minuman");
            System.out.println("5. Hapus Menu Minuman");
            System.out.println("6. Keluar");
            System.out.print("Pilihan Anda: ");

            String pilihan = scanner.nextLine();

            switch (pilihan) {
                case "1":
                    System.out.print("Masukkan Nama Minuman: ");
                    String namaMinuman = scanner.nextLine();
                    System.out.print("Masukkan Jenis Minuman: ");
                    String jenisMinuman= scanner.nextLine();
                    System.out.print("Masukkan Harga Minuman: ");
                    double harga = Double.parseDouble(scanner.nextLine());

                    Minuman C = new Minuman(namaMinuman, jenisMinuman, harga);
                    daftarMinuman.add(C);
                    System.out.println("Menu Minuman berhasil ditambahkan!");
                    break;

                case "2":
                    if (daftarMinuman.isEmpty()) {
                        System.out.println("Daftar Menu Minuman Tidak Ada");
                    } else {
                        System.out.println("Daftar Minuman:");
                        for (Minuman M : daftarMinuman) {
                            System.out.println(M);
                        }
                    }
                    break;

                case "3":
                    System.out.print("Masukkan Nama Minuman yang dicari: ");
                    String cariNamaMinuman = scanner.nextLine();
                    boolean ditemukan = false;

                    for (Minuman p : daftarMinuman) {
                        if (p.getNamaMinuman().equalsIgnoreCase(cariNamaMinuman)) {
                            System.out.println("Minuman ditemukan:");
                            System.out.println(p);
                            ditemukan = true;
                            break;
                        }
                    }

                    if (!ditemukan) {
                        System.out.println("Minuman tidak ditemukan.");
                    }
                    break;

                    
                case "4":
                    System.out.print("Masukkan Nama menu Minuman yang akan diupdate: ");
                    String namaUpdate = scanner.nextLine();
                    boolean ditemukanUpdate = false;

                    for (int i = 0; i < daftarMinuman.size(); i++) {
                        Minuman B = daftarMinuman.get(i);
                        if (B.getNamaMinuman().equalsIgnoreCase(namaUpdate)) {
                            System.out.print("Masukkan Nama Baru: ");
                            String namaBaru = scanner.nextLine();

                            System.out.print("Masukkan Jenis Baru: ");
                            String jenisBaru = scanner.nextLine();

                            System.out.print("Masukkan Harga Baru: ");
                            double hargaBaru = Double.parseDouble(scanner.nextLine())
                                    
                                    
                                    
                                    ;

                            
                            Minuman menuMinumanBaru = new Minuman(namaBaru, jenisBaru, hargaBaru);

                            
                            daftarMinuman.set(i, menuMinumanBaru);

                            System.out.println("Menu minuman berhasil diupdate!");
                            ditemukanUpdate = true;
                            break;
                        }
                    }

                    if (!ditemukanUpdate) {
                        System.out.println("Menu minuman tidak ditemukan.");
                    }
                    break;


                    
                case "5":
                    System.out.print("Masukan nama menu minuman yg ingin dihapus:");
                    String namaMinumanHapus = scanner.nextLine();

                    
                    Iterator<Minuman> iterator = daftarMinuman.iterator();
                    while (iterator.hasNext()) {
                        Minuman menuMinumann = iterator.next();
                        if (menuMinumann.getNamaMinuman().equalsIgnoreCase(namaMinumanHapus)) {
                            iterator.remove(); 
                        }
                    }
                    break;
               

                    
                case "6":
                    System.out.println("Terima kasih!");
                    scanner.close();
                    System.exit(0);

                default:
                    System.out.println("Pilihan tidak valid. Silakan pilih lagi.");
            }
        }
    }
}

Deklarasi dan Import:
Kode pertama mencakup deklarasi paket dan impor beberapa paket Java yang dibutuhkan untuk 
berfungsi dengan baik. Ini termasuk impor dari paket java.util dan impor dari paket 
project.minuman.Minuman yang mengacu pada kelas Minuman dari proyek yang berbeda.

Deklarasi Kelas Posstest2:
Kode ini mendeklarasikan kelas Posstest2. Kelas ini memiliki metode main yang digunakan sebagai 
titik masuk program.
Inisialisasi ArrayList dan Scanner:
Pada awal metode main, ArrayList dengan nama daftarMinuman digunakan untuk menyimpan 
daftar minuman yang diatur oleh pengguna. Scanner juga diinisialisasi untuk mengambil input dari 
pengguna.

Opsi 1: Tambah Menu Minuman:
![Screenshot 2023-10-12 211555](https://github.com/Brizah/Posttest-2/assets/126450007/b361fc29-b5e0-4871-9b8a-a2181654d16a)

Jika pengguna memilih opsi 1, program akan meminta nama minuman, jenis minuman, dan harga 
minuman. Kemudian, sebuah objek Minuman dibuat dengan informasi ini dan ditambahkan ke 
ArrayList daftarMinuman.

Opsi 2: Lihat Daftar Minuman:
![Screenshot 2023-10-12 211648](https://github.com/Brizah/Posttest-2/assets/126450007/2ca44fb8-7e3a-4c90-8c9c-e7153f3887e1)

Opsi ini digunakan untuk melihat daftar minuman yang telah ditambahkan. Program akan 
menampilkan daftar menu minuman yang ada di dalam daftarMinuman.

Opsi 3: Cari Menu Minuman:
![Screenshot 2023-10-12 211721](https://github.com/Brizah/Posttest-2/assets/126450007/bb146b01-d9ef-4645-84c9-ce2776cd841a)

Pengguna dapat mencari minuman berdasarkan nama. Program akan mencocokkan nama yang 
dimasukkan dengan nama minuman dalam daftarMinuman dan menampilkan hasilnya.

Opsi 4: Update Menu Minuman:
![Screenshot 2023-10-12 211805](https://github.com/Brizah/Posttest-2/assets/126450007/d028f706-48a9-4d43-8356-55cdc7d76e93)

Pengguna dapat mengupdate menu minuman dengan memasukkan nama menu yang ingin 
diupdate. Jika menu tersebut ditemukan, pengguna diminta untuk memasukkan informasi baru 
seperti nama, jenis, dan harga minuman. Menu minuman yang ada akan diupdate sesuai dengan 
input pengguna.

Opsi 5: Hapus Menu Minuman:
![Screenshot 2023-10-12 211909](https://github.com/Brizah/Posttest-2/assets/126450007/72c4ac59-4872-41a0-a179-66affc488aad)

Pengguna dapat menghapus menu minuman dengan memasukkan nama menu yang ingin dihapus. 
Program akan mencari menu tersebut dalam daftarMinuman dan menghapusnya jika ditemukan.

Opsi 6: Keluar:
Jika pengguna memilih opsi 6, program akan mengakhiri aplikasi setelah menampilkan pesan terima 
kasih dan menutup Scanner



