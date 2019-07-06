# Rangkuman-Modul6

Searhing
Searhing merupakan proses yang fundamental dalam pengolahan data.
Proses pensarian adalah menemukan nilai(data) tertentu didalam sekumpulan data yang bertipe sama
(baik bertipe dasar maupun bertipe bentukan).

Sebuah algoritma pencarian dijelaskan secara luas adalah sebuah algoritma yang menerima masukan berupa sebuah masalah dan
menghasilkan sebuah solusi untuk masalah tersebut, yang biasanya didapat dari evaluasi beberapa kemungkinan solusi.
Algoritma pencarian (searching algorithm) adalah algoritma yang menerima sebuah argumen kunci dan
dengan langkah-langkah tertentu akan mencari rekaman dengan kunci tersebut.
Setelah proses pencarian dilaksanakan, akan diperoleh salah satu dari dua kemungkinan, yaitu data yang dicari ditemukan atau
tidak ditemukan, ini menandakan apakah data berada di sekumpulan data ataukah tidak.
Proses pencarian sederhana ini sudah disediakan oleh python dengan menggunakan syntax in,
seperti contoh berikut:

a=[12,5,9,8,1,10,26]

11 in a

>>>
Running: False

12 in a

>>>
Running: True

15 in a

>>>
Running: False
A. Sequential search.

Sequential Search merupakan teknik pencarian data dengan cara membandingkan data yang dicari dengan seluruh data yang terdapat pada kumpulan data secara satu persatu, mulai dari data pertama sampai dengan data terakhir.

*Terdapat dua konsep untuk sequential search berdasarkan kumpulan data yang akan dicari, yaitu :

Unordered List Sequential Search

Ordered List Sequential Search

Unordered List Sequential Search
Pada unordered list sequential search, data berada pada keadaan acak, tidak terurut, sehingga pencarian harus dilakukan mulai dari indeks awal sampai indeks terakhir dari data, atau pencarian berhenti ketika data sudah ditemukan

*Berikut implementasi algoritma unordered list sequential search:

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
Ordered List Sequential Search
Pada ordered list sequential search, data sudah dalam keadaan terurut, hal ini tentunya dapat mengurangi waktu komputasi pencarian.

*Berikut implementasi algoritma sequential search pada ordered list

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

Binary Search adalah salah satu metode pencarian atau pengecekan sebuah elemen angka di dalam sebuah wadah. Jika di dalam wadah terdapat elemen angka yang dicari oleh user, maka program tersebut akan mengembalikan statement True. Begitu pun sebaliknya, jika di dalam wadah tersebut tidak terdapat elemen angka yang dicari oleh user maka program tersebut akan mengembalikan statement False.

Point penting yang harus sobat perhatikan disini adalah metode ini hanya bisa digunakan untuk wadah dengan angka yang sudah urut (wadah dengan elemen angka dari kecil ke besar). Program ini akan sangat berguna ketika wadah yang user gunakan mengandung banyak sekali elemen angka di dalamnya

*Berikut code untuk binary search dengan metode iteratif

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

>>>
Running: True
*Selain dengan model iteratif, algoritma binary search juga dapat ditulis secara rekursif, seperti yang ditunjukkan pada program berikut

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
    
>>>
Running: True
Praktikum Struktur Data – 2019 #Modul 6 – Searching
Buatlah fungsi sequential search (dapat juga menemukan posisi-posisi dari data yang sama), dengan argument atau parameter berupa :
a.	data yang akan dicari

b.	list data dari data yang akan dicari

a).	indeks-indeks atau posisi dari data yang dicari pada list (jika data ditemukan), dan ‘Data tidak ada’ jika data tidak ditemukan.

b).	Jumlah iterasi yang diperlukan selama proses pencarian

*Contoh hasil eksekusi dapat dilihat sebagai berikut :

a = [1, 5, 9, 8, 1, 5, 10, 26, 5, 12]

[hasil, jumlahIterasi]=seqSearch(a,0)
print('Posisi Data=', hasil)
print('Jumlah Iterasi=', jumlahIterasi)

>>>
Running: Posisi Data= Data tidak ada
         Jumlah Iterasi= 10
Pada contoh diatas, data ‘0’ tidak terdapat pada list a, dan jumlah iterasi pencarian yang dilakukan sebanyak 10x

a = [1, 5, 9, 8, 1, 5, 10, 26, 5, 12]

[hasil, jumlahIterasi]=seqSearch(a,9)
print('Posisi Data=', hasil)
print('Jumlah Iterasi=', jumlahIterasi)

>>>
Running: Posisi Data= [2]
         Jumlah Iterasi= 10
Pada contoh diatas, data ‘9’ berada di indeks ke-2, dan jumlah iterasi yang dilakukan sebanyak 10x

a = [1, 5, 9, 8, 1, 5, 10, 26, 5, 12]

[hasil, jumlahIterasi]=seqSearch(a,5)
print('Posisi Data=', hasil)
print('Jumlah Iterasi=', jumlahIterasi)

>>>
Running: Posisi Data= [1, 5, 8]
         Jumlah Iterasi= 10
Data ‘10’ berada pada indeks ke-1, 5, dan 8. Dan jumlah iterasi tetaplah 10 kali iterasi

Buatlah fungsi ordered sequential search (dapat juga menemukan posisi-posisi dari data yang sama), yaitu pencarian pada list data dimana semua data-data pada list tersebut dalam keadaan terurut (ascending). Argument atau parameter pada fungsi tersebut berupa :
a. data yang akan dicari

b. list data dari data yang akan dicari

a.) indeks-indeks atau posisi dari data yang dicari pada list (jika data ditemukan), dan ‘Data tidak ada’ jika data tidak ditemukan.

b.) Jumlah iterasi yang diperlukan selama proses pencarian

