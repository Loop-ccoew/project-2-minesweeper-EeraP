# project-2-minesweeper-EeraP
project-2-minesweeper-EeraP created by GitHub Classroom
import java.io.*;
public class Minesweeper
{
Minesweeper obj[];
static int num;
int score=0;
char m[][]=new char[4][4];
char n[][]=new char[4][4];
public static void main(String args[])throws IOException
{
	BufferedReader b=new BufferedReader(new InputStreamReader(System.in));
	System.out.println("\t\t\t\tMINESWEEPER\n In the following grid,out of 16 places,6 places contain a bomb.If you select a safe place,the # gets replaced by a _ and you score 4 points.If you select a bomb, the # gets replaced by a * and you lose one life and 1 mark gets deducted.You have 3 such lives.If you lose all lives before clearing all 10 safe places, you lose the game.\n Enter the number of players:");
	num=Integer.parseInt(b.readLine());
	Minesweeper obj[]=new Minesweeper[num];
	for(int i=0;i<num;i++)
	{
		System.out.println("Player "+(i+1));
		obj[i]=new Minesweeper();
		obj[i].display();
		obj[i].game();
	}	
}
void display()
{
	for(int i=0;i<4;i++)
	{
		for(int j=0;j<4;j++)
		{
			m[i][j]='#';
			n[i][j]='#';
			System.out.print(n[i][j]+" ");
		}
		System.out.println();
	}
	m[0][1]='*';
	m[0][3]='*';
	m[1][0]='*';
	m[2][2]='*';
	m[3][0]='*';
	m[3][3]='*';				
}
void game()throws IOException
{
	BufferedReader br=new BufferedReader(new InputStreamReader(System.in));
	int r,c,life=3,cnt=0,score=0;
	while(life>0 && cnt<10)
	{
		System.out.println("Enter row number:");
		r=Integer.parseInt(br.readLine());
		System.out.println("Enter column number:");
		c=Integer.parseInt(br.readLine());
		if(m[r-1][c-1]=='*')
		{
			life=life-1;
			score=score-1;
			System.out.println("Bad choice!You clicked on a bomb!You have "+life+" more chances left");
			n[r-1][c-1]='*';
		}
		else
		{
			score=score+4;
			cnt=cnt+1;
			n[r-1][c-1]='_';
		}
		for(int i=0;i<4;i++)
		{
			for(int j=0;j<4;j++)
			{
				System.out.print(n[i][j]+" ");
			}
			System.out.println();
		}
	}
	if(cnt==10)
	{
		System.out.println("Congratulations!You have found all the safe places!Your score is "+score);
	}
	else 
	{
		System.out.println("Game over.Your score is "+score);
	}
}
}
