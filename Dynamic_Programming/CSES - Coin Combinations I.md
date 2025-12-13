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
#define pll pair<ll,ll>
const ll MAX = 1e6+20, MOD = 1e9+7;
ll n, x, dp[MAX];
vec<ll> arr;
 
void solve(){        
    cin>>n>>x; arr.resize(n);
    for(auto &i : arr) cin>>i;
    sort(ALL(arr));
    dp[0]=1;
    for(int i=1; i<=x; ++i) {
        for(int j=0; j<n && arr[j] <= i; ++j) {
            dp[i] = (dp[i] + dp[i-arr[j]])%MOD;
        }
    }
    cout<<dp[x]<<endl;
}
 
signed main(){
    ios::sync_with_stdio(0);
    cin.tie(0); cout.tie(0);
    int T=1;
    while(T--){
        solve();
        //cout<<(solve()? "YES" : "NO")<<endl;
    }return 0;
}
