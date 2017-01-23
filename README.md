**[EN]**

Video recording problem
-----------------------

I use CM13.0 builded from sources and MT6737M (32-bit, prebuilt kernel 3.18.19) based phone.

- Initially i build CM13 with media_codecs.xml placed in codecs_cm13, it doesn't include MTK Encoders (media_codecs_mediatek_video.xml) as we see, in this
case video recording crashed after two seconds with following log - videoenc_cm13.txt.
2. Second, i've tried to add MTK Encoders to media_codecs.xml ... video recording wouldn't started, log - videoenc_cm13_mtk_codecs.txt. In log we see errors
about color format.

Log:


    01-23 18:40:22.898   270  1204 W ACodec  : do not know color format 0x7f000200 = 2130706944
    01-23 18:40:22.898   270  1204 W ACodec  : do not know color format 0x7f000789 = 2130708361
    01-23 18:40:22.899   270  1204 W ACodec  : do not know color format 0x7f000200 = 2130706944
    01-23 18:40:22.899   270  1204 W ACodec  : do not know color format 0x6 = 6
    01-23 18:40:22.899   270  1204 W ACodec  : do not know color format 0xb = 11
    01-23 18:40:22.900   270  1204 W ACodec  : do not know color format 0x10 = 16
    01-23 18:40:22.901   270  1204 W ACodec  : do not know color format 0x7f000300 = 2130707200
    01-23 18:40:22.901   270  1204 W ACodec  : do not know color format 0xf = 15
    01-23 18:40:22.932   270  2178 W ACodec  : do not know color format 0x7f000200 = 2130706944
    01-23 18:40:22.932   270  2178 W ACodec  : do not know color format 0x7f000789 = 2130708361
    01-23 18:40:22.932   270  2178 W ACodec  : do not know color format 0x7f000200 = 2130706944
    01-23 18:40:22.933   270  2178 I ACodec  : setupVideoEncoder succeeded
    01-23 18:40:22.934   270  2178 I ACodec  : codec does not support config priority (err -1010)
    01-23 18:40:23.019   270  2187 I ACodec  : codec does not support config priority (err -2147483648)
    01-23 18:40:23.088   270  2194 I ACodec  : codec does not support config priority (err -2147483648)
    01-23 18:40:24.111   270  2178 E ACodec  : [OMX.MTK.VIDEO.ENCODER.AVC] ERROR(0x80001005)
    01-23 18:40:24.111   270  2178 E ACodec  : signalError(omxError 0x80001005, internalError -2147483648)
    01-23 18:40:24.129   270  2178 E ACodec  : [OMX.MTK.VIDEO.ENCODER.AVC] ERROR(0x80001005)
    01-23 18:40:24.129   270  2178 E ACodec  : signalError(omxError 0x80001005, internalError -2147483648)
    01-23 18:40:24.145   270  2178 E ACodec  : [OMX.MTK.VIDEO.ENCODER.AVC] ERROR(0x80001005)
    01-23 18:40:24.145   270  2178 E ACodec  : signalError(omxError 0x80001005, internalError -2147483648)
    01-23 18:40:24.191   270  2215 I ACodec  : codec does not support config priority (err -2147483648)

- Third is log from stock firmware - videoenc_stock.txt.

Any advices how to make video recording work are welcome (with Mediatek Codecs, or without them, only with google.h264.encoder? ) .

**[RU]**

Проблема с записью видео
------------------------

Имеется прошивка CM13.0 скомпиленная из исходников, смартфон на базе MT6737M (32-bit, kernel 3.18.19, ядро стоковое).

- В прошивке собраннй с media_codecs.xml из папки codecs_cm13, кодеки от Mediatek прописанные в media_codecs_mediatek_video.xml не включены, 
в этом случае запись видео крашится через 2 секунды после начала, лог - videoenc_cm13.txt.
- Во втором случае в прошивку включены кодеки от Mediatek, т.е. подключены media_codecs_mediatek_video.xml . Запись видео вообще не стартует, лог - videoenc_cm13_mtk_codecs.txt.
В логе ошибки про неизвестный color format.

Log:

    01-23 18:40:22.898   270  1204 W ACodec  : do not know color format 0x7f000200 = 2130706944
    01-23 18:40:22.898   270  1204 W ACodec  : do not know color format 0x7f000789 = 2130708361
    01-23 18:40:22.899   270  1204 W ACodec  : do not know color format 0x7f000200 = 2130706944
    01-23 18:40:22.899   270  1204 W ACodec  : do not know color format 0x6 = 6
    01-23 18:40:22.899   270  1204 W ACodec  : do not know color format 0xb = 11
    01-23 18:40:22.900   270  1204 W ACodec  : do not know color format 0x10 = 16
    01-23 18:40:22.901   270  1204 W ACodec  : do not know color format 0x7f000300 = 2130707200
    01-23 18:40:22.901   270  1204 W ACodec  : do not know color format 0xf = 15
    01-23 18:40:22.932   270  2178 W ACodec  : do not know color format 0x7f000200 = 2130706944
    01-23 18:40:22.932   270  2178 W ACodec  : do not know color format 0x7f000789 = 2130708361
    01-23 18:40:22.932   270  2178 W ACodec  : do not know color format 0x7f000200 = 2130706944
    01-23 18:40:22.933   270  2178 I ACodec  : setupVideoEncoder succeeded
    01-23 18:40:22.934   270  2178 I ACodec  : codec does not support config priority (err -1010)
    01-23 18:40:23.019   270  2187 I ACodec  : codec does not support config priority (err -2147483648)
    01-23 18:40:23.088   270  2194 I ACodec  : codec does not support config priority (err -2147483648)
    01-23 18:40:24.111   270  2178 E ACodec  : [OMX.MTK.VIDEO.ENCODER.AVC] ERROR(0x80001005)
    01-23 18:40:24.111   270  2178 E ACodec  : signalError(omxError 0x80001005, internalError -2147483648)
    01-23 18:40:24.129   270  2178 E ACodec  : [OMX.MTK.VIDEO.ENCODER.AVC] ERROR(0x80001005)
    01-23 18:40:24.129   270  2178 E ACodec  : signalError(omxError 0x80001005, internalError -2147483648)
    01-23 18:40:24.145   270  2178 E ACodec  : [OMX.MTK.VIDEO.ENCODER.AVC] ERROR(0x80001005)
    01-23 18:40:24.145   270  2178 E ACodec  : signalError(omxError 0x80001005, internalError -2147483648)
    01-23 18:40:24.191   270  2215 I ACodec  : codec does not support config priority (err -2147483648)
    
- Лог из стоковой прошивки - videoenc_stock.txt.

Любые советы на тему как починить запись видео, с использованием MTK кодеков или без них - приветствуются.

Полезные ссылки:

- https://github.com/xen0n/android_device_meizu_arale/issues/17
- https://github.com/fire855/android_frameworks_av-mtk/commits/cm-13.0-mt6592
- https://github.com/xen0n/android_frameworks_av_mtk/commit/0e8649c
- https://github.com/xen0n/android_frameworks_av_mtk/commit/15b8851
- https://github.com/xen0n/android_frameworks_av_mtk/commit/9fd6fc6

