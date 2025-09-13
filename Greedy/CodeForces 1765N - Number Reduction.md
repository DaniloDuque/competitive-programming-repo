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
#define fun min
const ll MAX = 2e5+20, MOD = 1e9+7;
const ll K = 19;
ll n, k;
string s;
pll spt[K][1<<K];

void init(vec<pll> &a){
    for(ll i = 0; i < n; ++i) spt[0][i] = a[i];
    for(ll k = 1; k < K; ++k)
        for(ll i = 0; i <= n-(1LL<<k); ++i)
            spt[k][i] = fun(spt[k-1][i], spt[k-1][i+(1LL<<(k-1))]);
}

pll query(ll i, ll j){
    ll k = 63LL - __builtin_clzll(j-i);
    auto r = fun(spt[k][i], spt[k][j-(1LL<<k)]);
    return {r.fst, r.snd-i};
}

string greed(ll i, ll k) {
    if(!k) {
        auto f = s.substr(i, s.size());
        reverse(ALL(f));
        return f;
    }
    if(i+k>=n) return "";
    if(i!=0) {
        ll j = query(i, i+k+1).snd;
        return greed(i+j+1, k-j) + s[i+j];
    }
    pll mn = {s[i], 0};
    for(int j=0; j<=k; ++j) if(s[i+j]!='0') mn = min(mn, {s[i+j], j});
    ll j = mn.snd;
    return greed(i+j+1, k-j) + s[i+j];
}

string solve(){        
    cin>>s>>k;
    n = s.size();
    vec<pll> a;
    for(int i=0; i<n; ++i) a.pb({s[i], i}); 
    init(a);
    auto r = greed(0, k);
    reverse(ALL(r));
    return r;
}

signed main(){
    ios::sync_with_stdio(0);
    cin.tie(0); cout.tie(0);
    int T=1;
    cin>>T;
    while(T--){
        cout<<solve()<<endl;
        //cout<<(solve()? "YES" : "NO")<<endl;
    }return 0;
}
