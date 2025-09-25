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
ll n, x;
multiset<ll> mst;

ll solve(){        
    cin>>n; mst.clear();
    for(int i=0; i<n; ++i) cin>>x, mst.insert(x);
    ll s = 0, r = 0;
    while(mst.size() > 1) {
        auto mx = prev(mst.end());
        auto mn = mst.begin();
        ll i=*mn, j=*mx;
        mst.erase(mn);
        if(s+i >= j) {
            ll d = (j-s);
            r+=d+1;
            s=0;
            mst.erase(mx);
            if(i>d) mst.insert(i-d);
        }
        else r+=i, s+=i;
    }
    if(mst.empty()) return r;
    ll cur = *mst.begin();
    if(cur==1 || s >= cur) return r+1;
    return r+(cur-s+1)/2+1;
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
