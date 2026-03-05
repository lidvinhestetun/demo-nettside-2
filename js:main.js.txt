// ===============================
//  SMOOTH SCROLL FOR NAV LINKS
// ===============================
document.querySelectorAll('a[href^="#"]').forEach(link => {
    link.addEventListener('click', function (e) {
        const target = document.querySelector(this.getAttribute('href'));
        if (!target) return;

        e.preventDefault();
        target.scrollIntoView({
            behavior: 'smooth',
            block: 'start'
        });
    });
});


// ===============================
//  HEADER SHADOW ON SCROLL
// ===============================
const header = document.querySelector('.site-header');

window.addEventListener('scroll', () => {
    if (window.scrollY > 20) {
        header.classList.add('header-scrolled');
    } else {
        header.classList.remove('header-scrolled');
    }
});


// ===============================
//  FADE-IN EFFECT ON SECTIONS
// ===============================
const observer = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
        if (entry.isIntersecting) {
            entry.target.classList.add('show');
        }
    });
}, {
    threshold: 0.15
});

document.querySelectorAll('.section, .hero').forEach(section => {
    observer.observe(section);
});


// ===============================
//  MOBILE NAV (future-proof)
// ===============================
const mobileBtn = document.querySelector('.mobile-nav-btn');
const nav = document.querySelector('.main-nav');

if (mobileBtn) {
    mobileBtn.addEventListener('click', () => {
        nav.classList.toggle('nav-open');
        mobileBtn.classList.toggle('open');
    });
}
