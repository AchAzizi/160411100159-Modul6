# Rangkuman-Modul6
# Searching

Searching merupakan proses yang fundamental dalam pengolahan data.
Proses pensarian adalah menemukan nilai(data) tertentu didalam sekumpulan data yang bertipe sama
(baik bertipe dasar maupun bertipe bentukan).

Pada umumnya, proses pencarian data ini menghasilkan posisi data yang dicari terhadap keseluruhan data, akan tetapi untuk pencarian data yang sederhana, nilai True atau False saja yang dihasilkan, nilai ini menandakan apakah data berada di sekumpulan data ataukah tidak. Proses pencarian sederhana ini sudah disediakan oleh python dengan menggunakan syntax in, seperti contoh berikut:

	a=[12,5,9,8,1,10,26]
	11 in a

	12 in a

	15 in a



# Sequential search.

Sequential Search merupakan teknik pencarian data dengan cara membandingkan data yang dicari dengan seluruh data yang terdapat pada kumpulan data secara satu persatu, mulai dari data pertama sampai dengan data terakhir.

*Terdapat dua konsep untuk sequential search berdasarkan kumpulan data yang akan dicari, yaitu :

Unordered List Sequential Search

Ordered List Sequential Search

Unordered List Sequential Search
Pada unordered list sequential search, data berada pada keadaan acak, tidak terurut, sehingga pencarian harus dilakukan mulai dari indeks awal sampai indeks terakhir dari data, atau pencarian berhenti ketika data sudah ditemukan

Terdapat dua konsep untuk sequential search berdasarkan kumpulan data yang akan dicari, yaitu
1. unordered list sequential search.

		def seqSearch(listData, data):
				ind = 0
				found = False
				while ind < len(listData) and not found:
				if listData[ind] == data:
						found = True
				else:
						ind = ind+1
				return found

		a=[12,5,9,8,1,10,26]

		seqSearch(a,1)
	
	
2. Ordered List Sequential Search

		def orderedSeqSearch(listData, data):
				ind = 0
				found = False
				stop = False
				position=[]
				while ind < len(listData) and not found and not stop:
				if listData[ind] == data:
						found = True
						position.append(ind)
				else:
						if listData[ind] > data:
						stop = True
						else:
						ind = ind+1
		if found:
    		return ind
		else:
    		return ('Data tidak ada')
		
		a=[1,1,5,5,5,8,9,10,12,26]

		ind=orderedSeqSearch(a,5)
		print(ind)
		B. Binary Search


# Binary Search
adalah salah satu metode pencarian atau pengecekan sebuah elemen angka di dalam sebuah wadah. Jika di dalam wadah terdapat elemen angka yang dicari oleh user, maka program tersebut akan mengembalikan statement True. Begitu pun sebaliknya, jika di dalam wadah tersebut tidak terdapat elemen angka yang dicari oleh user maka program tersebut akan mengembalikan statement False.

Point penting yang harus kalian perhatikan disini adalah metode ini hanya bisa digunakan untuk wadah dengan angka yang sudah urut (wadah dengan elemen angka dari kecil ke besar). Program ini akan sangat berguna ketika wadah yang user gunakan mengandung banyak sekali elemen angka di dalamnya

1. Code binary search dengan metode iteratif

		def binarySearch(listData, data):
				first = 0
				last = len(listData) - 1
				found = False

				while first <= last and not found:
				midpoint = (first + last) // 2
				if listData[midpoint] == data:
						found = True
    		else:
        			if data < listData[midpoint]:
            			last = midpoint - 1
        			else:
            			first = midpoint + 1

		return found
	
		a=[4,6,10,34,56,78,99]
		print(binarySearch(a,34))


2. Code binary search dengan metode rekursif

		def binarySearch2(listData, data):
				if len(listData) == 0:
				return False
				else:
				midpoint = len(listData) // 2
    		if listData[midpoint] == data:
        			return True
    		else:
        			if data < listData[midpoint]:
            
            			return binarySearch2(listData[first:last+1], data)
        			else:
            
            			return binarySearch2(listData[midpoint + 1:], data)

		a=[4,6,10,34,56,78,99]

		binarySearch2(a,78)
    


