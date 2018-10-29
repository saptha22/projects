#include <stdio.h>
#include<conio.h>
#include <string.h>
#include<graphics.h>
char mat[3][3]={'1','2','3','4','5','6','7','8','9'};
char player1[20],player2[20];
int count=0;
void drawboard(){

  int i,j;
  for(i=0;i<3;i++){
    printf("\t|");
    for(j=0;j<3;j++){
        printf(" %c |",mat[i][j]);

    }
    printf("\n\t|---|---|---|\n");
  }
}
char checkwin(){
if(mat[0][0]=='X'&& mat[1][1]=='X'&& mat[2][2]=='X')//1st diagonal
    return 'X';
if(mat[0][2]=='X'&& mat[1][1]=='X'&& mat[2][0]=='X')//2nd diagonal
    return 'X';
if(mat[0][0]=='X'&& mat[1][0]=='X'&& mat[2][0]=='X')//1st col
     return 'X';
if(mat[0][1]=='X'&& mat[1][1]=='X'&& mat[2][1]=='X')//2nd col
     return 'X';
if(mat[0][1]=='X'&& mat[1][1]=='X'&& mat[2][1]=='X')//3rd col
     return 'X';
if(mat[0][0]=='X'&& mat[0][1]=='X'&& mat[0][2]=='X')//1st row
     return 'X';
if(mat[1][0]=='X'&& mat[1][1]=='X'&& mat[1][2]=='X')//2nd row
     return 'X';
if(mat[2][0]=='X'&& mat[2][1]=='X'&& mat[2][2]=='X')//3rd row
     return 'X';
else if(mat[0][0]=='O'&& mat[1][1]=='O'&& mat[2][2]=='O')//1st diagonal
    return 'O';
else if(mat[0][2]=='O'&& mat[1][1]=='O'&& mat[2][0]=='O')//2nd diagonal
    return 'O';
else if(mat[0][0]=='O'&& mat[1][0]=='O'&& mat[2][0]=='O')//1st col
     return 'O';
else if(mat[0][1]=='O'&& mat[1][1]=='O'&& mat[2][1]=='O')//2nd col
     return 'O';
else if(mat[0][1]=='O'&& mat[1][1]=='O'&& mat[2][1]=='O')//3rd col
     return 'O';
else if(mat[0][0]=='O'&& mat[0][1]=='O'&& mat[0][2]=='O')//1st row
     return 'O';
else if(mat[1][0]=='O'&& mat[1][1]=='O'&& mat[1][2]=='O')//2nd row
     return 'O';
else if(mat[2][0]=='O'&& mat[2][1]=='O'&& mat[2][2]=='O')//3rd row
     return 'O';
else
    return '/';
}
void get_input(){
    int i,j;
    char n,a;
  while(1){
         printf("\n\n\nTurn for %s....\n",player1);
         count ++;
         scanf("%c",&n);
        fflush(stdin);
        for(i=0;i<3;i++){
             for(j=0;j<3;j++){
                  if(n==mat[i][j]){
                        if(count%2==0)
                            mat[i][j]='O';
                      else
                        mat[i][j]='X';
                 }
        }

  }
   system("cls");
  drawboard();
  a=checkwin();
  if(a=='X'){
      printf("\n\nCongratulation %s.You won",player1);

      count=0;
      break;
  }
  else if(a=='/' && count==9){
      printf("\n\nMatch Draw!!!!!");

      count=0;
      break;
          }
   printf("\n\n\nTurn for %s....\n",player2);
   count ++;
   scanf("%c",&n);
   fflush(stdin);
        for(i=0;i<3;i++){
             for(j=0;j<3;j++){
                  if(n==mat[i][j]){
                        if(count%2==0)
                            mat[i][j]='O';
                   else
                        mat[i][j]='X';
                 }
        }

  }
  system("cls");
  drawboard();
  a=checkwin();
  if(a=='O'){
      printf("\n\nCongratulation %s.You won",player2);
      break;


   }
}
}
int main()
{
   // menu
  int ch;
  char c;
  int gd=0,gm,maxX,m,i;

 initgraph(&gd,&gm,"C:\\TC\\BGI");

 //game name animation
 settextstyle(1,HORIZ_DIR,6);
 setcolor(14);
 outtextxy(90,150,"T I C     T A C");
 outtextxy(200,240,"T O E");
 delay(4000);
 maxX=getmaxx();
 m=maxX - 400;
 for(i=0;i<m;i++)
 {
    settextstyle(3,HORIZ_DIR,4);
    setcolor(10);
    outtextxy(200,240,"Loading");
    setcolor(12);
    outtextxy(150+i,300,"||||||||||||||||||");
    delay(15);
    if(i<m)
       cleardevice();
}
  closegraph();
  Label :
  system("cls");
  printf("\n1.Start the game...");
  printf("\n2.Quit the game....");
  printf("\n3.How to play......");
  printf("\n\nEnter your choice....\n");
  scanf("%d",&ch);
  switch(ch){
     case 1 :{ system("cls");
              printf("\nWho will play for 'X'\n");
              fflush(stdin);
              gets(player1);
              printf("\nWelcome %s your sign is X",player1);
              printf("\n\n\nWho will play for 'O'\n");
              fflush(stdin);
              gets(player2);
              printf("\nWelcome %s your sign is O\n",player2);
              system("pause");
              system("cls");
              drawboard();
              get_input();
              printf("\n\tGAME OVER\n\n");
              system("pause");
              goto Label;
	      break ;
	      }
     case 2 :{
             system("cls");
             printf("\nAre you sure you want to exit?y/n");
             scanf("%s",&c);
             if(c=='y')
                exit(0);
             else
                goto Label;
	      break ;
	      }
     case 3 : {
	      system("cls");
	      printf("\n\t\t\t\tINSTRUCTION");
              printf("\n\t\t\t\t_____________\n\n");
              system("pause");
              goto Label;
	     break ;
	     }

  }


    getch();
    return 0;
}










