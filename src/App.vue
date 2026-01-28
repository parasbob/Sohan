<template>
  <div class="page" v-if="!isLoggedIn">
    <!-- HEADER -->
    <header class="top-header">
      <div class="header-left">
        <img src="@/assets/govEmblem.png" class="emblem" />
        <div>
          <h1>Part Plan And Zone Certificate Portal</h1>
          <p>Government of Maharashtra</p>
          <small>Town Planning and Valuation Department</small>
        </div>
      </div>

      <div class="header-right">
        <v-btn class="btn btn-yellow" @click="openLogin">APPLICANT LOGIN</v-btn>
        <button class="btn btn-outline">OFFICE LOGIN</button>
      </div>
    </header>

    <!-- NAV -->
    <nav class="nav">
      <a class="active">HOME</a>
      <a>FAQ</a>
      <a>CONTACT US</a>
      <a>English ▾</a>
      <a>User Guide</a>
    </nav>

    <!-- MAIN -->
    <main class="main">
      <div class="card map-card">
        <img src="@/assets/maharashtra-map.png" alt="Map" />
      </div>

      <div class="card action-card">
        <h2>Get Part Plan/Zone Certificate</h2>
        <p>Access and manage your zoning certificates through our secure online portal</p>

        <div class="actions">
          <button class="btn btn-primary">Applicant Login</button>
          <button class="btn btn-outline-primary">Applicant Registration</button>
        </div>
      </div>
    </main>

    <h3 class="section-title">Our Reach Across Maharashtra</h3>
    <!-- REACH SECTION -->
    <section class="reach-section">
      <!-- Filters -->
      <div class="filters">
        <select>
          <option>Select Division</option>
        </select>
        <select>
          <option>Select District</option>
        </select>
        <select>
          <option>Select Branch Office</option>
        </select>
        <select>
          <option>Service Type</option>
        </select>
      </div>

      <!-- Stats Grid -->
      <div class="stats-grid">
        <div class="stat-card">
          <h2>6</h2>
          <p>Divisions</p>
        </div>
        <div class="stat-card">
          <h2>34</h2>
          <p>Districts</p>
        </div>
        <div class="stat-card">
          <h2>36</h2>
          <p>Branch Offices</p>
        </div>

        <div class="stat-card">
          <h2>40,791</h2>
          <p>Application Received</p>
        </div>
        <div class="stat-card">
          <h2>32,652</h2>
          <p>Application Approved</p>
        </div>
        <div class="stat-card">
          <h2>4,263</h2>
          <p>Application Rejected</p>
        </div>

        <div class="stat-card">
          <h2>126</h2>
          <p>Maximum Day’s taken</p>
        </div>
        <div class="stat-card">
          <h2>1</h2>
          <p>Minimum Day’s taken</p>
        </div>

        <div class="stat-card">
          <h2>89%</h2>
          <p>Compliance percentage</p>
        </div>
        <div class="stat-card">
          <h2>7.48 days</h2>
          <p>Avg. time for Disposal</p>
        </div>
        <div class="stat-card">
          <h2>₹10,197,750</h2>
          <p>Service Charges</p>
        </div>
      </div>
      <section class="faq-section">
        <h2>Frequently Asked Questions</h2>
        <p class="faq-subtitle">Find answers to common questions about our services</p>
        <div class="faq-list">
          <div class="faq-item" v-for="(faq, index) in faqs" :key="index">
            <div class="faq-question" @click="toggleFaq(index)">
              <span>{{ faq.question }}</span>
              <span class="icon">
                {{ activeFaq === index ? '−' : '+' }}
              </span>
            </div>

            <div class="faq-answer" v-if="activeFaq === index">
              {{ faq.answer }}
            </div>
          </div>
        </div>
      </section>
    </section>

    <!-- CONTACT US SECTION -->
    <section class="contact-section">
      <h2 class="contact-title">Contact Us</h2>
      <div class="contact-underline"></div>

      <div class="contact-grid">
        <!-- Location -->
        <div class="contact-card">
          <div class="card-header">📍 Location</div>
          <div class="card-body">
            <iframe
              src="https://www.google.com/maps?q=Central%20Building%20Pune&output=embed"
              loading="lazy"
            ></iframe>
          </div>
        </div>

        <!-- Head Office -->
        <div class="contact-card">
          <div class="card-header">📍 Head Office</div>
          <div class="card-body info">
            <p>
              <strong>Address</strong><br />
              Central Building,<br />
              Ground Floor,<br />
              Pune 411001
            </p>

            <p>
              <strong>Email</strong><br />
              dirtpvd.pune@maharashtra.gov.in
            </p>

            <p>
              <strong>Phone</strong><br />
              020-26122076
            </p>
          </div>
        </div>

        <!-- Other Details -->
        <div class="contact-card">
          <div class="card-header">📞 Other Details</div>
          <div class="card-body info">
            <p>
              <strong>Telephone Directory</strong><br />
              Available on Request
            </p>

            <p>
              <strong>Office Hours</strong><br />
              9:45 AM to 6:15 PM
            </p>

            <p>
              <strong>Weekly Off</strong><br />
              Saturday and Sunday
            </p>

            <p>
              <strong>List of Public Holidays</strong><br />
              <a href="#">Download</a>
            </p>
          </div>
        </div>
      </div>
    </section>
    <!-- DIRECTORY SECTION -->
    <section class="directory-section">
      <h2 class="directory-title">Directory of Officials</h2>

      <div class="directory-underline"></div>

      <div class="directory-card">
        <table class="directory-table">
          <thead>
            <tr>
              <th>Sr. No.</th>
              <th>Officer Name</th>
              <th>Division</th>
              <th>Department</th>
              <th>Phone No.</th>
              <th>Email ID</th>
            </tr>
          </thead>

          <tbody>
            <tr v-for="(officer, index) in officials" :key="index">
              <td>{{ index + 1 }}</td>
              <td>{{ officer.name }}</td>
              <td>{{ officer.division }}</td>
              <td>{{ officer.department }}</td>
              <td>{{ officer.phone }}</td>
              <td>{{ officer.email }}</td>
            </tr>
          </tbody>
        </table>
      </div>
    </section>
    <footer class="footer">
      <div class="footer-container">
        <!-- Column 1 -->
        <div class="footer-col brand">
          <img src="@/assets/tpv-logo.png" alt="TPVD Logo" class="logo" />
          <h3>Town Planning and Valuation<br />Department</h3>
        </div>

        <!-- Column 2 -->
        <div class="footer-col">
          <h4>Follow us on</h4>
          <ul>
            <li><a href="#">Facebook</a></li>
            <li><a href="#">Twitter</a></li>
            <li><a href="#">Youtube</a></li>
            <li><a href="#">Instagram</a></li>
          </ul>
        </div>

        <!-- Column 3 -->
        <div class="footer-col">
          <h4>Quick Links</h4>
          <ul>
            <li><a href="#">Zone Certificate Application</a></li>
            <li><a href="#">Part Plan Application</a></li>
            <li><a href="#">Aaple Sarkar</a></li>
            <li><a href="#">User Manual / Help</a></li>
            <li><a href="#">Feedback / Suggestions</a></li>
            <li><a href="#">RTS - Right to Services</a></li>
            <li><a href="#">Government of Maharashtra</a></li>
            <li><a href="#">Town Planning & Valuation Department</a></li>
          </ul>
        </div>

        <!-- Column 4 -->
        <div class="footer-col">
          <h4>Legal</h4>
          <ul>
            <li><a href="#">Timeline GR</a></li>
            <li>
              <a href="#">Website Content Contribution, Moderation & Approval Policy (CMAP)</a>
            </li>
            <li><a href="#">Content Archival (CAP) Policy</a></li>
            <li><a href="#">Charges GR</a></li>
            <li><a href="#">Hyperlink Policies</a></li>
            <li><a href="#">Privacy Policies</a></li>
            <li><a href="#">Terms & Conditions</a></li>
            <li><a href="#">Website Monitoring Plan</a></li>
            <li><a href="#">Disclaimer</a></li>
          </ul>
        </div>

        <!-- Column 5 -->
        <div class="footer-col">
          <h4>Contact Us</h4>
          <ul>
            <li><a href="#">Contact Us</a></li>
            <li><a href="#">Feedback</a></li>
            <li><a href="#">Enquiry</a></li>
          </ul>
        </div>
      </div>

      <!-- Bottom bar -->
      <div class="footer-bottom">
        © 2025 Town Planning and Valuation Department. All rights reserved.
      </div>
    </footer>
  </div>
  <DashboardPage v-else :user="user" @logout="handleLogout" />
  <ApplicantLoginDialog ref="loginDialog" @login-success="handleLogin" />
