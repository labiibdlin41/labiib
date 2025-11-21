<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Portofolio Labiib | Biology Educator</title>
  
  <!-- Import Font Poppins -->
  <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;500;700&display=swap" rel="stylesheet">

<style>
  /* === BASE STYLES === */
  body {
    font-family: 'Poppins', sans-serif;
    margin: 0;
    background-color: #F7F9F0; /* Ghibli Cream */
    display: flex;
    justify-content: center;
    align-items: center;
    min-height: 100vh;
    padding: 20px;
    box-sizing: border-box;
  }

  /* === KARTU PROFIL === */
  .profile-card-custom {
    max-width: 850px;
    width: 100%;
    background: #ffffff;
    border: 1px solid #E8F5E9; 
    border-radius: 24px; 
    box-shadow: 0 15px 35px rgba(85, 124, 85, 0.12); 
    padding: 50px;
    box-sizing: border-box;
    display: flex;
    align-items: center; 
    gap: 50px; 
    
    /* Animasi Awal */
    opacity: 0;
    transform: translateY(30px);
    transition: all 0.8s cubic-bezier(0.22, 1, 0.36, 1);
  }

  .profile-card-custom.is-visible {
    opacity: 1;
    transform: translateY(0);
  }

  /* === FOTO === */
  .profile-pic-custom {
    width: 200px;
    height: 200px;
    border-radius: 50%;
    object-fit: cover;
    flex-shrink: 0;
    border: 6px solid #F1F8E9; 
    box-shadow: 0 8px 20px rgba(0,0,0,0.08);
  }

  /* === TEKS === */
  .profile-text-custom {
    flex: 1;
    text-align: left;
  }

  .profile-text-custom h2 {
    margin: 0 0 8px 0;
    font-size: 2.2rem;
    font-weight: 700;
    color: #2C3E50;
  }

  .profile-text-custom .subtitle {
    font-size: 0.95rem;
    font-weight: 600;
    color: #557C55; 
    margin-bottom: 25px;
    text-transform: uppercase;
    letter-spacing: 1.5px;
    display: inline-block;
    padding-bottom: 5px;
    border-bottom: 2px solid #EEF4D4;
  }

  #profile-bio p {
    font-size: 1.05rem;
    line-height: 1.8;
    color: #555555;
    margin-bottom: 15px;
  }

  /* === MOBILE === */
  @media (max-width: 768px) {
    .profile-card-custom {
      flex-direction: column;
      text-align: center;
      padding: 40px 25px;
      gap: 25px;
    }

    .profile-pic-custom {
      width: 150px;
      height: 150px;
      margin: 0 auto;
    }

    .profile-text-custom {
      text-align: center;
    }

    .profile-text-custom h2 {
      font-size: 1.8rem;
    }
  }
</style>
</head>
<body>

  <div class="profile-card-custom" id="myProfileCard">
    <img src="https://lh3.googleusercontent.com/pw/AP1GczOexhgpWTr35eHagJ29Ef9X-LCGadrJnKl_njuHuu36pGF9apJYHEUunM_ZLPlED1mSF3hlESvkuOuHO9q_ihEh_pFVs7_65BhSoz1JKurpNwPAr3aEh2tIXm8hJvYUGK2j7hJN_BsLeJzAXyHqnM7Q=w1024-h576-s-no-gm?authuser=0" 
         alt="Foto Profil" 
         class="profile-pic-custom" 
         id="profile-image" 
         onerror="this.src='https://placehold.co/200x200/E0E0E0/777777?text=Foto';">
    
    <div class="profile-text-custom">
      <h2 id="profile-name">Loading...</h2> 
      <div class="subtitle" id="profile-subtitle">Loading...</div> 
      <div id="profile-bio"></div> 
    </div>
  </div>

  <script>
    document.addEventListener('DOMContentLoaded', () => {
      const CONFIG = {
        name: "Halo, Saya Labiib!",
        subtitle: "Biology Educator | Visual Learning Specialist", 
        // GANTI FOTO DI SINI JIKA PERLU
        imageUrl: "https://lh3.googleusercontent.com/pw/AP1GczOexhgpWTr35eHagJ29Ef9X-LCGadrJnKl_njuHuu36pGF9apJYHEUunM_ZLPlED1mSF3hlESvkuOuHO9q_ihEh_pFVs7_65BhSoz1JKurpNwPAr3aEh2tIXm8hJvYUGK2j7hJN_BsLeJzAXyHqnM7Q=w1024-h576-s-no-gm?authuser=0",
        imageAlt: "Foto Profil Labiib",
        bio: [
          "Lulusan Pendidikan Biologi (S.Pd) dengan spesialisasi pengembangan media pembelajaran visual dan interaktif. Berpengalaman memimpin HIMA Biologi UNY dan mengelola proyek edukasi strategis.",
          "Saya menggabungkan sains dan kreativitas visual untuk mengubah materi biologi yang kompleks menjadi pengalaman belajar yang intuitif. Siap berkontribusi dalam dunia pendidikan, manajemen proyek, dan pengembangan konten kreatif."
        ]
      };

      try {
        document.getElementById('profile-name').textContent = CONFIG.name;
        document.getElementById('profile-subtitle').textContent = CONFIG.subtitle;
        const img = document.getElementById('profile-image');
        if(CONFIG.imageUrl) img.src = CONFIG.imageUrl;
        img.alt = CONFIG.imageAlt;
        const bio = document.getElementById('profile-bio');
        bio.innerHTML = '';
        CONFIG.bio.forEach(t => { 
          const p = document.createElement('p'); 
          p.textContent = t; 
          bio.appendChild(p); 
        });
      } catch (e) {}
      
      const card = document.getElementById('myProfileCard');
      if (card) {
        const obs = new IntersectionObserver((e) => {
          e.forEach(ent => { if (ent.isIntersecting) { ent.target.classList.add('is-visible'); obs.unobserve(ent.target); }});
        }, { threshold: 0.1 });
        obs.observe(card);
      }
    });
  </script>
</body>
</html>