# Soal Praktikum 
1. Buatlah fungsi sequential search (dapat juga menemukan posisi-posisi dari data yang sama), dengan argument atau parameter berupa :
	a. data yang akan dicari
	b. list data dari data yang akan dicari
   Sedangkan return value dari fungsi ini berupa:
	a. indeks-indeks atau posisi dari data yang dicari pada list (jika data ditemukan), dan ‘Data tidak ada’ jika data tidak 		   ditemukan.
	b. Jumlah iterasi yang diperlukan selama proses pencarian
	
Contoh hasil eksekusi dapat dilihat sebagai berikut :

		a = [1, 5, 9, 8, 1, 5, 10, 26, 5, 12]

		[hasil, jumlahIterasi]=seqSearch(a,0)
		print('Posisi Data=', hasil)
		print('Jumlah Iterasi=', jumlahIterasi)

		Posisi Data= Data tidak ada
		Jumlah Iterasi= 10
			 
Pada contoh diatas, data ‘0’ tidak terdapat pada list a, dan jumlah iterasi pencarian yang dilakukan sebanyak 10x

		a = [1, 5, 9, 8, 1, 5, 10, 26, 5, 12]

		[hasil, jumlahIterasi]=seqSearch(a,9)
		print('Posisi Data=', hasil)
		print('Jumlah Iterasi=', jumlahIterasi)

		Posisi Data= [2]
		Jumlah Iterasi= 
		
Pada contoh diatas, data ‘9’ berada di indeks ke-2, dan jumlah iterasi yang dilakukan sebanyak 10x

		a = [1, 5, 9, 8, 1, 5, 10, 26, 5, 12]

		[hasil, jumlahIterasi]=seqSearch(a,5)
		print('Posisi Data=', hasil)
		print('Jumlah Iterasi=', jumlahIterasi)

		Posisi Data= [1, 5, 8]
		Jumlah Iterasi= 10
		
Data ‘10’ berada pada indeks ke-1, 5, dan 8. Dan jumlah iterasi tetaplah 10 kali iterasi


2. Buatlah fungsi ordered sequential search (dapat juga menemukan posisi-posisi dari data yang sama), yaitu pencarian pada list data 	    dimana semua data-data pada list tersebut dalam keadaan terurut (ascending).
   Argument atau parameter pada fungsi tersebut berupa :
	a. data yang akan dicari
	b. list data dari data yang akan dicari
   Sedangkan return value dari fungsi ini berupa:
	a. indeks-indeks atau posisi dari data yang dicari pada list (jika data ditemukan), dan ‘Data tidak ada’ jika data tidak 		   ditemukan.
	b. Jumlah iterasi yang diperlukan selama proses pencarian
	
Contoh hasil eksekusi (dengan data pada list a sama dengan sebelumnya, hanya saja sudah dalam keaadaan terurut) dapat dilihat sebagai berikut : 

		a=[1,1,5,5,5,8,9,10,12,26]

		[hasil, iterasi]=orderedSeqSch(a,0)
		print('Posisi Data=', hasil)
		print('jumlah iterasi=', iterasi)

		Posisi Data= Data tidak ada
		jumlah iterasi= 1
		
Dapat dilihat bahwa data ‘0’ tidak terdapat pada list a, dan jumlah iterasi yang dilakukan hanya 1x saja (dibandingkan dengan fungsi sequential search sebelumnya, yang membutuhkan 10x iterasi)

		a=[1,1,5,5,5,8,9,10,12,26]

		[hasil, iterasi]=orderedSeqSch(a,9)
		print('Posisi Data=', hasil)
		print('jumlah iterasi=', iterasi)

		Posisi Data= [6]
		jumlah iterasi= 8
		
Jika dilakukan pencarian data ‘9’, maka data ditemukan pada indeks ke-6 dan hanya dilakukan 8 x iterasi pada proses pencarian.

		a=[1,1,5,5,5,8,9,10,12,26]

		[hasil, iterasi]=orderedSeqSch(a,5)
		print('Posisi Data=', hasil)
		print('jumlah iterasi=', iterasi)

		Posisi Data= [2, 3, 4]
		jumlah iterasi= 6
		
