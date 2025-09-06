```cpp
#include <bits/stdc++.h>
using namespace std;

#define SET(m,i) ((m)|(1ULL<<(i)))
#define TEST(m,i) ((m)&(1ULL<<(i)))
#define CLEAR(m,i) ((m)&~(1ULL<<(i)))
#define DEBUG(n) cout<<#n<<" = "<<n<<endl
#define DEBUG_ALL(a) for(auto &w:a)cout<<w<<' ';cout<<endl;
#define ALLN(x,n) begin(x), begin(x)+n
#define ALL(x) begin(x), end(x)
#define vec vector
#define snd second
#define fst first
#define pb push_back
#define ll long long
const ll MAX = 2e5+20, MOD = 1e9+7;
ll n, a[MAX], b[MAX];

bool solve(){        
    cin>>n;
    for(auto &i : span(a, n)) cin>>i;
    for(auto &i : span(b, n)) cin>>i;
    if(a[n-1]!=b[n-1]) return 0;
    for(int i=n-2; i>=0; --i) 
        if(a[i]!=b[i] && (a[i]^a[i+1])!=b[i] && (a[i]^b[i+1])!=b[i]) return 0;
    return 1;
}

signed main(){
    ios::sync_with_stdio(0);
    cin.tie(0); cout.tie(0);
    int T=1;
    cin>>T;
    while(T--){
        cout<<(solve()? "YES" : "NO")<<endl;
    }return 0;
}
