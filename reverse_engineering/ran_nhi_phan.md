Challenge cho 2 file Binary_snake.py và flag.
File Binary_snake.py là 1 chương trình python có dòng đầu tiên là một chuỗi gán giá trị song song dùng để che giấu các hàm và chức năng của hàm.
lllllllllllllll, llllllllllllllI, lllllllllllllIl, lllllllllllllII, llllllllllllIll, llllllllllllIlI, llllllllllllIIl, llllllllllllIII, lllllllllllIlll = ord, print, int, input, range, len, exit, open, chr

File flag chứa flag được mã hóa.

Dịch ngược file Binary_snake.py, thu được:
import sys
from random import randint
from math import log2

def decrypt_flag():
    """
    Giải mã chuỗi trong file 'flag' bằng phép XOR với khóa 'DEADBEEF'.
    """
    with open('flag', 'r') as file_handle:
        key = 'DEADBEEF'
        ciphertext = file_handle.read()
        
        for i in range(len(ciphertext)):
            decrypted_ascii = ord(ciphertext[i]) ^ ord(key[i % len(key)])
            print(chr(decrypted_ascii), end='') 
        
        file_handle.close()

target_index = randint(1, 512) 

hints_array = 513 * [0] 
for i in range(1, 513):
    if i < target_index:
        hints_array[i] = 'No, go ahead'
    elif i > target_index:
        hints_array[i] = 'No, go back'
hints_array[target_index] = 'Good hunter!!\n=====================\n'

max_attempts = int(log2(512)) 

while max_attempts > 0:
    try:
        user_guess = int(input('Select part of snake: '))
    except ValueError:
        continue

    if 1 <= user_guess <= 512:
        print(hints_array[user_guess])
        
        if user_guess == target_index:
            decrypt_flag()
            sys.exit(0)
            
        max_attempts -= 1
    else:
        print('There is no part of snake like that, try valid one ([1,512])')

Logic chương trình là: Đây là 1 trò chơi đoán số random từ 1 đến 512, người chơi có 9 lần đoán, nếu đoán đúng sẽ in ra flag. 2^9 = 512 nên nếu đoán theo thuật tìm kiếm nhị phân thì chắc chắn sẽ đoán đúng số.
<img width="381" height="398" alt="image" src="https://github.com/user-attachments/assets/ee36bdea-3bd3-4f51-8f28-2cb0234439dd" />

Flag: miniCTF{W3ird_sn4k3_6366}
