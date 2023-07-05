# TSL상에서 작동하는 HTTPS Web_Server
---
## 팀원들과 Github 협업한 주소입니다.</br>
https://github.com/RoughBoy0723/https_with_openssl/tree/min
</br></br>
**구현 계획**
 * HTTP -> HTTPS -> Domain connect HTTP -> PHP and Raspberry Pi Porting 
</br></br>

# **<span style="color:red"> Troubleshooting</span>**</br>
![Alt text](/image/handshake_err.JPG)
 </br>**사설 인증서를 통해 localhost로 접속 시</br> Hand_Shake error 발생후 connect되는 문제가 있었습니다.**</br>
</br>**해결방안 생각해보기**
  * **1**　Open Source인 OpenSSL의 HandShake의 역할을 하는 함수인 SSL_accept Code review</br></br>
   * **2**　Linux에서 Curl(Client url) -k을 통해 localhost 접속 시 handshake error 발생하지않음.
        * curl -k는 SSL/TLS 인증서의 유효성 검사를 건너뛰고 
        </br>연결을 하는 명령어
        * **∴** 사설 인증서로 인한 Hand_Shake error??</br></br>

***사설 인증서가 가장 유력한 문제라고 생각하였습니다.***</br>
비록 Localhost라고 할지라도 Chrom, Firefox 등등 인터넷 브라우저는
</br>사설 인증서를 인정해주지 않는다는 걸 알게 되었습니다.
</br>문제 해결을 위해 도메인 및 공인인증서를 발급 받았습니다.
</br></br>예상대로 Hand-Shake error의 원인이라고 생각한 사설인증서가</br> Trouble의 원인이이였고, 공인 인증서발급을 받아 Hand_Shake error를 해결하였습니다.
</br>

![Alt text](/image/domain.png)
![Alt text](/image/domain_wireshark.png)
