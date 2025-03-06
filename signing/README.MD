### Підпис аплікації:

 - Щоб згенерувати підпис в терміналі перейдіть в папку `signing` (не забудь відредагувати команду і вказати пароль):

```bash
keytool -genkey -v -keystore release-key.jks -keyalg RSA -keysize 2048 -validity 10000 -alias release-key-alias -storepass <пароль> -keypass <пароль>
```

- Взяти base64 для CI, в терміналі:

```bash
cat release-key.jks | base64 > keystore.jks.base64
```

### В налаштуваннях репозиторію визначити такі змінні:

 - BASE64_KEYSTORE -> вміст файлу `keystore.jks.base64`
 - KEYSTORE_PASSWORD -> пароль задається при створенні ключа
 - KEY_PASSWORD -> пароль задається при створенні ключа
 - KEY_ALIAS -> `release-key-alias`