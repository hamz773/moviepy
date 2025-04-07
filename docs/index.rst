:notoc:

***********************
MoviePy documentation
***********************

.. image:: /_static/medias/logo.png
    :width: 50%
    :align: center

**Date**: |today| **Version**: |version|
from moviepy.editor import *
from moviepy.video.tools.credits import credits1

# Durasi tiap bagian lirik (dalam detik)
durations = {
    "intro": 8,
    "verse1": 16,
    "verse2": 16,
    "chorus": 16,
    "verse3": 16,
    "bridge": 12,
    "chorus2": 16,
    "outro": 16,
    "ending": 12
}

# Gabungkan semua teks lirik dengan format yang diinginkan
lyrics = [
    ("[Intro]", durations["intro"]),
    ("Otak dan pikiran, sumber aliran\nTempat oksigen hidup dan berjalan\nSaat keras hati, napas pun terkunci\nJiwa tercekik oleh ego sendiri", durations["verse1"]),
    ("Banyak yang bicara hal esensial\nTapi tak kenal inti yang paling hakiki\nBagaimana bisa berpikir mendalam\nJika belum menyentuh esensi diri?", durations["verse2"]),
    ("Baligh bukan soal usia\nTapi ruh yang pulang pada cahaya\nKapitalisme dewasa luar\nTapi nuraninya belum mekar", durations["chorus"]),
    ("Mental terbentuk dari pikiran dan hati\nAkal yang jernih, rasa yang suci\nTapi manusia sering lupa nalurinya\nKarena nafsu dan akalnya bersekutu di dunia", durations["verse3"]),
    ("Hewan makan saat lapar\nManusia makan karena lapar mata\nYang satu tunduk pada alam\nYang lain dikendalikan gengsi dan kata", durations["bridge"]),
    ("Baligh bukan soal sistem\nTapi jiwa yang tahu arah dan ritme\nYang tak hanya tumbuh ke luar\nTapi bertumbuh ke dalam, jadi sadar", durations["chorus2"]),
    ("Jika kau ingin tahu arti cukup\nLihatlah hewan, bukan manusia yang rakus\nJika kau ingin hidup penuh makna\nKenali esensi, bukan hanya logika", durations["outro"]),
    ("Hidup ini bukan soal seberapa banyak kita miliki,\nTapi seberapa dalam kita mengerti.\nBukan tentang seberapa tinggi kita berdiri,\nTapi seberapa rendah hati saat kembali.\nJadilah jiwa yang benar-benar baligh —\nBukan hanya dewasa secara usia,\nTapi sadar akan makna, arah, dan cahaya.", durations["ending"])
]

# Total durasi video
total_duration = sum(d for _, d in lyrics)

# Buat background clip dengan gambar
background = ImageClip("background.jpg").set_duration(total_duration).resize(height=720)

# Fungsi untuk membuat clip teks dengan durasi tertentu
def make_text_clip(text, duration):
    return (TextClip(text, fontsize=40, font='Arial', color='white', size=background.size, method='caption', align='center')
            .set_duration(duration)
            .set_position('center'))

# Buat daftar klip teks berdasarkan lirik dan durasi
text_clips = [make_text_clip(text, dur) for text, dur in lyrics]

# Tempatkan klip teks secara berurutan (concatenate dengan crossfade)
video = concatenate_videoclips(text_clips, method="compose")

# Overlay teks pada background (bisa juga digabungkan dengan CompositeVideoClip)
final_video = CompositeVideoClip([background, video.set_position("center")])

# Tambahkan background musik
audio_background = AudioFileClip("acoustic_background.mp3").subclip(0, total_duration)
final_video = final_video.set_audio(audio_background)

# Render video akhir
final_video.write_videofile("balighnya_jiwa.mp4", fps=24)
**Useful links**:
`Binary Installers <https://pypi.org/project/moviepy/>`__ |
`Source Repository <https://github.com/Zulko/moviepy>`__ |
`Issues & Ideas <https://github.com/Zulko/moviepy>`__ |
`Q&A Support <https://www.reddit.com/r/moviepy/>`__ |

MoviePy is the `Python <https://www.python.org/>`__ reference tool for video editing automation! 

It's an open source, MIT-licensed library offering user-friendly video editing 
and manipulation tools for the `Python <https://www.python.org/>`__ programming language.

.. grid:: 1 2 2 2
    :gutter: 4
    :padding: 2 2 0 0
    :class-container: sd-text-center

    .. grid-item-card:: Getting started
        :img-top: _static/medias/index_getting_started.svg
        :class-card: intro-card
        :shadow: md

        New to *MoviePy*? Check out the getting started guides. They contain instructions
        to install *MoviePy* as well as introduction concepts and tutorials.

        +++

        .. button-ref:: getting_started
            :ref-type: ref
            :click-parent:
            :color: secondary
            :expand:

            To the starting guide

    .. grid-item-card::  User guide
        :img-top: _static/medias/index_user_guide.svg
        :class-card: intro-card
        :shadow: md

        The user guide provides in-depth information on the
        key concepts of *MoviePy* with useful background information and explanation.

        +++

        .. button-ref:: user_guide
            :ref-type: ref
            :click-parent:
            :color: secondary
            :expand:

            To the user guide

    .. grid-item-card::  API reference
        :img-top: _static/medias/index_api.svg
        :class-card: intro-card
        :shadow: md

        The reference guide contains a detailed description of
        the *MoviePy* API. The reference describes how the methods work and which parameters can
        be used. It assumes that you have an understanding of the key concepts.

        +++

        .. button-ref:: reference_manual
            :ref-type: ref
            :click-parent:
            :color: secondary
            :expand:

            To the reference guide

    .. grid-item-card::  Developer guide
        :img-top: _static/medias/index_contribute.svg
        :class-card: intro-card
        :shadow: md

        Saw a typo in the documentation? Want to improve
        existing functionalities? The contributing guidelines will guide
        you through the process of improving *MoviePy*.

        +++

        .. button-ref:: developer_guide
            :ref-type: ref
            :click-parent:
            :color: secondary
            :expand:

            To the development guide




Contribute!
--------------

MoviePy is an open source software originally written by Zulko_ and released under the MIT licence. It works on Windows, Mac, and Linux. 

.. raw:: html

    <a href="https://twitter.com/share" class="twitter-share-button"
    data-text="MoviePy - Video editing with Python" data-size="large" data-hashtags="MoviePy">Tweet
    </a>
    <script>!function(d,s,id){var js,fjs=d.getElementsByTagName(s)[0],p=/^http:/.test(d.location)?'http':'https';
    if(!d.getElementById(id)){js=d.createElement(s);js.id=id;js.src=p+'://platform.twitter.com/widgets.js';
    fjs.parentNode.insertBefore(js,fjs);}}(document, 'script', 'twitter-wjs');
    </script>

    <iframe type="text/html" src="https://ghbtns.com/github-btn.html?user=Zulko&repo=moviepy&type=watch&count=true&size=large"
    allowtransparency="true" frameborder="0" scrolling="0" width="152px" height="30px"></iframe>


.. toctree::
    :maxdepth: 3
    :hidden:
    :titlesonly:


    getting_started/index
    user_guide/index
    reference/index
    developer_guide/index


.. _PyPI: https://pypi.python.org/pypi/moviepy
.. _Zulko: https://github.com/Zulko/
.. _Stackoverflow: https://stackoverflow.com/
.. _Github: https://github.com/Zulko/moviepy
.. _Reddit: https://www.reddit.com/r/moviepy
