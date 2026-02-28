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
ll n, m, c;

void move(priority_queue<ll> &V, ll x) {
    ll y = V.top(); V.pop();
    if (y <= x) return;
    V.push(y-x);
}

void solve(){        
    cin>>n>>m;
    priority_queue<ll> A, B;
    for(int i=0; i<n; ++i) cin>>c, A.push(c);
    for(int i=0; i<m; ++i) cin>>c, B.push(c);
    for(int i=0; A.size() && B.size(); ++i) {
        if (i&1) {
            ll x = B.top();
            move(A, x);
        } else {
            ll x = A.top();
            move(B, x);
        }
    }
    if (B.empty()) cout<<"Alice"<<endl;
    else cout<<"Bob"<<endl;
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
