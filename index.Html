// ── InvoiceApp Global Utilities ───────────────────────────────────────────────

// ─── Dark mode ────────────────────────────────────────────────────────────────
(function () {
  const stored = localStorage.getItem('theme');
  const prefersDark = window.matchMedia('(prefers-color-scheme: dark)').matches;
  if (stored === 'dark' || (!stored && prefersDark)) {
    document.documentElement.classList.add('dark');
  }
})();

// ─── Exported helpers ─────────────────────────────────────────────────────────
window.App = (function () {

  function toggleDark() {
    const isDark = document.documentElement.classList.toggle('dark');
    localStorage.setItem('theme', isDark ? 'dark' : 'light');
    return isDark;
  }

  function fmt(n) {
    return new Intl.NumberFormat('de-DE', { style: 'currency', currency: 'EUR' }).format(n);
  }

  function fmtDate(iso) {
    if (!iso) return '—';
    return new Date(iso).toLocaleDateString('de-DE', { day: '2-digit', month: '2-digit', year: 'numeric' });
  }

  function fmtNum(n) {
    return Number(n).toLocaleString('de-DE', { minimumFractionDigits: 2, maximumFractionDigits: 2 });
  }

  const STATUS_LABEL = { draft: 'Entwurf', sent: 'Versendet', paid: 'Bezahlt', overdue: 'Überfällig' };

  function statusBadge(status) {
    const map = {
      draft:   'bg-gray-100 text-gray-700 dark:bg-gray-700 dark:text-gray-200',
      sent:    'bg-blue-100 text-blue-700 dark:bg-blue-900/60 dark:text-blue-300',
      paid:    'bg-emerald-100 text-emerald-700 dark:bg-emerald-900/50 dark:text-emerald-300',
      overdue: 'bg-red-100 text-red-700 dark:bg-red-900/50 dark:text-red-300',
    };
    const cls = map[status] || map.draft;
    return `<span class="inline-flex items-center text-xs font-semibold px-2.5 py-0.5 rounded-full ${cls}">${STATUS_LABEL[status] || status}</span>`;
  }

  function grossTotal(posten) {
    return posten.reduce((s, p) => {
      const net = p.menge * p.einzelpreis;
      return s + net + net * (p.mwst_satz / 100);
    }, 0);
  }

  function calcTotals(posten) {
    const net = posten.reduce((s, p) => s + p.menge * p.einzelpreis, 0);
    const vatMap = {};
    posten.forEach(p => {
      const k = String(p.mwst_satz);
      vatMap[k] = (vatMap[k] || 0) + p.menge * p.einzelpreis * (p.mwst_satz / 100);
    });
    const totalVat = Object.values(vatMap).reduce((a, b) => a + b, 0);
    return { net, vatMap, totalVat, gross: net + totalVat };
  }

  function toast(msg, type = 'success') {
    const el = document.createElement('div');
    const colors = type === 'success'
      ? 'bg-emerald-600 text-white'
      : type === 'error'
        ? 'bg-red-600 text-white'
        : 'bg-gray-800 text-white';
    el.className = `fixed bottom-5 right-5 z-50 px-4 py-3 rounded-xl shadow-xl text-sm font-medium ${colors} fade-in`;
    el.textContent = msg;
    document.body.appendChild(el);
    setTimeout(() => {
      el.style.opacity = '0';
      el.style.transition = 'opacity 0.3s';
      setTimeout(() => el.remove(), 350);
    }, 2800);
  }

  function spinner(text = 'Laden…') {
    return `<div class="flex items-center gap-3 text-gray-400 dark:text-slate-500 py-16 justify-center">
      <svg class="w-5 h-5 spin" fill="none" viewBox="0 0 24 24">
        <circle class="opacity-25" cx="12" cy="12" r="10" stroke="currentColor" stroke-width="4"></circle>
        <path class="opacity-75" fill="currentColor" d="M4 12a8 8 0 018-8V0C5.373 0 0 5.373 0 12h4z"></path>
      </svg>
      <span>${text}</span>
    </div>`;
  }

  function confirm(msg) {
    return window.confirm(msg);
  }

  // Highlight active nav link
  function markActiveNav(basePath) {
    const links = document.querySelectorAll('[data-nav]');
    links.forEach(link => {
      const href = link.getAttribute('href');
      link.classList.remove('nav-active');
      if (href && (window.location.pathname.endsWith(href) || window.location.href.includes(href))) {
        link.classList.add('nav-active');
      }
    });
  }

  // Sidebar nav HTML
  function sidebarHtml(firma) {
    const nav = [
      { href: 'index.html', label: 'Dashboard', icon: `<svg class="w-5 h-5" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="1.8"><rect x="3" y="3" width="7" height="7" rx="1"/><rect x="14" y="3" width="7" height="7" rx="1"/><rect x="3" y="14" width="7" height="7" rx="1"/><rect x="14" y="14" width="7" height="7" rx="1"/></svg>` },
      { href: 'invoices.html', label: 'Rechnungen', icon: `<svg class="w-5 h-5" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="1.8"><path stroke-linecap="round" stroke-linejoin="round" d="M9 12h6m-6 4h6M5 8h14M7 4h10a2 2 0 012 2v14a2 2 0 01-2 2H7a2 2 0 01-2-2V6a2 2 0 012-2z"/></svg>` },
      { href: 'settings-company.html', label: 'Firmenprofil', icon: `<svg class="w-5 h-5" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="1.8"><path stroke-linecap="round" stroke-linejoin="round" d="M10.325 4.317a1.724 1.724 0 012.35 0l.938.851a1.724 1.724 0 002.275-.18l.6-.737a1.724 1.724 0 012.828 1.632l-.272 1.227a1.724 1.724 0 001.274 2.073l1.227.272a1.724 1.724 0 010 3.373l-1.227.272a1.724 1.724 0 00-1.274 2.073l.272 1.227a1.724 1.724 0 01-2.828 1.632l-.6-.737a1.724 1.724 0 00-2.275.18l-.938.851a1.724 1.724 0 01-2.35 0l-.938-.851a1.724 1.724 0 00-2.275.18l-.6.737a1.724 1.724 0 01-2.828-1.632l.272-1.227A1.724 1.724 0 004.682 13.5l-1.227-.272a1.724 1.724 0 010-3.373l1.227-.272A1.724 1.724 0 005.956 7.51L5.684 6.283a1.724 1.724 0 012.828-1.632l.6.737a1.724 1.724 0 002.275.18l.938-.851z"/><circle cx="12" cy="12" r="3"/></svg>` },
      { href: 'settings-users.html', label: 'Benutzer', icon: `<svg class="w-5 h-5" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="1.8"><path stroke-linecap="round" stroke-linejoin="round" d="M17 20h5v-2a4 4 0 00-3-3.87M9 20H4v-2a4 4 0 013-3.87m6 5.87a4 4 0 100-8 4 4 0 000 8zm6-10a4 4 0 10-8 0 4 4 0 008 0z"/></svg>` },
    ];

    const links = nav.map(item => `
      <a href="${item.href}" data-nav="${item.href}"
        class="flex items-center gap-3 px-3 py-2.5 rounded-xl text-sm font-medium text-gray-600 dark:text-slate-400 hover:bg-gray-100 dark:hover:bg-slate-700/60 hover:text-gray-900 dark:hover:text-slate-100 transition-all">
        ${item.icon}
        <span>${item.label}</span>
      </a>`).join('');

    return `
      <aside class="hidden md:flex md:flex-col w-64 bg-white dark:bg-slate-800 border-r border-gray-200 dark:border-slate-700/80 flex-shrink-0 h-screen sticky top-0">
        <div class="px-6 py-5 border-b border-gray-100 dark:border-slate-700/60">
          <div class="flex items-center gap-3">
            <div class="w-9 h-9 rounded-xl bg-blue-600 flex items-center justify-center text-white font-bold text-sm shadow-sm flex-shrink-0">
              ${(firma?.name || 'F').charAt(0)}
            </div>
            <div class="min-w-0">
              <p class="font-semibold text-sm text-gray-900 dark:text-slate-100 truncate">${firma?.name || 'Firma'}</p>
              <p class="text-xs text-gray-400 dark:text-slate-500">Admin</p>
            </div>
          </div>
        </div>
        <nav class="flex-1 px-3 py-4 space-y-0.5 overflow-y-auto">${links}</nav>
        <div class="px-3 py-4 border-t border-gray-100 dark:border-slate-700/60 space-y-1">
          <button id="themeToggleSidebar"
            class="flex items-center gap-3 w-full px-3 py-2 rounded-xl text-sm text-gray-500 dark:text-slate-400 hover:bg-gray-100 dark:hover:bg-slate-700/60 transition-all">
            <svg id="sbSunIcon" class="w-5 h-5 hidden" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="1.8">
              <path stroke-linecap="round" stroke-linejoin="round" d="M12 3v1m0 16v1m8.66-9h-1M4.34 12h-1m15.07-5.66-.71.71M6.34 17.66l-.71.71M17.66 17.66l.71.71M6.34 6.34l-.71-.71M12 5a7 7 0 100 14A7 7 0 0012 5z"/>
            </svg>
            <svg id="sbMoonIcon" class="w-5 h-5 hidden" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="1.8">
              <path stroke-linecap="round" stroke-linejoin="round" d="M21 12.79A9 9 0 1111.21 3 7 7 0 0021 12.79z"/>
            </svg>
            <span id="sbThemeLabel">Dark Mode</span>
          </button>
          <a href="../auth/login.html"
            class="flex items-center gap-3 px-3 py-2 rounded-xl text-sm text-gray-500 dark:text-slate-400 hover:bg-gray-100 dark:hover:bg-slate-700/60 transition-all">
            <svg class="w-5 h-5" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="1.8">
              <path stroke-linecap="round" stroke-linejoin="round" d="M17 16l4-4m0 0l-4-4m4 4H7m6 4v1a3 3 0 01-3 3H6a3 3 0 01-3-3V7a3 3 0 013-3h4a3 3 0 013 3v1"/>
            </svg>
            Abmelden
          </a>
        </div>
      </aside>`;
  }

  function mobileNavHtml() {
    const nav = [
      { href: 'index.html', label: 'Dashboard', icon: `<svg class="w-5 h-5" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="1.8"><rect x="3" y="3" width="7" height="7" rx="1"/><rect x="14" y="3" width="7" height="7" rx="1"/><rect x="3" y="14" width="7" height="7" rx="1"/><rect x="14" y="14" width="7" height="7" rx="1"/></svg>` },
      { href: 'invoices.html', label: 'Rechnungen', icon: `<svg class="w-5 h-5" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="1.8"><path stroke-linecap="round" stroke-linejoin="round" d="M9 12h6m-6 4h6M5 8h14M7 4h10a2 2 0 012 2v14a2 2 0 01-2 2H7a2 2 0 01-2-2V6a2 2 0 012-2z"/></svg>` },
      { href: 'invoice-new.html', label: 'Neu', icon: `<svg class="w-5 h-5" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="1.8"><path stroke-linecap="round" stroke-linejoin="round" d="M12 4v16m8-8H4"/></svg>` },
      { href: 'settings-company.html', label: 'Einstellungen', icon: `<svg class="w-5 h-5" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="1.8"><path stroke-linecap="round" stroke-linejoin="round" d="M10.325 4.317a1.724 1.724 0 012.35 0l.938.851a1.724 1.724 0 002.275-.18l.6-.737a1.724 1.724 0 012.828 1.632l-.272 1.227a1.724 1.724 0 001.274 2.073l1.227.272a1.724 1.724 0 010 3.373l-1.227.272a1.724 1.724 0 00-1.274 2.073l.272 1.227a1.724 1.724 0 01-2.828 1.632l-.6-.737a1.724 1.724 0 00-2.275.18l-.938.851a1.724 1.724 0 01-2.35 0l-.938-.851a1.724 1.724 0 00-2.275.18l-.6.737a1.724 1.724 0 01-2.828-1.632l.272-1.227A1.724 1.724 0 004.682 13.5l-1.227-.272a1.724 1.724 0 010-3.373l1.227-.272A1.724 1.724 0 005.956 7.51L5.684 6.283a1.724 1.724 0 012.828-1.632l.6.737a1.724 1.724 0 002.275.18l.938-.851z"/><circle cx="12" cy="12" r="3"/></svg>` },
    ];
    return `<nav class="md:hidden fixed bottom-0 inset-x-0 z-50 bg-white dark:bg-slate-800 border-t border-gray-200 dark:border-slate-700 flex safe-area-bottom">
      ${nav.map(item => `
        <a href="${item.href}" data-nav="${item.href}"
          class="flex-1 flex flex-col items-center py-2.5 gap-0.5 text-xs text-gray-500 dark:text-slate-400 hover:text-blue-600 dark:hover:text-blue-400 transition-colors">
          ${item.icon}
          <span class="text-[10px]">${item.label}</span>
        </a>`).join('')}
    </nav>`;
  }

  function initSidebarTheme() {
    const sunIcon = document.getElementById('sbSunIcon');
    const moonIcon = document.getElementById('sbMoonIcon');
    const label = document.getElementById('sbThemeLabel');
    const btn = document.getElementById('themeToggleSidebar');

    function update() {
      const isDark = document.documentElement.classList.contains('dark');
      if (sunIcon) sunIcon.classList.toggle('hidden', !isDark);
      if (moonIcon) moonIcon.classList.toggle('hidden', isDark);
      if (label) label.textContent = isDark ? 'Light Mode' : 'Dark Mode';
    }
    update();
    if (btn) btn.addEventListener('click', () => { toggleDark(); update(); });
    markActiveNav();
  }

  return { toggleDark, fmt, fmtDate, fmtNum, statusBadge, grossTotal, calcTotals, toast, spinner, sidebarHtml, mobileNavHtml, initSidebarTheme, markActiveNav };
})();
