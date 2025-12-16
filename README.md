<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Debeatzgh Digital Hub</title>

<style>
body{
  margin:0;
  font-family: system-ui, -apple-system, BlinkMacSystemFont;
  background:#f3f4f6;
}

/* ====== CAROUSEL ====== */
.carousel-wrapper{
  padding:40px 16px;
}
.carousel{
  display:flex;
  gap:20px;
  overflow-x:auto;
  scroll-snap-type:x mandatory;
}
.card{
  min-width:300px;
  background:#fff;
  border-radius:18px;
  box-shadow:0 10px 30px rgba(0,0,0,.15);
  scroll-snap-align:center;
  display:flex;
  flex-direction:column;
}
.card img{
  height:160px;
  object-fit:cover;
  border-radius:18px 18px 0 0;
}
.card-content{
  padding:18px;
  flex:1;
}
.card h3{
  margin:0 0 8px;
}
.card p{
  font-size:14px;
  color:#555;
}
.card button{
  margin-top:14px;
  background:#16a34a;
  color:#fff;
  border:none;
  padding:12px;
  border-radius:14px;
  font-weight:700;
  cursor:pointer;
}
.card button:hover{opacity:.9}

/* ===== FLOATING LAUNCHER ===== */
#floating-launcher{
  position:fixed;
  top:20px;
  left:20px;
  background:#16a34a;
  color:#fff;
  padding:8px 14px;
  font-size:13px;
  font-weight:600;
  border-radius:18px;
  box-shadow:0 4px 12px rgba(0,0,0,.25);
  cursor:pointer;
  z-index:99999;
}

/* ===== FULLSCREEN OVERLAY ===== */
#overlay-browser{
  position:fixed;
  inset:0;
  background:#fff;
  display:none;
  flex-direction:column;
  z-index:100000;
}
#overlay-topbar{
  background:#111;
  color:#fff;
  padding:12px;
  display:flex;
  justify-content:space-between;
  align-items:center;
}
#overlay-title{
  font-size:14px;
}
#overlay-close{
  cursor:pointer;
  font-size:20px;
}
#overlay-viewer{
  flex:1;
  width:100%;
  border:none;
}
</style>
</head>

<body>

<!-- FLOATING BUTTON -->
<div id="floating-launcher" onclick="openOverlay('https://debeatzgh1.github.io/debeatzgh/','Debeatzgh Home')">
  App
</div>

<!-- CAROUSEL -->
<div class="carousel-wrapper">
  <h2 style="text-align:center;">🚀 Debeatzgh Digital Products</h2>

  <div class="carousel">

    <div class="card">
      <img src="https://debeatzgh.wordpress.com/wp-content/uploads/2025/08/createamoderncleanthumbnaildigitaltool.png">
      <div class="card-content">
        <h3>Digital Creator Essential Tools</h3>
        <p>Professional tools and guides to grow as a modern digital creator.</p>
        <button onclick="openOverlay('https://debeatzgh1.github.io/Digital-Creator-s-Essential-Guides-Tools/','Creator Tools')">
          Open App
        </button>
      </div>
    </div>

    <div class="card">
      <img src="https://debeatzgh.wordpress.com/wp-content/uploads/2025/08/createaicleanstarterkitthumbnail.png">
      <div class="card-content">
        <h3>Decode AI Starter Kit</h3>
        <p>Beginner-friendly AI resources to start using artificial intelligence.</p>
        <button onclick="openOverlay('https://debeatzgh1.github.io/Decode-AI-starter-kit-/','AI Starter Kit')">
          Launch
        </button>
      </div>
    </div>

    <div class="card">
      <img src="https://debeatzgh.wordpress.com/wp-content/uploads/2025/08/sidehustlethumbnail.png">
      <div class="card-content">
        <h3>Side Hustle Starter Kit</h3>
        <p>Actionable side hustle ideas and tools for online income.</p>
        <button onclick="openOverlay('https://debeatzgh1.github.io/Side-hustle-starter-kit-/','Side Hustle Kit')">
          View Kit
        </button>
      </div>
    </div>

    <div class="card">
      <img src="https://debeatzgh.wordpress.com/wp-content/uploads/2025/08/onlinebusinessthumbnail.png">
      <div class="card-content">
        <h3>Online Business Kit</h3>
        <p>Everything you need to start and scale an online business.</p>
        <button onclick="openOverlay('https://debeatzgh1.github.io/Online-business-kit/','Online Business')">
          Explore
        </button>
      </div>
    </div>

    <div class="card">
      <img src="https://debeatzgh.wordpress.com/wp-content/uploads/2025/08/affiliateproductsthumbnail.png">
      <div class="card-content">
        <h3>Digital Products Affiliate Shop</h3>
        <p>Curated digital products you can promote and earn from.</p>
        <button onclick="openOverlay('https://debeatzgh1.github.io/-My-Brand-Online-Digital-Products-Affiliate-Shop/','Affiliate Shop')">
          Open Shop
        </button>
      </div>
    </div>

  </div>
