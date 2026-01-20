# Student Attendance Management System (SAMS)

![Laravel](https://img.shields.io/badge/Laravel-10.x-FF2D20?style=for-the-badge&logo=laravel)
![PHP](https://img.shields.io/badge/PHP-8.1+-777BB4?style=for-the-badge&logo=php)
![MySQL](https://img.shields.io/badge/MySQL-8.0-4479A1?style=for-the-badge&logo=mysql)
![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-3.3-06B6D4?style=for-the-badge&logo=tailwindcss)

A comprehensive web-based Student Attendance Management System built with Laravel that streamlines attendance tracking for educational institutions.

## ✨ Features

### 👨‍💼 **Admin Panel**
- **Dashboard Analytics**: Real-time statistics and insights
- **Class Management**: Create, edit, and delete classes/sections
- **Teacher Management**: Add and manage teaching staff
- **Student Management**: Enroll and manage student records
- **Attendance Overview**: View all attendance records
- **Audit Logs**: Track all system activities

### 👩‍🏫 **Teacher Panel**
- **Attendance Marking**: Mark student attendance for assigned classes
- **Dashboard**: View class statistics and recent attendance
- **Class Management**: View assigned class details
- **Student Management**: View student lists

### 🎓 **Student Panel**
- **Attendance History**: View personal attendance records
- **Dashboard**: View attendance statistics and trends
- **Profile Management**: Update personal information

### 🔐 **Security Features**
- Role-based access control (Admin, Teacher, Student)
- Secure authentication system
- Password protection and encryption
- Session management
- Audit logging for all critical actions

## 🚀 Quick Start

### Prerequisites
- PHP 8.1 or higher
- Composer
- MySQL 5.7 or higher
- Node.js & NPM

### Installation

1. **Clone the repository**
```bash
git clone https://github.com/yourusername/sams.git
cd sams
```

2. **Install PHP dependencies**
```bash
composer install
```

3. **Install JavaScript dependencies**
```bash
npm install
npm run build
```

4. **Configure environment**
```bash
cp .env.example .env
php artisan key:generate
```

5. **Update `.env` file with your database credentials**
```env
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=anta_ams_db
DB_USERNAME=root
DB_PASSWORD=
```

6. **Run migrations and seeders**
```bash
php artisan migrate --seed
```

7. **Start the development server**
```bash
php artisan serve
```

8. **Access the application**
   - Open `http://localhost:8000` in your browser
   - Login with default credentials:
     - **Admin**: admin@attendance.com / password
     - **Teacher**: teacher@example.com / password
     - **Student**: student@example.com / password

## 📁 Project Structure

```
sams/
├── app/
│   ├── Http/
│   │   ├── Controllers/
│   │   │   ├── Admin/          # Admin controllers
│   │   │   ├── Teacher/        # Teacher controllers
│   │   │   ├── Student/        # Student controllers
│   │   │   └── Auth/          # Authentication controllers
│   │   └── Requests/          # Form request validation
│   ├── Models/                # Eloquent models
│   ├── Policies/              # Authorization policies
│   ├── Observers/             # Model observers
│   └── Providers/             # Service providers
├── resources/
│   ├── views/
│   │   ├── layouts/           # Base layouts
│   │   ├── admin/             # Admin views
│   │   ├── teacher/           # Teacher views
│   │   ├── student/           # Student views
│   │   ├── auth/              # Authentication views
│   │   └── profile/           # Profile views
│   └── js/                    # JavaScript files
├── database/
│   ├── migrations/            # Database migrations
│   └── seeders/              # Database seeders
├── routes/
│   ├── web.php               # Web routes
│   └── auth.php              # Authentication routes
└── public/                   # Public assets
```

## 🔧 Configuration

### Database Setup
```sql
-- Create database
CREATE DATABASE sams_db CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
```

### Environment Variables
Key environment variables to configure:

```env
APP_NAME="Student Attendance Management System"
APP_ENV=local
APP_KEY=
APP_DEBUG=true
APP_URL=http://localhost:8000

DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=anta_ams_db
DB_USERNAME=root
DB_PASSWORD=

MAIL_MAILER=smtp
MAIL_HOST=smtp.mailtrap.io
MAIL_PORT=2525
MAIL_USERNAME=
MAIL_PASSWORD=
MAIL_ENCRYPTION=tls
MAIL_FROM_ADDRESS="noreply@sams.com"
MAIL_FROM_NAME="${APP_NAME}"
```

## 👥 Default Users

After running seeders, you'll have these default users:

| Role | Email | Password | Access |
|------|-------|----------|---------|
| Admin | admin@attendance.com | password | Full system access |
| Teacher | teacher@example.com | password | Teacher dashboard, attendance marking |
| Student | student@example.com | password | Student dashboard, attendance view |

## 📊 Database Schema

### Core Tables
- **users**: User accounts and authentication
- **roles**: User roles (Admin, Teacher, Student)
- **role_user**: User-role relationships
- **classes**: Class/section information
- **students**: Student profiles
- **teachers**: Teacher profiles
- **attendances**: Attendance records
- **audit_logs**: System audit trail

### Relationships
- One User has One Role
- One Class has Many Students
- One Teacher belongs to One Class
- One Student has Many Attendance records
- One Teacher creates Many Attendance records

## 🛠️ Development

### Running Tests
```bash
php artisan test
```

### Code Style
```bash
# Run Laravel Pint
composer pint
```

### Database Commands
```bash
# Create migration
php artisan make:migration create_table_name

# Run migrations
php artisan migrate

# Rollback migrations
php artisan migrate:rollback

# Seed database
php artisan db:seed
```

### Creating Components
```bash
# Create controller
php artisan make:controller Admin/ClassController --resource

# Create model with migration
php artisan make:model Student -m

# Create request validation
php artisan make:request StoreStudentRequest
```

## 📈 Usage Guide

### For Administrators
1. **Manage Classes**: Navigate to Admin → Classes to add/edit classes
2. **Add Teachers**: Admin → Teachers → Add Teacher
3. **Enroll Students**: Admin → Students → Add Student
4. **View Reports**: Admin → Attendance for comprehensive reports

### For Teachers
1. **Mark Attendance**: Teacher → Mark Attendance
2. **View Class**: Teacher Dashboard shows assigned class
3. **Check History**: View previously marked attendance

### For Students
1. **View Attendance**: Student → Attendance History
2. **Check Stats**: Dashboard shows attendance percentage
3. **Update Profile**: Profile Settings

## 🚀 Deployment

### Production Setup
1. Update `.env` for production:
```env
APP_ENV=production
APP_DEBUG=false
APP_URL=https://yourdomain.com
```

2. Optimize application:
```bash
php artisan config:cache
php artisan route:cache
php artisan view:cache
```

3. Set up queue workers (if using):
```bash
php artisan queue:work
```

### Server Requirements
- Web server (Apache/Nginx)
- PHP 8.1+ with extensions:
  - BCMath
  - Ctype
  - Fileinfo
  - JSON
  - Mbstring
  - OpenSSL
  - PDO
  - Tokenizer
  - XML
- MySQL 5.7+ or MariaDB 10.2+
- Composer
- Node.js & NPM

## 🔒 Security Considerations

- All passwords are encrypted using bcrypt
- CSRF protection enabled
- XSS protection
- SQL injection prevention through Eloquent ORM
- Session security with encryption
- Rate limiting on authentication endpoints
- Audit logging for sensitive operations

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

### Development Workflow
```bash
# Create new feature
git checkout -b feature/new-feature

# Make changes and commit
git add .
git commit -m "Add new feature"

# Push to remote
git push origin feature/new-feature
```

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- [Laravel](https://laravel.com) - The PHP Framework
- [Tailwind CSS](https://tailwindcss.com) - Utility-first CSS framework
- [Font Awesome](https://fontawesome.com) - Icons
- [Chart.js](https://chartjs.org) - Charts and graphs

## 📞 Support

For support, email support@sams.com or create an issue in the GitHub repository.

## 🔗 Links

- **Live Demo**: [Coming Soon]
- **Documentation**: [Coming Soon]
- **Issue Tracker**: [GitHub Issues](https://github.com/yourusername/sams/issues)
- **Releases**: [GitHub Releases](https://github.com/yourusername/sams/releases)

---

<div align="center">
Made with ❤️ using Laravel & Tailwind CSS
</div>

## 🏗️ Roadmap

### Phase 1 (Current)
- [x] Basic attendance marking
- [x] Role-based authentication
- [x] Admin, Teacher, Student dashboards
- [x] Basic reporting

### Phase 2 (Upcoming)
- [ ] Advanced analytics dashboard
- [ ] Bulk student import/export
- [ ] SMS/Email notifications
- [ ] Mobile-responsive improvements
- [ ] API development

### Phase 3 (Future)
- [ ] Mobile app integration
- [ ] Biometric attendance
- [ ] Parent portal
- [ ] Advanced reporting
- [ ] Multi-language support

## 🐛 Troubleshooting

### Common Issues

1. **"Class not found" errors**
```bash
composer dump-autoload
```

2. **Permission issues on storage**
```bash
chmod -R 775 storage bootstrap/cache
```

3. **Migration errors**
```bash
php artisan migrate:refresh --seed
```

4. **Asset compilation issues**
```bash
npm run dev
# or for production
npm run build
```

### Debug Mode
For development, enable debug mode in `.env`:
```env
APP_DEBUG=true
```

For production, always set:
```env
APP_DEBUG=false
```

## 📊 Performance Optimization

1. **Enable Caching**
```bash
php artisan config:cache
php artisan route:cache
php artisan view:cache
```

2. **Optimize Autoloader**
```bash
composer dump-autoload -o
```

3. **Database Optimization**
- Add indexes to frequently queried columns
- Use database transactions for bulk operations
- Implement pagination for large datasets

## 🎯 Best Practices

### Code Standards
- Follow PSR-12 coding standards
- Use meaningful variable and function names
- Add comments for complex logic
- Write unit tests for critical functionality

### Security Practices
- Never commit `.env` files
- Use prepared statements for database queries
- Validate and sanitize all user inputs
- Implement proper error handling
- Regular security updates

### Database Practices
- Use migrations for schema changes
- Implement database transactions
- Add foreign key constraints
- Regular database backups

## 🔄 Update Instructions

To update to the latest version:

1. **Backup your data**
```bash
php artisan backup:run
```

2. **Pull latest changes**
```bash
git pull origin main
```

3. **Update dependencies**
```bash
composer install
npm install && npm run build
```

4. **Run migrations**
```bash
php artisan migrate
```

5. **Clear caches**
```bash
php artisan optimize:clear
```

## 📝 Changelog

### v1.0.0 (Current)
- Initial release
- Basic attendance management
- Three-role system
- Dashboard for each role
- Basic reporting

### v1.1.0 (Planned)
- Enhanced reporting
- Bulk operations
- Export functionality
- Improved UI/UX

---

**Note**: This is a production-ready system designed for educational institutions. Always test in a staging environment before deploying to production.
