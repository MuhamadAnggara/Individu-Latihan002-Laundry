```dart
// fungsi enum untuk bs memilih tipe laundry

enum TipeLaundry { biasa, kilat}

// class buat nampung data cucian yang ada

class Cucian {
  int noNota;
  double berat;
  TipeLaundry tipe;
  
  Cucian(this.noNota, this.berat, this.tipe);
}

// fungsinya buat ngecek apakah beratnya (minumum 2kg)

double cekBerat(double b) {
  if (b < 2.0) {
    return 2.0;
  } else {
    return b;
  }
}

// fungsi utamanya adalah buat menghitung duitnya

double hitungTotal(Cucian data) {
  
  double beratAsli = cekBerat(data.berat);
  double hargaDasar = beratAsli * 7000;
  
  // cek kalau misalnya dia milih kilat (express) kena charge 50%
  if (data.tipe == TipeLaundry.kilat) {
    double biayaTambahan = hargaDasar * 0.5;
    return hargaDasar + biayaTambahan;
  } else {
    return hargaDasar;
  }
}

void main() {
  
  List<Cucian> daftarPelanggan = [
    Cucian(1, 1.5, TipeLaundry.biasa),
    Cucian(2, 3.0, TipeLaundry.biasa),
    Cucian(3, 1.5, TipeLaundry.kilat),
    Cucian(4, 4.0, TipeLaundry.kilat),
    Cucian(5, 2.0, TipeLaundry.biasa),
  ];
  
  print("=== PROGRAM LAUNDRY CUCIAN");
  
  // Loop di pakai untuk for buat nampilin semua data laundry
  
  for (int i = 0; i < daftarPelanggan.length; i++) {
    var p = daftarPelanggan[i];
    double tagihan = hitungTotal(p);
    
    // mengubah tulisan enum menjadi string agar bisa di print <>
    
    String namaTipe = "";
    if (p.tipe == TipeLaundry.biasa) {
      namaTipe = "Reguler";
    } else {
      namaTipe = "Express";
    }
    
    print("Nota No : ${p.noNota}");
    print("Berat   : ${p.berat} KG");
    print("Paket   : $namaTipe");
    print("Bayar   : Rp${tagihan.toInt()}");
    print("------------------------------");
  }
}
```
