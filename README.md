
# Starter de sitio estático seguro (gratis)

Opciones de despliegue recomendadas (gratis):

## 1) Cloudflare Pages (recomendado)
1. Creá un repo en GitHub y subí estos archivos.
2. En Cloudflare → Pages → "Create a project" → conectá tu repo.
3. Build settings: *Framework preset*: None. Build command vacío. Output folder: `/`.
4. Una vez publicado, en Cloudflare (zona del dominio) activá:
   - SSL/TLS: "Full", "Always Use HTTPS"
   - Security → WAF (reglas administradas ON), Bot Fight Mode ON
   - Speed → Auto Minify (HTML, CSS, JS)
   - SSL/TLS → Edge Certificates → HSTS (con cuidado: activalo cuando tengas HTTPS estable)
5. En GoDaddy, cambiá los nameservers a los de Cloudflare para usar el proxy y WAF gratis.
6. En Pages → Custom domains → añadí `www.tudominio.com` y `tudominio.com`.

## 2) GitHub Pages
1. Subí estos archivos a un repo público.
2. Settings → Pages → Deploy from branch → `main` (root).
3. En GoDaddy, agregá un CNAME de `www` a `<usuario>.github.io` y A/ALIAS para apex (opcional).
4. Activa HTTPS forzado en Settings → Pages.

## 3) Netlify
1. "New site from Git" → conectá el repo → Deploy.
2. En "Domain settings" agregá tu dominio y apuntá los DNS desde GoDaddy.
3. El archivo `_headers` aplica las cabeceras de seguridad automáticamente.

### Extras
- Editá `sitemap.xml` para usar tu dominio real.
- Si añadís formularios o scripts de terceros, ajustá la CSP en `/_headers`.
- Habilitá DNSSEC en tu registrador si está disponible.
