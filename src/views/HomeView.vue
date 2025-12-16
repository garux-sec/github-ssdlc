<script setup>
import { RouterLink } from 'vue-router'

const links = [
  { label: 'Home', hash: '#home' },
  { label: 'Why SSDLC', hash: '#why' },
  { label: 'Journey', hash: '#journey' },
  { label: 'Phases', hash: '#phases' },
  { label: 'Tooling', hash: '#tooling' },
  { label: 'GitHub Actions', hash: '#actions' },
  { label: 'Policies', hash: '#policies' },
  { label: 'Playbooks', hash: '#playbooks' },
  { label: 'Resources', hash: '#resources' },
  { label: 'Credits', hash: '#credits' },
]
</script>

<template>
  <div class="page">
    <div class="glass">
      <header class="top">
        <div>
          <p class="eyebrow">DevSecOps · SSDLC Guide</p>
          <h1 class="brand">Secure Development on GitHub</h1>
        </div>
        <nav class="nav">
          <a
            v-for="link in links"
            :key="link.hash"
            class="nav-link"
            :href="link.hash"
          >
            {{ link.label }}
          </a>
          <RouterLink class="nav-link" to="/admin">Admin</RouterLink>
        </nav>
      </header>

      <section class="hero" id="home">
        <div class="identity">
          <p class="kicker">SSDLC on GitHub</p>
          <h2>Practical playbook for secure delivery</h2>
          <p class="headline">
            ตั้งแต่การออกแบบ ไปจนถึง deploy และ monitoring — ใช้ GitHub Actions, branch protections, SAST, SCA, secret scan,
            IaC scan และ CI/CD guardrails เพื่อให้ secure-by-default พร้อมขั้นตอนที่ลงมือทำจริง
          </p>

          <div class="cta-row">
            <a class="cta primary" href="#actions">Jump to workflows</a>
            <a class="cta ghost" href="#resources">Starter kit</a>
          </div>
        </div>

        <div class="card highlight">
          <p class="label">ผลลัพธ์ที่อยากได้</p>
          <h3>Secure-by-default delivery</h3>
          <p class="body">
            Dev และ Sec ทำงานร่วมกันบน workflow เดียวกัน: โค้ดปลอด secret, dependency ปลอดช่องโหว่, IaC ผ่าน baseline, image hardened,
            และมี report พร้อม evidence ในทุก pipeline run
          </p>
          <div class="stats-grid">
            <div class="stat-card">
              <p class="stat-num">30m</p>
              <p class="stat-label">detect secrets in PR</p>
            </div>
            <div class="stat-card">
              <p class="stat-num">1 pipeline</p>
              <p class="stat-label">SAST · SCA · IaC · DAST</p>
            </div>
            <div class="stat-card">
              <p class="stat-num">Always</p>
              <p class="stat-label">artifact integrity checks</p>
            </div>
          </div>
        </div>
      </section>

      <section class="section" id="highlights">
        <div class="section-header">
          <p class="label">Highlights</p>
          <h3>Guardrails at a glance</h3>
          <p class="section-copy">ภาพรวมสั้นๆ ว่า pipeline นี้ล็อกอะไรไว้บ้าง</p>
        </div>
        <div class="tile-grid">
          <div class="tile">
            <p class="label">Branch policy</p>
            <h4>🔒 Protected main</h4>
            <p class="body">Required reviews, signed commits, status checks, path-based approvals</p>
          </div>
          <div class="tile">
            <p class="label">Code & deps</p>
            <h4>🧪 SAST + SCA</h4>
            <p class="body">Semgrep/CodeQL, npm audit/Dependabot, license & severity thresholds</p>
          </div>
          <div class="tile">
            <p class="label">IaC & cloud</p>
            <h4>🏗️ IaC posture</h4>
            <p class="body">tfsec/checkov + Trivy config scan to stop misconfig before merge</p>
          </div>
          <div class="tile">
            <p class="label">Release</p>
            <h4>📝 SBOM + Sign</h4>
            <p class="body">SBOM attach, image scan, cosign signature, provenance recorded</p>
          </div>
        </div>
      </section>

      <section class="section" id="journey">
        <div class="section-header">
          <p class="label">Step-by-step</p>
          <h3>Journey we implement</h3>
          <p class="section-copy">สรุปสิ่งที่เราทำจริงแบบเป็นลำดับ</p>
        </div>
        <div class="journey">
          <div class="journey-step">
            <div class="pill accent">01</div>
            <div>
              <h4>ตั้ง baseline repository</h4>
              <p class="body">เปิด Branch protection, required reviews, signed commits, DCO, Dependabot alerts, push protection</p>
            </div>
          </div>
          <div class="journey-step">
            <div class="pill accent">02</div>
            <div>
              <h4>ใส่ guardrails ใน PR</h4>
              <p class="body">เพิ่ม Actions: secret scan (gitleaks), SAST (Semgrep/CodeQL), SCA, IaC scan, npm test; บังคับทุก PR ผ่าน</p>
            </div>
          </div>
          <div class="journey-step">
            <div class="pill accent">03</div>
            <div>
              <h4>Build + Sign</h4>
              <p class="body">สร้าง SBOM, สแกน image (Trivy), ลงนามด้วย cosign, เก็บ artifact พร้อม provenance</p>
            </div>
          </div>
          <div class="journey-step">
            <div class="pill accent">04</div>
            <div>
              <h4>Release & Operate</h4>
              <p class="body">Deploy แบบ immutable, เปิด audit log ไป SIEM, มี playbook incident/patch/hotfix พร้อม retest</p>
            </div>
          </div>
        </div>
      </section>

      <section class="section" id="why">
        <div class="section-header">
          <p class="label">ทำไมต้อง SSDLC</p>
          <h3>Shift-left + guardrails</h3>
          <p class="section-copy">ลดงาน incident, ลด MTTR, และทำให้ทีม dev ship ได้เร็วขึ้นโดยมี security baked-in</p>
        </div>
        <div class="timeline">
          <div class="timeline-item">
            <div>
              <p class="label">Design</p>
              <h4>Threat model + acceptance</h4>
              <p class="body">กำหนด misuse/abuse cases, ขอบเขตข้อมูล, trust boundary, และ non-functional security acceptance</p>
            </div>
            <div class="pill">Architecture</div>
          </div>
          <div class="timeline-item">
            <div>
              <p class="label">Build</p>
              <h4>Guardrails in CI</h4>
              <p class="body">SAST, SCA, secret scan, IaC scan, image scan, license policy ผ่านทุก PR</p>
            </div>
            <div class="pill">CI/CD</div>
          </div>
          <div class="timeline-item">
            <div>
              <p class="label">Release</p>
              <h4>Integrity & runtime</h4>
              <p class="body">Signed artifacts (sigstore), image provenance, runtime hardening, alerting และ retest ก่อนโปรโมต</p>
            </div>
            <div class="pill">Operate</div>
          </div>
        </div>
      </section>

      <section class="section" id="phases">
        <div class="section-header">
          <p class="label">SSDLC</p>
          <h3>Phases & checkpoints</h3>
          <p class="section-copy">รายการ checkpoint สั้นๆ ที่ทำได้จริงบน GitHub</p>
        </div>
        <div class="cards grid">
          <div class="card">
            <p class="label">Plan</p>
            <ul>
              <li>Define risk acceptance & compliance tags</li>
              <li>Data classification & secrets policy</li>
              <li>Threat model key user flows</li>
            </ul>
          </div>
          <div class="card">
            <p class="label">Build</p>
            <ul>
              <li>Pre-commit hooks: secrets + lint</li>
              <li>PR checks: SAST, SCA, IaC, tests</li>
              <li>Mandatory code review + DCO</li>
            </ul>
          </div>
          <div class="card">
            <p class="label">Release</p>
            <ul>
              <li>Container scan + SBOM attach</li>
              <li>Sign artifacts (cosign) + verify</li>
              <li>Deploy via immutable releases</li>
            </ul>
          </div>
          <div class="card">
            <p class="label">Operate</p>
            <ul>
              <li>Runtime policy (CIS/K8s hardening)</li>
              <li>Audit logs in SIEM (GitHub & cloud)</li>
              <li>Playbooks for incident & hotfix</li>
            </ul>
          </div>
        </div>
      </section>

      <section class="section" id="tooling">
        <div class="section-header">
          <p class="label">Tooling</p>
          <h3>Core scannersบน GitHub</h3>
          <p class="section-copy">เลือกใช้เครื่องมือที่คุมคุณภาพได้ทั้ง open-source และ managed</p>
        </div>
        <div class="cards grid">
          <div class="card">
            <p class="label">Secrets & Code</p>
            <ul>
              <li>gitleaks หรือ truffleHog ใน PR</li>
              <li>Semgrep / CodeQL สำหรับ SAST</li>
              <li>Conventional commits + DCO</li>
            </ul>
          </div>
          <div class="card">
            <p class="label">Dependencies & IaC</p>
            <ul>
              <li>Dependency review + npm audit (หรือ Snyk)</li>
              <li>tfsec / checkov สำหรับ IaC</li>
              <li>Trivy สำหรับ container/image</li>
            </ul>
          </div>
        </div>
      </section>

      <section class="section" id="actions">
        <div class="section-header">
          <p class="label">CI/CD</p>
          <h3>GitHub Actions blueprint</h3>
          <p class="section-copy">โครง workflow เดียวที่ครอบคลุม SAST + SCA + IaC + test + build + sign</p>
        </div>
        <div class="card code">
          <pre v-pre><code># .github/workflows/secure-ci.yml