Jika dilakukan pencarian data ‘5’ maka akan dihasilkan tiga indeks yaitu, indeks ke-2,3, dan 4. Sedangkan jumlah iterasi yang dilakukan hanyalah sebanyak 6x.

3. Buatlah fungsi binary search yang sudah dimodifikasi, sehingga dapat mencari data yang sama dan mengembalikan indeks-indeks dari data    yang sama tersebut.
   Argument atau parameter pada fungsi tersebut berupa :
	a. data yang akan dicari
	b. list data dari data yang akan dicari
   Sedangkan return value dari fungsi ini berupa:
	c. indeks-indeks atau posisi dari data yang dicari pada list (jika data ditemukan), dan ‘Data tidak ada’ jika data tidak 		   ditemukan.
	d. Jumlah iterasi yang diperlukan selama proses pencarian
Contoh hasil eksekusi dari fungsi tersebut adalah :

# Data yang dicari adalah ‘5’ :

		a=[1,1,5,5,5,8,9,10,12,26]

		[hasil, iterasi]=binSearch(a,5)
		print('Posisi Data=', hasil)
		print('jumlah iterasi=', iterasi)

Posisi Data= [4, 2, 3]
jumlah iterasi= 4

# Data yang dicari adalah ‘10’ :

		a=[1,1,5,5,5,8,9,10,12,26]

		[hasil, iterasi]=binSearch(a,10)
		print('Posisi Data=', hasil)
		print('jumlah iterasi=', iterasi)

Posisi Data= [7]
jumlah iterasi= 2

# Data yang dicari adalah ‘1’ :

		a=[1,1,5,5,5,8,9,10,12,26]

		[hasil, iterasi]=binSearch(a,1)
		print('Posisi Data=', hasil)
		print('jumlah iterasi=', iterasi)

Posisi Data= [1, 0]
jumlah iterasi= 3

# Data yang dicari adalah ‘20’ :

		a=[1,1,5,5,5,8,9,10,12,26]

		[hasil, iterasi]=binSearch(a,20)
		print('Posisi Data=', hasil)
		print('jumlah iterasi=', iterasi)

Posisi Data= data tidak ada
	 jumlah iterasi= 4
	 
	 
	 
# Jawaban Praktikum
#Nomer 1

	def seqSearch(listData, data): #fungsi sequential Search
		iterasi = 0 #iterasi dimuai dari 0
		hasil = [] #list ditampung didalam variabel hasil
		found = 'Data tidak ada' #jika found, maka akan muncul data tidak ada
		for i in range(len(listData)): #perulangan jumlah list data
			if listData[i] == data: #jika isi list data ke-i == data, maka
				hasil.append(i) #memunculkan nilai i
				found = hasil #diletakkan didalam hasil
				iterasi = iterasi+1 #nilai iterasi tidak lagi 0
		return found,iterasi #mengembalikan nilai hasil dan iterasi

	a = [1,5,9,8,1,5,10,26,5,12] #mengisi variabel a dengan list yang mau di cari
	[hasil,jumlahIterasi] = seqSearch(a,0) #mencari angka 0 dalam variabel 'a'
	print('Posisi Data =',hasil) #mencetak hasil
	print('Jumlah Iterasi =',jumlahIterasi) #mencetak banyak iterasi

