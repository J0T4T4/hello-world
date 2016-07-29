/*
/@author JXK3R
/@email JXK3R@protonmail.ch
*/
#include <conio.h>
#include <iostream>
#include <ctime>
#include <cstdlib>
#include <chrono>
#include <thread>

//parameters
constexpr unsigned wsize = 73;
constexpr unsigned hsize = 59;
constexpr int tick = 200;
constexpr char alive = 'O';
constexpr char dead = ' ';

void initialize(char world_[wsize][wsize])
{
	for (int i = 0; i < hsize; i++)
	{
		for (int j = 0; j < wsize; j++)
		{
			world_[i][j] = dead;
			
			
			if ((j == wsize/2))
			   world_[i][j] = alive;
			   
			if (j % 2)
			   world_[i][j] = alive;
			 /*  
			 if (j == 4 || j == 5 || i == 3)
			 world_[i][j] = alive;*/
		}
	}
}

//reppaces a with b
void wcopy(char worldA_[hsize][wsize], char worldB_[hsize][wsize])
{
	for (int i = 0; i < hsize; i++)
	{
		for (int j = 0; j < wsize; j++)
		{
			worldA_[i][j] = worldB_[i][j];
		}
	}
}

//swaps a with b
void swap(char worldA_[hsize][wsize], char worldB_[hsize][wsize])
{
	char wtemp[hsize][wsize];
	wcopy(wtemp, worldA_);
	wcopy(worldA_, worldB_);
	wcopy(worldB_, wtemp);
}

bool check(int i, int j)
{
	if (i > wsize - 1 || i < 0)
	{
		return false;
	}
	if (j > wsize - 1 || i < 0)
	{
		return false;
	}
	
	return true;
}

char calc(char world_[hsize][wsize], unsigned i, unsigned j)
{
	if (i >= hsize || j >= wsize)
		return 'X';
	else 
	{
		//count the neighbours
		int ncount = 0;
		for (int j_ = -1; j_ < 2; j_++)
		{
			if (world_[i-1][j+j_] == alive && check (i - 1, j + j_))
				++ncount;
		}
		
		for (int j_ = -1; j_ < 2; j_++)
		{
			if (world_[i +1][j+j_] == alive && check(i + 1, j + j_))
				++ncount;
		}
		
		if (world_[i][j - 1] == alive && check(i, j - 1))
				++ncount;
				
		if (world_[i][j + 1] == alive && check(i, j + 1))
				++ncount;
			
		//decide about life	
		if (ncount == 2)
		{
			return world_[i][j];
		} else if ( ncount == 3)
		{
			return alive;
		} else 
		{
			return dead;
		}
	}
	
	return 'X';
}

int main()
{	
	//needed stuff
	bool isAlive = false;
	
	//initialize
	char worldI[hsize][wsize];
	char worldO[hsize][wsize];
	initialize(worldI);
	initialize(worldO);
	
	while (true)
	{
	for (int i = 0; i < hsize; i++)
	{
		for ( int j = 0; j < wsize; j++)
		{
			worldO[i][j] = calc(worldI, i, j);
			std::cout << worldO[i][j];
		}
		
		std::cout << "\n";
	}
	//getch();
	std::this_thread::sleep_for(std::chrono::milliseconds(tick));
	clrscr();
	swap(worldO, worldI);
	}
}