name: secure-ci
on: [pull_request]
jobs:
  validate:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with: { node-version: 20 }
      - name: Secret scan
        uses: gitleaks/gitleaks-action@v2
      - name: SAST (Semgrep)
        uses: returntocorp/semgrep-action@v1
        with: { config: 'p/owasp-top-ten' }
      - name: SCA
        run: npm audit --audit-level=high
      - name: IaC scan
        uses: aquasecurity/trivy-action@master
        with: { scan-type: 'config', scan-ref: '.' }
      - name: Test
        run: npm test -- --runInBand</code></pre>
        </div>
        <div class="card code">
          <pre v-pre><code># .github/workflows/release.yml
name: release
on:
  push:
    tags: ['v*.*.*']
jobs:
  build-sign:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with: { node-version: 20 }
      - run: npm ci && npm run build
      - name: Build SBOM
        run: npm run sbom || true
      - name: Trivy image scan
        uses: aquasecurity/trivy-action@master
        with: { image-ref: 'ghcr.io/org/app:${&#123;&#123; github.ref_name &#125;&#125;}' }
      - name: Sign image
        uses: sigstore/cosign-installer@v3
      - run: cosign sign ghcr.io/org/app:${&#123;&#123; github.ref_name &#125;&#125;} --yes</code></pre>
        </div>
      </section>

      <section class="section" id="policies">
        <div class="section-header">
          <p class="label">Governance</p>
          <h3>GitHub policies & controls</h3>
          <p class="section-copy">ตั้งค่า repo และ org ให้ลดความเสี่ยงล่วงหน้า</p>
        </div>
        <div class="cards grid">
          <div class="card">
            <p class="label">Repo level</p>
            <ul>
              <li>Branch protection: required PR review + status checks</li>
              <li>Require signed commits (GPG/SSH) + DCO</li>
              <li>Dependabot alerts + updates</li>
            </ul>
          </div>
          <div class="card">
            <p class="label">Org level</p>
            <ul>
              <li>SSO + least privilege team/role mapping</li>
              <li>Secret scanning & push protection</li>
              <li>Required reviewers for sensitive paths</li>
            </ul>
          </div>
        </div>
      </section>

      <section class="section" id="playbooks">
        <div class="section-header">
          <p class="label">Runbooks</p>
          <h3>Playbooks ที่ต้องมี</h3>
          <p class="section-copy">ใช้ซ้ำได้ทั้ง incident และ hardening</p>
        </div>
        <div class="cards grid">
          <div class="card">
            <p class="label">Secret exposure</p>
            <ul>
              <li>Revoke keysทันที, rotate, purge cache</li>
              <li>Audit git history (gitleaks --redact) + force rotate</li>
              <li>Post-mortem + add pre-commit secret hook</li>
            </ul>
          </div>
          <div class="card">
            <p class="label">Critical CVE</p>
            <ul>
              <li>SBOM lookup → affected services list</li>
              <li>Hotfix branch with focused tests</li>
              <li>Retest + promote with signed release</li>
            </ul>
          </div>
          <div class="card">
            <p class="label">Pipeline failure</p>
            <ul>
              <li>Triaging false positives vs real</li>
              <li>Quarantine build artifacts if scan fails</li>
              <li>Update policy rules and baselines</li>
            </ul>
          </div>
          <div class="card">
            <p class="label">Release readiness</p>
            <ul>
              <li>Checklist: tests, scans, SBOM, signatures</li>
              <li>Approver list per system criticality</li>
              <li>Rollback plan + monitoring hooks</li>
            </ul>
          </div>
        </div>
      </section>

      <section class="section" id="resources">
        <div class="section-header">
          <p class="label">Resources</p>
          <h3>Template & docs</h3>
          <p class="section-copy">แนะนำให้เริ่มจาก repo template และ policy ต่อไปนี้</p>
        </div>
        <div class="cards grid">
          <div class="card">
            <p class="label">Templates</p>
            <ul>
              <li>GitHub Actions secure-ci.yml</li>
              <li>Branch protection baseline</li>
              <li>Threat model checklist (STRIDE-lite)</li>
            </ul>
          </div>
          <div class="card">
            <p class="label">Standards</p>
            <ul>
              <li>OWASP SAMM / ASVS mapping</li>
              <li>NIST SSDF quick reference</li>
              <li>CIS Benchmarks (cloud/K8s)</li>
            </ul>
          </div>
          <div class="card">
            <p class="label">Learning</p>
            <ul>
              <li>OWASP Top 10 & API Top 10 labs</li>
              <li>Secure coding dojo (internal)</li>
              <li>Semgrep rules tuning guide</li>
            </ul>
          </div>
        </div>
      </section>

      <section class="section credits" id="credits">
        <div class="card credit-card">
          <div>
            <p class="label">Credits</p>
            <h3>Phisit Pupiw</h3>
            <p class="body">
              Penetration Tester at Mitr Phol Group | eWPTX, eJPT | CC | PenTest+, CySA+, Security+ | CEH | HTB Pro Labs: Dante,
              FullHouse | CVE-2025-65300
            </p>
          </div>
          <a
            class="cta ghost"
            href="https://www.linkedin.com/in/phisit-pupiw-42a510339/"
            target="_blank"
            rel="noreferrer noopener"
          >
            LinkedIn Profile
          </a>
        </div>
      </section>
    </div>
  </div>
</template>

<style scoped>
.page {
  min-height: 100vh;
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 1.5rem 1rem;
  background:
    linear-gradient(135deg, rgba(4, 20, 16, 0.9), rgba(7, 42, 32, 0.85)),
    url('https://images.unsplash.com/photo-1517245386807-bb43f82c33c4?auto=format&fit=crop&w=1600&q=80')
      center/cover no-repeat fixed;
  color: #e9f7f2;
}

.glass {
  width: min(1400px, 100%);
  background: rgba(14, 30, 25, 0.7);
  border: 1px solid rgba(255, 255, 255, 0.08);
  border-radius: 20px;
  padding: 2.5rem;
  backdrop-filter: blur(10px);
  box-shadow:
    0 25px 80px rgba(0, 0, 0, 0.4),
    inset 0 1px 0 rgba(255, 255, 255, 0.06);
}

.top {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 1rem;
  flex-wrap: wrap;
  margin-bottom: 1.25rem;
}

.brand {
  margin: 0.25rem 0 0;
  font-size: 1.6rem;
  color: #f7fff9;
  letter-spacing: -0.02em;
}

.nav {
  display: flex;
  flex-wrap: wrap;
  gap: 0.65rem;
}

.nav-link {
  color: #d8f3e8;
  text-decoration: none;
  padding: 0.55rem 0.85rem;
  border-radius: 10px;
  border: 1px solid rgba(156, 224, 200, 0.25);
  background: rgba(156, 224, 200, 0.06);
  transition: all 0.2s ease;
}

.nav-link:hover {
  background: rgba(156, 224, 200, 0.16);
  transform: translateY(-1px);
}

.eyebrow {
  letter-spacing: 0.08em;
  text-transform: uppercase;
  font-size: 0.85rem;
  color: #9ce0c8;
}

.hero {
  display: grid;
  grid-template-columns: 1.2fr 1fr;
  gap: 1.5rem;
  align-items: start;
  margin-bottom: 2rem;
}

.identity {
  display: flex;
  flex-direction: column;
  gap: 0.75rem;
}

.kicker {
  font-size: 1rem;
  color: #9ce0c8;
  letter-spacing: 0.05em;
  text-transform: uppercase;
}

h2 {
  font-size: clamp(2.2rem, 5vw, 3rem);
  margin: 0;
  color: #f7fff9;
  letter-spacing: -0.02em;
}

.headline {
  color: #cde8dd;
  line-height: 1.6;
  font-size: 1.05rem;
}

.meta {
  display: flex;
  flex-wrap: wrap;
  gap: 0.65rem;
  margin-top: 0.25rem;
}

.chip {
  padding: 0.55rem 0.75rem;
  border-radius: 999px;
  border: 1px solid rgba(156, 224, 200, 0.4);
  color: #d9f5ea;
  font-size: 0.95rem;
  background: rgba(156, 224, 200, 0.06);
}

.cta-row {
  display: flex;
  gap: 0.75rem;
  margin-top: 0.25rem;
  flex-wrap: wrap;
}

.cta {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  padding: 0.65rem 1.2rem;
  border-radius: 12px;
  font-weight: 600;
  text-decoration: none;
  transition: transform 0.2s ease, box-shadow 0.2s ease, background 0.2s ease;
  cursor: pointer;
}

.stats-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(140px, 1fr));
  gap: 0.75rem;
  margin-top: 1rem;
}

