# DES Pada Program Java

Bagas Wahyu Putratama 

Array Tabel initial permutation(IP) 
Tabel ini di gunakan untuk melakukan permutasi pada plaintext

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
Array Tabel PC1 
Di gunakan untuk melakukan permutasi awal pada key dalam proses enkripsi  

    	private static final byte[] PC1 = {
		57, 49, 41, 33, 25, 17, 9,
		1,  58, 50, 42, 34, 26, 18,
		10, 2,  59, 51, 43, 35, 27,
		19, 11, 3,  60, 52, 44, 36,
		63, 55, 47, 39, 31, 23, 15,
		7,  62, 54, 46, 38, 30, 22,
		14, 6,  61, 53, 45, 37, 29,
		21, 13, 5,  28, 20, 12, 4
	};
Array Tabel PC2
Tabel ini di gunakan untuk melakukan permutasi yang ke 2 pada key 
Setelah melalui Left Circular shift dalam proses enkripsi
	
    private static final byte[] PC2 = {
		14, 17, 11, 24, 1,  5,
		3,  28, 15, 6,  21, 10,
		23, 19, 12, 4,  26, 8,
		16, 7,  27, 20, 13, 2,
		41, 52, 31, 37, 47, 55,
		30, 40, 51, 45, 33, 48,
		44, 49, 39, 56, 34, 53,
		46, 42, 50, 36, 29, 32
	};
Array rotations Sebuah array yang di susun untuk menyimpan jumlah pergeseran/rotasi yang harus di lakukan pada setiap putaran/pergeseran

    private static final byte[] rotations = {
		1, 1, 2, 2, 2, 2, 2, 2, 1, 2, 2, 2, 2, 2, 2, 1
	};
	 
array E(Expand)
di gunakan untuk plaintext setelah melalui initial permutation (IP) dalam proses enkripsi
	
    private static final byte[] E = {
		32, 1,  2,  3,  4,  5,
		4,  5,  6,  7,  8,  9,
		8,  9,  10, 11, 12, 13,
		12, 13, 14, 15, 16, 17,
		16, 17, 18, 19, 20, 21,
		20, 21, 22, 23, 24, 25,
		24, 25, 26, 27, 28, 29,
		28, 29, 30, 31, 32, 1
	};
	
array s-box
terdiri dari 64 bit (16 kolom dan 4 baris) pada masing-masing s-box
	
    private static final byte[][] S = { {
		14, 4,  13, 1,  2,  15, 11, 8,  3,  10, 6,  12, 5,  9,  0,  7,
		0,  15, 7,  4,  14, 2,  13, 1,  10, 6,  12, 11, 9,  5,  3,  8,
		4,  1,  14, 8,  13, 6,  2,  11, 15, 12, 9,  7,  3,  10, 5,  0,
		15, 12, 8,  2,  4,  9,  1,  7,  5,  11, 3,  14, 10, 0,  6,  13
	}, {
		15, 1,  8,  14, 6,  11, 3,  4,  9,  7,  2,  13, 12, 0,  5,  10,
		3,  13, 4,  7,  15, 2,  8,  14, 12, 0,  1,  10, 6,  9,  11, 5,
		0,  14, 7,  11, 10, 4,  13, 1,  5,  8,  12, 6,  9,  3,  2,  15,
		13, 8,  10, 1,  3,  15, 4,  2,  11, 6,  7,  12, 0,  5,  14, 9
	}, {
		10, 0,  9,  14, 6,  3,  15, 5,  1,  13, 12, 7,  11, 4,  2,  8,
		13, 7,  0,  9,  3,  4,  6,  10, 2,  8,  5,  14, 12, 11, 15, 1,
		13, 6,  4,  9,  8,  15, 3,  0,  11, 1,  2,  12, 5,  10, 14, 7,
		1,  10, 13, 0,  6,  9,  8,  7,  4,  15, 14, 3,  11, 5,  2,  12
	}, {
		7,  13, 14, 3,  0,  6,  9,  10, 1,  2,  8,  5,  11, 12, 4,  15,
		13, 8,  11, 5,  6,  15, 0,  3,  4,  7,  2,  12, 1,  10, 14, 9,
		10, 6,  9,  0,  12, 11, 7,  13, 15, 1,  3,  14, 5,  2,  8,  4,
		3,  15, 0,  6,  10, 1,  13, 8,  9,  4,  5,  11, 12, 7,  2,  14
	}, {
		2,  12, 4,  1,  7,  10, 11, 6,  8,  5,  3,  15, 13, 0,  14, 9,
		14, 11, 2,  12, 4,  7,  13, 1,  5,  0,  15, 10, 3,  9,  8,  6,
		4,  2,  1,  11, 10, 13, 7,  8,  15, 9,  12, 5,  6,  3,  0,  14,
		11, 8,  12, 7,  1,  14, 2,  13, 6,  15, 0,  9,  10, 4,  5,  3
	}, {
		12, 1,  10, 15, 9,  2,  6,  8,  0,  13, 3,  4,  14, 7,  5,  11,
		10, 15, 4,  2,  7,  12, 9,  5,  6,  1,  13, 14, 0,  11, 3,  8,
		9,  14, 15, 5,  2,  8,  12, 3,  7,  0,  4,  10, 1,  13, 11, 6,
		4,  3,  2,  12, 9,  5,  15, 10, 11, 14, 1,  7,  6,  0,  8,  13
	}, {
		4,  11, 2,  14, 15, 0,  8,  13, 3,  12, 9,  7,  5,  10, 6,  1,
		13, 0,  11, 7,  4,  9,  1,  10, 14, 3,  5,  12, 2,  15, 8,  6,
		1,  4,  11, 13, 12, 3,  7,  14, 10, 15, 6,  8,  0,  5,  9,  2,
		6,  11, 13, 8,  1,  4,  10, 7,  9,  5,  0,  15, 14, 2,  3,  12
	}, {
		13, 2,  8,  4,  6,  15, 11, 1,  10, 9,  3,  14, 5,  0,  12, 7,
		1,  15, 13, 8,  10, 3,  7,  4,  12, 5,  6,  11, 0,  14, 9,  2,
		7,  11, 4,  1,  9,  12, 14, 2,  0,  6,  10, 13, 15, 3,  5,  8,
		2,  1,  14, 7,  4,  10, 8,  13, 15, 12, 9,  0,  3,  5,  6,  11
	} };
	
