# EPSight Metrics

> Sistem Inspeksi Dimensi Quality Control untuk PT. Indonesia Epson Industry

Sistem manajemen inspeksi dimensi berbasis web yang terintegrasi dengan kamera untuk inspeksi real-time, analisis defek, dan pelaporan komprehensif dengan dukungan multi-role dan audit trail lengkap.

## 🎯 Fitur Utama

- **Inspeksi Real-time** - Inspeksi dimensi langsung dengan kamera dan notifikasi NG otomatis
- **Multi-Role Access** - Operator QC, Engineer, Quality Manager, Auditor, dan Admin
- **Dashboard Analytics** - Visualisasi tren NG rate, analisis defek, dan throughput
- **Audit Trail** - Log aktivitas lengkap dan verifikasi integritas data
- **Traceability** - Pelacakan batch, part, vendor, dan operator
- **Export & Reporting** - Export CSV/PDF untuk laporan inspeksi
- **Bilingual** - Dukungan Bahasa Indonesia dan English
- **Real-time Notifications** - SSE untuk notifikasi NG langsung ke manager

## 🏗️ Arsitektur

```
epsight-metrics/
├── epsight-metric-frontend/    # SvelteKit Frontend
└── epsight-metrics-backend/          # Express.js Backend + Prisma ORM
```

### Tech Stack

**Frontend:**
- SvelteKit 2.x
- Vite
- jsPDF & jsPDF-AutoTable

**Backend:**
- Node.js + Express.js
- Prisma ORM
- PostgreSQL
- JWT Authentication
- Helmet + CORS
- Rate Limiting

## 🚀 Quick Start

### Prerequisites

- Node.js 18+
- PostgreSQL 14+
- npm atau pnpm

### Backend Setup

```bash
cd epsight-metrics-backend

# Install dependencies
npm install

# Setup environment
cp .env.example .env
# Edit .env dengan konfigurasi database Anda

# Run migrations
npm run db:migrate

# Seed database
npm run db:seed

# Start server
npm run dev
```

Server akan berjalan di `http://localhost:3000`

### Frontend Setup

```bash
cd epsight-metric-frontend

# Install dependencies
npm install

# Start dev server
npm run dev
```

Frontend akan berjalan di `http://localhost:5173`

## 📋 Environment Variables

### Backend (.env)

```env
DATABASE_URL="postgresql://user:password@localhost:5432/epsight_db"
JWT_SECRET="your-secret-key-here"
PORT=3000
NODE_ENV=development
CORS_ORIGIN=*
RATE_LIMIT_WINDOW_MS=60000
RATE_LIMIT_MAX_REQUESTS=100
```

## 🗄️ Database Schema

### Models Utama

- **User** - Manajemen pengguna dengan role-based access
- **Part** - Master data part dengan vendor
- **Session** - Sesi inspeksi operator
- **InspectionBatch** - Batch inspeksi per sesi
- **Inspection** - Log inspeksi individual dengan dimensi
- **ActivityLog** - Audit trail aktivitas sistem

### Roles

- `OPERATOR_QC` - Melakukan inspeksi
- `ENGINEER` - Analisis teknis
- `QUALITY_MANAGER` - Dashboard dan reporting
- `AUDIT` - Audit dan verifikasi data
- `ADMIN` - Manajemen sistem dan user

## 🔌 API Endpoints

### Authentication
- `POST /api/auth/login` - Login
- `POST /api/auth/logout` - Logout

### Operator
- `GET /api/operator/session` - Get/create session
- `POST /api/operator/inspect` - Submit inspection
- `GET /api/operator/history` - Session history

### QC Manager
- `GET /api/qcmanager/dashboard` - Dashboard stats
- `GET /api/qcmanager/trends` - NG rate trends
- `GET /api/qcmanager/defects` - Defect analysis
- `GET /api/qcmanager/history` - Inspection history
- `GET /api/qcmanager/export/csv` - Export CSV
- `GET /api/qcmanager/export/pdf` - Export PDF

### Admin
- `GET /api/admin/users` - List users
- `POST /api/admin/users` - Create user
- `PUT /api/admin/users/:id` - Update user
- `DELETE /api/admin/users/:id` - Delete user
- `GET /api/admin/logs` - Activity logs

### Audit
- `GET /api/audit/inspections` - Inspection logs
- `GET /api/audit/traceability` - Traceability data
- `GET /api/audit/integrity` - Data integrity check

### Notifications
- `GET /api/notifications/stream` - SSE stream untuk NG alerts

## 🔒 Security

- JWT-based authentication
- Helmet.js untuk HTTP headers security
- Rate limiting per endpoint
- CORS configuration
- Password hashing dengan bcrypt
- Role-based access control (RBAC)
- Input validation dengan express-validator

## 📊 Features by Role

### Operator QC
- Live camera inspection
- Submit inspection results
- View session history
- NG alert handling

### Quality Manager
- Real-time dashboard
- NG rate trends
- Defect pattern analysis
- Vendor performance
- Export reports (CSV/PDF)
- Real-time NG notifications

### Auditor
- Inspection logs dengan advanced filter
- Traceability verification
- Data integrity check
- Audit reports

### Admin
- User management
- Activity logs
- System configuration
- User activation/deactivation

## 🌐 Internationalization

Sistem mendukung 2 bahasa:
- 🇮🇩 Bahasa Indonesia (default)
- 🇬🇧 English

Toggle bahasa tersedia di header aplikasi.

## 📦 Scripts

### Backend
```bash
npm run dev          # Development server
npm run start        # Production server
npm run db:migrate   # Run Prisma migrations
npm run db:seed      # Seed database
npm run db:studio    # Open Prisma Studio
```

### Frontend
```bash
npm run dev          # Development server
npm run build        # Production build
npm run preview      # Preview production build
```

## 🤝 Contributing

1. Fork repository
2. Create feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to branch (`git push origin feature/AmazingFeature`)
5. Open Pull Request

## 📝 License

Proprietary - PT. Indonesia Epson Industry

## 👥 Team

Developed for PT. Indonesia Epson Industry Quality Control Department

---

**Version:** 2.0  
**Last Updated:** 2025
