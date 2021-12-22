#include <stdio.h>
#include <string.h>
#define SIZE 300
#define store 100
#define size 300

int login(){
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



return 0;
}

void signup(char demail[], char dbank[]){
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



int main( ){

    login();
	
	return 0 ;
}

