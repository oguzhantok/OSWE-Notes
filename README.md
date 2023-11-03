<h1 style="margin:20%">OSWE-Notes</h1>

## Vulnerabilities:

<details>
<summary><b>1. SQL Injection</b></summary>
:white_large_square: <br/>
:white_check_mark:
</details>

<details>
<summary><b>2. Cross-Site Scripting (XSS)</b></summary>
</details>


<summary><b>3. Deserialization</b></summary>

 :white_large_square: Portswigger Deserialization Labs [link](https://portswigger.net/web-security/deserialization) </br>
 :white_large_square: OWASP Deserialization Cheat Sheet [link](https://cheatsheetseries.owasp.org/cheatsheets/Deserialization_Cheat_Sheet.html) </br>
 :white_large_square: Deserialization Vulnerability [link](https://www.exploit-db.com/docs/english/44756-deserialization-vulnerability.pdf) </br>
 :white_large_square: Serialization: the big threat [link](https://klezvirus.github.io/Advanced-Web-Hacking/Serialisation/) </br>
 :white_large_square: (AWAE Course) DotNetNuke Cookie Deserialization RCE </br>
 :white_large_square: (Youtube) Exploiting Deserialization Vulnerabilities in Java [link](https://www.youtube.com/watch?v=VviY3O-euVQ) </br>
 :white_large_square: (Youtube) DEF CON 25 Conference [link](https://www.youtube.com/watch?v=ZBfBYoK_Wr0) </br>
 :white_large_square: (Tool) ysoserial [link](https://github.com/frohoff/ysoserial/) </br>

 #### PHP 

 * Native methods for PHP serialization are <b>serialize()</b> and <b>unserialize()</b>
 * PHP uses human-readable string serialization format.
   
 User object with the attributes:
 ```
 $user->name = "carlos"; 
 $user->isLoggedIn = true;
 ```
 Serialized User object:
 ```
 O:4:"User":2:{s:4:"name":s:6:"carlos"; s:10:"isLoggedIn":b:1;}
 ```
 Vulnerable code snippet:
 ```
 // instantiate a User object based on the data from the cookie
 $user = unserialize($_COOKIE);
 if ($user->isAdmin === true) {
 // allow access to admin interface
 }
 ```
 Vulnerable code snippet:
 ```
 $login = unserialize($_COOKIE)
 if ($login['password'] == $password) {
 // log in successfully
 // 5 == "5" evaluates true
 // 5 == "5 of something" is in practice treated as 5 == 5
 // 0 == "Example string" evaluates true
 // attacker modified the password attribute so that it contained the integer 0 instead of the expected string. As long as the stored password does not start with a number, the condition would always return true, enabling an authentication bypass
 }
 ```

* User class'ının access_token attribute'unun CustomTemplate class'ı olarak set edilmesi (Type Casting hatası olsa bile obje çoktan create edilmiş oluyor.): 
```
O:4:"User":2:{s:8:"username";s:6:"wiener";s:12:"access_token";s:32:"hrrjw29gehwnau6rlbmb5natdyiarnns";}
```
```
O:4:"User":2:{s:8:"username";s:6:"wiener";s:12:"access_token";O:14:"CustomTemplate":2:{s:18:"template_file_path";s:23:"/home/carlos/morale.txt";s:14:"lock_file_path";s:23:"/home/carlos/morale.txt";};}
 ```
 #### JAVA
 * Java uses binary serialization format.
 * Serialized Java objects always begin with the same bytes, which are encoded as <b>ac ed</b> in hexadecimal and <b>rO0</b> in Base64
 * Any class that implements the interface <b>java.io.Serializable</b> can be serialized and deserialized. If you have source code access, take note of any code that uses the <b>readObject()</b> method, which is used to read and deserialize data from an <b>InputStream</b>
 * "Magic Byte" "AC ED"	"¬í"	"Serialized Java Data"
 #### .NET
 
 #### Python



<details>
<summary><b>4. Type Juggling</b></summary>
</details>

<details>
<summary><b>5. Prototype Pollution</b></summary>
</details>

<details>
<summary><b>6. JWT Vulnerabilities</b></summary>
</details>

<details>
<summary><b>7. Directory Traversal</b></summary>
</details>

<details>
<summary><b>8. Command Injection</b></summary>
</details>

<details>
<summary><b>9. File Upload Vulnerabilities</b></summary>
</details>

<details>
<summary><b>10. Race Conditions</b></summary>
</details>

<details>
<summary><b>11. Server Side Request Forgery (SSRF)</b></summary>
</details>

<details>
<summary><b>12. XXE Injection</b></summary>
</details>

<details>
<summary><b>13. Server Side Template Injection (SSTI)</b></summary>
</details>

<details>
<summary><b>14. HTTP Request Smuggling</b></summary>
</details>

<details>
<summary><b>15. OAuth Vulnerabilities</b></summary>
</details>

<details>
<summary><b>16. Remote Code Execution (RCE)</b></summary>
</details>

------------------------------------------------------------------------------------------
## Web-Frameworks:
