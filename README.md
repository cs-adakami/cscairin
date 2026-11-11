import React from 'react';

// ==========================================
// File: src/contact.js (Simulated Structure)
// ==========================================
export const ContactConfig = {
  // Peletakan nomor WhatsApp dikhususkan di bagian ini
  whatsappNumber: "6287788836766", 
  whatsappMessage: "Halo, saya memerlukan bantuan"
};

// ==========================================
// File: src/components/Config.js (Simulated Structure)
// ==========================================
export const BrandConfig = {
  brandName: "Cscairin",
  title: "Pusat Informasi Layanan Terpadu Cscairin",
  description: "Dapatkan panduan lengkap terkait akun dan penggunaan aplikasi secara resmi. Tim kami siap membantu memberikan solusi informasi terbaik untuk Anda.",
  bannerImage: "https://tanyaadakami-3q7en8kyd-adakami-x-projects.vercel.app/upscalemedia-transformed.jpeg",
  address: "Jakarta Selatan, Indonesia",
  disclaimer: "Informasi: Halaman ini menyediakan bantuan dan konsultasi umum. Segala bentuk kebijakan dan transaksi tetap mengacu pada penyedia layanan yang resmi."
};

// Helper function to generate the WhatsApp Link
const getWaLink = () => {
  return `https://wa.me/${ContactConfig.whatsappNumber}?text=${encodeURIComponent(ContactConfig.whatsappMessage)}`;
};

// ==========================================
// File: src/components/Hero.jsx
// ==========================================
const Hero = () => {
  return (
    <>
      <div className="col-md-12">
        <div className="box tengah">
          <h1 className="teks-utama">{BrandConfig.title}</h1>
          <p className="teks-sub">{BrandConfig.description}</p>
        </div>
      </div>
      <div className="col-md-12 tengah">
        <div className="box banner-box">
          <img 
            alt={`Banner Informasi ${BrandConfig.brandName}`} 
            className="melengkung banner-img" 
            src={BrandConfig.bannerImage} 
            fetchPriority="high" 
          />
        </div>
      </div>
    </>
  );
};

// ==========================================
// File: src/components/Header.jsx
// ==========================================
const Header = () => {
  return (
    <header id="header-home" className="latar-tema">
      <div className="konten">
        <div className="row">
          <Hero />
        </div>
      </div>
    </header>
  );
};

// ==========================================
// File: src/main.jsx (Content / Buttons logic)
// ==========================================
const MainContent = () => {
  const waLink = getWaLink();
  const buttons = [
    { icon: "fas fa-info-circle", text: "Informasi Panduan Akun" },
    { icon: "fas fa-edit", text: "Perubahan Data Profil" },
    { icon: "fas fa-question-circle", text: "Bantuan Penggunaan Umum" },
    { icon: "fas fa-comments", text: "Hubungi Admin Layanan" }
  ];

  return (
    <main id="main-content">
      <div className="konten action-konten">
        {buttons.map((btn, idx) => (
          <a key={idx} className="btn1" href={waLink} target="_blank" rel="noopener noreferrer">
            <i className={btn.icon} aria-hidden="true"></i>
            <span>{btn.text}</span>
          </a>
        ))}
      </div>
    </main>
  );
};

// ==========================================
// File: src/components/Footer.jsx
// ==========================================
const Footer = () => {
  return (
    <footer id="footer">
      <div className="konten">
        <div className="row footer-row">
          <div className="col-md-6">
            <div className="box">
              <p className="tebal">Tentang Layanan</p>
              <p className="kecil">Portal media informasi mandiri untuk membantu pengguna dalam memahami prosedur penggunaan platform secara benar.</p>
            </div>
          </div>
          <div className="col-md-6 location-box">
            <div className="box">
              <p className="tebal">Lokasi</p>
              <p className="kecil">
                <i className="fas fa-map-marker-alt" aria-hidden="true" style={{marginRight: '8px'}}></i> 
                {BrandConfig.address}
              </p>
            </div>
          </div>
        </div>
        <div className="row">
          <div className="col-md-12">
            <div className="box tengah disclaimer-box">
              <p className="disclaimer-text">
                <b>Informasi:</b> {BrandConfig.disclaimer}
              </p>
            </div>
          </div>
        </div>
      </div>
    </footer>
  );
};

