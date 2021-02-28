# DSO-NUS-CTF-Easysql
# Challenge Description
This challenge server can be accessed here:</br>
</br>
(Any one of the options below is fine)</br>
(Only accessible via web browser URL)</br>
ctf-85ib.balancedcompo.site:9000</br>
ctf-sn3y.balancedcompo.site:9000</br>
ctf-rv6w.balancedcompo.site:9000</br>
ctf-ptb1.balancedcompo.site:9000</br>
ctf-f3jj.balancedcompo.site:9000</br>
ctf-4q22.balancedcompo.site:9000</br>
ctf-7jca.balancedcompo.site:9000</br>
ctf-ea38.balancedcompo.site:9000</br>
ctf-jfi4.balancedcompo.site:9000</br>
ctf-ks5n.balancedcompo.site:9000</br>

# Apporach
For the challenge, upon accessing one of the links we are greeted with this webpage</br>
![image](https://user-images.githubusercontent.com/65858555/109410002-2d989700-79d2-11eb-8503-d2d7d46c5926.png)
</br>
I was not excatly sure on what to do, but since it was easy sql I decided to use the payload `'or 1=1 -- ` on the input field which gave this</br>
![image](https://user-images.githubusercontent.com/65858555/109409967-d85c8580-79d1-11eb-92db-b954e2ba7462.png)
</br>
I thought 114514 or ys in sha256 was the flag, but unfortunately it was wrong. I tried to ask for a hint but was told to explore the application more.
I used the payload `SELECT * FROM all_tables WHERE OWNER = 'DATABASE_NAME' `  to find the database table, but instead got this output</br>
![image](https://user-images.githubusercontent.com/65858555/109409975-ef9b7300-79d1-11eb-96fc-7e996ab8a45f.png)
</br>
With the input, I decided to do a google search on it, which led me to few CTF Writeups done on 强网杯 2019.
I went to look at the writeups, and found that it was very similar to the challenge, with the source code also having the title easy sql.
Thus following the writeup, I first used the payload `1';show tables# ` and got this output</br>
![image](https://user-images.githubusercontent.com/65858555/109409987-0a6de780-79d2-11eb-8a66-9e7c83de8231.png)
</br>
After seeing the same output as the one in the writeups, I read through the ways to get the flag and thought that using the handler on the table "1919810931114514" was the best way to get it. I injected the payload `1';handler `1919810931114514` open;handler `1919810931114514` read first# ` to get the results and it showed the flag.</br>
Note: 1919810931114514 with backticks for the payload to work
</br>
</br>
![image](https://user-images.githubusercontent.com/65858555/109410023-42752a80-79d2-11eb-8c7b-868a595a73c7.png)
# The flag
DSO-NUS{427a3c725d559d066e010131695880665436761182ac104f72d6a5d70912c2e6}
# Link to the writeup I referenced to
https://www.codenong.com/cs105730558/