.stat-card {
  padding: 0.65rem 0.8rem;
  border-radius: 12px;
  border: 1px solid rgba(156, 224, 200, 0.2);
  background: rgba(156, 224, 200, 0.04);
}

.stat-num {
  font-size: 1.4rem;
  font-weight: 700;
  color: #f7fff9;
  margin-bottom: 0.2rem;
}

.stat-label {
  color: #cde8dd;
  font-size: 0.95rem;
}

.card {
  background: rgba(255, 255, 255, 0.03);
  border-radius: 16px;
  border: 1px solid rgba(255, 255, 255, 0.08);
  padding: 1.25rem 1.5rem;
  box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.04);
}

.card h2,
.card h3 {
  margin: 0.35rem 0 0.6rem;
  color: #f5fff9;
  letter-spacing: -0.01em;
}

.body {
  color: #cde8dd;
  line-height: 1.55;
}

.label {
  text-transform: uppercase;
  letter-spacing: 0.08em;
  font-size: 0.85rem;
  color: #9ce0c8;
}

.grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
  gap: 1rem 1.25rem;
}

ul {
  list-style: none;
  padding: 0;
  margin: 0.5rem 0 0;
  color: #d8f3e8;
  line-height: 1.7;
}

.highlight {
  border: 1px solid rgba(63, 182, 139, 0.35);
  background: linear-gradient(135deg, rgba(63, 182, 139, 0.12), rgba(29, 143, 104, 0.08));
}

