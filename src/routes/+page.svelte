<div class="flex justify-center items-center h-screen">
    <div class="w-auto p-8 bg-base-100 rounded-lg shadow-lg">
        <!-- Üst menü -->
        <ul class="menu menu-horizontal bg-base-100 rounded-box">
            <li>
                <a class="text-primary-content">Home&nbsp;<i class="fa-solid fa-house text-success"></i></a>
            </li>
            <li>
                <a class="text-primary-content">Project&nbsp;<i class="fa-solid fa-code text-success"></i></a>
            </li>
            <li>
                <a class="text-primary-content">Skills&nbsp;<i class="fa-solid fa-star text-success"></i></a>
            </li>
            <li>
                <a class="text-primary-content">Music&nbsp;<i class="fa-solid fa-music text-success"></i></a>
            </li>
        </ul>
        <br>
        <br>

        <!-- Hwalil bilgileri -->
        <div class="text-left flex items-center justify-start">
            <div>
                <h1 class="text-4xl font-bold text-primary">Hwalil! <i class="fa-solid fa-house text-success"></i></h1>
                <h2 class="text-xl font-semibold mb-4 text-primary-content">A 18-year-old developer from Turkey</h2>
                <div class="flex space-x-4">
                    <!-- GitHub Icon -->
                    <a href="https://github.com/hwalil" target="_blank" class="text-primary-content">
                        <i class="fab fa-github text-2xl hover:text-primary-content"></i>
                    </a>
                    <!-- Instagram Icon -->
                    <a href="https://www.instagram.com/hwalil/" target="_blank" class="text-primary-content">
                        <i class="fab fa-instagram text-2xl hover:text-primary-content"></i>
                    </a>
                    <!-- Spotify Icon -->
                    <a href="https://open.spotify.com/user/hwalil" target="_blank" class="text-primary-content">
                        <i class="fab fa-spotify text-2xl hover:text-primary-content"></i>
                    </a>
                </div>
            </div>
        </div>

        <!-- Çizgi -->
        <div class="border-t border-gray-300 my-4"></div>

        <!-- Profil fotoğrafı ve kullanıcı adı (SOLDA) -->
        <div class="flex items-center justify-start"> <!-- text-left sınıfını ekledik ve flex ekledik -->
            <img src="https://cdn.discordapp.com/attachments/1076256339547926568/1133413196309479536/profilfoto.jpg" alt="Profil Fotoğrafı" class="rounded-full w-16 h-16 border-4 border-primary">
            <div class="ml-4">
                <p class="text-xl font-semibold text-primary">Hwalil#6686</p>
                <p class="text-primary-content">Hava çok güzel</p>
            </div>
        </div>

        <!-- Spotify Şarkıları (Statik veriyle örnek) -->
        <div class="mt-8">
            <h3 class="text-lg font-semibold text-primary-content">Spotify Şarkıları</h3>
            <ul class="list-disc list-inside mt-4 text-primary-content">
                <li>Fake Song - Fake Artist</li>
                <li>Another Fake Song - Another Fake Artist</li>
                <li>Yet Another Fake Song - Yet Another Fake Artist</li>
            </ul>
        </div>
    </div>
</div>


<script>
  // Last.fm API anahtarını buraya ekleyin
  const apiKey = '194eb0b0629f49d5f421873c498d5bf6';
  const username = 'hwalil';

  let songName = '';
  let artistName = '';
  let isLoading = true;

  const fetchLastFmData = async () => {
    try {
      const response = await fetch(
        `http://ws.audioscrobbler.com/2.0/?method=user.getrecenttracks&user=${username}&api_key=${apiKey}&format=json`
      );
      const data = await response.json();
      const song = data.recenttracks.track[0];
      songName = song.name;
      artistName = song.artist['#text'];
    } catch (error) {
      console.error(error);
    } finally {
      isLoading = false;
    }
  };

  fetchLastFmData();
</script>

<div class="flex justify-center items-center h-screen">
  {#if isLoading}
    <p class="text-primary-content">Yükleniyor...</p>
  {:else}
    <div class="w-auto p-8 bg-base-100 rounded-lg shadow-lg">
      <h1 class="text-4xl font-bold text-primary">Son Dinlediğiniz Şarkı</h1>
      <div class="border-t border-gray-300 my-4"></div>
      <div class="text-center text-primary-content">
        <p>{songName} - {artistName}</p>
      </div>
    </div>
  {/if}
</div>

<style>
  /* Stil düzenlemeleri burada yapabilirsiniz */
</style>