#include <stdio.h>
#include <string.h>
#define SIZE 300
#define store 100
#define size 300

void login();
void signup();
void logout();
void change(char login[], char Fname[],char Lname[],char Pass[], char Email[],char Bank[]);
void purchase(int *Totalprice);
void complete();
void delete();



 int main(){

    login();
 return 0 ;
}


int login(){ // THE LOGIN FUNCTION
int flag=0,balance,i;

char str[SIZE], usermail[SIZE], userpassword[SIZE], useranswer[SIZE],cont[SIZE];

char email[store],first[store],last[store],pass[store],bank[store],question[store],answer[store];

FILE *fptr;

fptr= fopen("database.txt", "r");

if(fptr == NULL){
printf("Error opening file!");
}

printf("Enter your Email: \n");
scanf("%s",usermail);

printf("Enter your Password: \n");
scanf("%s",userpassword);
fseek(fptr,0,0);

while(!feof(fptr)){
    fscanf(fptr,"%s %s %s %s %s %d %s %s", email, first, last, pass, bank, &balance, question, answer);

    if(strcmp(usermail, email)==0 && strcmp(userpassword, pass)==0){
    flag=1;
    }
}    
 
    if(flag==1){
    printf("Welcome! \n");
    }

    else{
        printf("User does not exist,how about signing up ?");
        scanf(" %s",cont);
        if(strcmp("yes",cont)==0){
             signup(*email,*bank);
        }

    }
}




void signup(char demail[], char dbank[]){ // THE SIGNUP FUNCTION
    char email[size],Fname[size],Lname[size],Pass[size],Bank[size],Quest[size],Answer[size];
    int balance[size];
	printf("Enter your email: ");
	scanf("%s", email);
	printf("Enter your first name: ");
	scanf("%s", Fname);
	printf("Enter your last name: ");
	scanf("%s", Lname);
	strcat(Fname, " ");
	strcat(Fname, Lname);
	printf("Enter a password: ");
	scanf(" %s", Pass);
	printf("Enter your bank account: ");
	scanf(" %s", Bank);
	printf("Enter your balance: ");
	scanf(" %d", &balance);
	printf("Enter the secret question: ");
	scanf(" %s", Quest);
	printf("Enter the answer of the question: ");
	scanf(" %s", Answer);
    if(strcmp(demail,email)!=0 && strcmp(dbank,Bank)!=0){
        printf("Welcome !");
    }
    else{
        printf("Information entered already exists, try again");
    }
		
}










void purchase(int *Totalprice){ THE MAKING ORDER FUNCTION
       char answer[3];
       int quantity1=0,quantity2=0,quantity3=0,quantity4=0,quantity5=0;
		 *Totalprice=0;
		int choice;

    do{	
	printf("This is the menu of the products. Choose the number of your purchase:\n"
	"1. book 200 MAD\n "
	"2. skincare 700 MAD\n "
	"3. watch 1000 MAD\n "
	"4. desk 4000 MAD\n "
	"5. laptop 6000 MAD.\n");
    scanf("%d", &choice);
    
        if(choice==1){
        printf("Enter the quantity: ");
        scanf("%d", &quantity1);
        }
        
         if(choice==2){
        printf("Enter the quantity: ");
        scanf("%d", &quantity2);
        } 
        
        if(choice==3){
        printf("Enter the quantity: ");
        scanf("%d", &quantity3);
        } 
        
        if(choice==4){
        printf("Enter the quantity: ");
        scanf("%d", &quantity4);
        } 
        
        if(choice==5){
        printf("Enter the quantity: ");
        scanf("%d", &quantity5);
        }
        
         *Totalprice= *Totalprice+(quantity1*200)+(quantity2*700)+(quantity3*1000)+(quantity4*4000)+(quantity5*6000);
       
        printf("Do you want to make another purchase? If yes type yes, if no type no: ");
       scanf(" %s", answer);
        
       
    }while(!strcmp("yes", answer));
    
     printf("\nThe total price tof your purchases is: %d", *Totalprice);
    
}




 
 
  void change( char login[], char Fname[],char Lname[],char Pass[], char Email[],char Bank[] ){ THE MAKING CHANGE FUNCTION
  	 int choice; 
  	 
  	
  	printf("Enter the password to re-authenticate :");
  	scanf("%s", Pass);
  	
  	
  	if(strcmp(login, Pass )==0){
	 
  	printf("Select the number of information you would like to change: \n");
	printf("1. Profile name \n");
	printf("2. Password \n");
 	printf( "3. Email \n");
	printf("4. Account number-banking account \n");
	   
	   scanf("%d", &choice);
	   
	   switch(choice){
	   	
	   	case 1:
	   		printf("Enter a new profile name: ");
	   		scanf("%s", Fname);
	   		scanf("%s", Lname);
	   		strcat(Fname, " ");
	   		strcat(Fname, Lname);
	   	case 2:
	   		printf("Enter a new password: ");
	   		scanf("%s", Pass);
	    case 3:
	    	printf("Enter a new email: ");
	   		scanf("%s", Email);
	   	case 4: 
	   	printf("Enter a new bank account: ");
	   		scanf("%s", Bank);
	    
	   		}
	}
	else{
		printf("******Incorrect password******");
	}
	   
	   
  }
  
  
  
  