.section {
  margin-top: 1.5rem;
  padding-top: 1.5rem;
  border-top: 1px solid rgba(255, 255, 255, 0.08);
}

.section-header {
  margin-bottom: 1rem;
}

.timeline {
  display: grid;
  gap: 1rem;
}

.timeline-item {
  display: flex;
  justify-content: space-between;
  gap: 1rem;
  padding: 1rem 1.1rem;
  border-radius: 14px;
  border: 1px solid rgba(156, 224, 200, 0.2);
  background: rgba(156, 224, 200, 0.04);
}

.timeline-item h4 {
  margin: 0.15rem 0 0.4rem;
  color: #f7fff9;
}

.journey {
  display: grid;
  gap: 0.75rem;
}

.journey-step {
  display: flex;
  gap: 0.8rem;
  padding: 0.95rem 1rem;
  border-radius: 14px;
  border: 1px solid rgba(156, 224, 200, 0.25);
  background: rgba(156, 224, 200, 0.04);
}

.pill.accent {
  background: linear-gradient(135deg, #3fb68b, #1d8f68);
  color: #0b1b15;
  border: none;
  min-width: 44px;
  text-align: center;
  font-weight: 700;
}

.pill {
  align-self: flex-start;
  padding: 0.45rem 0.75rem;
  border-radius: 999px;
  border: 1px solid rgba(156, 224, 200, 0.4);
  background: rgba(156, 224, 200, 0.08);
  color: #d8f3e8;
  font-size: 0.9rem;
}

.section-copy {
  color: #cde8dd;
  margin-top: 0.35rem;
}

.cards {
  gap: 1rem;
}

.method-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
  gap: 1rem;
}

