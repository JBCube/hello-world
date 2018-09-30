# hello-world
//demo
    /*input
                James Bond OO7

        */                 
        // Bursting Balloons
        #include <bits/stdc++.h>
        #define mod 1000000007
        #define pb push_back
        #define mp make_pair
        #define int long long
        #define nodes 100001
        #define level 18  // ceil(log2(nodes))
        #define N 15000005
        using namespace std;

        
        int32_t main()
        {
            ios_base::sync_with_stdio(false);
            cin.tie(NULL);
            

       #ifndef ONLINE_JUDGE
        // for getting input from input.txt
        freopen("C:/Users/Arpan/Desktop/input.txt", "r", stdin);
        // for writing output to output.txt

        freopen("C:/Users/Arpan/Desktop/output.txt", "w", stdout);
        #endif
          
         
         int n;
         cin>>n;

         int arr[n];
         for(int i=0;i<n;i++) cin>>arr[i];

        int dp[n][n];
        memset(dp,0,sizeof(dp));
        for(int len=1;len<=n;len++)
        {
            for(int i=0;i<=n-len;i++)
            {
                int j = i+len-1;
                for(int k=i;k<=j;k++)
                {
                    int left = 1, right = 1;

                    if(i!=0) left = arr[i-1];
                    if(j!=n-1) right = arr[j+1];

                    int before=0, after =0;

                    if(i!=k) before = dp[i][k-1];
                    if(j!=k) after = dp[k+1][j];

                    dp[i][j] = max(dp[i][j], left*arr[k]*right + before + after);
                }
            }
        }
        cout<<dp[0][n-1];
            
            return 0;
        }
