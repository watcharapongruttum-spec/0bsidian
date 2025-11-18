
![[Pasted image 20231108160418.png]]


![[Pasted image 20231108162448.png]]

![[Pasted image 20231108162532.png]]

![[Pasted image 20231108162655.png]]

![[Pasted image 20231108162638.png]]

![[Pasted image 20231108162741.png]]

![[Pasted image 20231108162811.png]]

![[Pasted image 20231108163401.png]]

**Build and deploy again**
```shell
npm run build
firebase deploy
```

![[Pasted image 20231108163543.png]]

![[Pasted image 20231108163629.png]]

.htaccess
```
RewriteEngine On
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule ^ index.html [QSA,L]
```