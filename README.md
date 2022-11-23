# Jak logować się do GitHuba przy użyciu kluczy SSH?

**1. Sprawdź czy masz już jakieś klucze SSH**

- wprowadź komendę **`ls -al ~/.ssh`**, która wyświetli pliki z folderu _.ssh_, jeżeli istnieją lub zwróci informację o braku takiego folderu
- jeżeli nie wyświetliły się klucze lub nie chcesz użyć istniejących kluczy, przejdź do **punktu 2**
- jeżeli wyświetliła się para kluczy publiczny i prywatny i chcesz ich użyć, przejdź do **puntku 4**

**2. Wygeneruj nowe klucze SSH**

- wprowadź komendę **`ssh-keygen -t rsa -b 4096 -C komentarz`**, wstawiając w miejsce _komentarz_ dowolny komentarz, który ułatwi tobie identyfikację klucza
- potwierdź lokalizację, w której chcesz zapisać plik (wciśnij enter dla domyślnej)
- wprowadź _passphrase_ (wciśnij enter dla pustego znaku)

**3. Dodaj swój nowo utworzony klucz SSH do agenta SHH**

- uruchm w tle agenta ssh, wprowadzając komendę **`eval $(ssh-agent -s)`**
- dodaj swój klucz SSH do agenta ssh **`ssh-add ~/.ssh/id_rsa`**

**4. Dodaj swój nowo utworzony klucz SSH do konta GitHub**

- skopuj swój klucz SSH do schowka, wpisując komendę
  - na Windowsie **`clip < ~/.ssh/id_rsa.pub`**
  - na Macu **`pbcopy < ~/.ssh/id_rsa.pub`**
  - na Linuxie **`sudo apt-get install xclip`**, a następnie **`xclip -sel clip < ~/.ssh/id_rsa.pub`**
- przejdź do twojego konta GitHub, do _Settings -> SSH and GPG Keys -> SSH Keys -> New SSH key_,
  ![1](https://user-images.githubusercontent.com/25466575/199001564-501e1ef4-73d5-4d5c-b57c-fe7add9e825c.png)
- nadaj tytuł kluczowi i wklej go w pole _Key_
  ![2](https://user-images.githubusercontent.com/25466575/199001539-e910f290-53ff-4750-b707-19b53f9d3497.png)

- potwierdź operację swoim kontem do GitHuba

**5. Gotowe** :smile:

- **zaloguj się do swojego konta GitHub** - teraz możesz już klonować repozytoria linkiem SSH
- przy pierwszym klonowaniu możesz zobaczyć info o kluczu RSA i pytanie w terminalu, czy chcesz kontynuować połączenie - potwierdź wpisując `yes`
- jakby coś nie zadziałało to w :link: poniżej jest pełna instrukja :point_down:

# Źródło:

https://docs.github.com/en/github/authenticating-to-github/connecting-to-github-with-ssh
