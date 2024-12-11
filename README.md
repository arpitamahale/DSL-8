# DSL-8
// Practical No -08  
// Problem Statement: The ticket booking system of Cinemax theater has to be implemented using C++ program. There are 10 rows and 7 seats in each row. Doubly circular linked list has to be maintained to keep track of free seats at rows. Assume some random booking to start with. Use array to store pointers (Head pointer) to each row. On demand 
// a) The list of available seats is to be displayed 
// b) The seats are to be booked 
// c) The booking can be cancelled.
// Program:-
#include <iostream>
#include<stdlib.h>
using namespace std;
class node
{ public:
node* next;
node* prev;
int seat;
string id;
int status;
};
class cinemax
{
public:
node* head,* tail ,* temp;
cinemax()
{
head=NULL;
}
void create_list();
void display();
void book();
void cancel();
void avail();

};
void cinemax::create_list()
{
int i=1;
temp=new node;
temp->seat=1;
temp->status=0;
temp->id="null";
tail=head=temp;
for(int i=2;i<=70;i++)
{
node *p;
p= new node;
p->seat=i;
p->status=0;
p->id="null";
tail->next=p;
p->prev=tail;
tail=p;
tail->next=head;
head->prev=tail;

}
}
void cinemax::display()
{
{ int r=1;
node* temp;
temp=head;
int count=0;
cout<<"\n------------------------------------------------------------------------------------\n";
cout<<" Screen this way \n";
cout<<"------------------------------------------------------------------------------------\n";
while(temp->next!=head)
{
if(temp->seat/10==0)
cout<<"S0"<<temp->seat<<" :";
else
cout<<"S"<<temp->seat<<" :";

if(temp->status==0)
cout<<"|___| ";
else
cout<<"|_B_| ";
count++;
if(count%7==0)
{
cout<<endl;
r++;
}
temp=temp->next;
}
cout<<"S"<<temp->seat<<" :";
if(temp->status==0)
cout<<"|___| ";
else
cout<<"|_B_| ";
}
}
void cinemax::book()
{ int x;
string y;
label:
cout<<"\n\n\nEnter seat number to be booked\n";
cin>>x;
cout<<"Enter your ID number\n";
cin>>y;
if(x<1||x>70)
{
cout<<"Enter correct seat number to book (1-70)\n";
goto label;
}
node *temp;
temp=new node;
temp=head;
while(temp->seat!=x)
{
temp=temp->next;
}

if(temp->status==1)
cout<<"Seat already booked!\n";
else{
temp->status=1;
temp->id=y;
cout<<"Seat "<<x<<" booked!\n";
}

}
void cinemax::cancel()
{
int x;
string y;
label1:
cout<<"Enter seat number to cancel booking\n";
cin>>x;
cout<<"Enter you ID\n";
cin>>y;
if(x<1||x>70)
{
cout<<"Enter correct seat number to cancel (1-70)\n";
goto label1;
}
node *temp;
temp=new node;
temp=head;
while(temp->seat!=x)
{
temp=temp->next;
}
if(temp->status==0)
{
cout<<"Seat not booked yet!!\n";
}
else
{
if(temp->id==y)
{
temp->status=0;
cout<<"Seat Cancelled!\n";
}

else
cout<<"Wrong User ID !!! Seat cannot be cancelled!!!\n";
}
}
void cinemax::avail()
{
int r=1;
node* temp;
temp=head;
int count=0;
cout<<"\n\n\n\n";
cout<<"\n------------------------------------------------------------------------------------\n";
cout<<" Screen this way \n";
cout<<"------------------------------------------------------------------------------------\n";
while(temp->next!=head)
{
{
if(temp->seat/10==0)
cout<<"S0"<<temp->seat<<" :";
else
cout<<"S"<<temp->seat<<" :";
if(temp->status==0)
cout<<"|___| ";
else if(temp->status==1)
cout<<" ";

count++;
if(count%7==0)

{

cout<<endl;

}

}
temp=temp->next;
}
if(temp->status==0)
{
cout<<"S"<<temp->seat<<" :";

if(temp->status==0)
cout<<"|___| ";
}

}
int main()
{ cinemax obj;
obj.create_list();
int ch;
char c='y';
while(c=='y')
{ obj.display();
cout<<"\n*********************************************\n";
cout<<" CINEMAX MOVIE THEATRE\n";
cout<<"*********************************************\n";
cout<<"\nEnter Choice\n1.Current SeatStatus\n2.Book Seat \n3.Available Seat\n4.CancelSeat\n";
cin>>ch;
switch(ch)
{
case 1:obj.display();
break;
case 2: obj.book();
break;
case 3:obj.avail();
break;
case 4: obj.cancel();
break;
default: cout<<"Wrong choice input\n";
}
cout<<"\nDo you want to perform any other operation : (y/n)\n";
cin>>c;
}
return 0;
}