</template>

<script setup>
import { ref } from 'vue'
import ApplicantLoginDialog from '@/views/ApplicantLoginDialog.vue'
import DashboardPage from '@/views/DashboardPage.vue'
const activeFaq = ref(null)
const loginDialog = ref(null)
const isLoggedIn = ref(false)
const user = ref(null)

const handleLogin = (payload) => {
  user.value = payload
  isLoggedIn.value = true
}
const openLogin = () => {
  loginDialog.value.open()
}
const faqs = ref([
  {
    question: 'What is a Part Plan?',
    answer:
      'A Part Plan is a certified plan issued by the Town Planning Department showing the exact location and boundaries of a specific land parcel.',
  },
  {
    question: 'What is a Zone Certificate?',
    answer:
      'A Zone Certificate specifies the zoning classification of land as per the Development Plan.',
  },
  {
    question: 'For what purpose is the Part Plan and Zone Certificate required?',
    answer:
      'These documents are required for construction permissions, land development, and legal verification.',
  },
  {
    question: 'What documents are required while applying for Part Plan and Zone Certificate?',
    answer:
      'Ownership proof, identity proof, land details, and relevant supporting documents are required.',
  },
  {
    question: 'How can an applicant apply for a Part Plan and Zone Certificate in Maharashtra?',
    answer:
      'Applicants can apply online through this portal by registering and submitting the required documents.',
  },
  {
    question: 'How much time does it take to receive the Part Plan and Zone Certificate?',
    answer: 'On average, the process takes 7–10 working days depending on verification.',
  },
])
const officials = ref([
  {
    name: 'Shri. Jitendra Bhople',
    division: 'Head Office',
    department: 'Director, Town Planning, Maharashtra State, Pune',
    phone: '020-26122076',
    email: 'dirtpvd.pune@maharashtra.gov.in',
  },
  {
    name: 'Mr. Owais Ejaz Momin',
    division: 'Amravati',
    department: 'Joint Director, Town Planning, Amravati',
    phone: '0721-2570226',
    email: 'jdtpdn_amravati@rediffmail.com',
  },
  {
    name: 'Mr. Navnath Bhausaheb Nagargoje',
    division: 'Chatrapati Sambhaji Nagar',
    department: 'Joint Director, Town Planning, Chatrapati Sambhaji Nagar Division',
    phone: '0240-2334354',
    email: 'jdtpdn_abad@rediffmail.com',
  },
  {
    name: 'Mr. Shrikant Marutirao Deshmukh',
    division: 'Kokan',
    department: 'Joint Director, Town Planning, Kokan Division',
    phone: '022-27571569 / 022-27572271',
    email: 'jdtpdn_kokan@rediffmail.com',
  },
  {
    name: 'Mr. Vijay Babarav Shende',
    division: 'Nagpur',
    department: 'Joint Director, Town Planning, Nagpur Division',
    phone: '0712-2565020',
    email: 'jdtpdn_nagpur@rediffmail.com',
  },
  {
    name: 'Mr. Akash Tikaram Bagul',
    division: 'Nashik',
    department: 'Joint Director, Town Planning, Nashik Division',
    phone: '0253-2462305',
    email: 'jdtpdn_nashik@rediffmail.com',
  },
  {
    name: 'Mr. Rajendra Mahadev Pawar',
    division: 'Pune',
    department: 'Joint Director, Town Planning, Pune Division',
    phone: '020-26125922',
    email: 'jdtpdn_pune@rediffmail.com',
  },
])
function toggleFaq(index) {
  activeFaq.value = activeFaq.value === index ? null : index
}
const handleLogout = () => {
  isLoggedIn.value = false
}
</script>

