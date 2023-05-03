# Apache için macOS'ta homebrew PHP modülü nasıl imzalanır ?


**1. Adım: Kod İmzalama için Sertifika Yetkilisi nasıl oluşturulur?** 

https://www.simplified.guide/macos/keychain-ca-code-signing-create 

**2. Adım: kod imzalama sertifikası nasıl oluşturulur?** 

https://www.simplified.guide/macos/keychain-cert-code-signing-create 

**3. Adım: Oluşturduğunuz kod imzalama sertifikası adıyla codesign kullanarak PHP modülünü imzalama**

`codesign --sign "varienos" --force --keychain ~/Library/Keychains/login.keychain-db /opt/homebrew/opt/php@7.4/lib/httpd/modules/libphp7.so`

**4. Adım: Apache'de PHP'yi etkinleştirmek için httpd.conf'a aşağıdakini ekleyin ve Apache'yi yeniden başlatın**

`LoadModule php7_module /opt/homebrew/opt/php@7.4/lib/httpd/modules/libphp7.so`

**5. Adım: Apache Restart **

`sudo apachectl -k restart`
