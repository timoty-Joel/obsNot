nano biodata.sh
#! /bin/bash
echo "Nama"
echo "npm"
echo "Kelas"

exit

chmod 775 biodata.sh
./biodata.sh

//2
nano volumepersegipanjang.sh
#!/bin/bash
echo "Volume Persegi Panjang"

echo "Panjang"
read P
echo "Lebar"
read L
echo "Tinggi"
read T

n =  $[P* L * T]
echo "Volumenya adalah $n"
