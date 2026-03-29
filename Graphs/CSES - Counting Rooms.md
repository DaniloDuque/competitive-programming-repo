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
const ll MAX = 2e3, MOD = 1e9+7;
ll n, m, M[MAX*MAX];
vec<vec<ll>> G;
 
struct UnionFind{
    vector<ll> uf;
    void init(ll n){uf.assign(n, -1);}
    ll Find(ll i){return (uf[i]==-1)? i : uf[i] = Find(uf[i]);}
    bool Union(ll i, ll j){
        bool e = Find(i)==Find(j);
        if(!e) uf[Find(i)] = Find(j);
        return e;
    }
};
 
void solve(){        
    cin>>n>>m;
    char c;
    UnionFind uf; uf.init(n*m);
    for (int i=0; i<n*m; ++i) cin>>c, M[i]=(c=='.');
    for (int i=0; i<n; ++i) 
        for (int j=0; j<m; ++j) {
            auto idx = i*m+j;
            if (!M[idx]) continue;
            if (j+1 < m && M[idx+1]) uf.Union(idx, idx+1);
            if (i+1 < n && M[idx+m]) uf.Union(idx, idx+m);
        }
    set<ll> st;
    for(int i=0; i<n*m; ++i) {
        if (M[i]) st.insert(uf.Find(i));
    }
    cout<<st.size()<<endl;
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
 
