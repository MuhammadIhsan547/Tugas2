# AplikasiCekNomorGenapGanjil
 Tugas2 - Muhammad Ihsan - 2210010286
Berikut adalah file README yang bisa langsung Anda salin dan gunakan:

---

# Aplikasi Konversi Suhu

### Deskripsi Program
Aplikasi ini adalah program GUI sederhana untuk mengonversi nilai suhu antara berbagai skala: Celsius, Fahrenheit, Kelvin, dan Reamur. Pengguna dapat:
1. Memasukkan nilai suhu.
2. Memilih skala awal menggunakan JRadioButton.
3. Memilih skala tujuan konversi melalui JComboBox.
4. Hasil konversi ditampilkan langsung setelah tombol ditekan, atau secara otomatis jika fitur perubahan langsung diaktifkan.

---

### Komponen GUI yang Digunakan
1. **JFrame**: Sebagai jendela utama aplikasi.
2. **JPanel**: Untuk mengelompokkan dan mengatur tata letak komponen.
3. **JLabel**: Memberikan keterangan untuk setiap komponen.
4. **JTextField**: Tempat pengguna memasukkan nilai suhu.
5. **JComboBox**: Untuk memilih jenis konversi.
6. **JButton**: Tombol untuk menjalankan atau mereset proses konversi.
7. **JRadioButton**: Pilihan skala suhu awal.

---

### Logika Program
1. **Rumus Konversi**:
   - Setiap jenis konversi memiliki rumus matematis yang sesuai untuk mengonversi suhu antara skala yang dipilih.
2. **Validasi Input**:
   - Hanya angka yang diizinkan sebagai input. Pesan kesalahan akan muncul jika input tidak valid.
3. **Fitur Tambahan**:
   - Konversi otomatis saat input berubah.

---

### Events yang Digunakan
1. **ActionListener**:
   - Digunakan untuk mendeteksi klik pada tombol konversi. 
   - Tombol akan memicu logika konversi berdasarkan pilihan pengguna.
2. **KeyAdapter**:
   - Membatasi input hanya angka pada JTextField.
3. **ItemListener**:
   - Digunakan pada JRadioButton untuk mengubah daftar pilihan pada JComboBox berdasarkan skala suhu awal yang dipilih.
4. **DocumentListener**:
   - Untuk mengaktifkan konversi otomatis setiap kali nilai pada JTextField berubah.

---

### Cara Menggunakan Aplikasi
1. Pilih skala suhu awal menggunakan JRadioButton (Celsius, Fahrenheit, Kelvin, Reamur).
2. Masukkan nilai suhu pada JTextField.
3. Pilih jenis konversi pada JComboBox.
4. Klik tombol **Konversi** untuk melihat hasil. Atau biarkan sistem menghitung otomatis saat Anda mengetik.

---

### Variasi Fitur
- Tambahan skala suhu seperti Reamur dan Kelvin.
- Fitur konversi otomatis saat nilai input berubah.
- Validasi input yang lebih ketat untuk memastikan pengguna hanya memasukkan angka.

---

### Contoh Tampilan Kode untuk Event dan Variasi

**1. Event KeyAdapter pada JTextField (InputanSuhu):**
```java
private void InputanSuhuKeyTyped(java.awt.event.KeyEvent evt) {                                     
    char c = evt.getKeyChar();
    if (!Character.isDigit(c) && c != '.') { // Hanya angka dan titik yang diizinkan
        evt.consume();
    }
}
```

**2. Event ItemListener pada JRadioButton:**
```java
private void jRadioButtonCelsiusItemStateChanged(java.awt.event.ItemEvent evt) {
    if (evt.getStateChange() == ItemEvent.SELECTED) {
        ComboBoxKonversi.removeAllItems();
        ComboBoxKonversi.addItem("Celsius ke Fahrenheit");
        ComboBoxKonversi.addItem("Celsius ke Kelvin");
        ComboBoxKonversi.addItem("Celsius ke Reamur");
    }
}
```

**3. Event ActionListener untuk Tombol Konversi:**
```java
private void TombolHitungActionPerformed(java.awt.event.ActionEvent evt) {
    try {
        double inputSuhu = Double.parseDouble(InputanSuhu.getText());
        String hasilKonversi = (String) ComboBoxKonversi.getSelectedItem();
        double hasil = 0.0;

        // Logika konversi berdasarkan skala yang dipilih
        if (jRadioButtonCelsius.isSelected()) {
            switch (hasilKonversi) {
                case "Celsius ke Fahrenheit":
                    hasil = celsiusToFahrenheit(inputSuhu);
                    break;
                case "Celsius ke Kelvin":
                    hasil = celsiusToKelvin(inputSuhu);
                    break;
                case "Celsius ke Reamur":
                    hasil = celsiusToReamur(inputSuhu);
                    break;
                default:
                    JOptionPane.showMessageDialog(this, "Pilihan konversi tidak valid!");
                    return;
            }
        }
        // Skala lainnya seperti Fahrenheit, Kelvin, dan Reamur mengikuti pola serupa
        HasilKonversi.setText("" + hasil);
    } catch (NumberFormatException e) {
        JOptionPane.showMessageDialog(this, "Masukkan angka yang valid!");
    }
}
```

**4. Konversi Otomatis (DocumentListener):**
```java
private void setupDocumentListener() {    
    InputanSuhu.getDocument().addDocumentListener(new javax.swing.event.DocumentListener() {
        @Override
        public void insertUpdate(javax.swing.event.DocumentEvent e) {
            TombolHitungActionPerformed(null);
        }

        @Override
        public void removeUpdate(javax.swing.event.DocumentEvent e) {
            TombolHitungActionPerformed(null);
        }

        @Override
        public void changedUpdate(javax.swing.event.DocumentEvent e) {
            TombolHitungActionPerformed(null);
        }
    });
}
```

---

### Pembuat
**Nama Pembuat:** Muhammad Ihsan  
**NPM:** 2210010286 

**Kelas:** 5A Ti Reg Pagi BJM

---

Silakan sesuaikan nama dan tanggal pembuatan sesuai dengan kebutuhan Anda.
        @Override
        public void changedUpdate(javax.swing.event.DocumentEvent e) {
            TombolHitungActionPerformed(null);
        }
    });
}
```
