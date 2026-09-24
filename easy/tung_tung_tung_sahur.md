# tung_tung_tung_sahur (easy)
## tung_tung_tung_sahur.py
<img width="428" height="484" alt="image" src="https://github.com/user-attachments/assets/39874a6e-b677-4a60-81bc-0597e3d9f273" />

## Phân tích file
- Trong file **tung_tung_tung_shahur.py** ta thấy $C = m^e$ và cứ $C < N$ là $C$ sẽ tăng gấp đôi và chương trình sẽ in ra "Tung!". Khi $C > N$ thì $C$ bị trừ đi một lượng $N$ và chương trình sẽ in ra "Sahur!".
- Điều này có nghĩa là sau cuối chương trình $C$ đã gấp thêm $2^k$ lần với k bằng số lần xuất hiện của "Tung!" và bị trừ đi $N$.
- Ta đảo ngược quá trình lại sẽ thu được $C_{bđ} = (C + N)/(2^k)$ với $k = 164$.
- Sau khi có $C_{bđ}$ ta dễ dàng tìm ra $m = \sqrt[e]{C_{bđ}}$. Từ đó tìm ra **flag**.

## Python code
```python
e = 3
N = 140435453730354645791411355194663476189925572822633969369789174462118371271596760636019139860253031574578527741964265651042308868891445943157297334529542262978581980510561588647737777257782808189452048059686839526183098369088517967034275028064545393619471943508597642789736561111876518966375338087811587061841
C = 49352042282005059128581014505726171900605591297613623345867441621895112187636996726631442703018174634451487011943207283077132380966236199654225908444639768747819586037837300977718224328851698492514071424157020166404634418443047079321427635477610768472595631700807761956649004094995037741924081602353532946351

# Tung! xuất hiện 164 lần
C_bđ = (C + N)//(2**164)

from sympy import integer_nthroot
m,b = integer_nthroot(C_bđ,e)

print(bytes.fromhex(hex(m)[2:]).decode())
```
