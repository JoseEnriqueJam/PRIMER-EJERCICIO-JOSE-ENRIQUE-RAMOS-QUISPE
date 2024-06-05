escribe una funcioon que tome un arreglo de enteros y un numero K y determinesi existen dos numeros en el 
arreglo cuya suma sea igual a K.






#include <iostream>
#include <unordered_set>
#include <vector>

bool encuentra_suma(std::vector<int>& arr, int K) {
    // Crea un conjunto para almacenar los números ya vistos
    std::unordered_set<int> numeros_vistos;

    // Itera a través de los números en el arreglo
    for (int num : arr) {
        // Calcula el complemento necesario para que la suma sea K
        int complemento = K - num;
        // Si el complemento está en el conjunto de números vistos, significa que encontramos dos números cuya suma es K
        if (numeros_vistos.find(complemento) != numeros_vistos.end()) {
            return true;
        }
        // Agrega el número actual al conjunto de números vistos
        numeros_vistos.insert(num);
    }
    
    // Si no se encontraron dos números cuya suma sea K, retorna false
    return false;
}

int main() {
    // Ejemplo de uso:
    std::vector<int> arr = {1, 2, 3, 4, 5};
    int K = 9;
    if (encuentra_suma(arr, K)) {
        std::cout << "Se encontraron dos números cuya suma es " << K << std::endl;
    } else {
        std::cout << "No se encontraron dos números cuya suma es " << K << std::endl;
    }
    return 0;
}
