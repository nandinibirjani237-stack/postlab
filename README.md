# postlab
#include<stdio.h>
int calculateTotal(int *ptr1,int size){
int total=0;
for(int i=0;i<size;i++){
  total+=*(ptr1+i);
}
return total;
}
int deposit(int balance1,int amount){
return balance1+amount;
}
int withdraw(int balance1,int amount){
if(amount>balance1){
    printf("invalid\n");
    return balance1;
}
return balance1-amount;
}
void processtransaction(int *balance1 ,int amount,int (*action)(int,int)){
*balance1=action(*balance1,amount);
}
int main(){
    int num,index,deposit1;
int balance[5]={15000, 25000, 18000, 32000, 12000};

printf("enter the number\n");
scanf("%d",&num);
index=num-1;
int *ptr=&balance[index];
printf("%d",*ptr);
printf("%p",ptr);
printf("enter the deposit\n ");
scanf("%d",&deposit1);
*ptr=*ptr+deposit1;
printf("%d",*ptr);

int transaction[2][3]={{120000, 150000,180000}, {200000, 170000, 220000}};
int (*p)[3]=transaction;
int branchtotal;
for(int i=0;i<2;i++){
    branchtotal=0;
    printf("row %d",i+1);
      printf("row %p",(p+i));
    for(int j=0;j<3;j++){
        int value=*(*(p+i)+j);
        branchtotal+=value;
    }
    printf("total of each branch \n %d %d",i+1,branchtotal);
}
int branch1[3]={15000,23000, 32000};
int branch2[4]={12000, 21000, 27000, 35000};
int size[2]={3,4};
int *branch[2]={branch1,branch2};
for(int i=0;i<2;i++){
    int branchtotal1=0;
printf("%d\n",i+1);
for(int j=0;j<size[i];j++){
   int value=*(branch[i]+j);
   branchtotal1+=value;
   printf("%p\n",branch[i]+j);

}
printf("branch total %d\n",branchtotal1);
}

int branch3[]= {15000, 23000, 32000};
int branch4[]={12000, 21000, 27000, 35000};

int total1=calculateTotal(branch3,3);
int total2=calculateTotal(branch4,4);
printf("%d\n",total1);
printf("%d\n",total2);

int balance1 = 2500;
int amount=500;
printf(" current balance%d\n",balance1);
 processtransaction(&balance1,amount ,deposit);
 printf(" after deposit the balance%d\n",balance1);
 processtransaction(&balance1,amount ,withdraw);
printf(" after withdrawal the balance%d\n",balance1);
return 0;

# task 1
#include<stdio.h>
int main(){
int balance[5]={15000, 25000, 18000, 32000, 12000};
int num,deposit,index;
printf("Enter the number which you wanna access");
scanf("%d",&num);
index=num-1;
if(index<0  || index >=5){
    printf("inavlid");
    return 1;
}
int *ptr= &balance[index];
printf("%p\n",ptr);
printf("%d",*ptr);

printf("enter the deposit");
scanf("%d",&deposit);
*ptr=*ptr+deposit;
printf("deposit amount is %d",*ptr);
    return 0;
} 
# task 2
#include<stdio.h>
int main(){
    int branchtotal;
int transaction[2][3]={{120000, 150000,180000}, {200000, 170000, 220000}};
int (*p)[3]=transaction;
 for(int i=0;i<2;i++){
    branchtotal=0;
    printf("%d\n",i+1);
    printf("%p\n",(p+i));

 
 for(int j=0;j<3;j++){
int value =*(*(p+i)+j);
printf("%d\n",value);
branchtotal+=value;
 }
 printf("balance total %d %d",i+1,branchtotal);
 }
    return 0;
}
# task 3
#include<stdio.h>
int main(){
int branchtotal;
int branch1[3]={15000, 23000, 32000};
int branch2[4]={12000, 21000, 27000, 35000};
int *branch[2]={branch1,branch2};
int size[2]={3,4};
for(int i=0;i<2;i++){
    printf("Branch %d Accounts\n", i + 1);
    branchtotal=0;
    for(int j=0;j<size[i];j++){
      int value=  *(branch[i]+j);
        int *p= branch[i]+j;
        printf(" \t \n%p",p);
        branchtotal+=value;
    }
    printf("\nbranch total %d",branchtotal);
}



    return 0;
}
# task 4
#include<stdio.h>
 int CreatecalculateTotal(int *ptr,int size){
int total=0;
for(int i=0;i<size;i++){
    total+=*(ptr+i);

}
return total;
}
int main(){
int branch1[3]= {15000, 23000, 32000};
int branch2[4]={12000, 21000, 27000, 35000};
int total1=CreatecalculateTotal(&branch1[0],3);
int total2=CreatecalculateTotal(&branch2[1],4);
printf("%d\n",total1);
printf("%d",total2);
return 0;
}
# task 5
#include<stdio.h>

int deposit(int balance,int amount ){
return balance+amount;
}
int withdrawal(int balance,int amount ){
if(amount>balance){
    printf("insufficient amount\n");
}
return balance-amount;
}
void processtransaction(int *balance,int amount,int ( *action)(int,int)){
*balance =action(*balance,amount);

}
int main(){
int balance = 2500;
int amount=900;
printf("balance %d\n",balance);
processtransaction(&balance,amount,deposit);
printf("balance %d\n",balance);
processtransaction(&balance,amount,withdrawal);
printf("balance %d",balance);
return 0;

}
# task 6
#include<stdio.h>

int deposit(int currentbalance,int amount ){
return currentbalance+amount;
}
int withdrawal(int currentbalance,int amount ){
if(amount>currentbalance){
    printf("insufficient amount\n");
    return currentbalance; 
}
return currentbalance-amount;

}
int processtransaction(int currentbalance,int amount,int ( *action)(int,int)){
int newbalance=action(currentbalance,amount);
return newbalance;

}
int main(){
int balance = 2500;
int amount=900;
printf("balance %d\n",balance);
balance = processtransaction(balance,amount,deposit);
printf("balance %d\n",balance);
balance=processtransaction(balance,amount,withdrawal);
printf("balance %d",balance);
return 0;

}


}