// Output:
// ------------------------------------------------------------------------------------
//  Screen this way 
// ------------------------------------------------------------------------------------
// S01 :|___| S02 :|___| S03 :|___| S04 :|___| S05 :|___| S06 :|___| S07 :|___| 
// S08 :|___| S09 :|___| S10 :|___| S11 :|___| S12 :|___| S13 :|___| S14 :|___| 
// S15 :|___| S16 :|___| S17 :|___| S18 :|___| S19 :|___| S20 :|___| S21 :|___| 
// S22 :|___| S23 :|___| S24 :|___| S25 :|___| S26 :|___| S27 :|___| S28 :|___| 
// S29 :|___| S30 :|___| S31 :|___| S32 :|___| S33 :|___| S34 :|___| S35 :|___| 
// S36 :|___| S37 :|___| S38 :|___| S39 :|___| S40 :|___| S41 :|___| S42 :|___| 
// S43 :|___| S44 :|___| S45 :|___| S46 :|___| S47 :|___| S48 :|___| S49 :|___| 
// S50 :|___| S51 :|___| S52 :|___| S53 :|___| S54 :|___| S55 :|___| S56 :|___| 
// S57 :|___| S58 :|___| S59 :|___| S60 :|___| S61 :|___| S62 :|___| S63 :|___| 
// S64 :|___| S65 :|___| S66 :|___| S67 :|___| S68 :|___| S69 :|___| S70 :|___|
// *********************************************
//  CINEMAX MOVIE THEATRE
// *********************************************

// Enter Choice
// 1.Current SeatStatus
// 2.Book Seat
// 3.Available Seat
// 4.CancelSeat
// 1

// ------------------------------------------------------------------------------------
//  Screen this way
// ------------------------------------------------------------------------------------
// S01 :|___| S02 :|___| S03 :|___| S04 :|___| S05 :|___| S06 :|___| S07 :|___|
// S08 :|___| S09 :|___| S10 :|___| S11 :|___| S12 :|___| S13 :|___| S14 :|___|
// S15 :|___| S16 :|___| S17 :|___| S18 :|___| S19 :|___| S20 :|___| S21 :|___|
// S22 :|___| S23 :|___| S24 :|___| S25 :|___| S26 :|___| S27 :|___| S28 :|___|
// S29 :|___| S30 :|___| S31 :|___| S32 :|___| S33 :|___| S34 :|___| S35 :|___|
// S36 :|___| S37 :|___| S38 :|___| S39 :|___| S40 :|___| S41 :|___| S42 :|___|
// S43 :|___| S44 :|___| S45 :|___| S46 :|___| S47 :|___| S48 :|___| S49 :|___| 
// S50 :|___| S51 :|___| S52 :|___| S53 :|___| S54 :|___| S55 :|___| S56 :|___|
// S57 :|___| S58 :|___| S59 :|___| S60 :|___| S61 :|___| S62 :|___| S63 :|___|
// S64 :|___| S65 :|___| S66 :|___| S67 :|___| S68 :|___| S69 :|___| S70 :|___|
// Do you want to perform any other operation : (y/n)
// y

// ------------------------------------------------------------------------------------
//  Screen this way
// ------------------------------------------------------------------------------------
// S01 :|___| S02 :|___| S03 :|___| S04 :|___| S05 :|___| S06 :|___| S07 :|___|
// S08 :|___| S09 :|___| S10 :|___| S11 :|___| S12 :|___| S13 :|___| S14 :|___|
// S15 :|___| S16 :|___| S17 :|___| S18 :|___| S19 :|___| S20 :|___| S21 :|___|
// S22 :|___| S23 :|___| S24 :|___| S25 :|___| S26 :|___| S27 :|___| S28 :|___|
// S29 :|___| S30 :|___| S31 :|___| S32 :|___| S33 :|___| S34 :|___| S35 :|___|
// S36 :|___| S37 :|___| S38 :|___| S39 :|___| S40 :|___| S41 :|___| S42 :|___| 
// S43 :|___| S44 :|___| S45 :|___| S46 :|___| S47 :|___| S48 :|___| S49 :|___|
// S50 :|___| S51 :|___| S52 :|___| S53 :|___| S54 :|___| S55 :|___| S56 :|___|
// S57 :|___| S58 :|___| S59 :|___| S60 :|___| S61 :|___| S62 :|___| S63 :|___|
// S64 :|___| S65 :|___| S66 :|___| S67 :|___| S68 :|___| S69 :|___| S70 :|___|
// *********************************************
//  CINEMAX MOVIE THEATRE
// *********************************************

