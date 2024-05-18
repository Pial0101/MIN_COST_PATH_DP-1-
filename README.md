#include <bits/stdc++.h>
using namespace std;
#define ll long long

ll dp_code(vector<vector<ll>>& arr, ll n, ll m) {
    vector<vector<ll>> dp(n, vector<ll>(m));
    dp[0][0] = arr[0][0];
    

    for (ll j = 1; j < m; j++) {
        dp[0][j] = dp[0][j-1] + arr[0][j];
    }

 
    for (ll i = 1; i < n; i++) {
        dp[i][0] = dp[i-1][0] + arr[i][0];
    }


    for (ll i = 1; i < n; i++) {
        for (ll j = 1; j < m; j++) {
            dp[i][j] = min(dp[i-1][j], dp[i][j-1]) + arr[i][j];
        }
    }

    return dp[n-1][m-1];
}

void solve() {
    ll n, m;
    cin >> n >> m;
    vector<vector<ll>> arr(n, vector<ll>(m));
    
    for (ll i = 0; i < n; ++i) {
        for (ll j = 0; j < m; ++j) {
            cin >> arr[i][j];
        }
    }

    ll result = dp_code(arr, n, m);
    cout << result << endl;
}

int main() {
    ios_base::sync_with_stdio(false);
    cin.tie(NULL);
    
    int t;
    cin >> t;
    while (t--) {
        solve();
    }
    return 0;
}

