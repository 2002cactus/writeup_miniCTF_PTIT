Challenge cho 2 file .txt:
file_du_lieu.txt
```
#include <iostream>
using namespace std;
#define flag_string flag[i]++
int main()
{
    int n = flag.size();
    for (int i = 0; i < n; i++) flag_string;
    return 0;
}
```

noi_dung_ki_la.txt
njojDUG|Xf2d1n4`u1`Wv2oe4s2boe

File file_du_lieu.txt cho biết quy tắc mã hóa flag là tăng giá trị ASCII của tất cả các ký tự trong flag lên 1.

Vậy để giải mã file noi_dung_ki_la.txt thì cần giảm giá trị ASCII của tất cả các ký tự trong flag xuống 1.
Sử dụng https://www.onlinegdb.com/online_c++_compiler để chạy chương trình giải mã.

Chương trình giải mã:
```
#include <iostream>
#include <string>

using namespace std;

int main()
{
    string encrypted_flag = "njojDUG|Xf2d1n4`u1`Wv2oe4s2boe";
    int n = encrypted_flag.size();
    
    for (int i = 0; i < n; i++) {
        encrypted_flag[i]--;
    }

    cout << "Flag: " << encrypted_flag << endl; 
    
    return 0;
}
```

Chạy chương trình, thu được flag.
<img width="969" height="829" alt="image" src="https://github.com/user-attachments/assets/5583c571-fe39-4c4f-bad5-414fe491afab" />

Flag: miniCTF{We1c0m3_t0_Vu1nd3r1and}