// ==========================================
// File: src/components/FloatingWhatsApp.jsx
// ==========================================
const FloatingWhatsApp = () => {
  return (
    <a 
      href={getWaLink()} 
      className="wa-float" 
      aria-label="Hubungi via WhatsApp"
      target="_blank" 
      rel="noopener noreferrer"
    >
      <img 
        src="https://upload.wikimedia.org/wikipedia/commons/6/6b/WhatsApp.svg" 
        alt="Ikon WhatsApp" 
        loading="lazy" 
      />
    </a>
  );
};

// ==========================================
// File: src/App.jsx (Main Application)
// ==========================================
export default function App() {
  return (
    <div id="landingpage">
      {/* 
        File: src/styles.css (Simulated Structure) 
        Injected directly to ensure a functional single-file component 
      */}
      <style>{`
        @import url('https://fonts.googleapis.com/css?family=Poppins:400,500,700&display=swap');
        @import url('https://use.fontawesome.com/releases/v5.15.4/css/all.css');

        * {
          box-sizing: border-box;
        }
        body {
          font-family: 'Poppins', sans-serif;
          margin: 0;
          padding: 0;
          background-color: #f9fafb;
          color: #333;
        }
        .konten {
          max-width: 650px;
          margin: 0 auto;
          padding: 20px;
        }
        .action-konten {
          padding-top: 10px;
        }
        .tengah {
          text-align: center;
        }
        .teks-utama {
          font-size: 26px;
          font-weight: 700;
          color: #1a1a1a;
          margin-bottom: 12px;
          line-height: 1.3;
        }
        .teks-sub {
          font-size: 15px;
          color: #555;
          margin-bottom: 25px;
          line-height: 1.6;
        }
        .banner-box {
          margin-bottom: 30px;
        }
        .banner-img {
          width: 100%;
          max-width: 100%;
          height: auto;
          display: block;
        }
        .melengkung {
          border-radius: 16px;
          box-shadow: 0 8px 20px rgba(0,0,0,0.08);
        }
        .btn1 {
          display: flex;
          align-items: center;
          background: #ffffff;
          color: #333;
          padding: 16px 20px;
          margin-bottom: 16px;
          border-radius: 12px;
          text-decoration: none;
          font-weight: 500;
          font-size: 15px;
          box-shadow: 0 2px 8px rgba(0,0,0,0.04);
          border: 1px solid #f0f0f0;
          transition: all 0.3s ease;
        }
        .btn1:hover {
          background: #f8fafc;
          box-shadow: 0 4px 12px rgba(0,0,0,0.08);
          transform: translateY(-2px);
          color: #111;
        }
        .btn1 i {
          width: 30px;
          font-size: 22px;
          color: #25d366;
          text-align: center;
          margin-right: 15px;
        }
        footer {
          background: #ffffff;
          padding: 30px 0 20px;
          margin-top: 40px;
          border-top: 1px solid #eee;
        }
        .footer-row {
          display: flex;
          flex-wrap: wrap;
          gap: 20px;
          margin-bottom: 20px;
        }
        .footer-row > div {
          flex: 1;
          min-width: 200px;
        }
        .tebal {
          font-weight: 700;
          font-size: 16px;
          margin-bottom: 5px;
          color: #222;
        }
        .kecil {
          font-size: 13.5px;
          color: #666;
          line-height: 1.5;
          margin: 0;
        }
        .disclaimer-box {
          border-top: 1px solid #eee;
          padding-top: 20px;
          margin-top: 10px;
        }
        .disclaimer-text {
          font-size: 12px;
          color: #888;
          line-height: 1.6;
          margin: 0;
        }
        .wa-float {
          position: fixed;
          bottom: 25px;
          right: 25px;
          z-index: 100;
          background: #25d366;
          border-radius: 50%;
          width: 60px;
          height: 60px;
          display: flex;
          align-items: center;
          justify-content: center;
          box-shadow: 0 4px 12px rgba(37, 211, 102, 0.4);
          transition: transform 0.3s ease;
        }
        .wa-float:hover {
          transform: scale(1.1);
        }
        .wa-float img {
          width: 35px;
          height: 35px;
        }
        @media (max-width: 600px) {
          .teks-utama { font-size: 22px; }
          .teks-sub { font-size: 14px; }
          .wa-float { bottom: 20px; right: 20px; width: 55px; height: 55px; }
          .wa-float img { width: 32px; height: 32px; }
        }
      `}</style>

      <Header />
      <MainContent />
      <Footer />
      <FloatingWhatsApp />
    </div>
  );
}