</div>

<!-- FULLSCREEN OVERLAY -->
<div id="overlay-browser">
  <div id="overlay-topbar">
    <span id
    


<style>
  /* 🌟 Fade Slide Animation */
  @keyframes fadeSlideUp {
    0% { opacity: 0; transform: translateY(0) translateX(20px); }
    100% { opacity: 1; transform: translateY(0) translateX(0); }
  }

  /* ❤️ Heartbeat Animation */
  @keyframes heartbeat {
    0% { transform: scale(1); }
    25% { transform: scale(1.08); }
    50% { transform: scale(1); }
    75% { transform: scale(1.08); }
    100% { transform: scale(1); }
  }

  .floating-btn-group {
    animation: fadeSlideUp 0.6s ease-out;
  }

  /* Iframe Modal Styles */
  #iframe-modal {
    display: none;
    position: fixed;
    z-index: 9999;
    left: 0;
    top: 0;
    width: 100%;
    height: 115%;
    background: rgba(0,0,0,0.6);
    backdrop-filter: blur(4px);
  }

  .modal-content {
    position: relative;
    margin: 2% auto;
    background: #fff;
    border-radius: 16px;
    width: 95%;
    height: 90%;
    box-shadow: 0 8px 24px rgba(0,0,0,0.3);
    overflow: hidden;
    animation: fadeIn 0.3s ease;
  }

  #modal-iframe {
    width: 100%;
    height: 105%;
    border: none;
  }

  .close-btn {
    position: absolute;
    top: 10px;
    right: 18px;
    font-size: 30px;
    color: #333;
    cursor: pointer;
    transition: color 0.2s;
    z-index: 10;
  }

  .close-btn:hover {
    color: #e11d48;
  }

  @keyframes fadeIn {
    from {opacity: 0; transform: translateY(-10px);}
    to {opacity: 1; transform: translateY(0);}
  }
</style>

<script>
document.addEventListener("DOMContentLoaded", function () {

  // 🔹 Floating Button at TOP-LEFT
  const btnGroup = document.createElement("div");
  btnGroup.className = "floating-btn-group";
  Object.assign(btnGroup.style, {
    position: "fixed",
    top: "20px",          // Top-left positioning
    left: "20px",
    zIndex: "9999",
    animation: "heartbeat 2.5s infinite ease-in-out, fadeSlideUp 0.6s ease-out forwards"
  });

  // -------------------------------------------------------
  // 📌 Updates Button
  // -------------------------------------------------------
  const button = document.createElement("a");
  button.href = "#";
  button.innerText = "📌 Updates";
  Object.assign(button.style, {
    background: "#16a34a",
    color: "#fff",
    padding: "12px 24px",
    borderRadius: "30px",
    textDecoration: "none",
    fontSize: "15px",
    fontWeight: "700",
    boxShadow: "0 4px 10px rgba(0,0,0,0.25)",
    whiteSpace: "nowrap",
  });

  // 🔹 Iframe Modal
  const modal = document.createElement("div");
  modal.id = "iframe-modal";
  modal.innerHTML = `
    <div class="modal-content">
      <span class="close-btn">&times;</span>
      <iframe id="modal-iframe" src="" loading="lazy"></iframe>
    </div>
  `;

  document.body.appendChild(modal);

  // 🔹 Open Iframe on click
  button.addEventListener("click", function (e) {
    e.preventDefault();
    document.getElementById("modal-iframe").src = "https://debeatzgh1.github.io/Digital-Creator-s-Essential-Guides-Tools/";
    modal.style.display = "block";
  });

  btnGroup.appendChild(button);
  document.body.appendChild(btnGroup);

  // 🔹 Close Modal
  document.addEventListener("click", function (e) {
    if (e.target.classList.contains("close-btn") || e.target.id === "iframe-modal") {
      modal.style.display = "none";
      document.getElementById("modal-iframe").src = "";
    }
  });

  // 🔹 Auto-open external ads in a new tab
  document.getElementById("modal-iframe").addEventListener("load", function () {
    try {
      const links = this.contentDocument.querySelectorAll("a");
      links.forEach(link => {
        if (!link.href.includes("debeatzgh.wordpress.com")) {
          link.setAttribute("target", "_blank");
          link.setAttribute("rel", "noopener");
        }
      });
    } catch (err) {
      console.warn("External site - cannot rewrite links");
    }
  });

});
</script>


