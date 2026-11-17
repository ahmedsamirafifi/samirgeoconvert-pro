# Installing SamirGeoConvert Pro as an app (PWA)

The tool itself is still one self-contained HTML file and keeps working exactly as before
when you just double-click it. This folder adds the extra pieces that let a browser offer
an **"Install app"** button, so it opens like a normal installed app (its own window, icon
on the desktop/home screen, works offline after the first load).

## Why it doesn't show up just by double-clicking the file

Chrome/Edge only offer the install prompt when the page is served over `http://` or
`https://` — never for a file opened directly from disk (`file:///...`). So these 4 files
need to sit together in one folder, served by *some* web server. You don't need a real
website for this — any of the options below takes a few minutes:

### Option A — quickest, just for yourself on this PC
1. Install Python (already on most PCs) or Node.js.
2. Open a terminal in this folder and run:
   - Python: `python -m http.server 8080`
   - Node: `npx serve .`
3. Open `http://localhost:8080/SamirGeoConvert_Pro.html` in Chrome/Edge.
4. You'll see an **"⬇ Install app"** button appear in the top bar (or the install icon in
   the address bar) — click it.

### Option B — free hosting, so you (and your team) can open it from anywhere
1. Create a free GitHub account (if you don't have one) and a new repository.
2. Upload all the files in this folder (`SamirGeoConvert_Pro.html`, `manifest.json`,
   `sw.js`, the 3 icon PNGs) to that repository.
3. In the repository settings, enable **GitHub Pages** (branch: main, root folder).
4. GitHub gives you a link like `https://yourname.github.io/yourrepo/SamirGeoConvert_Pro.html`.
5. Open that link in Chrome/Edge on your phone or PC → **Install app**.

### Option C — your own company server
Copy these same 5 files to any folder served by IIS/Apache/Nginx (or a shared drive with a
tiny static server). No build step, no backend — it's just static files.

## Files in this folder
- `SamirGeoConvert_Pro.html` — the app itself (same file as always).
- `manifest.json` — tells the browser the app's name, icon and colors.
- `sw.js` — the service worker that caches the app so it still opens with no internet.
- `icon-192.png`, `icon-512.png`, `icon-512-maskable.png` — the app icons.

## Notes
- The Map viewer still needs internet for the map tiles — everything else (conversions,
  COGO, leveling, RINEX, reports…) works fully offline once installed.
- If you just want the single HTML file with none of this, `SamirGeoConvert_Pro.html` on
  its own is still exactly the same tool as before — nothing about its normal use changed.

---

# تثبيت SamirGeoConvert Pro كبرنامج (PWA)

الأداة لسه ملف HTML واحد بذاته وتفتح بنفس الطريقة بالظبط لو دبلت كليك عليها. المجلد ده
بيضيف الملفات الإضافية اللي بتخلي المتصفح يعرض زرار **"تثبيت البرنامج"**، فيفتح زي أي
برنامج متثبت على جهازك (نافذة خاصة بيه، أيقونة على الديسكتوب، ويشتغل أوفلاين بعد أول فتح).

## ليه مش بيظهر لو فتحت الملف على طول

كروم/إيدج بيعرضوا زرار التثبيت بس لما الصفحة تتفتح من سيرفر (`http://` أو `https://`) —
مش لما تفتحها كملف من الجهاز مباشرة. يعني الملفات الأربعة دي لازم تكون مع بعض في مجلد واحد
وتتفتح من خلال سيرفر بسيط — مش لازم موقع حقيقي، الخيارات تحت بتاخد دقايق بس:

### الطريقة الأسهل — على جهازك بس
1. شغّل من التيرمينال داخل المجلد ده: `python -m http.server 8080` (أو `npx serve .`)
2. افتح `http://localhost:8080/SamirGeoConvert_Pro.html` في كروم أو إيدج.
3. هيظهر زرار **"⬇ تثبيت البرنامج"** فوق — دوس عليه.

### استضافة مجانية (عشان تفتحه من أي جهاز)
ارفع الملفات الخمسة دي على مستودع GitHub وفعّل **GitHub Pages** من إعدادات المستودع —
هيديك لينك تقدر تفتحه من أي جهاز أو موبايل وتثبته من كروم.

### سيرفر الشركة
انسخ نفس الملفات الخمسة لأي فولدر على سيرفر IIS/Apache/Nginx — مفيش build ولا backend،
ملفات ثابتة بس.
