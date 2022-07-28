# SoC-2022

Project for me in SoC 2022 is Introduction to Competative programming

In first weeks I have gone through problems of CSES and studied the book of CSES.

After that I have participated in contests of code forces, solved few problems in leet code, and solving problems of Scalar Academy.


Here are codes of some problems I have done:
(I am not including codes of all problems, I am including the problems for which I faced difficulty only)

1.Once Bob needed to find the second order statistics of a sequence of integer numbers. Lets choose each number from the sequence exactly once and sort them. The value on the second position is the second order statistics of the given sequence. In other words it is the smallest element strictly greater than the minimum. Help Bob solve this problem.

Input
The first input line contains integer n (1 ≤ n ≤ 100) — amount of numbers in the sequence. The second line contains n space-separated integer numbers — elements of the sequence. These numbers don't exceed 100 in absolute value.

Output
If the given sequence has the second order statistics, output this order statistics, otherwise output NO.

Code:
#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;
int main()
{  int n,a;
cin>>n;
	vector<int> v;
for(int i=0;i<n;i++){
    cin>>a;
    v.push_back(a);
}
	vector<int>::iterator ip;
 
	
	std::sort(v.begin(), v.end());
	
 
	
	ip = std::unique(v.begin(), v.end());
	
 
	
	v.resize(std::distance(v.begin(), ip));
 
	
	if(v.size()<2){
	    cout<<"NO";
	}
    else {
        cout<<v[1];
    }
	return 0;
}
                   
 2.Petya has an array a consisting of n integers. He wants to remove duplicate (equal) elements.

Petya wants to leave only the rightmost entry (occurrence) for each element of the array. The relative order of the remaining unique elements should not be changed.

Input
The first line contains a single integer n (1≤n≤50) — the number of elements in Petya's array.

The following line contains a sequence a1,a2,…,an (1≤ai≤1000) — the Petya's array.

Output
In the first line print integer x — the number of elements which will be left in Petya's array after he removed the duplicates.

In the second line print x integers separated with a space — Petya's array after he removed the duplicates. For each unique element only the rightmost entry should be left.
                   
  Code:
             #include <iostream>
#include <vector>
 
 
using namespace std;
 
int main()
{
 int n,a;
 vector<int> v;
 vector<int> v1;
 cin>>n;
 for(int i=0;i<n;i++){
     cin>>a;
    v.push_back(a);
 }
 int k=v.size();
 v1.push_back(v[k-1]);
 for(int i=k-2;i>=0;i--){
     int p=0;
     int q=v1.size();
     for(int j=0;j<q;j++){
     if(v[i]==v1[j]){
         p=1;
     }
     }
     if(p==0){
         v1.push_back(v[i]);
     }
 }
 int q=v1.size();
 cout<<q<<endl;
 for(int i=q-1;i>=0;i--){
     cout<<v1[i]<<" ";
 }
 
    return 0;
}
  
  
  
  3. Spring has come, and the management of the AvtoBus bus fleet has given the order to replace winter tires with summer tires on all buses.

You own a small bus service business and you have just received an order to replace n tires. You know that the bus fleet owns two types of buses: with two axles (these buses have 4 wheels) and with three axles (these buses have 6 wheels).

You don't know how many buses of which type the AvtoBus bus fleet owns, so you wonder how many buses the fleet might have. You have to determine the minimum and the maximum number of buses that can be in the fleet if you know that the total number of wheels for all buses is n.

Input
The first line contains an integer t (1≤t≤1000) — the number of test cases. The following lines contain description of test cases.

The only line of each test case contains one integer n (1≤n≤1018) — the total number of wheels for all buses.

Output
For each test case print the answer in a single line using the following format.

Print two integers x and y (1≤x≤y) — the minimum and the maximum possible number of buses that can be in the bus fleet.

If there is no suitable number of buses for the given n, print the number −1 as the answer.
  
  
  Code:
  
  #include <iostream>
using namespace std;
 
void testcase(){
	long long int n;
	cin >> n;
  if(n<4){
    cout<<"-1"<<endl;
  }
  else
	if(n%4!= 0 && (n-4)%6!=0 && (n-8)%6!=0 && (n-6)%4!=0 ){
    cout<<"-1"<<endl;
  }
  else 
  if(n%4 == 0 && n%6 == 0 ){
    cout<<n/6<<" "<<n/4<<endl;
  }
  else
  if(n%4 != 0 && n%6 == 0 && n>6){
    cout<<n/6<<" "<<((n-6)/4+1)<<endl;
  }
  else 
  if(n%4 == 0 && n%6!= 0 &&  n>4 && (n-4)%6 ==0){
    cout<<((n-4)/6+1)<<" "<<(n)/4<<endl;
  }
  else
  if(n%4 == 0 && n%6 != 0 &&  n!=8 && (n-8)%6 ==0){
    cout<<((n-8)/6 +2)<<" "<<(n)/4<<endl;
  }
  else
  if(n%4!=0 && n%6!=0 && (n-4)%6==0 && (n-6)%4==0){
      cout<<((n-4)/6+1)<<" "<< ((n-6)/4+1)<<endl;
  }
  else
  if(n%4!=0 && n%6!=0 && (n-8)%6==0 && (n-6)%4==0){
      cout<<((n-8)/6+2)<< " "<<((n-6)/4+1)<<endl;
  }
  else
  if(n==4){
      cout<<n/4<<" "<<n/4<<endl;
  }
  else
  if(n==8){
      cout<<n/4<<" "<<n/4<<endl;
  }
  else
  if(n==6){
      cout<<n/6<<" "<<n/6<<endl;
  }
}
 
 
int main(){
	int tt;
	cin >> tt;
	while(tt--){
		testcase();
	}
	return 0;
}
  
  4.Alice and Bob play a game. Alice has n cards, the i-th of them has the integer ai written on it. Bob has m cards, the j-th of them has the integer bj written on it.

