# Definitions

* **Протокол** — это то, как два участника видеосвязи (почти всегда это клиент и сервер) обмениваются данными 
с целью получения данных. Клиентом называют того, кто приходит к серверу и инициирует сессию связи. 
Видеопоток может течь от сервера к клиенту (тогда это обычное проигрывание) или от клиента к серверу (тогда это публикация).

* **Транспорт**, или транспортный контейнер, или контейнер — это то, как сжатое видео упаковывается в байты 
для передачи от одного участника к другому (по какому-то протоколу).

* **Кодек** — многозначный термин. Здесь он означает способ сжать сырое видео. 
Разница между кодеком и транспортом в том, что кодек — это про подготовку видео, 
а транспорт — про передачу видео по протоколу. Видео, сжатое одним кодеком, 
можно пересылать по разными протоколам и разными транспортами. 
Большинство видеостриминговых серверов не залезают глубже кодированного видео и оперируют только протоколами и транспортами.

Примеры кодеков: h264, aac, mp3.

* **Видеоконтейнер** - Любой видеофайл является файловым контейнером, в котором хранятся другие файлы. 
Аудио- и видеодорожки объединяются для воспроизведения видеоролика. 
Метаданные содержат информацию о данном видеоролике — изображение обложки, субтитры и пр. 
К популярным форматам видеоконтейнеров относятся следующие
    * Ogg (.ogv, .oga, .ogx, .ogg) — формат-контейнер с открытым исходным кодом для видеокодека Theora и аудио Vorbis. 
    Работает в Firefox, Chrome и Opera.
      MIME-тип: video/ogg.
    * MPEG 4 (.mp4) — формат-контейнер для видеокодека H.264 и аудиокодека AAC. Работает в Safari и Chrome. 
    Кодирует видео, в том числе высокой четкости, для полного спектра устройств, таких как iPhone, iPod и iPad.
      MIME-тип: video/mp4.
    * WebM (.webm) — формат-контейнер с открытым исходным кодом для видеокодека VP8 от Google и аудиокодека Ogg Vorbis. 
    Работает в Firefox, Chrome, Opera и Adobe Flash Player.
      MIME-тип: video/webm.
    * Audio Video Interleave (.avi) — формат предназначен для записи звука и движущихся изображений, соответствует спецификации RIFF.
      MIME-тип: video/vnd.avi, video/avi, video/msvideo, video/x-msvideo.
    * Matroska (.mkv) — популярный видеоконтейнер, может содержать видео в формате H.264, VP8 или Theora.
      MIME-тип: video/x-matroska, audio/x-matroska.        

* **Adaptive HTTP streaming technologies**
The basic idea is to generate multiple versions of the same content (e.g., different bitrates or spatial resolutions) 
and chop these versions into segments (e.g., two seconds).
The segments are provided on a web server and can be downloaded through HTTP standard compliant GET requests. 
Typically, the relationship between the different versions is described by a manifest, which is provided to the client prior to the streaming session. 
The manifest represents the different qualities of the media content and the individual segments of each quality with HTTP Uniform Resource Locators (URLs). 
This structure provides the binding of the segments to the bitrate (resolution, etc.)  among others (e.g., start time, duration of segments). 
As a consequence, each client will first request the manifest that contains the temporal and structural information for the media content, 
and based on that information it will request the individual segments that fit best for its requirements.

The adaptation to the bitrate or spatial resolution is done on the client side for each segment, e.g., 
the client can switch to a higher bitrate – if bandwidth permits – on a per segment basis, or to a lower bitrate – if bandwidth decreases. 
This has several advantages because the client knows its capabilities such as the received throughput, delay, device capabilities 
(e.g., screen resolution), etc. best.
    * Feature comparison of the proprietary adaptive streaming technologies: https://bitmovin.com/mpeg-dash-vs-apple-hls-vs-microsoft-smooth-streaming-vs-adobe-hds/

* **HTML5** - Основным различием между HTML и HTML5 может стать то, что ни аудио, ни видео не являются составной частью HTML, 
тогда как они оба могут рассматриваться как неотъемлемые части HTML5.
В спецификации HTML5 не описаны протоколы, транспорты и кодеки для видео. 
Поэтому авторы браузеров сами выбирают, что поддерживать, а под «HTML5-стримингом» подразумевают разные вещи.
При этом есть комбинации, которые поддерживаются значительной частью браузеров.
    * Read more about HTML5 vs HTML here: https://www.hostinger.com.ua/rukovodstva/chto-takoe-html-i-ih-razlichiya

* **Тег video in HTML5**
    * Атрибут autoplay не работает без muted в хроме.
    * в спецификации HTML5 не описаны протоколы, транспорты и кодеки. Поэтому авторы браузеров сами выбирают, 
    что поддерживать, а под «HTML5-стримингом» подразумевают разные вещи.
    * Как и в случае с аудиофайлами, рекомендуется перечислять в <source> все форматы, начиная с более предпочтительного. 
    Также нужно указывать MIME-тип для каждого видеофайла.
    * Для универсального воспроизведения в указанных браузерах видео кодируют с помощью разных кодеков и добавляют файлы одновременно
```
<video>
  <source src="movie.mp4"' />
  <source src="movie.webm"' />
</video>>
```

* **Video Codecs**
    * ogg/theora: (IE: -, Chrome: +, Opera: +, Safari: -, Firefox: +)
        * The Ogg container format with the Theora video codec and the Vorbis audio codec is supported in desktop/mobile Gecko (Firefox), Chrome, and Opera, 
        and support for the format can be added to Safari (but not on iOS) by installing an add-on. The format is not supported in Internet Explorer in any way.
          
          WebM is generally preferred over Ogg Theora Vorbis when available, 
          because it provides a better compression to quality ratio and is supported in more browsers. 
          The Ogg format can however be used to support older browser versions (for example Firefox 3.5/3.6 don't support WebM, but do support Ogg.)
    * H.264       (IE: +, Chrome: +, Opera: -, Safari: +, Firefox: -)  
    * WebM        (IE: -, Chrome: +, Opera: +, Safari: -, Firefox: +)
        * Поддержка формата может быть добавлена в Internet Explorer и Safari (но не на iOS) установкой плагина. 
        Нативная поддержка VP9 WebM в Edge сейчас в стадии разработки.

* **HLS protocol**
Поскольку запросы используют только стандартные транзакции HTTP, 
протокол позволяет потоку преодолевать межсетевые экраны или прокси-сервера, 
пропускающие HTTP-трафик, в отличие от протоколов на базе UDP, таких как RTP. 
Это также позволяет раздавать контент посредством HTTP-серверов общего назначения в качестве источника, 
а также доставлять до потребителей через существующие CDN.

This protocol also includes a number of other built-in features. For example, HLS is an adaptive bitrate protocol. 
This means that the client device and server dynamically detect the internet speed of the user, and then adjust video quality in response.
Therefore, a mobile user can receive a full HD stream while using speedy, home WiFi. 
The same user can receive a medium-quality stream after walking out the door via 4G. 
Finally, that user can even maintain a low-quality stream when encountering areas of poor cell service. 
All of this happens automatically with HLS.

Other HLS features include embedded closed captions, synchronized playback of multiple streams, 
good support for advertising standards (i.e., VPAID and VAST), DRM support, and more.        

* **HLS** vs. **MPEG-DASH**
    * Docs: https://www.dacast.com/blog/mpeg-dash-vs-hls-what-you-should-know/

