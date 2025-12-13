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
    dp[0] = 0;
    for(int i=1; i<=x; ++i) {
        dp[i] = MOD;
        for(int j=0; j<n && arr[j] <= i; ++j) 
            dp[i] = min(dp[i], 1+dp[i-arr[j]]); 
    }
    ll r = dp[x];
    cout<<((r >= MOD)? -1 : r)<<endl;
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
