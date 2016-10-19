Protokół
********

Protokół aplikacji oprzemy na szeroko stosownym i opisanym w literaturze bezstanowy protokole HTTP/1.1. Jest powszechnie stosowany w aplikacjach sieciowych, dostępne jest szereg bibliotek i literatury na jego temat. Jest prostszy w użyciu i debugowaniu od protokołów binarnych, więc będzie przyjaźniejszy dla nowych ludzi. 

.. todo:: Dyskusja czy stosować protokół HTTP, czy np. Protobuf lub inne.

Protokół HTTP jest protokołem poziomu aplikacji dla hipermedialnych systemów informatycznych. W obu wersjach jest to protokół bezstanowy, tzn. ani serwer (ani klient) nie przechowuje informacji o tym, jakie były wcześniej zapytania pomiędzy określonym serwerem i klientem oraz nie posiada stanu wewnętrznego. Wykorzystuje wyłącznie protokół TCP do komunikacji klient-serwer. W najczęstszej konfiguracji działa na porcie 80.

Protokół HTTP jest protokołem żądania i odpowiedzi. Klient wysyła żądanie do serwera w postaci linii żądania zawierającej informacje metody żądania, URI i wersji protokołu, a następnie komunikatu podobnego do wiadomości MIME (ang. Multipurpose Internet Mail Extensions) zawierającego modyfikatory żądania, metainformacje o docelowym serwerze i kliencie (dalej: nagłówki, ang. headers) oraz ewentualnie - oddzielone pustym wierszem – zawartość ciała (ang.body). W odpowiedzi otrzymuje kod statusu odpowiedzi, metainformacje i ciało oddzielone poprzez pusty wiersz.

W przypadku protokołu proponuje się tylko częściową implementacje protokołu HTTP, ale kompatybilną z popularnymi klientami tego protokołu.

Przykładowe żądanie bez dodatkowych informacji przedstawia: 

.. code-block:: html
   :linenos:

   GET /sciezka HTTP/1.1
   User-Agent: curl/7.47.0

   HELLO

gdzie:

 * ``GET /sciezka HTTP/1.1`` - linia żądania, składająca się z:

  - ``GET`` – metoda HTTP wykorzystywaną do komunikacji, co w przypadku tego protokołu oznacza wartość POST, PUT, GET lub DELETE,
  - ``/sciezka`` – adres punktu wejścia dla danego żądania (ang. entry point),
  - ``HTTP/1.1`` – wersja protokołu HTTP,

 * ``User-Agent: curl/7.47.0`` – nagłówek żadania o nazwie ``User-Agent`` i wartośći ``curl/7.47.0``
 * ``HELLO`` - treść ciała żądania

W przypadku zamiaru przekazania ciała żądania należy wykorzystać nagłówek ```Content-Length``` dla określenia rozmiaru ciala, a następnie po przesłaniu nagłówków przesłać dodatkowy enter i przesłać ciało w formie tekstowej.

Do uwierzytelniania użytkowników wykorzystać mechanizm „Basic Access Authentication” przedstawiony w RFC2617. Możliwość zachowania stanów pomiędzy żądaniami zapewnić powiązanie określonych danych z konkretnym użytkownikiem po stronie aplikacji. 

Ścieżki
#######

Wszelkie zasoby udostępniane przez API są identyfikowane przez ścieżkę. To jest podstawowa forma do identyfikowania jakiegoś rodzaju danych, które mają zostać zmienione przez API.

.. todo:: Zdefiniować strukturę API z wykorzystaniem `OpenAPI Specification <http://swagger.io/specification/>`_, które wykorzystuje `JSON Schema <http://json-schema.org/>`_

.. todo:: Przedstawić komunikacje z wykorzystaniem `mscgen <https://mscgen.js.org/>`_ i `sphinxcontrib-mscgen <http://pythonhosted.org/sphinxcontrib-mscgen/>`_