<!doctype html>



<style>
  /* 🌟 Floating Button Animation */
  @keyframes fadeSlideUp {
    0% { opacity: 0; transform: translateX(-50%) translateY(20px); }
    100% { opacity: 1; transform: translateX(-50%) translateY(0); }
  }

  .floating-btn-group {
    animation: fadeSlideUp 0.6s ease-out;
  }

  .floating-btn-group a:hover {
    transform: scale(1.05);
    transition: transform 0.3s ease;
  }

  /* 🌟 Iframe Modal */
  #iframe-modal {
    display: none;
    position: fixed;
    z-index: 9999;
    left: 0;
    top: 0;
    width: 100%;
    height: 115%;
    background: rgba(0,0,0,0.6);
    backdrop-filter: blur(4px);
  }

  .modal-content {
    position: relative;
    margin: 2% auto;
    background: #fff;
    border-radius: 16px;
    width: 95%;
    height: 90%;
    box-shadow: 0 8px 24px rgba(0,0,0,0.3);
    overflow: hidden;
    animation: fadeIn 0.3s ease;
  }

  #modal-iframe {
    width: 100%;
    height: 105%;
    border: none;
  }

  .close-btn {
    position: absolute;
    top: 10px;
    right: 18px;
    font-size: 30px;
    color: #333;
    cursor: pointer;
    transition: color 0.2s;
    z-index: 10;
  }

  .close-btn:hover {
    color: #e11d48;
  }

  @keyframes fadeIn {
    from {opacity: 0; transform: translateY(-10px);}
    to {opacity: 1; transform: translateY(0);}
  }
</style>

<script>
document.addEventListener("DOMContentLoaded", function () {

  // 🔹 Create Floating Button Group
  const btnGroup = document.createElement("div");
  btnGroup.className = "floating-btn-group";
  Object.assign(btnGroup.style, {
    position: "fixed",
    bottom: "16px",
    left: "50%",
    transform: "translateX(-50%)",
    display: "flex",
    gap: "10px",
    zIndex: "9999",
    background: "rgba(0,0,0,0.1)",
    padding: "6px 10px",
    borderRadius: "10px",
    boxShadow: "0 4px 8px rgba(0,0,0,0.2)",
    opacity: "0",
    animation: "fadeSlideUp 0.6s ease-out forwards"
  });

  // -------------------------------------------------------
  // ✅ BUTTONS INCLUDING NEW “IDEAS” BUTTON
  // -------------------------------------------------------
  const buttons = [
    {
      text: "🔥 Blog",
      bg: "#1e90ff",
      url: "https://beatzde4.blogspot.com/"
    },
    {
      text: "📌 Feed",
      bg: "#16a34a",
      url: "https://debeatzgh.wordpress.com/"
    },
    {
      text: "💡 Ideas",
      bg: "#c026d3",
      url: "https://msha.ke/debeatzgh"
    }
  ];

  // 🔹 Create Iframe Modal
  const modal = document.createElement("div");
  modal.id = "iframe-modal";
  modal.innerHTML = `
    <div class="modal-content">
      <span class="close-btn">&times;</span>
      <iframe id="modal-iframe" src="" loading="lazy"></iframe>
    </div>
  `;
  document.body.appendChild(modal);

  // 🔹 Add Buttons to Page
  buttons.forEach(function (btn) {
    const a = document.createElement("a");
    a.href = "#";
    a.innerText = btn.text;
    Object.assign(a.style, {
      background: btn.bg,
      color: "#fff",
      padding: "8px 14px",
      borderRadius: "20px",
      textDecoration: "none",
      fontSize: "13px",
      fontWeight: "600",
      whiteSpace: "nowrap",
      boxShadow: "0 2px 6px rgba(0, 0, 0, 0.2)",
      transition: "opacity 0.3s ease, transform 0.3s ease"
    });

    a.addEventListener("click", function (e) {
      e.preventDefault();
      document.getElementById("modal-iframe").src = btn.url;
      document.getElementById("iframe-modal").style.display = "block";
    });

    btnGroup.appendChild(a);
  });

  document.body.appendChild(btnGroup);

  // 🔹 Close Modal
  document.addEventListener("click", function (e) {
    if (e.target.classList.contains("close-btn") || e.target.id === "iframe-modal") {
      modal.style.display = "none";
      document.getElementById("modal-iframe").src = "";
    }
  });

  // 🔹 Auto-open external ads in new tab safely
  document.getElementById("modal-iframe").addEventListener("load", function () {
    try {
      const links = this.contentDocument.querySelectorAll("a");
      links.forEach(link => {
        if (!link.href.includes("debeatzgh.wordpress.com")) {
          link.setAttribute("target", "_blank");
          link.setAttribute("rel", "noopener");
        }
      });
    } catch (err) {
      console.warn("External site - cannot rewrite links");
    }
  });

});
</script>

