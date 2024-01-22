#include<iostream>
#include<ctime>
#include<cstdlib>
using namespace std;

int main() {
    srand(time(0));

    char choice;
    do {

        int player;
        char toss;
        int coin;
        int random;
        char melee_attack;
        char ult_attack;
        bool player1Turn;
        int hp1 = 1000;
        int hp2 = 1000;
        int hit;
        int ult_hit;
        int damage;
        int turn;


        cout << "      Welcome to Number Fight        " << endl;
        cout << "-------------------------------------" << endl;
        cout << "Press P to Play" << endl;
        cout << "Press R to see Rules" << endl;
        cout << "Enter your choice: ";
        cin >> choice;

        if (choice == 'P' || choice == 'p') {

            cout<<"Enter number of turns: ";
            cin>>turn;
            cout << "Player 1 will choose head/tail to determine attack sequence" << endl;
            cout << " " << endl;
            cout << "Press H for Head" << endl;
            cout << "Press T for Tail" << endl;
            cout << " " << endl;

           int move_count1=turn/2;
           int move_count2=turn/2;
            // Keep asking until a valid choice is entered
            do {
                cout << "Enter your choice: ";
                cin >> toss;
                if (toss != 'H' && toss != 'h' && toss != 'T' && toss != 't') {
                    cout << "Invalid choice. Please enter H or T." << endl;
                }
            } while (toss != 'H' && toss != 'h' && toss != 'T' && toss != 't');

            cout << "---Tossing a coin---" << endl;
            cout << "---                   ---" << endl;
            coin = (rand() % 2) + 1;

            if ((toss == 'H' || toss == 'h') && coin == 1) {
                cout << "You won the toss" << endl;
                cout << "You will attack first" << endl;
                cout << " " << endl;
                player1Turn = true;
                cout << " " << endl;
            } else if ((toss == 'T' || toss == 't') && coin == 2) {
                cout << "You won the toss" << endl;
                cout << "You will attack first" << endl;
                cout << " " << endl;
                player1Turn = true;
                cout << " " << endl;
            } else {
                cout << "You lost the toss" << endl;
                cout << "You will attack second" << endl;
                cout << " " << endl;
                player1Turn = false;
                cout << " " << endl;
            }

            cout << "          Let the fight begin        " << endl;
            cout << "-------------------------------------" << endl;
            cout << " " << endl;
            cout << "Current HP of Player 1: " << hp1 << endl;
            cout << "Current HP of Player 2: " << hp2 << endl;
            cout << "Move count of Player 1:" <<move_count1<< endl;
            cout << "Move count of Player 2:" <<move_count2<< endl;
            cout << " " << endl;

            for (int i = 0; i < turn; i++) {
                if (player1Turn) {
                    cout << "Player 1 will attack" << endl;
                    cout << "Press e for Melee Attack" << endl;
                    cout << "Attack: ";
                    cin >> melee_attack;
                    hit = (rand() % 2) + 1;
                    if (hit == 1) {
                        cout << "You hit the enemy" << endl;
                        cout << " " << endl;
                        damage = (rand() % 300) + 50;
                        if (damage > 200) {
                            cout << "Critical Hit" << endl;
                            cout << " " << endl;
                        } else {
                            cout << " " << endl;
                        }
                        hp2 = hp2 - damage;
                        cout << "Current HP of Player 1: " << hp1 << endl;
                        cout << "Current HP of Player 2: " << hp2 << endl;
                        cout << "Move count of Player 1:" <<-- move_count1<< endl;
                        cout << " " << endl;
                        if (hp1 <= 0) {
                            cout << "Player 1 dies" << endl;
                            break;
                        } else if (hp2 <= 0) {
                            cout << "Player 2 dies" << endl;
                            break;
                        }
                    } else if (hit == 2) {
                        cout << "You missed the enemy" << endl;
                        cout << " " << endl;
                        cout << "Current HP of Player 1: " << hp1 << endl;
                        cout << "Current HP of Player 2: " << hp2 << endl;
                        cout << "Move count of Player 1:" << --move_count1<< endl;
                        if (hp1 <= 0) {
                            cout << "Player 1 dies" << endl;
                            break;
                        } else if (hp2 <= 0) {
                            cout << "Player 2 dies" << endl;
                            break;
                        }
                    } else {
                        cout << "Invalid choice" << endl;
                        cout << " " << endl;
                    }
                } else {
                    cout << "Player 2 will attack" << endl;
                    cout << "Press e for Melee Attack" << endl;
                    cout << "Attack: ";
                    cin >> melee_attack;
                    hit = (rand() % 2) + 1;
                    if (hit == 1) {
                        cout << "Player 2 hit the enemy" << endl;
                        cout << " " << endl;
                        damage = (rand() % 300) + 50;
                        if (damage > 200) {
                            cout << "Critical Hit" << endl;
                            cout << " " << endl;
                        } else {
                            cout << " " << endl;
                        }
                        hp1 = hp1 - damage;
                        cout << "Current HP of Player 1: " << hp1 << endl;
                        cout << "Current HP of Player 2: " << hp2 << endl;
                        cout << "Move count of Player 2:" << --move_count2<< endl;
                        cout << " " << endl;
                        if (hp1 <= 0) {
                            cout << "Player 1 dies" << endl;
                            break;
                        } else if (hp2 <= 0) {
                            cout << "Player 2 dies" << endl;
                            break;
                        }
                    } else if (hit == 2) {
                        cout << "Player 2 missed the enemy" << endl;
                        cout << " " << endl;
                        cout << "Current HP of Player 1: " << hp1 << endl;
                        cout << "Current HP of Player 2: " << hp2 << endl;
                        cout << "Move count of Player 2:" << --move_count2<< endl;
                        cout << " " << endl;
                        if (hp1 <= 0) {
                            cout << "Player 1 dies" << endl;
                        } else if (hp2 <= 0) {
                            cout << "Player 2 dies" << endl;
                        }
                    } else {
                        cout << "Invalid choice" << endl;
                        cout << " " << endl;
                    }
                }
                player1Turn = !player1Turn;
            }

            if (hp1 > hp2) {
                cout << "Player 1 wins" << endl;
            } else if (hp1 < hp2) {
                cout << "Player 2 wins" << endl;
            } else {
                cout << "It's a draw" << endl;
                cout << " " << endl;
                cout << "Now it's time for the ultimate attack" << endl;
                ult_hit = (rand() % 2) + 1;
                if (ult_hit == 1) {
                    cout << "Player 1 will attack" << endl;
                    cout << "Press e for Ultimate Attack" << endl;
                    cout << "Attack: ";
                    cin >> ult_attack;
                    damage = (rand() % 600) + 200;
                    if (damage > 1000) {
                        cout << "Critical Hit" << endl;
                        cout << " " << endl;
                    } else {
                        cout << " " << endl;
                    }
                    hp2 = hp2 - damage;
                    cout << "Current HP of Player 1: " << hp1 << endl;
                    cout << "Current HP of Player 2: " << hp2 << endl;
                    cout << " " << endl;
                } else if (ult_hit == 2) {
                    cout << "Player 2 will attack" << endl;
                    cout << "Press e for Ultimate Attack" << endl;
                    cout << "Attack: ";
                    cin >> ult_attack;
                    damage = (rand() % 600) + 200;
                    if (damage > 1000) {
                        cout << "Critical Hit" << endl;
                        cout << " " << endl;
                    } else {
                        cout << " " << endl;
                    }
                    hp1 = hp1 - damage;
                    cout << "Current HP of Player 1: " << hp1 << endl;
                    cout << "Current HP of Player 2: " << hp2 << endl;
                    cout << " " << endl;
                    if (hp1 <= 0) {
                        cout << "Player 1 dies" << endl;
                    } else if (hp2 <= 0) {
                        cout << "Player 2 dies" << endl;
                    }
                } else {
                    cout << "Invalid choice" << endl;
                    cout << " " << endl;
                }
            }

            cout << "Do you want to play again? (Y for again/N for another time): ";
            cin >> choice;
        } else if (choice == 'R' || choice == 'r') {
            cout << "               Rules                 " << endl;
            cout << "-------------------------------------" << endl;
            cout << "1. There will be 2 players" << endl;
            cout << "2. Each player will have 1000 HP" << endl;
            cout << "3. There will be a move/total hit counter which will be a countdown to 0" << endl;
            cout << "4. The player reaching 0 HP first will lose" << endl;
            cout << "5. If none of the players reach 0 HP before the countdown reaches 0, the player with the highest HP will win" << endl;
        } else {
            cout << "Thanks for playing!" << endl;
        }
    } while (choice == 'Y' || choice == 'y');

    return 0;
}
