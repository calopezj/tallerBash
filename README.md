# Taller Bash . Ciencia de Datos



# 1 - Lectura de archivos

while IFS=, read  col1 col2 col3
    do           
        echo "Columna 1->${col1}"
        echo "Columna 2->${col2}"   
        echo "Columna 3->${col3}"              
    done < out.csv
		

# 2- Limpieza general del archivo

		filename="data1.csv"
        sed "s/\t/,/g" $filename > out.csv
        sed -i 's/[[:space:]]\+/,/g' out.csv
        sed -i "s/ /,/g" out.csv        
        sed -i '/^ *$/d' out.csv
        sed -i "s/[,]+/,/g" out.csv
        cat out.csv
		
		
		
# 3 - Llevando la información a arrays

IFS=',' read -ra arraylinea <<< "${col1}"


# 4 - Recorriendo un array:

#!/bin/bash
numeros=(1 2 3 4 5)
#echo ${numeros[@]}

linea="bbb:2,hhh:0,ccc:4,fff:1,aaa:7"
#echo ${linea}
IFS=',' read -ra arraylinea <<< "${linea}"
#echo ${arraylinea[@]}
#Recorramos el arreglo:
    for i in "${arraylinea[@]}"; do
            echo "$i"
    done

		
# 5 - Leer todos los archivos en un directorio

for i in $(ls *.csv -C1)
do     
    filename=$i
	echo "archvio->${filename}"
done
