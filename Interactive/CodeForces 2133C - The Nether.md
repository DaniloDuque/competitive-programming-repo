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
const ll MAX = 5e2+20, MOD = 1e9+7;
ll n;
map<ll, vec<ll>> lens;
vec<ll> rslt;

ll query(ll x, ll k, vec<ll> S) {
    ll rs;
    cout<<"? "<<x<<" "<<k;
    for(auto &i : S) cout<<' '<<i;
    cout<<endl;
    cin>>rs;
    return rs;
}

void dfs(ll cur, ll dep) {
    rslt.pb(cur);
    if(dep == 1) return;
    for(auto &i : lens[dep-1]) {
        if(query(cur, 2, {cur, i}) == 1) continue;
        dfs(i, dep-1);
        break;
    }
}

void solve(){        
    cin>>n; 
    rslt.clear(); lens.clear();
    vec<ll> S(n); iota(ALL(S), 1);
    for(int i=1; i<=n; ++i) lens[query(i, n, S)].pb(i);
    auto cur = lens.rbegin();
    dfs(cur->snd[0], cur->fst);
    cout<<"! "<<rslt.size();
    for(auto &i : rslt) cout<<' '<<i;
    cout<<endl;
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
