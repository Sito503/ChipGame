# ChipGame
#include <stdio.h>
#include <iostream>
#include <cstdlib>
using namespace std;

const int MAX_CHIPS = 100;
const float MAX_TURN = .5;

int main()
{
    bool  player1turn = true;
    bool gameover = false;
    
    int chipsinpile = 0;
    int chipstaken = 0;
    int maxperturn = 0;
    string playername[2];
    char userChoice;
    
    //seed the random number generator
    srand(time(0));
    
    //ask players for the their names, then store in an array
    cout<<"player 1, enter your name please: \n";
    cin>>playername[0];cout<<"thank you, goodluck!\n";
    cout<<"player 2, enter your name please: \n";
    cin>>playername[1];cout<<"thank you, goodluck!\n";
    
    
    do
    {
    
    chipsinpile = (rand() % MAX_CHIPS) + 1;
    
    cout<<"This round will start with "<< chipsinpile<<" chips in the pile\n";
    gameover = false;
    while(gameover == false)
    {
      
    do
    {
    maxperturn = (MAX_TURN * chipsinpile);
    if (player1turn)
    
        {  
        cout<<playername[0]<<" how many chips would you like:\n";
        }
    else
            {
        cout<<playername[1]<<" how many chips would you like:\n";
            }
    
    cout<<"you can take up to ";
    
    if (maxperturn == 0)
    {
        cout<<" 1\n";
    }
    else
        {
        cout<<maxperturn<<endl;
        }
    cin>>chipstaken;
    }while((chipstaken > maxperturn) && (chipsinpile > 1));
      
    
    //chipstaken=(rand()% maxperturn) + 1;
    //cout<<"number taken: "<<chipstaken<<endl;
    
    chipsinpile = chipsinpile - chipstaken;
    cout<<"there are "<<chipsinpile<<" left in the pile\n";
    if (chipsinpile==0)
    {
        gameover=true;
        if (player1turn)
        {
            cout<< playername[0]<<", congratulations you won\n";
        }
        else
        {
            cout<< playername[1]<<", congratulations you won\n";
        }
    }
    else 
    {
        player1turn = !player1turn;
    }
    
        
    }
    cout<<"do you wish to play again? (Y/N)\n";
    cin>>userChoice;
    
    
    }while((userChoice == 'y') || (userChoice == 'Y'));
    
   
}


