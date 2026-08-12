#include<bits/stdc++.h>
#define ll long long
#define endl '\n'
#define pb push_back
#define fi first
#define se second
#define dbl double
using namespace std;

const ll INF = 67e14, mod1 = 1e9 + 7ll, mod2 = 998244353ll;
const int MAXIN = 1e9 + 67;

void addself(ll &a, ll b){a = (a + b) % mod1;}
void subself(ll &a, ll b){a = (mod1 + a - b) % mod1;}
void multself(ll &a, ll b){a = (a * b) % mod1;}

int conv(char x){
    if(x == '0') return 0;
    if(x == '1') return 1;
    if(x == '2') return 2;
    if(x == '3') return 3;
    if(x == '4') return 4;
    if(x == '5') return 5;
    if(x == '6') return 6;
    if(x == '7') return 7;
    if(x == '8') return 8;
    if(x == '9') return 9;
}

ll bin(ll a, ll b){
    
}

int main(){
    ios_base::sync_with_stdio(false); // kalo interactive gausah pake
    cin.tie(0); // kalo interactive gausah pake
    // tiati overflow 1e5 * 1e15 > LONG LONG MAX

    // precompute
    vector<string>pc = {"0000", "1111", "6248", "1397", "6464", "5555", "6666", "1793", "6842", "1919"};

    int tt; cin >> tt;
    while(tt--){
        string a, b; cin >> a >> b;
        int m;
        if(b.size() >= 3){
            b = b.substr(b.size() - 2, 2);
        }
        m = stoi(b);
        vector<ll>dp(10, 0ll);
        for(int i = 0; i < a.size(); i++){
            int co = conv(a[i]);
            addself(dp[co], 1ll);
            vector<ll>tm(10, 0ll);
            for(int j = 1; j < 10; j++){
                if(co + j >= 10){
                    int t = (co + j + 1) % 10;
                    addself(tm[t], dp[j]);
                    // cout << t << " " << dp[t] << endl;
                }
                else{
                    int t = co + j;
                    addself(tm[t], dp[j]);
                    // cout << t << " " << dp[t] << endl;
                }
            }
            for(int i = 1; i < 10; i++){
                addself(dp[i], tm[i]);
            }
        }
        // for(int i = 1; i < 10; i++){
        //     cout << dp[i] << " ";
        // }
        // cout << endl;
        for(int i = 9; i >= 1; i--){
            if(dp[i] != 0){
                cout << dp[i] << endl;
                break;
            }
            
        }
    }
}

// check for n = 1?
// edge case? maybe for some cases it doesnt work?
// reassure the greedy
// variables
// search for another approaches
// integer overflow
// check constraint
// brute force is possible