array permutasi 

    private static final byte[] P = {
		16, 7,  20, 21,
		29, 12, 28, 17,
		1,  15, 23, 26,
		5,  18, 31, 10,
		2,  8,  24, 14,
		32, 27, 3,  9,
		19, 13, 30, 6,
		22, 11, 4,  25
	};
	
array permutasi akhir atau inverse permutasi

    private static final byte[] FP = {
		40, 8, 48, 16, 56, 24, 64, 32,
		39, 7, 47, 15, 55, 23, 63, 31,
		38, 6, 46, 14, 54, 22, 62, 30,
		37, 5, 45, 13, 53, 21, 61, 29,
		36, 4, 44, 12, 52, 20, 60, 28,
		35, 3, 43, 11, 51, 19, 59, 27,
		34, 2, 42, 10, 50, 18, 58, 26,
		33, 1, 41, 9, 49, 17, 57, 25
	};
	
key di bagi 2 masing-masing menjadi 28 bit dengan inisial C dan D
sebelum nantinya dilakukan perputaran (left circular shift)

    private static int[] C = new int[28];
	  private static int[] D = new int[28];
plaintext yang sudah dijadikan biner maka setiap bitnya dimasukan ke dalam urutan array tabel IP melalui fungsi berikut
		
    int newBits[] = new int[inputBits.length];
		for(int i=0 ; i < inputBits.length ; i++) {
			newBits[i] = inputBits[IP[i]-1];
		}
kemudian plaintext yang sudah melalui tahap IP maka plaintext tersebut di bagi 2 masing-masing 32 bit dengan inisial L dan R
dengan fungsi berikut

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
RotationTimes merupakan variabel yang digunakan untuk menampung array rotations
yang fungsinya untuk mengatur berapa banyak pergeseran untuk diselesaikan 

    int rotationTimes = (int) rotations[round];
		C1 = leftShift(C, rotationTimes);
		D1 = leftShift(D, rotationTimes);
selanjutnya C1 dan D1 di tampung dalam sebuah variabel yaitu CnDn yang berisikan 56 bit gabungan dari bit C1 dan D1 	
  
    int CnDn[] = new int[56];
		System.arraycopy(C1, 0, CnDn, 0, 28);
		System.arraycopy(D1, 0, CnDn, 28, 28);
setelah itu CnDn di masukan kedalam proses array tabel PC2, hasil dari proses tersebut akan mengubah yang tadinya 56 bit menjadi 48 bit 		
    
		int Kn[] = new int[48];
		for(int i=0 ; i < Kn.length ; i++) {
			Kn[i] = CnDn[PC2[i]-1];
		}
tahap expand dimana plaintext bagian R yang memilki 32 bit di masukan ke dalam proses array E. Hasil dari tahap tersebut akan mengubah yang tadinya 32 bit menjadi 48 bit

    int expandedR[] = new int[48];
		for(int i=0 ; i < 48 ; i++) {
			expandedR[i] = R[E[i]-1];
		}
variabel temp menampung proses xor dimana R yang sudah di expand dan key yang sudah melalui proses PC2

    int temp[] = xor(expandedR, roundKey);    
nilai a merupakan R yang sudah di expand dan nilai b merupakan key yang sudah melalui proses PC2, berikut merupakan fungsi untuk melakukan xor 

    private static int[] xor(int[] a, int[] b) {
		int answer[] = new int[a.length];
		for(int i=0 ; i < a.length ; i++) {
			answer[i] = a[i]^b[i];
		}
		return answer;
	}
berikut ini adalah fungsi yang di gunakan untuk melakukan pergeseran/rotasi

     private static int[] leftShift(int[] bits, int n) {
   
pergeseran kiri terjadi di sini, i.n. setiap bit diputar ke kiri dan bit paling kiri disimpan di bit paling kanan. Ini adalah operasi left shift

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
	
	