<style scoped>
.footer {
  background: linear-gradient(180deg, #062b4f, #031c35);
  color: #ffffff;
  padding: 60px 0 0;
  margin-top: 80px;
}

.footer-container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 24px;
  display: grid;
  grid-template-columns: 1.3fr 1fr 1.5fr 1.8fr 1fr;
  gap: 40px;
}

.footer-col h4 {
  color: #ffd200;
  font-size: 15px;
  margin-bottom: 14px;
  position: relative;
}

.footer-col h4::after {
  content: '';
  display: block;
  width: 50px;
  height: 2px;
  background: rgba(255, 210, 0, 0.5);
  margin-top: 6px;
}

.footer-col ul {
  list-style: none;
  padding: 0;
  margin: 0;
}

.footer-col ul li {
  margin-bottom: 10px;
}

.footer-col ul li a {
  color: #ffffff;
  text-decoration: none;
  font-size: 14px;
  opacity: 0.85;
}

.footer-col ul li a:hover {
  opacity: 1;
  text-decoration: underline;
}

.brand .logo {
  width: 80px;
  margin-bottom: 16px;
}

.brand h3 {
  color: #ffd200;
  font-size: 18px;
  line-height: 1.4;
}

.footer-bottom {
  margin-top: 40px;
  border-top: 1px solid rgba(255, 255, 255, 0.15);
  text-align: center;
  padding: 16px;
  font-size: 13px;
  opacity: 0.8;
}
/* ---------- DIRECTORY SECTION ---------- */
.directory-section {
  background: #ffffff;
  padding: 80px 40px 90px;
}

