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
const ll MAX = 2e5+20, MOD = 1e9+7;
ll n, s1, s2, x;
vec<pll> arr;

void solve(){        
    cin>>n>>s1>>s2; arr.clear();
    for(int i=0; i<n; ++i) cin>>x, arr.pb({x, i+1});
    sort(ALL(arr), greater<pll>());
    vec<ll> a, b;
    for(auto &[x, y] : arr) {
        if(s1*(a.size()+1) < s2*(b.size()+1)) a.pb(y);
        else b.pb(y);
    }
    cout<<a.size();
    for(auto &i : a) cout<<' '<<i; cout<<endl;
    cout<<b.size();
    for(auto &i : b) cout<<' '<<i; cout<<endl;
}

signed main(){
    ios::sync_with_stdio(0);
    cin.tie(0); cout.tie(0);
    int T=1;
    cin>>T;
    while(T--){
        solve();
        //cout<<(solve()? "YES" : "NO")<<endl;
    }return 0;
}
