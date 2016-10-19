# kontribusi kelompok 7
1. ikut hadir pada saat presentasi
2. membantu dalam proses pencarian referensi
3. membantu dalam proses IP sampai Leftshift namun dalam bahasa pemrograman java yang nantinya akan di ubah ke dalam bahasa pemrograman php :

Array Tabel initial permutation(IP) Tabel ini di gunakan untuk melakukan permutasi awal pada plaintext dalam proses enkripsi

      private static final byte[] IP = { 
      58, 50, 42, 34, 26, 18, 10, 2,
      60, 52, 44, 36, 28, 20, 12, 4,
      62, 54, 46, 38, 30, 22, 14, 6,
      64, 56, 48, 40, 32, 24, 16, 8,
      57, 49, 41, 33, 25, 17, 9,  1,
      59, 51, 43, 35, 27, 19, 11, 3,
      61, 53, 45, 37, 29, 21, 13, 5,
      63, 55, 47, 39, 31, 23, 15, 7 
      };
Array Tabel PC1 Di gunakan untuk melakukan permutasi awal pada key dalam proses enkripsi

    private static final byte[] PC1 = {
    57, 49, 41, 33, 25, 17, 9,
    1,  58, 50, 42, 34, 26, 18,
    10, 2,  59, 51, 43, 35, 27,
    19, 11, 3,  60, 52, 44, 36,
    63, 55, 47, 39, 31, 23, 15,
    7,  62, 54, 46, 38, 30, 22,
    14, 6,  61, 53, 45, 37, 29,
    21, 13, 5,  28, 20, 12, 4
Array rotations Sebuah array yang di susun untuk menyimpan jumlah pergeseran/rotasi yang harus di lakukan pada setiap putaran/pergeseran

      private static final byte[] rotations = {
      1, 1, 2, 2, 2, 2, 2, 2, 1, 2, 2, 2, 2, 2, 2, 1
      };
plaintext yang sudah dijadikan biner maka setiap bitnya dimasukan ke dalam urutan array tabel IP melalui fungsi berikut

      int newBits[] = new int[inputBits.length];
      for(int i=0 ; i < inputBits.length ; i++) {
        newBits[i] = inputBits[IP[i]-1];
      }
kemudian plaintext yang sudah melalui tahap IP maka plaintext tersebut di bagi 2 masing-masing 32 bit dengan inisial L dan R dengan fungsi berikut

      int L[] = new int[32];
      int R[] = new int[32];
      int i;
fungsi berikut merupakan tahap pembagian key menjadi 2 yaitu C dan D yang masing-masing memiliki 28 bit sedangkan 8 bit terakhir di hilangkan

dimana C dimulai dari bit 0-27

      for(i=0 ; i < 28 ; i++) {
        C[i] = keyBits[PC1[i]-1];
      }
sedangkan D dimulai dari bit 28-55

      for( ; i < 56 ; i++) {
        D[i-28] = keyBits[PC1[i]-1];
      }

C1 dan D1 merupakan sebuah nilai baru dari C dan D yang mana akan dilakukan perubahan yaitu rotasi

      int C1[] = new int[28];
      int D1[] = new int[28];
RotationTimes merupakan variabel yang digunakan untuk menampung array rotations yang fungsinya untuk mengatur berapa banyak pergeseran untuk diselesaikan

      int rotationTimes = (int) rotations[round];  
        C1 = leftShift(C, rotationTimes);
        D1 = leftShift(D, rotationTimes);
selanjutnya C1 dan D1 di tampung dalam sebuah variabel yaitu CnDn yang berisikan 56 bit gabungan dari bit C1 dan D1

      int CnDn[] = new int[56];
      System.arraycopy(C1, 0, CnDn, 0, 28);
      System.arraycopy(D1, 0, CnDn, 28, 28);

berikut ini adalah fungsi yang di gunakan untuk melakukan pergeseran/rotasi

(n) berfungsi sebagai jumlah pergeseran bits

      private static int[] leftShift(int[], int n) {
nantinya pergeseran key yang sudah di bagi 2 menjadi C dan D terjadi di sini, yang mana bit awal di geser ke bit terakhir dan sisanya setiap bit digeser ke kiri

      int answer[] = new int[bits.length];
      System.arraycopy(bits, 0, answer, 0, bits.length);
      for(int i=0 ; i < n ; i++) {
        int temp = answer[0];
        for(int j=0 ; j < bits.length-1 ; j++) {
            answer[j] = answer[j+1];
        }
        answer[bits.length-1] = temp;
      }
      return answer;
      }