.directory-title {
  text-align: center;
  font-size: 30px;
  font-weight: 600;
  color: #1b2f8a;
}

.directory-underline {
  width: 70px;
  height: 3px;
  background: #1b2f8a;
  margin: 10px auto 40px;
  border-radius: 2px;
}

/* Card */
.directory-card {
  max-width: 1200px;
  margin: auto;
  background: #fff;
  border-radius: 10px;
  box-shadow: 0 10px 28px rgba(0, 0, 0, 0.08);
  overflow-x: auto;
}

/* Table */
.directory-table {
  width: 100%;
  border-collapse: collapse;
  font-size: 14px;
}

.directory-table thead {
  background: linear-gradient(135deg, #1b2f8a, #2f46c5);
  color: #ffffff;
}

.directory-table th,
.directory-table td {
  padding: 14px 16px;
  text-align: left;
}

.directory-table th {
  font-weight: 600;
  font-size: 14px;
}

.directory-table tbody tr {
  border-bottom: 1px solid #e9ecef;
}

.directory-table tbody tr:hover {
  background: #f8f9fb;
}

.directory-table td {
  color: #333;
}

/* Responsive */
@media (max-width: 768px) {
  .directory-section {
    padding: 60px 16px;
  }
}

/* ---------- CONTACT SECTION ---------- */
.contact-section {
  background: #f5f7fb;
  padding: 80px 40px 100px;
}

.contact-title {
  text-align: center;
  font-size: 30px;
  font-weight: 600;
  color: #1b2f8a;
}

.contact-underline {
  width: 60px;
  height: 3px;
  background: #1b2f8a;
  margin: 10px auto 50px;
  border-radius: 2px;
}

/* Grid */
.contact-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 30px;
  max-width: 1200px;
  margin: auto;
}

/* Card */
.contact-card {
  background: #ffffff;
  border-radius: 10px;
  overflow: hidden;
  box-shadow: 0 10px 28px rgba(0, 0, 0, 0.08);
}