.tile-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
  gap: 0.9rem;
}

.tile {
  padding: 1rem 1.1rem;
  border-radius: 14px;
  border: 1px solid rgba(156, 224, 200, 0.2);
  background: linear-gradient(135deg, rgba(63, 182, 139, 0.08), rgba(29, 143, 104, 0.05));
  box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.05);
}

.code {
  overflow: auto;
}

.code pre {
  background: rgba(0, 0, 0, 0.35);
  padding: 1rem;
  border-radius: 12px;
  border: 1px solid rgba(156, 224, 200, 0.25);
  color: #d8f3e8;
  font-size: 0.9rem;
}

.primary {
  background: linear-gradient(135deg, #3fb68b, #1d8f68);
  color: #0b1b15;
  box-shadow: 0 10px 30px rgba(63, 182, 139, 0.35);
}

.primary:hover {
  transform: translateY(-1px);
  box-shadow: 0 14px 36px rgba(63, 182, 139, 0.45);
}

.ghost {
  border: 1px solid rgba(156, 224, 200, 0.4);
  color: #d6f3e7;
  background: rgba(156, 224, 200, 0.05);
}

.ghost:hover {
  background: rgba(156, 224, 200, 0.12);
  transform: translateY(-1px);
}

.credits {
  margin-bottom: 0.5rem;
}

.credit-card {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 1rem;
}

@media (max-width: 900px) {
  .top {
    flex-direction: column;
    align-items: flex-start;
  }

  .nav {
    width: 100%;
    justify-content: flex-start;
  }

  .hero {
    grid-template-columns: 1fr;
  }

  .glass {
    padding: 2rem;
  }

  .credit-card {
    flex-direction: column;
    align-items: flex-start;
  }

}

@media (max-width: 600px) {
  .page {
    padding: 1.5rem 1rem;
  }

  .headline {
    font-size: 1rem;
  }

  .cta {
    width: 100%;
    justify-content: center;
  }
}
</style>