*Contoh hasil eksekusi (dengan data pada list a sama dengan sebelumnya, hanya saja sudah dalam keaadaan terurut) dapat dilihat sebagai berikut : a=[1,1,5,5,5,8,9,10,12,26]

[hasil, iterasi]=orderedSeqSch(a,0)
print('Posisi Data=', hasil)
print('jumlah iterasi=', iterasi)

>>>
Running: Posisi Data= Data tidak ada
	 jumlah iterasi= 1
Dapat dilihat bahwa data ‘0’ tidak terdapat pada list a, dan jumlah iterasi yang dilakukan hanya 1x saja (dibandingkan dengan fungsi sequential search sebelumnya, yang membutuhkan 10x iterasi)

a=[1,1,5,5,5,8,9,10,12,26]

[hasil, iterasi]=orderedSeqSch(a,9)
print('Posisi Data=', hasil)
print('jumlah iterasi=', iterasi)

>>>
Running: Posisi Data= [6]
	 jumlah iterasi= 8
Jika dilakukan pencarian data ‘9’, maka data ditemukan pada indeks ke-6 dan hanya dilakukan 8 x iterasi pada proses pencarian.

a=[1,1,5,5,5,8,9,10,12,26]

[hasil, iterasi]=orderedSeqSch(a,5)
print('Posisi Data=', hasil)
print('jumlah iterasi=', iterasi)

>>>
Running: Posisi Data= [2, 3, 4]
	 jumlah iterasi= 6
Jika dilakukan pencarian data ‘5’ maka akan dihasilkan tiga indeks yaitu, indeks ke-2,3, dan 4. Sedangkan jumlah iterasi yang dilakukan hanyalah sebanyak 6x.

Buatlah fungsi binary search yang sudah dimodifikasi, sehingga dapat mencari data yang sama dan mengembalikan indeks-indeks dari data yang sama tersebut. Argument atau parameter pada fungsi tersebut berupa :
a. data yang akan dicari

b. list data dari data yang akan dicari

c. indeks-indeks atau posisi dari data yang dicari pada list (jika data ditemukan), dan ‘Data tidak ada’ jika data tidak ditemukan.

d. Jumlah iterasi yang diperlukan selama proses pencarian

*Contoh hasil eksekusi dari fungsi tersebut adalah :

Data yang dicari adalah ‘5’ :

a=[1,1,5,5,5,8,9,10,12,26]

[hasil, iterasi]=binSearch(a,5)
print('Posisi Data=', hasil)
print('jumlah iterasi=', iterasi)

>>>
Running: Posisi Data= [4, 2, 3]
	 jumlah iterasi= 4
Data yang dicari adalah ‘10’ :

a=[1,1,5,5,5,8,9,10,12,26]

[hasil, iterasi]=binSearch(a,10)
print('Posisi Data=', hasil)
print('jumlah iterasi=', iterasi)

>>>
Running: Posisi Data= [7]
	 jumlah iterasi= 2
Data yang dicari adalah ‘1’ :

a=[1,1,5,5,5,8,9,10,12,26]

[hasil, iterasi]=binSearch(a,1)
print('Posisi Data=', hasil)
print('jumlah iterasi=', iterasi)

>>>
Running: Posisi Data= [1, 0]
	 jumlah iterasi= 3
Data yang dicari adalah ‘20’ :

a=[1,1,5,5,5,8,9,10,12,26]

[hasil, iterasi]=binSearch(a,20)
print('Posisi Data=', hasil)
print('jumlah iterasi=', iterasi)

>>>
Running: Posisi Data= data tidak ada
	 jumlah iterasi= 4
Jawaban Praktikum
#Nomer 1

print("============ Sequential Search============")
def seqSearch(listData, data):
		ind = 0
		found = False
		hasil = []
		stop = False
		while ind < len(listData) and not found:
    		if listData[ind] == data:
        			found = True
        			hasil.append(ind)
			
    		else:
        			ind = ind+1
		if found:
    		return ind
		else:
    		return("data tidak ada")

a=[1,5,9,5,10,26,5,12]
hasil=seqSearch(a,5)
print("Posisi Data: "+"[",hasil,"]")
#Nomer 2

print("============ Ordered Seq Search============")
def OrderedSeqSearch(listData, data):
		ind = 0
		found = False
		stop = False
		position = []

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
    		return ("data tidak ada")

c = [1,1,5,5,5,8,9,10,12,26]
position=ind = OrderedSeqSearch(c, 9)
print("Posisi data: ", position)
#Nomer 3

print("======= Binary Search =======")
def binarySearch(listData, data):
	first = 0
	iterasi = 0
	last = len(listData) - 1
	found = False
	hasil = []
	while first <= last and not found:
		midpoint = (first + last) // 2
		if listData[midpoint] == data and listData[midpoint-1] == data and listData[midpoint-2] != data:
			found = True
			hasil.append(midpoint)
			hasil.append(midpoint-1)
			iterasi += 2
		elif listData[midpoint]==data and listData[midpoint-1] == data and listData[midpoint-2] ==data:
			found = True
			hasil.append(midpoint)
			hasil.append(midpoint-2)
			hasil.append(midpoint-1)
			iterasi += 4
		elif listData[midpoint]==data and listData[midpoint-1] != data:
			found = True
			hasil.append(midpoint)
			iterasi += 1
		else:
			if data < listData[midpoint]:
				last = midpoint - 1
				iterasi += 1
			else:
				first = midpoint + 1
				iterasi += 1
	if found :
		return hasil,iterasi
	else:
		return "data tidak ada",iterasi
c = [1,1,5,5,5,8,9,10,12,26]
[hasil,iterasi] = binarySearch(c,9)
print('Posisi Data =',hasil)
print('Jumlah Iterasi =',iterasi)