/* Header */
.card-header {
  background: linear-gradient(135deg, #1b2f8a, #2f46c5);
  color: #fff;
  padding: 14px 18px;
  font-weight: 600;
  font-size: 15px;
}

/* Body */
.card-body {
  padding: 18px;
  font-size: 14px;
  color: #333;
}

/* Info text */
.card-body.info p {
  margin-bottom: 16px;
  line-height: 1.6;
}

.card-body a {
  color: #1b2f8a;
  font-weight: 500;
  text-decoration: none;
}

/* Map */
.card-body iframe {
  width: 100%;
  height: 250px;
  border: none;
  border-radius: 6px;
}

/* Responsive */
@media (max-width: 992px) {
  .contact-grid {
    grid-template-columns: 1fr;
  }
}
.faq-section {
  background: #ffffff;
  padding: 70px 20px 90px;
}

.faq-section h2 {
  text-align: center;
  font-size: 28px;
  font-weight: 600;
  margin-bottom: 8px;
}

.faq-subtitle {
  text-align: center;
  color: #6c757d;
  font-size: 14px;
  margin-bottom: 40px;
}

/* FAQ List */
.faq-list {
  max-width: 900px;
  margin: auto;
}

/* FAQ Item */
.faq-item {
  border: 1px solid #e6e9ef;
  border-radius: 6px;
  margin-bottom: 14px;
  overflow: hidden;
}

/* Question */
.faq-question {
  padding: 18px 20px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  cursor: pointer;
  font-size: 15px;
  font-weight: 500;
  background: #fff;
}

.faq-question:hover {
  background: #f8f9fb;
}

/* Icon */
.icon {
  font-size: 20px;
  color: #0b5ed7;
  font-weight: 600;
}

/* Answer */
.faq-answer {
  padding: 16px 20px 20px;
  font-size: 14px;
  color: #555;
  background: #fafbfe;
  line-height: 1.6;
}
/* ---------- REACH SECTION ---------- */
.reach-section {
  padding: 20px 60px 60px;
  background: #f5f7fb;
}

/* Filters */
.filters {
  display: flex;
  justify-content: center;
  gap: 16px;
  margin-bottom: 40px;
}

.filters select {
  padding: 10px 14px;
  border-radius: 6px;
  border: 1px solid #dcdfe6;
  background: white;
  font-size: 14px;
  min-width: 180px;
}

/* Stats Grid */
.stats-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 24px;
  max-width: 900px;
  margin: auto;
}

.stat-card {
  background: white;
  padding: 26px 20px;
  text-align: center;
  border-radius: 8px;
  box-shadow: 0 6px 18px rgba(0, 0, 0, 0.06);
}

.stat-card h2 {
  color: #0b5ed7;
  font-size: 28px;
  font-weight: 600;
  margin-bottom: 6px;
}

.stat-card p {
  font-size: 14px;
  color: #6c757d;
}

/* ---------- ROOT ---------- */
.page {
  font-family: 'Poppins', sans-serif;
  background: #f5f7fb;
  color: #1f2d3d;
}

/* ---------- HEADER ---------- */
.top-header {
  background: linear-gradient(135deg, #1b4f9c, #0b6cc4);
  color: white;
  padding: 18px 40px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.header-left {
  display: flex;
  gap: 16px;
}

.emblem {
  height: 58px;
}

.header-left h1 {
  font-size: 20px;
  font-weight: 600;
  margin: 0;
}

.header-left p {
  margin: 2px 0;
  font-size: 14px;
}

.header-left small {
  font-size: 12px;
  opacity: 0.9;
}

/* ---------- BUTTONS ---------- */
.btn {
  padding: 10px 18px;
  font-size: 14px;
  font-weight: 500;
  border-radius: 4px;
  cursor: pointer;
  border: none;
}

.btn-yellow {
  background: #f9c400;
  color: #003366;
}

.btn-outline {
  background: transparent;
  border: 1px solid #fff;
  color: white;
  margin-left: 10px;
}

.btn-primary {
  background: #0b5ed7;
  color: white;
  width: 260px;
}

.btn-outline-primary {
  background: white;
  border: 1px solid #0b5ed7;
  color: #0b5ed7;
  width: 260px;
}

/* ---------- NAV ---------- */
.nav {
  background: #0a3d78;
  padding: 10px 40px;
  display: flex;
  gap: 28px;
}

.nav a {
  color: white;
  font-size: 13px;
  text-decoration: none;
  opacity: 0.85;
}

.nav a.active {
  border-bottom: 3px solid #f9c400;
  padding-bottom: 6px;
  opacity: 1;
}

/* ---------- MAIN ---------- */
.main {
  display: grid;
  grid-template-columns: 1fr 1.2fr;
  gap: 40px;
  padding: 50px 60px;
}

.card {
  background: white;
  border-radius: 8px;
  padding: 30px;
  box-shadow: 0 8px 24px rgba(0, 0, 0, 0.08);
}

.map-card img {
  width: 100%;
}

/* ---------- ACTION CARD ---------- */
.action-card h2 {
  font-size: 26px;
  margin-bottom: 10px;
}

.action-card p {
  color: #6c757d;
  margin-bottom: 30px;
}

.actions {
  display: flex;
  gap: 20px;
}

/* ---------- SECTION ---------- */
.section-title {
  text-align: center;
  margin: 40px 0;
  font-weight: 600;
}
</style>