On the first turn of the game, the first player chooses one of his/her cards and puts it on the table (plays it). On the second turn, the second player chooses one of his/her cards such that the integer on it is greater than the integer on the card played on the first turn, and plays it. On the third turn, the first player chooses one of his/her cards such that the integer on it is greater than the integer on the card played on the second turn, and plays it, and so on — the players take turns, and each player has to choose one of his/her cards with greater integer than the card played by the other player on the last turn.

If some player cannot make a turn, he/she loses.

For example, if Alice has 4 cards with numbers [10,5,3,8], and Bob has 3 cards with numbers [6,11,6], the game may go as follows:

Alice can choose any of her cards. She chooses the card with integer 5 and plays it.
Bob can choose any of his cards with number greater than 5. He chooses a card with integer 6 and plays it.
Alice can choose any of her cards with number greater than 6. She chooses the card with integer 10 and plays it.
Bob can choose any of his cards with number greater than 10. He chooses a card with integer 11 and plays it.
Alice can choose any of her cards with number greater than 11, but she has no such cards, so she loses.
Both Alice and Bob play optimally (if a player is able to win the game no matter how the other player plays, the former player will definitely win the game).

You have to answer two questions:

who wins if Alice is the first player?
who wins if Bob is the first player?
Input
The first line contains one integer t (1≤t≤1000) — the number of test cases. Each test case consists of four lines.

The first line of a test case contains one integer n (1≤n≤50) — the number of cards Alice has.

The second line contains n integers a1,a2,…,an (1≤ai≤50) — the numbers written on the cards that Alice has.

The third line contains one integer m (1≤m≤50) — the number of Bob's cards.

The fourth line contains m integers b1,b2,…,bm (1≤bi≤50) — the numbers on Bob's cards.

Output
For each test case, print two lines. The first line should be Alice if Alice wins when she is the first player; otherwise, the first line should be Bob. The second line should contain the name of the winner if Bob is the first player, in the same format.
  
  Code:
  
  #include <bits/stdc++.h>
#include <vector>
 
using namespace std;
 
int
main ()
{
  int tt, z = 1;
  cin >> tt;
  while (z <= tt)
    {
      vector < int > a;
      vector < int > b;
      int n, m;
      cin >> n;
      for (int i = 0; i < n; i++){
	  int y;
      cin>>y;
		a.push_back(y);
	}
      cin >> m;
      for (int j = 0; j < m; j++)
	{int z;
    cin>>z;
		b.push_back(z);
	}
      sort (a.begin (), a.end ());
      sort (b.begin (), b.end ());
      if (a[n - 1] > b[m - 1])
	{
	  cout << "Alice" << endl;
	  cout << "Alice" << endl;
	}
      if (a[n - 1] < b[m - 1])
	{
	  cout << "Bob" << endl;
	  cout << "Bob" << endl;
	}
      if (a[n - 1] == b[m - 1])
	{
	  cout << "Alice" << endl;
	  cout << "Bob" << endl;
	}
      z++;
    }
  
}
                         
  5. Given a sequence a1,a2,…,an, find the minimum number of elements to remove from the sequence such that after the removal, the sum of every 2 consecutive elements is even.

Input
Each test contains multiple test cases. The first line contains a single integer t (1≤t≤100) — the number of test cases. Description of the test cases follows.

The first line of each test case contains a single integer n (3≤n≤105).

The second line of each test case contains n integers a1,a2,…,an (1≤ai≤109) — elements of the sequence.

It is guaranteed that the sum of n over all test cases does not exceed 105.

Output
For each test case, print a single integer — the minimum number of elements to remove from the sequence such that the sum of every 2 consecutive elements is even.
                         
   Code:
                         
                         #include<iostream>
 
using namespace std;
 
 
int main(){
	int t,e=0,o=0;
	cin>>t;
	while(t>=1){
	    int n;
	    e=0;o=0;
	cin>>n;
	int a[n];
	for (int i = 0; i < n; i++)
	{
		cin>>a[i];
	}
	for (int i = 0; i < n; i++)
	{
		if(a[i]%2==0){
			e++;}
		else
		{o++;}
	}
	
	if(e>o){
		cout<<o<<endl;}
	else {
		cout<<e<<endl;}
		
	t--;}}
