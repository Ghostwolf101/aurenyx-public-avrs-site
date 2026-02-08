# Deployment Documentation

## GitHub Pages Configuration

This site is deployed via GitHub Pages using the workflow defined in `.github/workflows/pages.yml`.

### Domain Configuration

- **Primary domain**: `avrs.aurenyx.com`
- **CNAME file**: Contains `avrs.aurenyx.com` (subdomain)

### DNS Setup Requirements

For the site to be accessible at `avrs.aurenyx.com`, the following DNS records must be configured in your DNS provider (Cloudflare or other):

#### Option 1: CNAME Record (Recommended)
Add a CNAME record:
- **Type**: CNAME
- **Name**: `avrs` (or `avrs.aurenyx.com` depending on your DNS provider)
- **Target**: `ghostwolf101.github.io`
- **TTL**: Auto or 3600

#### Option 2: A Records (Alternative)
If using apex domain or if CNAME doesn't work, add A records pointing to GitHub Pages IPs:
- **Type**: A
- **Name**: `avrs`
- **Target**: GitHub Pages IP addresses:
  - `185.199.108.153`
  - `185.199.109.153`
  - `185.199.110.153`
  - `185.199.111.153`

### Cloudflare Specific Settings

If using Cloudflare:

1. **Proxy Status**: Can be proxied (orange cloud) or DNS only (grey cloud)
   - Proxied provides DDoS protection and caching
   - DNS only is faster to propagate initially

2. **SSL/TLS Mode**: Set to "Full" or "Full (strict)"

3. **Page Rules**: None required for basic setup

### Verification

After DNS configuration:

1. Wait for DNS propagation (can take up to 48 hours, usually much faster)
2. Check DNS resolution: `nslookup avrs.aurenyx.com`
3. Verify HTTPS certificate is issued (may take a few minutes after first access)
4. Access the site at: https://avrs.aurenyx.com

### Troubleshooting

**Site not accessible:**
- Verify DNS records are correct
- Check GitHub Pages deployment status in Actions tab
- Ensure CNAME file contains correct domain name
- Wait for DNS propagation (check with `dig avrs.aurenyx.com`)

**Certificate errors:**
- GitHub Pages automatically provides HTTPS certificates
- Initial certificate generation can take a few minutes
- Ensure the custom domain is properly configured in repository settings

**404 errors:**
- Verify the main branch has the latest changes
- Check that the GitHub Actions workflow completed successfully
- Ensure repository has GitHub Pages enabled in Settings > Pages

### Accessing via Apex Domain

If you want users to access via `aurenyx.com` (without the `avrs` subdomain):
1. Update the CNAME file to contain `aurenyx.com` instead of `avrs.aurenyx.com`
2. Configure DNS A records to point the apex domain to GitHub Pages IPs
3. Or set up a redirect from `aurenyx.com` to `avrs.aurenyx.com` in Cloudflare Page Rules