// Enter Choice
// 1.Current SeatStatus
// 2.Book Seat
// 3.Available Seat
// 4.CancelSeat
// 2

// Enter seat number to be booked
// 23
// Enter your ID number
// 222
// Seat 23 booked!

// Do you want to perform any other operation : (y/n)
// y

// ------------------------------------------------------------------------------------
//  Screen this way
// ------------------------------------------------------------------------------------
// S01 :|___| S02 :|___| S03 :|___| S04 :|___| S05 :|___| S06 :|___| S07 :|___|
// S08 :|___| S09 :|___| S10 :|___| S11 :|___| S12 :|___| S13 :|___| S14 :|___|
// S15 :|___| S16 :|___| S17 :|___| S18 :|___| S19 :|___| S20 :|___| S21 :|___|
// S22 :|___| S23 :|_B_| S24 :|___| S25 :|___| S26 :|___| S27 :|___| S28 :|___|
// S29 :|___| S30 :|___| S31 :|___| S32 :|___| S33 :|___| S34 :|___| S35 :|___|
// S36 :|___| S37 :|___| S38 :|___| S39 :|___| S40 :|___| S41 :|___| S42 :|___|
// S43 :|___| S44 :|___| S45 :|___| S46 :|___| S47 :|___| S48 :|___| S49 :|___|
// S50 :|___| S51 :|___| S52 :|___| S53 :|___| S54 :|___| S55 :|___| S56 :|___|
// S57 :|___| S58 :|___| S59 :|___| S60 :|___| S61 :|___| S62 :|___| S63 :|___| 
// S64 :|___| S65 :|___| S66 :|___| S67 :|___| S68 :|___| S69 :|___| S70 :|___|
// *********************************************
//  CINEMAX MOVIE THEATRE
// *********************************************

// Enter Choice
// 1.Current SeatStatus
// 2.Book Seat
// 3.Available Seat
// 4.CancelSeat
// 3 

// ------------------------------------------------------------------------------------
//  Screen this way
// ------------------------------------------------------------------------------------
// S01 :|___| S02 :|___| S03 :|___| S04 :|___| S05 :|___| S06 :|___| S07 :|___|
// S08 :|___| S09 :|___| S10 :|___| S11 :|___| S12 :|___| S13 :|___| S14 :|___|
// S15 :|___| S16 :|___| S17 :|___| S18 :|___| S19 :|___| S20 :|___| S21 :|___|
// S22 :|___| S23 : S24 :|___| S25 :|___| S26 :|___| S27 :|___| S28 :|___|
// S29 :|___| S30 :|___| S31 :|___| S32 :|___| S33 :|___| S34 :|___| S35 :|___|
// S36 :|___| S37 :|___| S38 :|___| S39 :|___| S40 :|___| S41 :|___| S42 :|___|
// S43 :|___| S44 :|___| S45 :|___| S46 :|___| S47 :|___| S48 :|___| S49 :|___| 
// S50 :|___| S51 :|___| S52 :|___| S53 :|___| S54 :|___| S55 :|___| S56 :|___|
// S57 :|___| S58 :|___| S59 :|___| S60 :|___| S61 :|___| S62 :|___| S63 :|___|
// S64 :|___| S65 :|___| S66 :|___| S67 :|___| S68 :|___| S69 :|___| S70 :|___|
// Do you want to perform any other operation : (y/n)
// y

