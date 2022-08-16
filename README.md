# sortingAlgo
This Tutorial help to How To Sorte Linked List Using Five Sorting Algorithm.
#include <iostream>
#include <string>

using namespace std;

int get_bin_representation(char x){

  if(x == '1'){
    return 1;
  }
  else if(x == '0'){
    return 0;
  }
}
int gen_hamming_code(string token){

  int bits[4];
  int temp(0);

  for(int k=0; k<4; k++){
    bits[k] = get_bin_representation(token.at(k));
  }

  int ham_code[7];

  ham_code[0] = bits[0] + bits[1] + bits[3];
  ham_code[1] = bits[0] + bits[2] + bits[3];
  ham_code[2] = bits[0];
  ham_code[3] = bits[1] + bits[2] + bits[3];
  ham_code[4] = bits[1];
  ham_code[5] = bits[2];
  ham_code[6] = bits[3];

  for(int h=0; h<7; h++){
    temp = ham_code[h];
    ham_code[h] = temp%2;
    temp = 0;
  }

  for(int e=0; e<7; e++){
    cout << ham_code[e];
  }
  cout << endl;

  return 0;
}
int main(){

  string usr_input;
  string msg;
  int index(0);

  cout << "Hamming Code Program" << endl;

  while(true){

    cout << endl << ": ";
    getline(cin, usr_input);

    if(usr_input.find("gen") != std::string::npos){
        for(int i=0; i<usr_input.length(); i++){
            if(usr_input.at(i) == ' '){
                index = i;
            }
        }

        for(int j=index; j<usr_input.length(); j++){
            msg+=usr_input.at(j);
        }

        cout << "Hamming code (7,4): ";
        gen_hamming_code(msg);
    }
  }
}
