
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