// ------------------------------------------------------------------------------------
//  Screen this way
// ------------------------------------------------------------------------------------
// S01 :|___| S02 :|___| S03 :|___| S04 :|___| S05 :|___| S06 :|___| S07 :|___|
// S08 :|___| S09 :|___| S10 :|___| S11 :|___| S12 :|___| S13 :|___| S14 :|___|
// S15 :|___| S16 :|___| S17 :|___| S18 :|___| S19 :|___| S20 :|___| S21 :|___|
// S22 :|___| S23 :|_B_| S24 :|___| S25 :|___| S26 :|___| S27 :|___| S28 :|___| 
// S29 :|___| S30 :|___| S31 :|___| S32 :|___| S33 :|___| S34 :|___| S35 :|___|
// S36 :|___| S37 :|___| S38 :|___| S39 :|___| S40 :|___| S41 :|___| S42 :|___|
// S43 :|___| S44 :|___| S45 :|___| S46 :|___| S47 :|___| S48 :|___| S49 :|___|
// S50 :|___| S51 :|___| S52 :|___| S53 :|___| S54 :|___| S55 :|___| S56 :|___|
// S57 :|___| S58 :|___| S59 :|___| S60 :|___| S61 :|___| S62 :|___| S63 :|___|
// S64 :|___| S65 :|___| S66 :|___| S67 :|___| S68 :|___| S69 :|___| S70 :|___|
// *********************************************
//  CINEMAX MOVIE THEATRE
// *********************************************

// Enter Choice
// 1.Current SeatStatus
// 2.Book Seat
// 3.Available Seat
// 4.CancelSeat
// 4
// Enter seat number to cancel booking
// 23
// Enter you ID
// 222
// Seat Cancelled!

// Do you want to perform any other operation : (y/n)
// y

// ------------------------------------------------------------------------------------
//  Screen this way
// ------------------------------------------------------------------------------------
// S01 :|___| S02 :|___| S03 :|___| S04 :|___| S05 :|___| S06 :|___| S07 :|___|
// S08 :|___| S09 :|___| S10 :|___| S11 :|___| S12 :|___| S13 :|___| S14 :|___|
// S15 :|___| S16 :|___| S17 :|___| S18 :|___| S19 :|___| S20 :|___| S21 :|___|
// S22 :|___| S23 :|___| S24 :|___| S25 :|___| S26 :|___| S27 :|___| S28 :|___|
// S29 :|___| S30 :|___| S31 :|___| S32 :|___| S33 :|___| S34 :|___| S35 :|___| 
// S36 :|___| S37 :|___| S38 :|___| S39 :|___| S40 :|___| S41 :|___| S42 :|___|
// S43 :|___| S44 :|___| S45 :|___| S46 :|___| S47 :|___| S48 :|___| S49 :|___|
// S50 :|___| S51 :|___| S52 :|___| S53 :|___| S54 :|___| S55 :|___| S56 :|___|
// S57 :|___| S58 :|___| S59 :|___| S60 :|___| S61 :|___| S62 :|___| S63 :|___|
// S64 :|___| S65 :|___| S66 :|___| S67 :|___| S68 :|___| S69 :|___| S70 :|___|
// *********************************************
//  CINEMAX MOVIE THEATRE
// *********************************************

// Enter Choice
// 1.Current SeatStatus
// 2.Book Seat
// 3.Available Seat
// 4.CancelSeat
// 1

// ------------------------------------------------------------------------------------
//  Screen this way
// ------------------------------------------------------------------------------------
// S01 :|___| S02 :|___| S03 :|___| S04 :|___| S05 :|___| S06 :|___| S07 :|___|
// S08 :|___| S09 :|___| S10 :|___| S11 :|___| S12 :|___| S13 :|___| S14 :|___|
// S15 :|___| S16 :|___| S17 :|___| S18 :|___| S19 :|___| S20 :|___| S21 :|___|
// S22 :|___| S23 :|___| S24 :|___| S25 :|___| S26 :|___| S27 :|___| S28 :|___|
// S29 :|___| S30 :|___| S31 :|___| S32 :|___| S33 :|___| S34 :|___| S35 :|___|
// S36 :|___| S37 :|___| S38 :|___| S39 :|___| S40 :|___| S41 :|___| S42 :|___|
// S43 :|___| S44 :|___| S45 :|___| S46 :|___| S47 :|___| S48 :|___| S49 :|___|
// S50 :|___| S51 :|___| S52 :|___| S53 :|___| S54 :|___| S55 :|___| S56 :|___| 
// S57 :|___| S58 :|___| S59 :|___| S60 :|___| S61 :|___| S62 :|___| S63 :|___|
// S64 :|___| S65 :|___| S66 :|___| S67 :|___| S68 :|___| S69 :|___| S70 :|___|
// Do you want to perform any other operation : (y/n)
// n
