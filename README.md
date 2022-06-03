#include <iostream>
using namespace std;
class stok_brg {
  public :
    void input_menu();
    void sorting();
    void output();
    void cari_id();
    
  private :
    int nim[50], jml_input, telp[50]; //INPUT STOK
    string nama[50], prodi[50];
    
    int id_cari; //INPUT CARI BARANG
    
    int temp_telp, temp_nim; //TEMP UNTUK SORTING
    string temp_nama, temp_prodi;                    
};

void stok_brg::input_menu(){
	cout<<"\n\t||\t\t        PENGUMPULAN DATA MAHASISWA \t\t      ||"<<endl;
	cout<<"\n\t||====================================================================||"<<endl;
	cout<<"\n\t  MASUKAN BANYAK INPUTAN -> ";cin>>jml_input;
	system("cls");
	for(int i=0; i<jml_input; i++){
		cout<<"\n\t||====================================================================||"<<endl;
    	cout<<"\n\t   STOK KE -"<<i+1<<endl;
      	cout<<"\n\t     MASUKAN NIM \t\t : ";cin>> nim[i];
      	cout<<"\t     MASUKAN NAMA \t : ";cin>>nama[i];
      	cout<<"\t     MASUKAN PRODI \t : ";cin>>prodi[i];
      	cout<<"\t     MASUKAN NO.TELP \t\t : ";cin>> telp[i];
  		cout<<"\n\t||====================================================================||"<<endl;
  		system("cls");
    }
}

void stok_brg::sorting(){
  	for(int i=1; i<jml_input; i++){
    	for(int j=jml_input-1; j>=1; j--){
        	if(telp[j]<telp[j-1]){
        		
				//SORTING NIM 
            	temp_nim=nim[j];
            	nim[j]=nim[j-1];
             	nim[j-1]=temp_nim;
             
              	//SORTING NAMA 
            	temp_nama=nama[j];
            	nama[j]=nama[j-1];
            	nama[j-1]=temp_nama;
            	
            	//SORTING PRODI
            	temp_prodi=prodi[j];
            	prodi[j]=prodi[j-1];
            	prodi[j-1]=temp_prodi;
            	
        		//SORTING TELP 
            	temp_telp=telp[j];
            	telp[j]=telp[j-1];
            	telp[j-1]=temp_telp;
          	}
        }
    }
}

void stok_brg::output(){
	system("cls");
	cout<<"\n\t  \t\t          DATA MAHASISWA \t\t              "<<endl;
	cout<<"\t||====================================================================||"<< endl;
	cout <<"\n\t    NIM \t\t    NAMA \t\t    PRODI \t\t  TELEPON \n" << endl;
	cout<<"\t||====================================================================||"<< endl;
	for(int i=0; i<jml_input; i++){
    	cout<< "\n\t\t"<<nim[i]<<"\t\t\t"<<nama[i]<<"\t\t\t"<<prodi[i]<<"\t\t\t"<< telp[i]<<endl;
		cout<<"\n\t||====================================================================||"<< endl;
    }
}

void stok_brg::cari_id(){
	cari:
		cout<<"\n\t   MASUKAN NIM YANG ANDA DICARI : "; cin>>id_cari;
		for(int i=0; i<jml_input; i++){
    		if(id_cari==nim[i]){
				cout<<"\n\t||====================================================================||\n"<< endl;
        		cout << "\n\t     NIM -> "<< nim[i]<<" || NAMA -> "<< nama[i]<<" || PRODI -> "<< prodi[i]<<" || STOK -> "<< telp[i]<<endl;;
        		cout<<"\n\n\t||====================================================================||"<< endl;
      		}else{
				cout<<"\n\t||====================================================================||"<< endl;
				cout<<"\n\t\t        BIODATA TIDAK TERDAFTAR!!!"<< endl;
				cout<<"\n\t||    ============================================================    ||"<< endl;
				goto cari;
	  		}
    	}
}
// FUNGSI MAIN
main(){
	stok_brg a;
	a.input_menu();
	a.sorting();
	a.output();
	a.cari_id();
}
                                                                                                   