#Nomer 2

	def orderedSeqSearch(listData, data):#fungsi Ordered Sequential Search
		ind = 0 #index dimulai dari 0
		iterasi = 0 #perulangan dimulai dari 0
		found = False #found disetel false terlebih dahulu
		stop = False # stop disetel false terlebih dahulu
		position=[] #list ditampung didalam position
		while ind < len(listData) and not found and not stop: #perulangan ketika ada isinya
			if listData[ind] == data and listData[ind+1] == data: #jika index dalam listData == data dan +1, maka
				position.append(ind)#index ditambahkan dalam posisi
				found = False #found masih bernilai salah
				iterasi += 1 #perulangan bertambah
				ind = ind+1 #ind juga bukan lagi 0
			elif listData[ind] == data and listData[ind+1] != data: #jika index+1 dalam listData tidak sama dengan data, maka
				position.append(ind) #index dimasukkan dalam position
				iterasi += 2 #iterasi ditambah 2
				found = True #nilai ketemu
			else: #jika tidak, maka
				if listData[ind] > data: #jika index dalam listData lebih besar dari data, maka
					iterasi += 1#iterasi ditambah 1
					stop = True #berhenti
				else: #jika tidak, maka
					iterasi += 1 #iterasi ditambah 1
					ind = ind+1 #nilai index ditambah1

		if found: #jika ketemu, maka
			return position,iterasi	#mengembalikan nilai position dan iterasi
		else: #jika tidak, maka
			return ('Data tidak ada',iterasi)#Data tidak ada

	a = [1,1,5,5,5,8,9,10,12,26] #membuat variabel a dengan list yang sudah urut
	[hasil,iterasi] = orderedSeqSearch(a,5) #mencari ordered Sequential Search angka 5 dalam a
	print('Posisi Data =',hasil) #mencetak hasil
	print('Jumlah Iterasi =',iterasi) #mencetak jumlah iterasi

#Nomer 3

	def binarySearch(listData, data): #fungsi binarySearch
		first = 0 #dimulai dari 0
		iterasi = 0 #iterasi dimulai dari 0
		last = len(listData) - 1 #karena menentukan nilai akhir, maka panjangnya dikurangi 1
		found = False #found di setel false terlebih dahulu
		hasil = [] #manampung nilai dalam list hasil
		while first <= last and not found: #perulangan jika pertama kurang dari sama dengan last dan benar
			midpoint = (first + last) // 2 #menentukan midpoint dengan jumlah first + last dibagi 2
			if listData[midpoint] == data and listData[midpoint-1] == data and listData[midpoint-2] != data: #jika midpoint dalam listData dan midpoint-2 tidak sama dengan data, maka
				found = True #nilai found menjadi benar
				hasil.append(midpoint) #midpoint diletakkan didalam list hasil
				hasil.append(midpoint-1) #nilai midpoint-1 diletakkan didalam list hasil
				iterasi += 2 #iterasi ditambah 2
			elif listData[midpoint]==data and listData[midpoint-1] == data and listData[midpoint-2] ==data: #jika midpoint dalam listData== data dan midpoint-2 dalam listData == data, maka
				found = True #found bernilai benar
				hasil.append(midpoint)#nilai midpoint diletakkan didalam list hasil
				hasil.append(midpoint-2) #nilai midpoint-2 diletakkan didalam list hasil
				hasil.append(midpoint-1) #nilai midpoint-1 diletakkan didalam list hasil
				iterasi += 4 #iterasi ditambah 4
			elif listData[midpoint]==data and listData[midpoint-1] != data: #jika midpoint-1 dalam listData tidak sama dengan data, maka
				found = True #found bernilai True
				hasil.append(midpoint) #nilai midpoint diletakan didalam list hasil
				iterasi += 1 #iterasi ditambah 1
			else: #jika tidak
				if data < listData[midpoint]: #jika data kurang dari midpoint dalam listData, maka
					last = midpoint - 1 #nilai last adalah midpoint-1
					iterasi += 1 #iterasi ditambah 1
				else: #jika tidak, maka
					first = midpoint + 1 #nilai awal adalah midpoint + 1
					iterasi += 1 #iterasi ditambah 1
		if found : #jika ketemu
			return hasil,iterasi #mengebalikan nilai hasil dan iterasi
		else: #jika tidak
			return "data tidak ada",iterasi #memunculkan banyaknya iterasi
	a = [1,1,5,5,5,8,9,10,12,26] #variabel a untuk menampung list
	[hasil,iterasi] = binarySearch(a,10) #mencari angka 10 dalam variabel a
	print('Posisi Data =',hasil) #cetak hasil letak data
	print('Jumlah Iterasi =',iterasi) #cetak banyaknya perulangan
