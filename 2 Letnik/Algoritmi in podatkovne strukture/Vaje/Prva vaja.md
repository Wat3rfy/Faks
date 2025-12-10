```cpp
#include <iostream>
#include <string>
#include <vector>
#include <utility>
#include <algorithm>

using namespace std;

/*
8 5
ANA 20
MIHA 13
TADEJ 18
PETRA 17
SIMON 21
TONE 25
JOZE 24
KATJA 15
*/


int main(){
    int k,n;
    cin >> n >> k;
    vector<pair<string, int>> vnos(n);
    
    for(int i = 0; i<n; ++i){
        cin >> vnos[i].first >> vnos[i].second;
    }

    cout << endl;
    for(auto v : vnos){
        cout << v.first << " " << v.second << endl;
    }
    
    sort(vnos.begin(), vnos.end(), [](auto &a, auto &b){return a.second>b.second;});
    
    auto it_end = vnos.begin();
    advance(it_end, k);
    sort(vnos.begin(), it_end, [](auto &a, auto &b){return a.first<b.first;});


    
    cout << endl;
    for(vector<pair<string,int>>::iterator it = vnos.begin(); it != it_end; ++it){
        cout << it->first << " " << it->second << endl;

    }
 


    return 0;
}
```

Includi za 

```cpp
#include <iostream> // za cout, cin
#include <string>   // za string
#include <vector>   // za vector
#include <utility>  // za pair
#include <algorithm>// za sort
```

Inicializiramo vektor parov

```cpp
vector<pair<string, int>> vnos(n);
```