# 🧠 Digital Creator’s Ultimate Project Collection

Welcome to **DebeatzGH’s Creative Hub** — your gateway to mastering AI, online business, and digital side hustles.  
Each section below features a project complete with tutorials, visuals, and interactive tools for digital creators and entrepreneurs.

---

## 🔍 Decode AI Starter Kit
<img src="https://debeatzgh.wordpress.com/wp-content/uploads/2025/11/1761391370669_18092671662032788462.jpg" alt="Decode AI Starter Kit" width="700">

**Description:**  
Uncover the real power of Artificial Intelligence. Learn how AI works, explore real-world applications, and discover practical tools to transform your daily workflows and business operations.

<p>
  <a href="https://debeatzgh1.github.io/Decode-AI-starter-kit-/" target="_self">
    <img src="https://img.shields.io/badge/Explore%20Decode%20AI-00C853?style=for-the-badge&logo=google-chrome&logoColor=white" alt="Explore Decode AI">
  </a>
</p>

---

## 💼 Online Business Starter Kit
<img src="https://debeatzgh.wordpress.com/wp-content/uploads/2025/08/designadigitalproductse-commerceonlinedeals3545265155247625100.jpg" alt="Online Business Starter Kit" width="700">

**Description:**  
Turn your vision into an online brand. This kit walks you through setting up a digital business — from branding to AI-driven marketing — so you can sell smarter and grow faster.

<p>
  <a href="https://debeatzgh1.github.io/Online-business-kit/" target="_self">
    <img src="https://img.shields.io/badge/Start%20Building-00B0FF?style=for-the-badge&logo=google-chrome&logoColor=white" alt="Online Business Kit">
  </a>
</p>

---

## 💰 Side Hustle Starter Kit
<img src="https://debeatzgh.wordpress.com/wp-content/uploads/2025/08/wp-17550753355015215823208011315422.jpg" alt="Side Hustle Starter Kit" width="700">

**Description:**  
Learn the art of earning extra income with smart side hustles powered by AI. Build flexible digital income streams while mastering tools that work for you, not against you.

<p>
  <a href="https://debeatzgh1.github.io/Side-hustle-starter-kit-/" target="_self">
    <img src="https://img.shields.io/badge/Learn%20More-00C853?style=for-the-badge&logo=google-chrome&logoColor=white" alt="Side Hustle Starter Kit">
  </a>
</p>

---

## ⚙️ Tech & AI Mastery Hub
<img src="https://debeatzgh.wordpress.com/wp-content/uploads/2025/09/asleekandmoderngoogleclassroombannerfortechaihubfeaturingfuturisticdigitalelements261807892942313727.jpg" alt="Tech and AI Mastery Hub" width="700">

**Description:**  
Explore the frontier of technology and AI innovation. From coding resources to automation workflows, this hub equips you with the skills and tools for modern digital success.

