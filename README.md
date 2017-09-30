# dontknow
#include <iostream>
#include <math.h>
#include <string>

using namespace std;

int ConvBin(int decimal, int aux, int bin){
	bin += (decimal%2)*aux;
	aux *= 10;
	decimal = decimal/2;

	if(decimal <=0)
		return bin;
	bin = ConvBin(decimal, aux, bin);
}

int ConvDec(string binario){
    int bin, dec = 0;
    auto aux = (int) binario.length() - 1;
    for (char i:binario){
        if(i == '0' || i == '1'){
            if(aux>=0){
	            if(i == '0')
	                    aux--;
	            else{
	                    bin = 1;
	                    dec += bin * pow(2, aux);
	                    aux--;
	            }
	        }
        }else
            cout << "O número não é binário";
    }

    return dec;
}

int main(){
	int escolha;
	cout << "Qual conversão você quer fazer? 1-Decimal para Binário  2-Binário para Decimal"<<endl;
	cin >> escolha;
	if(escolha == 1){
		int decimal;
		cout << "Digite um número: ";
		cin >> decimal;
		int bin = 0;
		int aux = 1;
		bin = ConvBin(decimal,aux, bin);
		cout << "O número "<< decimal<<" em binário é: "<<bin<< endl;
	}else if(escolha == 2){
		string binario;
		int dec;
		cout << "Digite um número binário: "<< endl;
		cin >> binario;
		dec = ConvDec(binario);
		cout << "O binario "<< binario<<" em decimal é: "<<dec<< endl;

	}else
		cout << "Digite uma opção válida"<< endl;
	return 0;
}
