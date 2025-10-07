Challenge cho dãy số 
109, 214, 110, 215, 67, 151, 70, 193, 72, 124, 112, 192, 121, 216, 66, 115, 114, 198, 104, 199, 68, 120, 89, 122, 125
và file file.txt có nội dung:

#include <iostream>

using namespace std;

int main()
{
    int n = flag.size();
    int flag_string[n];
    for (int i = 0; i < n; i++)
    {
        if (i % 2 == 0) flag_string[i] = flag[i];
        else flag_string[i] = flag[i] + flag_string[i-1];
    }
    for (int i = 0; i < n; i++)
        cout << flag_string[i] << " ";
    return 0;
}

File này là 1 chương trình C++ cho biết quy tắc mã hóa flag: 
- Nếu số thứ tự của kí tự là chẵn: Giá trị mã hóa là giá trị ASCII của kí tự gốc.
- Nếu số thứ tự của kí tự là chẵn: Giá trị mã hóa là tổng của giá trị ASCII của ký tự gốc và giá trị mã hóa của phần tử ngay trước đó.

Quy tắc giải mã: 
- Nếu số thứ tự của kí tự là chẵn: Từ giá trị mã hóa, chuyển đổi ASCII thu được kí tự gốc.
- Nếu số thứ tự của kí tự là chẵn: Từ giá trị mã hóa, trừ đi giá trị mã hóa của phần tử ngay trước đó, sau đó chuyển đổi ASCII thu được kí tự gốc.

Sử dụng https://www.onlinegdb.com/online_c++_compiler để chạy chương trình giải mã:
Chương trình giải mã:
#include <iostream>
#include <vector>
#include <string>

using namespace std;

int main()
{
    vector<int> encrypted_array = {
        109, 214, 110, 215, 67, 151, 70, 193, 72, 124, 
        112, 192, 121, 216, 66, 115, 114, 198, 104, 199, 
        68, 120, 89, 122, 125
    };

    int n = encrypted_array.size();
    string decrypted_flag = "";
    int current_ascii_value;

    for (int i = 0; i < n; i++)
    {
        if (i % 2 == 0) {
            current_ascii_value = encrypted_array[i];
        } else {
            current_ascii_value = encrypted_array[i] - encrypted_array[i-1];
        }
        
        decrypted_flag += (char)current_ascii_value;
    }

    cout << "Flag:" << endl;
    cout << decrypted_flag << endl;
    
    return 0;
}

Chạy chương trình, thu được flag.
<img width="1191" height="1244" alt="image" src="https://github.com/user-attachments/assets/8a6d7c54-bd60-454b-a5b3-5fc1fc4fe8eb" />

Flag: miniCTF{H4pPy_B1rTh_D4Y!}