<p>
  <a href="https://debeatzgh1.github.io/Tech-and-AI-Hub-/" target="_self">
    <img src="https://img.shields.io/badge/Enter%20Hub-FF6F00?style=for-the-badge&logo=google-chrome&logoColor=white" alt="Tech and AI Mastery">
  </a>
</p>

---

## 📊 Slides & Visual Showcase
<img src="https://debeatzgh.wordpress.com/wp-content/uploads/2025/11/acleanmoderndashboardscreenshotdisplayingcolor-codedcardsandguidetitles5623056496093453602.jpg" alt="Slides View" width="700">

**Description:**  
A beautifully designed set of AI-powered presentation slides showcasing learning modules, startup visuals, and digital education frameworks — all crafted to inspire.

<p>
  <a href="https://debeatzgh1.github.io/AI-Tech-Mastery-Hub-/" target="_self">
    <img src="https://img.shields.io/badge/View%20Slides-FF4081?style=for-the-badge&logo=google-chrome&logoColor=white" alt="Slides View">
  </a>
</p>

---

## 🧩 Personal Portfolio
<img src="https://debeatzgh.wordpress.com/wp-content/uploads/2025/08/adarkthemepreviewofapersonalportfoliowebsitewithglowingblueaccentsprojectshowcasecardsandamodernnavigationbar8701627220551173592.jpg" alt="Personal Portfolio" width="700">

**Description:**  
A sleek digital showcase highlighting your journey, projects, and brand identity. This portfolio blends creativity with professionalism for a modern creator’s personal brand.

<p>
  <a href="https://debeatzgh1.github.io/Personal-Portfolio-site-/" target="_self">
    <img src="https://img.shields.io/badge/Visit%20Portfolio-007ACC?style=for-the-badge&logo=google-chrome&logoColor=white" alt="Visit Portfolio">
  </a>
</p>

---

## 🌐 Connect & Collaborate
<p align="center">
  <a href="https://debeatzgh1.blogspot.com/" target="_self">
    <img src="https://img.shields.io/badge/Blog-FF5722?style=for-the-badge&logo=blogger&logoColor=white" alt="Blog">
  </a>
  <a href="https://www.linkedin.com/in/david-kumah-ab7392299?utm_source=share&utm_campaign=share_via&utm_content=profile&utm_medium=android_app" target="_self">
    <img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn">
  </a>
  <a href="https://youtube.com/@debeatzgh?si=pergdMFCCxaicS2g" target="_self">
    <img src="https://img.shields.io/badge/YouTube-FF0000?style=for-the-badge&logo=youtube&logoColor=white" alt="YouTube">
  </a>
</p>

---

---




# 🌐 Dkonsult – AI Tech Mastery Hub  

**Welcome to Dkonsult!**  
Unlock practical ways to **monetize online businesses, content, and audiences** with the **AI Tech Mastery Hub**.  
This project is built for **side hustlers, entrepreneurs, students, and digital creators** who want to leverage **AI-powered strategies and tools** for digital success.  

---

## 🚀 Live Demo & Slides  

🎥 Explore the project slide decks and guides:  
- [📊 AI Tech Mastery Hub – Main Slides](https://www.socialcreator.com/debeatzgh/?s=317509)  
- [📖 Docs & Resources Hub](https://www.socialcreator.com/debeatzgh/?s=317279)  

🔗 **Preview on Blog:** [App](https://debeatzgh1.github.io/Home-/)  

---

## 🌟 Features  

✅ **Actionable Monetization Tactics** – ready-to-use guides for creators & entrepreneurs  
✅ **Step-by-Step Playbooks** – AI, blogging, and marketing strategies simplified  
✅ **Templates & Tools** – professional resources to grow content and audiences  
✅ **Community Support** – collaborate, share, and scale your digital journey  
✅ **Beginner-Friendly Slides** – simple breakdowns for students and startups  

---

## 🖼️ Thumbnails Preview  

| AI Tech Mastery Hub | Digital Marketing Deck | Blogger Tools |
|---------------------|------------------------|---------------|
| ![AI Hub](https://img.icons8.com/color/96/artificial-intelligence.png) | ![Marketing](https://img.icons8.com/color/96/marketing.png) | ![Blogger Tools](https://img.icons8.com/color/96/blog.png) |

---

## 🛠️ Getting Started  

Clone this repository:  

```bash
git clone https://github.com/debeatzgh1/AI-Tech-Mastery-Hub-.git
