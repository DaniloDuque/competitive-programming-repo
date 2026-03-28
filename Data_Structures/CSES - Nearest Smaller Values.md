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
 
ll n, x, rslt[MAX];
set<pair<ll, ll>> st;
set<ll> ind;
 
ll find_nearest(ll i) {
    auto it = ind.lower_bound(i);
    if (it == ind.begin()) return 0;
    --it;
    return *it;
}
 
void solve(){        
    cin >> n;
    st.clear();ind.clear();
    map<ll, vec<ll>> mp;
    for(int i = 1; i <= n; ++i) {
        cin >> x;
        mp[x].pb(i);
    }
    for (auto &[val, v] : mp) {
        for (auto &i : v) rslt[i] = find_nearest(i);
        for (auto &i : v) ind.insert(i);
    }
    for(int i = 1; i <= n; ++i) cout << rslt[i] << ' ';
    cout << '\n';
}
 
signed main(){
    ios::sync_with_stdio(0);
    cin.tie(0); cout.tie(0);
    int T = 1;
    while(T--){
        solve();
    }
    return 0;
}
